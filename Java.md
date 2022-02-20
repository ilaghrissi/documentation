# Java

## Java features with examples :

### Java 8

### Java 9 (published September 2017)

### Java 10 (published March 2018)

### Java 11 (published September 2018)

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

### Java 16 (published March 2021)

## Java 17 (published September 2021)
