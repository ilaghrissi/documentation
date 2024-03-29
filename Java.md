<!-- TOC -->
* [Java](#java)
  * [Introduction](#introduction)
  * [Java 8 (published March 2014)](#java-8--published-march-2014-)
    * [Functional interface](#functional-interface)
    * [Lambda expressions](#lambda-expressions)
    * [Optional](#optional)
    * [Default methods](#default-methods)
    * [forEach Method](#foreach-method)
    * [DateTime API](#datetime-api)
    * [Default methods](#default-methods-1)
    * [Static methods in interface](#static-methods-in-interface)
    * [Nashorn JavaScript engine](#nashorn-javascript-engine)
    * [Method references](#method-references)
    * [Concurrency API improvements](#concurrency-api-improvements)
    * [Stream API](#stream-api)
      * [Filtering](#filtering)
        * [filter()](#filter--)
        * [distinct()](#distinct--)
      * [Slicing](#slicing)
        * [takeWhile](#takewhile)
        * [dropWhile](#dropwhile)
        * [limit](#limit)
        * [skip](#skip)
      * [Mapping](#mapping)
        * [map](#map)
        * [FlatMap](#flatmap)
      * [Finding and Matching](#finding-and-matching)
        * [allMatch](#allmatch)
        * [noneMatch](#nonematch)
        * [findAny](#findany)
        * [findFirst](#findfirst)
      * [Reducing](#reducing)
          * [Example 1 : Numbers](#example-1--numbers)
          * [Example 2 : String](#example-2--string)
      * [Numeric stream](#numeric-stream)
        * [Mapping to numeric stream](#mapping-to-numeric-stream)
          * [mapToInt()](#maptoint--)
        * [Converting numeric stream to stream of object](#converting-numeric-stream-to-stream-of-object)
        * [default values for OptionalInt](#default-values-for-optionalint)
        * [Numeric range](#numeric-range)
      * [Building streams](#building-streams)
        * [sorted](#sorted)
    * [collecting data](#collecting-data)
      * [collectors](#collectors)
      * [reducing and summarizing](#reducing-and-summarizing)
      * [grouping](#grouping)
      * [partitioning](#partitioning)
      * [collector interface](#collector-interface)
      * [developing your own collector](#developing-your-own-collector)
    * [Collection API improvements](#collection-api-improvements)
      * [Collection factories](#collection-factories)
      * [removeIf](#removeif)
      * [replaceAll](#replaceall)
    * [Java 9 (published September 2017)](#java-9--published-september-2017-)
    * [Java 10 (published March 2018)](#java-10--published-march-2018-)
      * [Type inference](#type-inference)
    * [Java 11 (published September 2018)](#java-11--published-september-2018-)
      * [Type inference in lambda expression](#type-inference-in-lambda-expression)
      * [New methods to the String class](#new-methods-to-the-string-class)
    * [Java 12 (published March 2019)](#java-12--published-march-2019-)
      * [Switch Expressions](#switch-expressions)
    * [Java 13 (published September 2019)](#java-13--published-september-2019-)
    * [Java 14 (published March 2020)](#java-14--published-march-2020-)
    * [Java 15 (published September 2020)](#java-15--published-september-2020-)
      * [1. Record](#1-record)
      * [2. Sealed](#2-sealed)
        * [Sealed Interfaces](#sealed-interfaces)
        * [Sealed classes](#sealed-classes)
        * [Sealed records](#sealed-records)
        * [Reflection support](#reflection-support)
      * [3. Hidden](#3-hidden)
      * [4. Pattern Matching Type Checks](#4-pattern-matching-type-checks)
    * [Java 16 (published March 2021)](#java-16--published-march-2021-)
    * [Java 17 (published September 2021)](#java-17--published-september-2021-)
  * [Most used Operation Java](#most-used-operation-java)
    * [Convert String to int](#convert-string-to-int)
    * [Convert String to an Integer](#convert-string-to-an-integer)
    * [Convert int to String](#convert-int-to-string)
    * [Convert List to Map](#convert-list-to-map)
    * [Convert Map to List](#convert-map-to-list)
    * [Convert List to Set](#convert-list-to-set)
    * [Convert Set to List](#convert-set-to-list)
    * [Java 18 (published March 2022)](#java-18--published-march-2022-)
    * [Java 19 (published September 2022)](#java-19--published-september-2022-)
    * [Java 20 (published March 2023)](#java-20--published-march-2023-)
    * [Java 21 (published September 2023)](#java-21--published-september-2023-)
      * [Interpolation](#interpolation)
      * [pattern matching](#pattern-matching)
      * [pattern matching for switch](#pattern-matching-for-switch)
  * [Java questions](#java-questions)
    * [What is the difference between Checked vs Unchecked Exceptions in Java ?](#what-is-the-difference-between-checked-vs-unchecked-exceptions-in-java-)
      * [- Checked Exception :](#--checked-exception-)
      * [- UnChecked Exception :](#--unchecked-exception-)
<!-- TOC -->


# Java
## Introduction
In this article we will list Java Features by version.
## Java 8 (published March 2014)
This is Java 8 features :
### Functional interface

| Type      | Abstract Method | Argument | Return  | Method  |
|-----------|-----------------|----------|---------|---------|
| Predicate | test (T)        | Yes      | boolean | filter  |
| Function  | apply (T)       | Yes      | R       | map     |
| Consumer  | accept (T)      | Yes      | void    | forEach |
| Supplier  | get()           | No       | T       |         |

### Lambda expressions
### Optional
### Default methods
### forEach Method
### DateTime API
### Default methods
### Static methods in interface 
Similar to Default Method in Interface, the static method in an interface can be defined in the interface, but cannot be overridden in Implementation Classes
### Nashorn JavaScript engine
### Method references 
is used to refer method of Functional interface, There are following types of method references :
  - Reference to a static method.
  - Reference to an instance method.
  - Reference to a constructor.
### Concurrency API improvements



### Stream API 
#### Filtering
##### filter()
take predicate as argument
- Example filter with predicate <br/>


    List.stream()
    .filter(u-> u.age()>23)
    .forEach(System.out::println);
    // return  User[id=3, name=test 2, age=26] User[id=2, name=test 3, age=24] User[id=4, name=test 4, age=28]


##### distinct()
return a stream with unique elements according to implementation of hashcode and equals methods of the object produced by the stream
- Example filter unique element <br/>


    Stream.of("A","B","C","A","C","D","","E")
        .filter(Predicate.not(String::isBlank)) // return A, B, C, A, C, D, E
        .distinct() // return A, B, C, D, E
        .forEach(System.out::println); 

#### Slicing
##### takeWhile
        
    var user1 = new User(1,"test 1");
    var user2 = new User(3,"test 2");
    var user3 = new User(2,"test 3");
    var user4 = new User(4,"test 4");

    var userList = List.of(user1,user2, user3,user4);
    userList.stream()
        .takeWhile( u -> u.id()<3)
        .forEach(s->System.out.println(s.id()));  // show 1

##### dropWhile

    System.out.println("result dropWhile is ");
    userList.stream()
        .dropWhile(u -> u.id()<3).forEach(s->System.out.println(s.id())); // dropWhile is complement of takeWhile
    // show 3, 2, 4

##### limit

    System.out.println("result limit is ");
    userList.stream()
        .limit(3)
        .forEach(s->System.out.println(s.id())); // show 1, 3, 2


##### skip

    System.out.println("result skip is ");
    userList.stream()
        .skip(2)
        .forEach(s->System.out.println(s.id())); // show 2, 4


#### Mapping
##### map
map take function as argument this function is applied to each element

    Stream.of("Apple","Banana","orange","Kiwi")
          .map(String::length)
          .forEach(System.out::println); // return 5, 6, 6, 4
##### FlatMap

    public record Book(int id, String title, double price){
    }
    public record User(int id, String name, int age, List<Book> books) {
    }

    var book1 = new Book(1,"book 1",12.5);
    var book2 = new Book(2,"book 2",17);
    var book3 = new Book(3,"book 3",15);
    var user1 = new User(1,"test 1",22, Arrays.asList(book1));
    var user2 = new User(3,"test 2",26, Collections.EMPTY_LIST);
    var user3 = new User(2,"test 3",24, Arrays.asList(book1,book2));
    var user4 = new User(4,"test 4",28, Arrays.asList(book2, book3));

    var userList = List.of(user1,user2, user3,user4);

- Example 1 : list distinct books for all users


    userList.stream()
    .map(User::books)
    .flatMap(Collection::stream)
    .distinct()
    .forEach(System.out::println); // return all unique books Book[id=1, title=book 1, price=12.5], Book[id=2, title=book 2, price=17.0], Book[id=3, title=book 3, price=15.0]

- Example 2 : list distinct prices of books for all users


    userList.stream()
    .map(User::books)
    .flatMap(lb -> lb.stream().map(Book::price))
    .distinct()
    .forEach(System.out::println); // return 12.5, 17.0, 15.0

#### Finding and Matching
##### allMatch
check if predicate matches all elements

    var user1 = new User(1,"test 1",22);
    var user2 = new User(3,"test 2",26);
    var user3 = new User(2,"test 3",24);
    var user4 = new User(4,"test 4",28);

    var userList = List.of(user1,user2, user3,user4);
    userList.stream().allMatch(u-> u.age()>25) // false

##### noneMatch
opposite of allMatch, check if no elements in the stream match the given predicate

    userList.stream().noneMatch(u-> u.age()>29)) // true

##### findAny
perform single element and finish as soon as a result is found

    userList.stream()
        .filter(u-> u.age()>24)
        .findAny().get()); // User[id=3, name=test 2, age=26]

##### findFirst
the same as findAny, but findAny use parallel stream

####  Reducing 

###### Example 1 : Numbers
Sum of numbers :

    List<Integer> numbers = Arrays.asList(3,2,1,9,4);
    numbers.stream().reduce(0, (v,w)-> v + w); // return 19
    numbers.stream().reduce(Integer::sum) // or this return also 19

Min value :

    numbers.stream().reduce(Integer::min) // return Optional[1]

Max value :
    
    numbers.stream().reduce(Integer::max) // return  Optional[9]

NB : to calculate AVG you can use other methods in java 8
  
    numbers.stream().mapToInt(x -> x).average().getAsDouble();
    numbers.stream().mapToInt(x -> x).summaryStatistics().getAverage();
    userList.stream().mapToInt(x -> x.age()).summaryStatistics().getAverage())

###### Example 2 : String
concat string :

    List<String> letters = Arrays.asList("h","e","l","l","o");
    letters.stream().reduce("", (v,w)-> v+w);  // return hello
    letters.stream().reduce(String::concat); // return Optional[hello]


#### Numeric stream
##### Mapping to numeric stream
###### mapToInt()


    var user1 = new User(1,"test 1",22, Arrays.asList(book1));
    var user2 = new User(3,"test 2",26, Collections.EMPTY_LIST);
    var user3 = new User(2,"test 3",24, Arrays.asList(book1,book2));
    var user4 = new User(4,"test 4",28, Arrays.asList(book2, book3));
    var userList = List.of(user1,user2, user3,user4);

    System.out.println("sum = "+userList.stream().mapToInt(User::age).sum()); // sum = 100
    System.out.println("average = "+userList.stream().mapToInt(User::age).average()); // average = OptionalDouble[25.0]
    System.out.println("max = "+userList.stream().mapToInt(User::age).max()); // max = OptionalInt[28]
    System.out.println("min = "+userList.stream().mapToInt(User::age).min()); // min = OptionalInt[22]

##### Converting numeric stream to stream of object
boxed () convert : <br/>
- IntStream to Stream<Integer>
- DoubleStream to Stream<Double>
- LongStream to Stream<Long>


    IntStream intStream = userList.stream().mapToInt(User::age);
    Stream<Integer> stream = intStream.boxed();

##### default values for OptionalInt


    var userList2 = new ArrayList<>(userList); // created new List because we can change immutable collection
    userList2.clear();  // remove all elements
    System.out.println("min = "+userList2.stream().mapToInt(User::age).min().orElse(0)); // min = 0


##### Numeric range

#### Building streams
#####  sorted

    List<String> letters = Arrays.asList("h","e","l","l","o");
    letters.stream().sorted().forEach(System.out::println); // return e, h, l, l, o
    letters.stream().sorted(Comparator.naturalOrder()).forEach(System.out::println); // ASC return e, h, l, l, o
    letters.stream().sorted(Comparator.reverseOrder()).forEach(System.out::println); // DESC return o, l, l, h, e

###  collecting data
####  collectors
####  reducing and summarizing
####  grouping
####  partitioning
####  collector interface
####  developing your own collector

### Collection API improvements
#### Collection factories

- List factory  
- Set factory  
- Map factory  
#### removeIf

#### replaceAll

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
    .collect(Collectors.toList()); // return "New example ", "for java ", "developers."

    assertThat(lines).containsExactly("New example ", "for java ", "developers.");


### Java 12 (published March 2019)
#### Switch Expressions
- Multiple case labels
- Switch expression returning value via break (replaced with yield in Java 13 switch expressions)
  - Switch expression returning value via label rules (arrow)

- Before : traditional switch
 


      private static String getTextBefore12(int number) {
          String result = "";
          switch (number) {
                  case 1:
                  case 2:
                      result = "one or two";
                      break;
                  case 3:
                      result = "three";
                      break;
                  case 4:
                  case 5:
                  case 6:
                      result = "four or five or six";
                      break;
                  default:
                      result = "unknown";
              };
              return result;
              }
      }
- After : Multiple case


    private static String getTextMultipleLabels(int number) {
    String result = "";
    switch (number) {
          case 1, 2:
          result = "one or two";
          break;
          case 3:
          result = "three";
          break;
          case 4, 5, 6:
          result = "four or five or six";
          break;
          default:
          result = "unknown";
    };
          return result;
    }

- Return value via Break


      private static String getTextViaBreak(int number) {
        String result = switch (number) {
            case 1:
            case 2:
                break "one or two"; 
            case 3:
                break "three";
            case 4:
            case 5:
            case 6:
                break "four or five or six";
            default:
                break "unknown";
        };
        return result;
    }

- Return value via Arrow


      boolean isWeekend(String day){
          return  switch (day){
            case "MONDAY", "TUESDAY", "WEDNESDAY", "THURSDAY", "FRIDAY" -> false;
            case "SATURDAY", "SUNDAY" -> true;
            default -> throw new IllegalArgumentException();
          };
      }
### Java 13 (published September 2019)
- adding a new **yield** keyword to return a value from the switch expression.
- Before : return value with break

      private static int getValueViaBreak(String mode) {
      int result = switch (mode) {
          case "a":
          case "b":
              break 1;
          case "c":
              break 2;
          case "d":
          case "e":
          case "f":
              break 3;
          default:
              break -1;
      };
      return result;
    }
  - After : return value with yield
  

      private static int getValueViaYield(String mode) {
      int result = switch (mode) {
          case "a", "b":
          yield 1;
          case "c":
          yield 2;
          case "d", "e", "f":
          // do something here...
          System.out.println("Supports multi line block!");
          yield 3;
          default:
          yield -1;
      };
      return result;
      }

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
- Sealing allows classes and interfaces to define their permitted subtypes
- A sealed class allows you to restrict or choose its sub-classes. A class can not extend a sealed class, if it is not in the list of permitted child classes of parent class.
- Before A final class can have no subclasses. A package-private class can only have subclasses in the same package.

##### Sealed Interfaces
sealed interfaces allows you specifies the classes that are permitted to implement the sealed interface
- Example

      public sealed interface Service permits Teacher, Student {
    
      int getName();
    
      default String getDepartement() {
        return "IT department";
      }
    
    }

##### Sealed classes
- Example : Person can only be extended by Teacher and Student classes

  
    public sealed class Person permits Teacher, Student {
    }

- A class that extends a sealed class (Computer, Mobile) must have either final, sealed or non-sealed keyword in its declaration
- This is because by making a child class :
  1. **final** means, that it cannot be sub-classed further.
  2. **sealed** means, that we need to declare child classes with permits.
  3. **non-sealed** means, that we are ending the parent-child hierarchy here.

Teacher

    public final class Teacher extends Person implements Service {

    private final int salary;
    }


Student

    public non-sealed class Student extends Person implements Service {

    private final String course;


##### Sealed records
- A record can not extend a normal class, so it can only implement a sealed interface
- a record is implicitly final


    public sealed interface Device permits Laptop {
    }

    public record Laptop(String brand) implement Device {
    }

##### Reflection support
java reflection provides support for sealed classes. Following two methods
1. getPermittedSubclasses() : It returns an array of java.lang.Class containing all the classes permitted by this class object <br/>
Example : 

   
    Class<?>[] permittedSubclasses = p.getClass().getPermittedSubclasses();
    for (Class<?> sc : permittedSubclasses){
    System.out.println(sc.getName());
    }

2. isSealed() : It returns true if the class or interface on which it is called is sealed.
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



### Java 18 (published March 2022) 
### Java 19 (published September 2022) 
### Java 20 (published March 2023) 
### Java 21 (published September 2023) 
#### Interpolation

    Before
    System.out.println("x : "+ x +" y : ": y);
    With Java 21
    System.out.println(STR."x : \{x} y : \{y}");

#### pattern matching

    record Employee(int id, double salary){}

    Before
    if (person instanceof Employee e) {
      System.out.println("id : "+ e.id() +" salary : ": e.salary())
    //...
    }
    with Java 21
    if (person instanceof Employee(int id, double salary)) {
      System.out.println("id : "+ id +" salary : ": salary)
    //...
    }
#### pattern matching for switch

## Java questions 

### What is the difference between Checked vs Unchecked Exceptions in Java ?
#### - Checked Exception : 
the exceptions that are checked at compile time.
- fully checked exceptions : exception where all its child classes are also checked like IOException, and InterruptedException
- partially checked exceptions : some of its child classes are unchecked, like an Exception 
#### - UnChecked Exception : 
These are the exceptions that are not checked at compile time Example : ArithmeticException, ArrayIndexOutOfBoundsException, NullPointerException 
	
	
### SOLID Principles ?
- (S) : Single responsibility => Class has one job to do
- (O) : Open/closed => class is open for extension and closed for modification.
- (L) : Liskov substitution => class can be replaced by any of its children without any problem. children classes inherit parent's behaviours.
- (I) : Interface segregation => larger interfaces should be split into smaller ones. to avoid force class to use no needed methods.
- (D) : Dependency inversion => decoupling dependencies between modules by using abstraction.