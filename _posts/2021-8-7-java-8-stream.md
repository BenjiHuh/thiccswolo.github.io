---
layout: post
title: Java 8 Stream
---

The Stream, a data processing layer that is supported starting in Java 8, that utilize lambda expressions and stacking methods that result in more efficent coding. They are not to be confused with Java I/O Streams. They are a "wrapper" around a data source (arrays, sets, etc.), not changing the data source but outputting a changed result. Since Streams can be used for so many data types, in addition to the ability to chain/stack methods in one stream means that in practice, you are able to do bulk data processing efficently and elegantly (shown in below code).

While Streams aren't able to be called more than once after use, because it dosen't change the original data, you are able to make multiple instances with the same or slightly different processes. Java Streams come with methods commonly used in data processing, such as map, filter, sorted, statistics, and more. Once these "intermediate" processes are done, in order to output the data, you will commonly use the collect method to output the processed data for use. This stream can be referenced by a variable, printed, or simply outputted by collect.

In the below code, I am trying to find the 3 smallest integers from the array, without modifying the array itself. When not using streams, I would make a duplicate of the array, sort the copied array (to not make changes to original data), then print the first 3 elements in the array.

```java
class Main {
  public static void main(String{} args) {
    int[] numbers = {4, 1, 13, 90, 16, 2, 0}
    int[] copy = Arrays.copyOf(numbers, numbers.length);
    Arrays.sort(copy);
    for (int i=0; i< 3; i++) {
      System.out.println(copy[i]);
    }
  }
}
```

If I were to use streams however, I would be able to do all the processes I did above, however only have used 1 line of code. In addition to the above data processes, I also added the distinct method in the case where the array has duplicates of an integer. I used the forEach method as my terminal process, where for each element in the array I print out the integer in a new line until it has iterated through the final stream.

```java
class Main {
  public static void main(String[] args) {
    int[] numbers = {4, 1, 13, 90, 16, 2, 0};
    IntStream.of(numbers).distinct().sorted().limit(3).forEach(System.out::println);
    }
  }
}
```

In conclusion, Java Streams are a very important and useful thing to master as it will make data processing much more simpler for yourself and others to understand along with the minimal amount of coding compared to alternative solutions.
