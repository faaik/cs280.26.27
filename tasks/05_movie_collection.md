# Task 5 — Build a movie collection

Create a Java class called `Movie` with these private fields:

- `String title`
- `int releaseYear`
- `int durationMinutes`

Assume that titles are never `null`.

## Requirements

1. Add a constructor, getters, setters, and a readable `toString()`.
2. Override `equals()` so that two movies are equal when they have the same **title and release year**. Compare titles case-sensitively.
3. Override `hashCode()` using those same two fields.
4. Implement `Comparable<Movie>` with these rules:
   - Sort by title alphabetically.
   - If the titles match, sort by release year, oldest first.
   - Movies considered equal must compare as zero.

## Test your implementation

In `Main`:

1. Create an `ArrayList<Movie>` containing at least six movies.
2. Include two movies with the same title but different release years.
3. Print the collection before and after sorting.
4. Print only movies longer than 120 minutes.
5. Calculate the average movie duration.
6. Find and print the oldest movie.
7. Check whether a particular movie exists using a newly created `Movie` object.

## Check your understanding

Why is sorting only by title insufficient for the ordering rules in this task?
