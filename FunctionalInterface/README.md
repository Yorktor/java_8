```
Source: https://mkyong.com/tutorials/java-8-tutorials/
```
## Function
Function takes an argument (object of type T) and returns an object (object of type R). The argument and output can be a different type.<br />
```
@FunctionalInterface
public interface Function<T, R> {
    R apply(T t);
}
```
T – Type of the input to the function.<br />
R – Type of the result of the function.<br />

### 1. Basic example
Function<String, Integer> len = x -> x.length();<br />
Integer result = len.apply("Hello");<br />
System.out.println(result);<br />

### 2. Chain (andThen)
Function<Integer, Integer> multiply = x -> x * 2;<br />
Integer result = len.andThen(multiply).apply("Hello");<br />
System.out.println(result);<br />

## BiFunction
BiFunction takes two arguments and returns an object.<br />
```
@FunctionalInterface
public interface BiFunction<T, U, R> {
      R apply(T t, U u);
}
```
T – Type of the first argument to the function.<br />
U – Type of the second argument to the function.<br />
R – Type of the result of the function.<br />

### Basic example
BiFunction<Integer, Integer, String> func = (x, y) -> "result: " + x + y;<br />
String result = func.apply(2, 3);<br />
System.out.println(result);<br />

## BinaryOperator
The BinaryOperator takes two arguments of the <strong>same</strong> type and returns a result of the same type of its arguments.<br />
```
@FunctionalInterface
public interface BinaryOperator<T> extends BiFunction<T,T,T> {
}
```
BinaryOperator<Integer> func2 = (x1, x2) -> x1 + x2;<br />
Integer result2 = func.apply(2, 3);<br />
System.out.println(result2);<br /><br />
The BiFunction takes two arguments of any type, and returns a result of <strong>any</strong> type.<br />
```
@FunctionalInterface
public interface BiFunction<T, U, R> {
      R apply(T t, U u);
}
```
BiFunction<Integer, Integer, Integer> func = (x1, x2) -> x1 + x2;<br />
Integer result = func.apply(2, 3);<br />
System.out.println(result);<br />

## UnaryOperator
The UnaryOperator takes one argument, and returns a result of the same type of its arguments.<br />
```
@FunctionalInterface
public interface UnaryOperator<T> extends Function<T, T> {
}
```
UnaryOperator<Integer> func2 = x -> x * 2;
Integer result = func2.apply(2);
System.out.println(result); 

## Predicate
```
In Java 8, Predicate is a functional interface, which accepts an argument and returns a boolean. Usually, it used to apply in a filter for a collection of objects.<br />
@FunctionalInterface
public interface Predicate<T> {
  boolean test(T t);
}
```
Predicate<Integer> noGreaterThan5 = x -> x > 5;<br />
List< Integer > list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);<br />
List< Integer > collect = list.stream().filter(noGreaterThan5).collect(Collectors.toList());<br />
System.out.println(collect);<br />

### and()
List< Integer > collect1 = list.stream().filter(noGreaterThan5.and((x) -> x < 9)).collect(Collectors.toList());<br />
System.out.println(collect1);<br />

### or()
List< Integer > collect2 = list.stream().filter(noGreaterThan5.or((x) -> x < 3)).collect(Collectors.toList());<br />
System.out.println(collect2);<br />

