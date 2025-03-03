# ood
# Library System

## Overview
The Library System is a simple Java application that models the functionalities of a library, allowing users to manage items, sign up customers, and process purchases. The system includes different roles, such as librarians and customers, with various features for each role.

## Features
- **User Management**: Sign up, log in, and log out users (librarians and customers).
- **Item Management**: Add, remove, and manage items such as books, DVDs, and newspapers.
- **Purchasing**: Customers can buy items with or without a membership, with discounts available for members.

## Classes

### User Class
```java
import java.util.ArrayList;
import java.util.Scanner;

public abstract class User {
    private Scanner scanner = new Scanner(System.in);
    private int nbUsers;
    private int userId;
    private String fname;
    private String lname;
    private String phoneNumber;
    private String password;

    // Constructor with all parameters
    public User(int userId, String fname, String lname, String phoneNumber, String password, int nbUsers) {
        this.userId = userId;
        this.fname = fname;
        this.lname = lname;
        this.phoneNumber = phoneNumber;
        this.password = password;
        this.nbUsers = nbUsers;
    }

    // Constructor with nbUsers only
    public User(int nbUsers) {
        this(-1, "", "", "", "", nbUsers);
    }

    // Default constructor
    public User() {
        this(-1, "", "", "", "", -1);
    }

    // Copy constructor
    public User(User user) {
        this(user.getUserId(), user.getFname(), user.getLname(), user.getPhoneNumber(), user.getPassword(), user.getNbUsers());
    }

    // Getters and Setters
    public int getNbUsers() { return nbUsers; }
    public int getUserId() { return userId; }
    public String getFname() { return fname; }
    public String getLname() { return lname; }
    public String getPhoneNumber() { return phoneNumber; }
    public String getPassword() { return password; }
    
    public void setUserId(int userId) { this.userId = userId; }
    public void setFname(String fname) { this.fname = fname; }
    public void setLname(String lname) { this.lname = lname; }
    public void setPhoneNumber(String phoneNumber) { this.phoneNumber = phoneNumber; }
    public void setPassword(String password) { this.password = password; }
    public void setNbUsers(int nbUsers) { this.nbUsers = nbUsers; }

    @Override
    public String toString() {
        return "First name: " + fname + " Last name: " + lname + " Phone number: " + phoneNumber + " Password: " + password;
    }

    private boolean checkPhoneNumber(String phoneNumber, ArrayList<User> users) {
        if (phoneNumber.length() != 11) {
            return false;
        }
        for (User user : users) {
            if (phoneNumber.equals(user.getPhoneNumber())) {
                return false;
            }
        }
        return true;
    }

    public int signUp(ArrayList<User> users, int nbUsers, User user) {
        System.out.println("Enter your phone number: ");
        String phoneNum = scanner.nextLine();
        System.out.println("Enter your password: ");
        String pass = scanner.nextLine();
        System.out.println("Enter your first name: ");
        String fn = scanner.nextLine();
        System.out.println("Enter your last name: ");
        String ln = scanner.nextLine();

        if (checkPhoneNumber(phoneNum, users)) {
            user.setUserId(nbUsers);
            user.setNbUsers(nbUsers);
            user.setFname(fn);
            user.setLname(ln);
            user.setPassword(pass);
            user.setPhoneNumber(phoneNum);
            System.out.println("Your user ID is: " + userId);
            return 1;
        } else {
            System.out.println("Invalid phone number");
            return -1;
        }
    }

    public int login(ArrayList<User> users, int Id, String pass) {
        System.out.println("Enter your userID: ");
        int x = -1;
        int p = 0;
        for (int i = 0; i < users.size(); i++) {
            if (Id == users.get(i).getUserId()) {
                if (pass.equals(users.get(i).getPassword())) {
                    x = 1;
                    break;
                } else {
                    x = -2;
                }
            }
        }
        if (x == 1) {
            System.out.println("Login successful. Welcome " + users.get(p).getFname());
            return Id;
        } else if (x == -1) {
            System.out.println("Login failed. Invalid userID.");
            return -1;
        } else {
            System.out.println
