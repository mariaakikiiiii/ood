# ood
# Library Management System

## Overview
This Library Management System is a Java-based application that allows users to manage a library where items (books, newspapers, DVDs) can be bought or borrowed. The system consists of different user types, including **Managers**, **Librarians**, and **Customers**, who interact with the library in various ways.

## Features
- **User Authentication:** Managers, Librarians, and Customers can sign up, log in, and log out.
- **Item Management:** Books, DVDs, and newspapers can be added, bought, or borrowed.
- **Customer Actions:** Customers can buy items, borrow items, and manage memberships.
- **Librarian Actions:** Librarians can manage the library and oversee transactions.
- **Manager Actions:** Managers can create and delete librarians, set salaries, and manage the library system.
- **Balance Management:** Customers have a balance they can use to purchase items or memberships.

## Classes Summary

### 1. `Item`
Base class representing an item in the library.
- Attributes: `stock`, `itemId`, `borrowPrice`, `buyPrice`
- Methods: Getters and setters for item attributes.

### 2. `Book` (extends `Item`)
Represents a book in the library.
- Additional attributes: `title`, `author`, `publisher`, `ISBN`, `genres`

### 3. `Dvd` (extends `Item`)
Represents a DVD available in the library.
- Additional attributes: `filmName`, `genre`

### 4. `NewsPaper` (extends `Item`)
Represents a newspaper.
- Additional attributes: `date`

### 5. `User`
Abstract base class for all users.
- Attributes: `userId`, `username`, `phoneNumber`, `password`
- Methods: Login, logout, and authentication management.

### 6. `Customer` (extends `User`)
Represents a customer who can buy or borrow items.
- Additional attributes: `isMember`, `balance`, `borrowedItems`
- Methods: `signUp()`, `buyItem()`, `borrowItem()`, `buyMembership()`, `returnItem()`

### 7. `Librarian` (extends `User`)
Represents a librarian who manages the library.
- Additional attributes: `salary`, `jobStatus`
- Methods: `signUp()` (specific to librarian registration)

### 8. `Manager` (extends `Librarian`)
Represents a manager with authority over librarians and the library system.
- Additional methods:
  - `createLibrarian()`: Adds a new librarian.
  - `createManager()`: Creates another manager (admin only).
  - `deleteManager()`: Deletes a manager (admin only).
  - `deleteLibrarian()`: Removes a librarian.
  - `setSalary()`: Updates a librarian’s salary.
  - `viewAllSalaries()`: Displays salaries of all librarians and managers.
  - `viewAllLibrarians()`: Lists all librarians.

### 9. `LibrarySystem`
Manages users and items in the library.
- Methods:
  - `addItem()`, `removeItem()`: Manage library items.
  - `addUser()`, `removeUser()`: Manage users.
  - `authenticateUser()`: Verifies login credentials.
  - `getAllItems()`, `getAllUsers()`: Retrieve all records.

### 10. `Library`
Represents the library itself.
- Attributes: `name`, `phoneNumber`, `openHours`, `catalog`
- Methods: `addItem()`, `manageUsers()`, `buyItem()`, `borrowItem()`

### 11. `Main`
The entry point of the application where users can log in, sign up, buy items, and borrow books.
- Handles user interaction, library transactions, and account management.

## How It Works
1. **User Signup/Login**
   - Customers, librarians, and managers can sign up with their details.
   - A customer can buy a membership for discounts.
   - Users can log in using their phone number and password.

2. **Buying & Borrowing Items**
   - Customers can buy books, DVDs, and newspapers if they have enough balance.
   - Borrowed items must be returned within a specific period.

3. **Library & User Management**
   - Librarians oversee inventory and customer transactions.
   - Managers handle librarian and manager roles, salaries, and overall system management.

## How to Run
1. Compile the Java files:
   ```sh
   javac *.java
   ```
2. Run the application:
   ```sh
   java Main
   ```

## Future Enhancements
- Implement a graphical user interface (GUI) for better interaction.
- Add a database to store user data and item inventory.
- Introduce overdue penalties for borrowed items.
- Improve security by hashing passwords.

## Author
Created as a project to demonstrate Object-Oriented Programming (OOP) concepts in Java.

