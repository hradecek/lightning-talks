---?color=#90CAF9
@title[Intro]
@snap[north span-100]
### @color[#e26c00f9](Functional programming in Java)
@snapend
![Java Logo](assets/img/java_logo.png)
@snap[south]
@color[#5382a1ff](by Ivo Hrádek)
@snapend

---?image=assets/img/singularity.jpg
@title[In the beginning]
@snap[north span-100]
## @color[#EEEEEE](In the beginning)
@snapend
@snap[south span-100]
## @color[#EEEEEE](there was nothing)
@snapend

---?image=assets/img/big_bang.jpg
@title[Let there be a lambda]
@transition[zoom]
## Let there be
![Lambda](assets/img/lambda.png)

---?color=#90CAF9
@title[λ-calculus]
## λ-calculus
 - introduced by Alonzo Church in 1930s
 - *formal system for expressing computation based on function abstraction and application*
 - point of view on functions:
 `\[
 plus(x, y) = x + y \\
 (x, y) \mapsto x + y
 \]`
 - λ-calculus example:
`\[
\lambda f.\lambda a.\lambda b. f a b
\]`

---?color=#90CAF9
## Functions in Java
`\[
plus(x, y) = x + y
\]`
```Java
public static int plus(int x, int y) {
  return x + y;
}
```
@[1-3](Named function)

`\[
(x, y) \mapsto x + y\quad \textrm{or}\quad \lambda x.\lambda y. x + y
\]`
```Java
(x, y) -> x + y;
```
@[4](Anonymous function)

---?color=#90CAF9
## OOP ∘ FP
- function = class with one abstract method
- [First-class citizen](https://en.wikipedia.org/wiki/First-class_citizen)

```java
@FunctionalInterface
public interface Comparator<T> {
  int compare(T o1, T o2);
}
```
```java
Collections.sort(list, new Comparator<Integer>() {
  public int compare(int x, int y) {
    return (x < y) ? -1 : ((x == y) ? 0 : 1);
  }
});
Collections.sort(list, (x, y) -> (x < y) ? -1 : ((x == y) ? 0 : 1));
Collections.sort(list, Integer::compare);
```
@[1-4](Comparator - functional interface)
@[1-4, 5-9](Anonymous class)
@[1-4, 10](Lambda expression)
@[1-4, 11](Method reference)

---?color=#90CAF9
## Functional interfaces
### (@since 1.8)

 - package [`java.util.function`](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)

---?image=assets/img/functions_everywhere.jpg

---?color=#90CAF9
### `Function<T,R>`

- takes one argument of type `T`
- returns a value of type `R`

```
public static String intToString1(int number) {
  return String.valueOf(number);
}

Function<Integer, String> intToString2 = number -> String.valueOf(number);

Function<Integer, String> intToString3 = String::valueOf;
```

@[1-3](Function)
@[5](Lambda expression)
@[7](Method reference)

---?color=#90CAF9
### `BiFunction<T,U,R>`
 - takes two arguments of types `T` and `U`
 - returns a value of type `R`

```
public static String take1(int n, String str) {
  return str.substring(0, Math.min(str.length(), n));
}

BiFunction<Integer, String, String> take2 =
    (n, str) -> str.substring(0, Math.min(str.length(), n));
```

@[1-3](Function)
@[5-6](Lambda expression)

---?color=#90CAF9]

```
BiFucntion<A, B, C> bif...

BiFunction<String, Integer, String> duplicates = (n, str) -> { ... }

private static String duplicates(int n, String str) {
  final StringBuilder sb = new StringBuilder();
  for (Character ch : str.toCharArray()) {
      for (int i = 0; i < n; ++n) {
	sb.append(ch);
      }
	}
  }
   return sb.toString();
}


Operator<A> = Function<A, A>
BiOperator<A> = BiFunction<A, A, A>
Consumer<A> ==  Function<A, Void>
Supplier<A> == Function<Void, A>
Predicate<A> == Function<A, Boolean>

First class functions

# High order functions
a bit tedious in Java 8 due to poor type interference (getting better in Java 10)
 - May:
   - takes function as parameter,
   - or return function.

```Sorting

```

partial application and currying

 - Everything is a function
 - pure functinos
 - referential transparent
 - side effects
 - recursion

treats computation as the evaluation of mathematical function.
 - stateless

@snap[east span-50]
![](assets/img/presentation.png)
@snapend

---?color=#E58537
@title[It's all about evaluation]

@snap[north-west]
#### Add a splash of @color[cyan](**color**) and you are ready to start presenting...
@snapend

@snap[west span-55]
@ul[spaced text-white]
- You will be amazed
- What you can achieve
- *With a little imagination...*
- And **GitPitch Markdown**
@ulend
@snapend

@snap[east span-45]
@img[shadow](assets/img/conference.png)
@snapend

---?image=assets/img/presenter.jpg

@snap[north span-100 headline]
## Now It's Your Turn
@snapend

@snap[south span-100 text-06]
[Click here to jump straight into the interactive feature guides in the GitPitch Docs @fa[external-link]](https://gitpitch.com/docs/getting-started/tutorial/)
@snapend
