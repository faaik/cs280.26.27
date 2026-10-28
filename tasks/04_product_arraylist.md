# Task 4 — Manage an ArrayList of products

Use your `Product` class from Task 3.

## Requirements

1. Create an `ArrayList<Product>`.
2. Add at least five products in an unsorted order.
3. Print all products using an enhanced `for` loop.
4. Print the number of products.
5. Retrieve and print the product at index `2`.
6. Replace the product at index `1`.
7. Remove one product by index.
8. Sort the list using:

   ```java
   Collections.sort(products);
   ```

9. Print the sorted list.

Then create a **new object** whose product code matches a product already in the list, but whose name and price are different.

Use that new object to test these operations and print their return values:

```java
products.contains(searchProduct);
products.indexOf(searchProduct);
products.remove(searchProduct);
```

## Check your understanding

Explain why these operations can find an object even though it is a different instance.
