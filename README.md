# documentation

## Git
<table>
<thead>
  <tr>
    <th>Command</th>
    <th>Description</th>
  </tr>
<thead>
<tbody>
  <tr>
    <td>git fetch --all --tags --prune</td>
    <td>Fetch remote tags</td>
  </tr>
    <tr>
      <td>git branch -d feature/BRC-1 <br/>
      git push origin --delete feature/BRC-1
      </td>
      <td>Delete branch</td>
    </tr>
  <tr>
    <td>git tag -d TAG_NAME <br/>
        git push --delete origin TAG_NAME 
    </td>
    <td>Delete tag</td>
  </tr>
  <tr>
    <td>git checkout branchA <br/>
        git merge branchB</td>
    <td>Merge branchB to branchA</td>
  </tr>
  <tr>
    <td>git reset HEAD~1</td>
    <td>Revert local commit</td>
  </tr>
  <tr>
    <td>git commit --amend --no-edit  <br/>
        git push -f origin YOUR_BRANCH
    </td>
    <td>commit without  change the last comment :</td>
  </tr>
  <tr>
    <td>git tag -l "v*.*.*-suffix"</td>
    <td>Get tags start with v and terminate with -suffix </td>
  </tr>
</tbody>
</table>

<h3>Delete multiple commits</h3>
Step 1: git checkout YOUR_BRANCH <br/>
Step 2 : git rebase -i develop <br/>
remove 'pick' and add 's' before commit to delete <br/>
Step 3:  echap <br/>
Step 4 ':wq' and then enter <br/>
it ask you to  choose comment to keep : add  # before comment that you don't like to keep <br/> 
Step 5: git push -f origin YOUR_BRANCH <br/> 
## Git Flow

### Release Delivery Steps 
(Example from develop with version 1.0.0-SNAPSHOT) : <br/>
Step 1 : mvn clean install <br/>
Step 2 : git flow release start v1.0.0 (it will create new branch release/v1.0.0 and checkout this branch) <br/>
Step 3 : mvn versions:set -DnewVersion=1.0.0 -DgenerateBackupPoms=false <br/>
Step 4 : mvn clean install <br/>
Step 5 : git add -A <br/>
Step 6 : git commit -a -m "Bump version to 1.0.0" <br/>
Step 7 : git flow release finish v1.0.0 (after this merge release/v1.0.0 to develop you have to add message for tag and it will return to develop) <br/>
Step 8 : git push origin --tags <br/>
Step 9 : mvn versions:set -DnewVersion=1.1.0-SNAPSHOT -DgenerateBackupPoms=false <br/>
Step 10 : git add -A <br/>
Step 11 : git commit -a -m "Bump version to 1.1.0-SNAPSHOT" <br/>
Step 12 : git push origin develop <br/>
Step 13 : git checkout master <br/>
Step 14 : git push origin master <br/>


### Hotfix Delivery Steps 
(Example from master with version : 1.0.0) : <br/> 

Step 1 : git flow hotfix start v1.0.1 <br/>
Step 2 : add resolution <br/>
Step 3 : git add -A <br/>
Step 4 : git commit -a -m "Resolve bug" <br/>
Step 5 : mvn versions:set -DnewVersion=1.0.1 -DgenerateBackupPoms=false <br/>
Step 6 : git add -A <br/>
Step 7 : git commit -a -m "Bump version to 1.0.1" <br/>
Step 8 : git flow hotfix finish v1.0.1 (after this command you will have conflits pom take yours in develop) <br/>
Step 9 : git push origin develop (it will push also tag v1.0.1) <br/>
Step 10 : git push origin master <br/>
Step 11 : git push origin --tags <br/>


## show server logs
<pre>
tail -f -n500 logs/catalina.out
</pre>