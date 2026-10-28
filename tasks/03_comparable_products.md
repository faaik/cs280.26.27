# Task 3 — Make products sortable

Create a Java class called `Product` with these private fields:

- `String productCode`
- `String name`
- `double price`

Assume that product codes are never `null`.

## Requirements

1. Add a constructor, getters, setters, and `toString()`.
2. Override `equals()` and `hashCode()` using only `productCode`.
3. Implement `Comparable<Product>`.
4. Implement `compareTo()` so that products are ordered alphabetically by `productCode`.

## Test your implementation

Create products with these codes:

```text
P003
P001
P004
P002
```

Before using a list, compare individual objects:

```java
System.out.println(firstProduct.compareTo(secondProduct));
```

## Check your understanding

Identify examples where `compareTo()` returns a negative number, zero, and a positive number. Two products with the same code should compare as zero.
