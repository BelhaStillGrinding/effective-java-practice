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
Generate an array of 50 random integers (values 1–100)

Search for the target number

Return the index if found

Otherwise, print a "not found" message

Effective Java – Item 57

Minimize the scope of local variables.

Declare loop counters inside the for loop, not outside.

Expected Output:

> Searching for: 42
Number found at index 12


or

Number not present in the array

Exercise 2: Single-Pass Analysis

Goal:

Generate an array of 20 random integers

Find both minimum and maximum values

Effective Java – Item 59

Know and use the libraries.

While manual loops are good practice, be aware that:

Arrays.stream(arr).summaryStatistics()


is the modern standard.

Expected Output:

Array: [12, 45, 2, 99, ...]
Max = 99, Min = 2

Exercise 3: Array Reversal

Goal:

Create an array of integers from 1 to 10

Print it in original order

Reverse it manually (swap indices)

Print the reversed array

Effective Java – Item 58

Prefer for-each loops when reading data, but recognize when index manipulation is required.

Expected Output:

Original: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
Reversed: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1

Exercise 4: Conditional Summation

Goal:

Generate an array of 20 random numbers

Calculate the sum of even numbers only

Effective Java – Item 45

Use streams judiciously.

This logic can be expressed as:

Arrays.stream(arr).filter(x -> x % 2 == 0).sum();


Expected Output:

Array: [2, 5, 8, 11, ...]
Sum of even numbers: 10

🧩 Module 2: The Object Contract (Entities)

Focus: Objects that behave correctly in HashSet, HashMap, and JPA.

Exercise 5: Immutable Person Class

Goal:
Create an immutable Person class with:

firstName (String)

lastName (String)

birthDate (LocalDate)

Rules:

All fields private final

Initialized via constructor

No setters

Effective Java – Item 17

Minimize mutability.

Immutable objects are:

Thread-safe

Easier to reason about

Safer in collections

Exercise 6: Equality Implementation

Goal:
Override:

equals()

hashCode()

Two Person objects are equal if:

First name

Last name

Birth date
are all identical.

Effective Java – Item 11

Always override hashCode when you override equals.

Exercise 7: Set Uniqueness

Goal:

Create 4 Person objects

2 of them must have identical data

Add all to a HashSet

Print the set size

Effective Java – Item 10

Obey the general contract of equals.

Expected Output:

Number of people in the set: 3

⚖️ Module 3: Object Ordering

Focus: Sorting for APIs, UI responses, and business logic.

Exercise 8: Natural Ordering (Comparable)

Goal:

Make Person implement Comparable<Person>

Sort by age (ascending)

Effective Java – Item 14

Consider implementing Comparable.

Use:

Integer.compare()
LocalDate.compareTo()


instead of subtraction.

Expected Output:

Sorting by Age (Comparable):
John Doe (Age: 25)
Mario Rossi (Age: 30)
Jane Smith (Age: 35)

Exercise 9: Custom Comparator

Goal:

Create a separate Comparator

Sort by:

Last Name

First Name (if last names match)

Effective Java – Item 14

Use Comparator construction methods.

Example:

Comparator.comparing(Person::getLastName)
          .thenComparing(Person::getFirstName);


Expected Output:

Sorting by Name (Comparator):
Jane Smith
Mario Rossi
John Verdi

🛡️ Module 4: Robustness & Exceptions

Focus: Validation, error handling, and defensive coding.

Exercise 10: Input Sanitization

Goal:

Ask user to input 10 names

Store them in an ArrayList

Reject inputs containing numbers or symbols

Do not advance the counter on invalid input

Effective Java – Item 69

Use exceptions only for exceptional conditions.

Validation should use if/else, not try/catch.

Expected Output:

> Enter name: Mario123
Invalid input: Name cannot contain numbers. Try again.
> Enter name: Mario
Name added.

Exercise 11: Safe List Removal

Goal:

Ask the user for a name to remove

Check existence before removing

Effective Java – Item 54

Return empty collections or Optional, not null.

Expected Output:

> Enter name to remove: Giovanni
Name not found in the list.
> Enter name to remove: Mario
Mario removed successfully.

Exercise 12: Custom Exceptions

Goal:

Create a custom checked exception: ProfanityException

Scan a user-input sentence

If it contains a banned word → throw exception

Otherwise, check if it contains "Java" (case-insensitive)

Effective Java – Items 70 & 72

Use checked exceptions for recoverable business conditions.

Expected Output:

> Input: This is a badword
Exception: Profanity detected in the input!

> Input: I love coding
The sentence does NOT contain 'Java'.

> Input: I love Java programming
The sentence contains the word 'Java'.
