# Java

## Java features with examples :

### Java 8
This is Java 8 features :
- Functional interface
- Lambda expressions
- Optional
- Default methods
- Stream API
- forEach Method
- DateTime API
- Default methods
- Static methods in interface : Similar to Default Method in Interface, the static method in an interface can be defined in the interface, but cannot be overridden in Implementation Classes
- Nashorn JavaScript engine
- Method references : is used to refer method of Functional interface, There are following types of method references :
  - Reference to a static method.
  - Reference to an instance method.
  - Reference to a constructor.
- Concurrency API improvements
- Collection API improvements


#### Stream API 
#####  reduce() Method
#####  collect() Method

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
record were introduced to reduce repetitive boilerplate code in data model POJOs

    public record User(int id, String name) { };

This simple declaration will automatically add :
a constructor, getters, equals, hashCode and toString methods for us

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


## Most used Operation Java
### Convert String to int
    Integer.parseInt(str)

Example :
    
    String str = "25";
    try{
        int number = Integer.parseInt(str);
        System.out.println(number);
    }
    catch (NumberFormatException ex){
        ex.printStackTrace();
    }

### Convert String to an Integer 
    Integer.valueOf(str)
    or
    new Integer(Integer.parseInt(s))

### Convert int to String 
    String s = String.valueOf(i) or String s = Integer.toString(i);  

### Convert List to Map
Example : 

    public class User {
        private int id;
        private String name;

    //  constructor/getters/setters
    }
Convert List of User to HashMap with key id and value User object

    public Map<Integer, User> convertListAfterJava8(List<User> users) {
        Map<Integer, User> map = 
                users.stream()
                     .collect(
                        Collectors.toMap(User::getId, Function.identity())
                            );
            return map;
    }

### Convert Map to List

    Map<Integer, String> students = new HashMap<>();
    students.put(132, "imad");
    students.put(563, "Kamal");
    students.put(895, "Ahmed");

    ArrayList<Integer> keyList = new ArrayList<>(students.keySet()); // key list
    ArrayList<String> valueList = new ArrayList<>(students.values()); // value list

Example 2 with object 

    Map<Integer, User> users = new HashMap<>();

    List<String> names = users.values().stream().map(User::name)
        .collect(Collectors.toList());

### Convert List to Set
- Method 1 :
  
        List<Integer> sourceList = Arrays.asList(0, 1, 2, 3, 4, 5);
        Set<Integer> targetSet = new HashSet<>(sourceList);

- Method 2 (Java 10):
  
      List sourceList = Lists.newArrayList(0, 1, 2, 3, 4, 5);
      Set targetSet = Set.copyOf(sourceList);

### Convert Set to List
- Method 1 :
        
        Set<Integer> sourceSet = Sets.newHashSet(0, 1, 2, 3, 4, 5);
        List<Integer> targetList = new ArrayList<>(sourceSet);

- Method 2 :
        
      Set<Integer> sourceSet = Sets.newHashSet(0, 1, 2, 3, 4, 5);
      List<Integer> targetList = List.copyOf(sourceSet);


## Java questions 

### What is the difference between Checked vs Unchecked Exceptions in Java ?
#### - Checked Exception : 
the exceptions that are checked at compile time
- fully checked exceptions : exception where all its child classes are also checked like IOException, and InterruptedException
- partially checked exceptions : some of its child classes are unchecked, like an Exception 
#### - UnChecked Exception : 
These are the exceptions that are not checked at compile time Example : ArithmeticException, ArrayIndexOutOfBoundsException, NullPointerException 
	
	
