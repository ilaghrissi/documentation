# Java

## Java features with examples :

### Java 8

### Java 9 (published September 2017)

### Java 10 (published March 2018)

#### Type inference
**Before**

    List<String> list = List.of("Oracle", "Java", "Mysql");

**After**

    var otherList = List.of("Oracle", "Java", "Mysql");

### Java 11 (published September 2018)

#### Type inference in lambda expression
Type inference for lambda parameters. Java 10 brought vars, but you couldn't use them in parameters of lambda expressions. This is now fixed with Java 11
<br/>
Example :

    var original = List.of("Oracle", "Java", "Mysql");
    original.stream().filter((var s) -> s.contains("X")).forEach(System.out::println);

#### New methods to the String class
Adds a few new methods to the String class: isBlank, lines, strip, stripLeading, stripTrailing, and repeat
<br/>

Example :
    
    String multilineString = "New example \n \n for java \n developers.";
    List<String> lines = multilineString.lines()
    .filter(line -> !line.isBlank())
    .map(String::strip)
    .collect(Collectors.toList());

    assertThat(lines).containsExactly("New example ", "for java ", "developers.");


### Java 12 (published March 2019)

### Java 13 (published September 2019)

### Java 14 (published March 2020)

### Java 15 (published September 2020)

#### 1. Record
The **record** is a new type of class in Java that makes it easy to _create immutable data objects_.
<br/>
A record class without any constructor declarations is automatically given a canonical constructor that assigns all the private fields to the corresponding arguments of the new expression which instantiated the record. For example, the record declared earlier — record Point(int x, int y) { } — is compiled as if it were:

    record Point(int x, int y) {
        // Implicitly declared fields
        private final int x;
        private final int y;
        
        // Other implicit declarations elided ...
    
        // Implicitly declared canonical constructor
        Point(int x, int y) {
            this.x = x;
            this.y = y;
        }
    }

#### 2. Sealed

#### 3. Hidden


#### 4. Pattern Matching Type Checks
**Before**

    if (person instanceof Employee) {
    Employee employee = (Employee) person;
    Date hireDate = employee.getHireDate();
    //...
    }

**After**

    if (person instanceof Employee employee) {
    Date hireDate = employee.getHireDate();
    //…
    }

We can also combine the new binding variable with conditional statements :

    if (person instanceof Employee employee && employee.getYearsOfService() > 5) {
    //...
    }


### Java 16 (published March 2021)

### Java 17 (published September 2021)
