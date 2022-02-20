# Jenkins

## 1. Create pipeline

### 1.1 Build maven project
    tools {
        maven 'Maven3'
        jdk 'JDK8'
    }
    stage('Build') {
        steps {
              sh 'mvn clean install deploy -U'
        }
    }

With :
Maven3 : name of maven installation
JDK8 : name of jdk installation

### 1.2 Run sonar analysis
    environment {
        SONAR_URL = 'http://domain.com:9000'
    }

And :

    stage('Sonar Quality Analysis') {
            steps {
                    script{
                        scannerHome = tool name:'Sonarqube 3.2', type:'hudson.plugins.sonar.SonarRunnerInstallation';
                    }
                    withSonarQubeEnv('sonarqube') {
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.host.url=${SONAR_URL}"
                    }
            }
    }

Sonarqube 3.2 : is the name of installation of sonarqube in global config of jenkins 

### 1.3 Get git changes from jenkins pipeline :

    @NonCPS
    def getChangeString() {
        MAX_MSG_LEN = 100
        def changeString = ""
    
        echo "Gathering SCM changes"
        def changeLogSets = currentBuild.changeSets
        for (int i = 0; i < changeLogSets.size(); i++) {
            def entries = changeLogSets[i].items
            for (int j = 0; j < entries.length; j++) {
                def entry = entries[j]
                truncated_msg = entry.msg.take(MAX_MSG_LEN)
                changeString += " - ${truncated_msg} [${entry.author}]\n"
            }
        }
    
        if (!changeString) {
            changeString = " - No new changes"
        }
        return changeString
    }


### 1.4 Send changes in email
    environment {
        EMAIL_RECIPIENTS = 'mail1@gmail.com,mail2@gmail.Com'
    }

And : 

    def sendEmail(status) {
    mail(
        to: "$EMAIL_RECIPIENTS",
        subject: "Build $BUILD_NUMBER - " + status + " (${currentBuild.fullDisplayName})",
        body: "Changes:\n " + getChangeString() + "\n\n Check console output at: $BUILD_URL/console" + "\n")
    }

### 1.5 Send email all the time after stages

if you want to always send email
you have to add this code after stages section :

    post {
        success {
            sendEmail("Successful");
        }
        unstable {
            sendEmail("Unstable");
        }
        failure {
            sendEmail("Failed");
        }
    }

### 1.6 Add trigger to check new git commits
Five stars : to check every second if there is same changes in scm

    triggers {
        pollSCM('* * * * *')
    }

### 1.7 Deploy application
Example of parallel stages to deploy develop in lab and master in production when build SUCCESS

        stage('Deploy') {
            parallel {
                stage('Lab') {
                     when {
                        allOf { expression{env.BRANCH_NAME == 'develop'};
                                expression{currentBuild.currentResult == "SUCCESS"}
                            }
                        }
                    steps {
							echo "Start deploying ${env.BRANCH_NAME} in Lab"
                            deploy()
                    }
                }
                stage('Production') {
	                 when {
	                    allOf { expression{env.BRANCH_NAME == 'master'};
	                            expression{currentBuild.currentResult == "SUCCESS"}
	                        }
	                    }
	                    steps {
				             echo "Start deploying ${env.BRANCH_NAME} in production"
                             deploy()
	                    }
                }
            }
        }
#### 1.7.1 deploy in external tomcat with ssh
// TODO implement deploy method

### 1.7.2 deploy in kubernetes
// TODO implement deploy method


## 3. Jenkins Set Environment Variables

| Environment Variable | Description                                                                                               |
|----------------------|-----------------------------------------------------------------------------------------------------------|
| BUILD_NUMBER         | The current build number, such as "153"                                                                   |
| BUILD_ID             | The current build id, such as "2005-08-22_23-59-59" (YYYY-MM-DD_hh-mm-ss, defunct since version 1.597)    |
| BUILD_URL            | The URL where the results of this build can be found (e.g. http://buildserver/jenkins/job/MyJobName/666/) |

Reference : [https://wiki.jenkins.io/display/JENKINS/Building+a+software+project](https://wiki.jenkins.io/display/JENKINS/Building+a+software+project)



## 2. Create jenkins library



## Useful jenkins plugins

1. https://plugins.jenkins.io/gitlab-plugin/
2. https://www.jenkins.io/doc/pipeline/steps/pipeline-utility-steps/
3. https://plugins.jenkins.io/kubernetes/

For all plugins : https://plugins.jenkins.io/