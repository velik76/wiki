# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Compiling](#compiling)
  - [Applets](#applets)
  - [How do I get name of enum constant?](#how-do-i-get-name-of-enum-constant)

## Compiling

For SW compiling use:

```bash
javac example.java
```

## Applets

I could't start applets because icedtea6-plugin was not installed. Here [Link](http://askubuntu.com/questions/84638/why-can-i-not-see-java-applets-in-firefox-8-on-ubuntu-10-04) I found solution how to fix this problem

I found some applets [here](http://www.jgiesen.de/javascript/Beispiele/Beispiele.html)

## How do I get name of enum constant?

This example demonstrate how to user enum‘s name() method to get enum constant name exactly as declared in the enum declaration. package org.kodejava.example.fundamental;

```java
 enum ProcessStatus {
   IDLE, RUNNING, FAILED, DONE;

   @Override
   public String toString() {
       return "Process Status: " + this.name();
   }
 }

 public class EnumNameDemo {
   public static void main(String[] args) {
       for (ProcessStatus ps : ProcessStatus.values()) {
           //
           // Gets the name of this enum constant, exactly as
           // declared in its enum declaration.
           //
           System.out.println(ps.name());
   
           //
           // Here we call to our implementation of the toString
           // method to get a more friendly message of the
           // enum constant name.
           //
           System.out.println(ps.toString());
       }
   }
 }
```

Our program result:
 IDLE
 Process Status: IDLE
 RUNNING
 Process Status: RUNNING
 FAILED
 Process Status: FAILED
 DONE
 Process Status: DONE

