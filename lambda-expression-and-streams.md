### What you should know ?

- Lambda expressions were introduced with Java 8.
- They can be used to replace **anonymous inner classes**
- With java 8 we have functional interfaces
- 2 packages are supported in Java for functional Interface 1. java.util.function 2. java.util.stream
  > Note: **Lambda expressions** ( introduced in Java 8 ) use both of this new packages

### Functional Interface:

- An interface that contains at most one **abstract function**
- Represents abstract concepts such as functions, actions, or predicates

### Types of Functional Interface

**Predicate** - It takes one argument, return a boolean. It will have test method.

**Consumer** - It accepts single argument with no return value.

**Function** - It accepts one argument and produces a result.

**Supplier** - It supplies a result.

**UnaryOperator** - Single argument with return value.

**BinaryOperator** - Operation on 2 argumennts and returns a single output. Ex - Summation, multiplication, division etc.

#### Working example:

```
package com.morgam.round3;

import java.util.function.*;

public class PredefinedFunctionalInterface {

    public static void main(String[] args) {
        // Demonstration of Predicate Functional Interface. For more details and official definition hover over Predicate
        Predicate<String> strLen = (s) -> s.length() < 10;
        System.out.println(strLen.test("Salman"));

        // Demonstration of Consumer Functional Interface. For more details and official definition hover over Consumer
        Consumer<String> consumer = (s) -> System.out.println("Name of person : " + s);
        consumer.accept("Salman");

        // Demonstration of Function Functional Interface. For more details and official definition hover over Function
        Function<Integer, String> converter = (num) -> Integer.toString(num);
        System.out.println(converter.apply(26).length());

        // Demonstration of BinaryOperator Functional Interface. For more details and official definition hover over BinaryOperator
        Supplier<String> supplier = () -> "Salman";
        System.out.println("Name of the person : " + supplier.get());

        // Demonstration of BinaryOperator Functional Interface. For more details and official definition hover over BinaryOperator
        UnaryOperator<Integer> unaryOperator = (num) -> (num + 1);
        System.out.println("Increase number : " + unaryOperator.apply(12));

        // Demonstration of BinaryOperator Functional Interface. For more details and official definition hover over BinaryOperator
        BinaryOperator<Integer> binaryOperator = (n1, n2) -> (n1+n2);
        System.out.println("Sum of 2 numbers : " + binaryOperator.apply(2, 3));
    }

}

```

### Collection API:

- Collection API was introduced with Java 7.
- A collection is a group of elements
- They can store, retrieve, manipulate, and communicate aggregate data.

#### java.util.stream:

- This package contains interfaces for using streams.
- A stream represents a sequence of elements.
- The stream package was added to traverse collections.
- Most stream operations take a lambda expression.
- Stream operations are either intermediate or terminal.
- Terminal operations are either void or return a type.
- Intermediate operations returns the stream itself.
- Common operations include - map, filter and forEach
- sorted and collect are also very useful.
- sorted is an intermediate operation. Which returns sorted view of stream
- collect is used as terminal operation - To transform the elements of stream into a different kind of result.
- Elements of a stream can not be changed. - You can save them to a new collection.

### Example of Stream Operation

```
package lambdas_02_02;
import java.util.Arrays;
import static java.util.Arrays.asList;
import java.util.HashSet;
import java.util.List;
import java.util.Set;
import java.util.function.BinaryOperator;
import java.util.stream.Collectors;
import static java.util.stream.Collectors.toList;
import java.util.stream.Stream;

public class Lambdas_02_02 {
    public static void main(String[] args) {
        // First of all converting array to list then converting list to stream then sorting the // list view then printing the 1st element of the sorted stream. Note that the original
        // list will be as it is
        Arrays.asList("red", "green", "blue")
        .stream()
        .sorted()
        .findFirst()
        .ifPresent(System.out::println);

        //example of Stream.of with a filter
        // Uncomment Sysout to see how flow goes while doing stream operation
        Stream.of("apple", "pear", "banana", "cherry", "apricot")
                .filter(fruit -> {
                  //  System.out.println("filter: " + fruit);
                    return fruit.startsWith("a"); //predicate
                })
                //if the foreach is removed, nothing will print,
                //the foreach makes it a terminal event
                .forEach(fruit -> System.out.println("Starts with A: " + fruit));

        //using a stream and map operation to create a list of words in caps
        List<String> collected = Stream.of("Java", " Rocks")
                .map(string -> string.toUpperCase())
                .collect(toList());
        System.out.println(collected.toString());
    }
}
```

### Example of Stream with Collections and Class

##### Book Class

```
package lambdas_02_01;

public class Book {
    private String title;
    private String authorFName;
    private String authorLName;
    private int pages;

    public Book(String title, String authorFName, String authorLName,
            int pages) {
        this.title = title;
        this.authorFName = authorFName;
        this.authorLName = authorLName;
        this.pages = pages;

    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getAuthorFName() {
        return authorFName;
    }

    public void setAuthorFName(String authorFName) {
        this.authorFName = authorFName;
    }

    public String getAuthorLName() {
        return authorLName;
    }

    public void setAuthorLName(String authorLName) {
        this.authorLName = authorLName;
    }

    public int getPages() {
        return pages;
    }

    public void setPages(int pages) {
        this.pages = pages;
    }
    public String toString()
    {
        return getTitle()+" Written By: "+getAuthorFName()+" " +getAuthorLName()+"\n";
    }
}
```

##### Lambdas_With_Collection_And_Class class

```
package lambdas_02_01;

import java.util.Arrays;
import static java.util.Arrays.asList;
import java.util.Collection;
import java.util.Collections;
import java.util.Comparator;
import java.util.HashSet;
import java.util.List;
import java.util.Set;
import java.util.stream.Collectors;

public class Lambdas_With_Collection_And_Class {

    public static void main(String[] args) {
        List<String> names = Arrays.asList("Paul", "Jane", "Michaela", "Sam");
        //way to sort prior to Java 8 lambdas
        Collections.sort(names, new Comparator<String>() {
            @Override
            public int compare(String a, String b) {
                return b.compareTo(a);
            }
        });
        //first iteration with lambda
        Collections.sort(names, (String a, String b) -> {
            return b.compareTo(a);
        });
        //now remove the return statement
        Collections.sort(names, (String a, String b) -> b.compareTo(a));

        //now remove the data types and allow the compile to infer the type
        Collections.sort(names, (a, b) -> b.compareTo(a));


        //total pages in your book collection
        Book book1 = new Book("Miss Peregrine's Home for Peculiar Children",
                "Ranson", "Riggs", 382);
        Book book2 = new Book("Harry Potter and The Sorcerers Stone",
                "JK", "Rowling", 411);
        Book book3 = new Book("The Cat in the Hat",
                "Dr", "Seuss", 45);

        List<Book> books = Arrays.asList(book1, book2, book3);
        int total = books.stream()
                .collect(Collectors.summingInt(Book::getPages));
        System.out.println(total);

        //create a list with duplicates
        List<Book> dupBooks = Arrays.asList(book1, book2, book3, book1, book2);
        System.out.println("Before removing duplicates: ");
        System.out.println(dupBooks.toString());

        Collection<Book> noDups = new HashSet<>(dupBooks);
        System.out.println("After removing duplicates: ");
        System.out.println(noDups.toString());


        //aggregate author first names into a list
        List<String> list = books.stream()
                .map(Book::getAuthorLName)
                .collect(Collectors.toList());
        System.out.println(list);

        //example of using Set to eliminate dups and sort automatically
        Set<Integer> numbers = new HashSet<>(asList(4, 3, 3, 3, 2, 1, 1, 1));
        System.out.println(numbers.toString());
    }
}
```

### Example of Lambda Expression with numbers

```
package lambdas_02_03;

import java.util.Arrays;
import java.util.stream.IntStream;
import java.util.stream.Stream;

public class Lambdas_For_Nums {

    public static void main(String[] args) {
        IntStream.range(1, 4)
                .forEach(System.out::println);

        //find the average of the numbers squared
        Arrays.stream(new int[]{1, 2, 3, 4})
                .map(n -> n * n)
                .average()
                .ifPresent(System.out::println);

        //map doubles to ints
        Stream.of(1.5, 2.3, 3.7)
                .mapToInt(Double::intValue)
                .forEach(System.out::println);
    }

}

```

### Custom Functional Interface Example

```
public class CustomFunctionalInterface {

    @FunctionalInterface
    public interface MathematicalOperations {
        public abstract int operation(Integer n1, Integer n2);
    }
    public static void main(String[] args) {

        MathematicalOperations addition = (n1, n2) -> (n1+n2);
        System.out.println("Sum of 2 numbers : " + addition.operation(2, 3));

        MathematicalOperations subtraction = (n1, n2) -> (n1-n2);
        System.out.println("Difference of 2 numbers : " + subtraction.operation(5, 3));

        MathematicalOperations multiplication = (n1, n2) -> (n1*n2);
        System.out.println("Multiplication of 2 numbers : " + multiplication.operation(2, 3));

        MathematicalOperations divison = (n1, n2) -> (n1/n2);
        System.out.println("Divison of 2 numbers : " + divison.operation(200, 10));


    }

}
```
