# Task 6 — Challenge: a course roster

Use your `Student` class from Task 2 to create a Java class called `Course` with these fields:

```java
private String courseCode;
private String courseName;
private ArrayList<Student> students;
```

Initialize `students` as an empty list in the constructor.

## Required methods

Implement these methods:

```java
public boolean addStudent(Student student)
public boolean removeStudent(int studentId)
public Student findStudent(int studentId)
public void sortStudents()
public void printStudents()
public int getStudentCount()
```

## Rules

- `addStudent()` must reject a student whose ID is already present and return `false`. Otherwise, it adds the student and returns `true`.
- `removeStudent()` returns whether a student was removed.
- `findStudent()` returns the matching student, or `null` if none exists.
- Make `Student` implement `Comparable<Student>`, ordering students by ID in ascending order.
- `sortStudents()` sorts the existing list.
- Override `Course.toString()` to return something like:

  ```text
  CS280 - Object-Oriented Programming (4 students)
  ```

For this task, keep student IDs unchanged after students are added to a course.

## Test scenario

Add four students, attempt to add a duplicate ID, find an existing and a missing student, sort the roster, remove a student, and print the final result.
