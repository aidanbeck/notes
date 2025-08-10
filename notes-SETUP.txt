==== Java Setup ====
https://github.com/readme/featured/java-programming-language?utm_source=github&utm_medium=referral&utm_campaign=&scid=&utm_content=octoverse

Java
- high level
- object oriented
- platform independent bytecode
- 4th most popular language on Github

Java Runtime Enviornment //combine with above
- Java compiles into platform-independent bytecode
- This bytecode runs on the Java Virtual Machine, the interpreter
- A Java Program can run on any machine with JRE installed
- Java is compiled and interpreted simultaneously
// what is the difference between JVM and JRE

Java Trifecta (Father, Son, Holy Spirit)
- Java Runtime Enviornment
- Java Virtual Machine
- Java Development Kit


Java Runtime Enviornment (JRE)
- communicates between Operating System & Java Program
- gains access to memory & files
- If installed, Java can run.
JRE Core Components
- Bytecode Verifier: compiler verifies code before loading into JVM
- Interpreter: creates the JVM instance that runs the program
- ClassLoader: A collection of Class libraries

Java Virtual Machine (JVM)
- pretends to be a computer
- consistent enviornment to run in
- translates Java Bytecode into Machine Code
- settings can be altered, such as memory usage

Java Development Kit (JDK)
- collection of software tools
- contains javac (java compiler) creates bytecode
- contains the JVM and JRE too

Included in the JDK
https://docs.oracle.com/en/java/javase/11/tools/tools-and-command-reference.html
Development Tools
- javac - compiler
- java - launches java app
- javadoc - generates HTML pages of API docs //of your project? or of java itself?
- jar - archives classes & resources, restores from archive
JRE
- bytecode verifier
- libraries
JVM
- java interpreter
- garbage collector
- JIT compiler //?


# Getting Started with Java
- Oracle has a JVM, but everyone uses the OpenJDK JVM
- Java 8, 11, 17, and 21 are supported. We will use 17.

Install the JDK
- https://www.openlogic.com/openjdk-downloads
- Download Java 17 JDK for your OS (msi for installer)
- In your terminal (any terminal) enter `java --version` to verify install

IntelliJ: Java's Favorite IDE
- bonus features to enhance Java development
- code completion
- debugging
- its own compiler

Install IntelliJ
- https://www.jetbrains.com/idea/download (ensure you are downloading for the correct platform)
- Main version is paid, get the Community Edition
- Install the program
- Reboot

Connect IntelliJ with Github
- Download & Install Github Desktop
- Sign in with account
- File > Options > Integrations
- Set External Editor as IntelliJ Idea Community Editor

Create a new IntelliJ Project
- File > New Project
- name-the-project, choose location to hold it
- add JDK from disk
- choose Mavern for the build system.

Example Code
- Find Main.java, it should be a simple hello world program.
- Run it by pressing the green play button
- As a real program, it would open a command prompt window
- In IntelliJ, it outputs into our terminal

Controlling with Github
- Create a Repository and copy the address
- On the left side, ... > Commit
- Click "Create Git Repository"
- Defaults to the location of your project, which is ideal
- Check "unversioned files" to add all files
- Write a comment, and press "Commit & Push"
- In the opened Dialogue box, hit "Define Remote". Enter the repository address.
- Push.
- Log in via github
- Click the folder to return.