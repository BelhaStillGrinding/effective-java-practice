# ☕ Java Bootcamp – Effective Java Practice

This repository is a **hands-on Java bootcamp** designed to bridge the gap between **basic Java syntax** and **professional Spring Boot development**.

It contains **12 structured exercises**, inspired by Joshua Bloch’s book  
📘 **_Effective Java_**, one of the most important books for writing clean, robust, and maintainable Java code.

Each exercise references a specific *Effective Java* item to help you build **correct mental models**, not just working code.

---

## 🎯 Goals of This Bootcamp

- Strengthen core Java fundamentals
- Learn how Java objects behave in real-world applications
- Understand how Java concepts apply directly to **Spring Boot & JPA**
- Practice writing **clean, professional-grade code**
- Prepare for backend interviews and real projects

---

## 🧱 Structure

The bootcamp is divided into **4 modules**:

| Module | Focus Area |
|------|-----------|
| Module 1 | Logic & Arrays |
| Module 2 | Object Contract (equals, hashCode, immutability) |
| Module 3 | Ordering & Sorting |
| Module 4 | Robustness & Exceptions |

---

# 🏗️ Module 1: Logic & Array Manipulation
**Focus:** Algorithmic thinking, loops, and standard libraries.

---

## Exercise 1: Robust Search

**Goal:**  
Create a method:

```java
int findNumber(int target, int[] data)
```

1. Generate an array of 50 random integers (values 1–100).
2. Search for the target number.
3. Return the index if found.
4. Otherwise, print a "not found" message.

**_Effective Java – Item 57_**  
Minimize the scope of local variables. Declare loop counters inside the for loop, not outside.

**Expected Output:**
```plaintext
> Searching for: 42
Number found at index 12

OR

Number not present in the array
```

---

## Exercise 2: Single-Pass Analysis

**Goal:**  
1. Generate an array of 20 random integers.
2. Find both minimum and maximum values.

**_Effective Java – Item 59_**  
Know and use the libraries. While manual loops are good practice, be aware that:

```java
Arrays.stream(arr).summaryStatistics()
```

is the modern standard.

**Expected Output:**
```plaintext
Array: [12, 45, 2, 99, ...]
Max = 99, Min = 2
```

---

## Exercise 3: Array Reversal

**Goal:**  
1. Create an array of integers from 1 to 10.
2. Print it in original order.
3. Reverse it manually (swap indices).
4. Print the reversed array.

**_Effective Java – Item 58_**  
Prefer for-each loops when reading data, but recognize when index manipulation is required.

**Expected Output:**
```plaintext
Original: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
Reversed: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

---

## Exercise 4: Conditional Summation

**Goal:**  
1. Generate an array of 20 random numbers.
2. Calculate the sum of even numbers only.

**_Effective Java – Item 45_**  
Use streams judiciously. This logic can be expressed as:

```java
Arrays.stream(arr).filter(x -> x % 2 == 0).sum();
```

**Expected Output:**
```plaintext
Array: [2, 5, 8, 11, ...]
Sum of even numbers: 10
```

---

# 🧩 Module 2: The Object Contract (Entities)
**Focus:** Objects that behave correctly in `HashSet`, `HashMap`, and JPA.

---

## Exercise 5: Immutable Person Class

**Goal:**  
Create an immutable `Person` class with:

- `firstName` (String)
- `lastName` (String)
- `birthDate` (LocalDate)

**Rules:**  
- All fields `private final`
- Initialized via constructor
- No setters

**_Effective Java – Item 17_**  
Minimize mutability. Immutable objects are:
- Thread-safe
- Easier to reason about
- Safer in collections

---

## Exercise 6: Equality Implementation

**Goal:**  
Override the following methods for a `Person` object:

- `equals()`
- `hashCode()`

Two `Person` objects are equal if:
1. `firstName`
2. `lastName`
3. `birthDate`

...are all identical.

**_Effective Java – Item 11_**  
Always override `hashCode` when you override `equals`.

---

## Exercise 7: Set Uniqueness

**Goal:**  
1. Create 4 `Person` objects.
2. Ensure 2 of them have identical data.
3. Add all objects to a `HashSet`.
4. Print the set size.

**_Effective Java – Item 10_**  
Obey the general contract of `equals`.

**Expected Output:**
```plaintext
Number of people in the set: 3
```

---

# ⚖️ Module 3: Object Ordering
**Focus:** Sorting for APIs, UI responses, and business logic.

---

## Exercise 8: Natural Ordering (Comparable)

**Goal:**  
1. Make `Person` implement `Comparable<Person>`.
2. Sort by age (ascending).

**_Effective Java – Item 14_**  
Consider implementing `Comparable`. Use:

```java
Integer.compare()
LocalDate.compareTo()
```

...instead of subtraction.

**Expected Output:**
```plaintext
Sorting by Age (Comparable):
John Doe (Age: 25)
Mario Rossi (Age: 30)
Jane Smith (Age: 35)
```

---

## Exercise 9: Custom Comparator

**Goal:**  
Create a separate `Comparator` to sort by:

1. Last Name
2. First Name (if last names match)

**_Effective Java – Item 14_**  
Use `Comparator` construction methods. Example:

```java
Comparator.comparing(Person::getLastName)
          .thenComparing(Person::getFirstName);
```

**Expected Output:**
```plaintext
Sorting by Name (Comparator):
Jane Smith
Mario Rossi
John Verdi
```

---

# 🛡️ Module 4: Robustness & Exceptions
**Focus:** Validation, error handling, and defensive coding.

---

## Exercise 10: Input Sanitization

**Goal:**  
1. Ask user to input 10 names.
2. Store them in an `ArrayList`.
3. Reject inputs containing numbers or symbols.
4. Do not advance the counter on invalid input.

**_Effective Java – Item 69_**  
Use exceptions only for exceptional conditions. Validation should use `if/else`, not `try/catch`.

**Expected Output:**
```plaintext
> Enter name: Mario123
Invalid input: Name cannot contain numbers. Try again.
> Enter name: Mario
Name added.
```

---

## Exercise 11: Safe List Removal

**Goal:**  
1. Ask the user for a name to remove.
2. Check existence before removing.

**_Effective Java – Item 54_**  
Return empty collections or `Optional`, not null.

**Expected Output:**
```plaintext
> Enter name to remove: Giovanni
Name not found in the list.
> Enter name to remove: Mario
Mario removed successfully.
```

---

## Exercise 12: Custom Exceptions

**Goal:**  
1. Create a custom checked exception: `ProfanityException`.
2. Scan a user-input sentence.
3. If it contains a banned word → throw exception.
4. Otherwise, check if it contains "Java" (case-insensitive).

**_Effective Java – Items 70 & 72_**  
Use checked exceptions for recoverable business conditions.

**Expected Output:**
```plaintext
> Input: This is a badword
Exception: Profanity detected in the input!

> Input: I love coding
The sentence does NOT contain 'Java'.

> Input: I love Java programming
The sentence contains the word 'Java'.
```
