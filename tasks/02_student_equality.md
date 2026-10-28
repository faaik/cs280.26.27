# Task 2 — When are two students equal?

Create a Java class called `Student` with these private fields:

- `int studentId`
- `String fullName`
- `String studyProgram`

## Requirements

1. Add a constructor, getters, setters, and `toString()`.
2. Override `equals()` so that **two students are equal if they have the same `studentId`**, even if their other fields differ.
3. Override `hashCode()` using the same field used by `equals()`.

## Test your implementation

Create these objects in `Main`:

```java
Student first = new Student(101, "Amina Hodzic", "Computer Science");
Student second = new Student(101, "Amina H.", "Software Engineering");
Student third = new Student(102, "Amar Basic", "Computer Science");
```

Test and explain the results of:

```java
System.out.println(first == second);
System.out.println(first.equals(second));
System.out.println(first.equals(third));
System.out.println(first.equals(null));
System.out.println(first.equals("Amina"));
System.out.println(first.hashCode() == second.hashCode());
```

## Check your understanding

Equal objects must have equal hash codes. Must unequal objects always have different hash codes?
