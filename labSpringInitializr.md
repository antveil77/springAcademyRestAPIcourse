# Lab : Spring Initializr  
Notes du lab Sring Initializr  
https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/bootstrap-lab

## Create project ##  

### Spring Initializr ###  
Select the following options:

Project: Gradle - Groovy
Language: Java
SpringBoot: Choose the latest 3.3.X version
Enter the following values next to the corresponding Project Metadata fields:

Group: example
Artifact: cashcard
Name: CashCard
Description: CashCard service for Family Cash Cards
Packaging: Jar
Java: 17
Note: You don't have to enter the "Package name" field -- Spring Initializr will fill this in for you!

Select the ADD DEPENDENCIES... button from the Dependencies panel.

Select the following option, since we know that we'll be creating a web application:

Web options: Spring Web
Later on in the course, you'll be adding additional dependencies without using Spring Initializr.



Click the CREATE button. Spring Initializr generates a zip file of code and unzips it in your home directory.

From the command line in the Terminal tab, enter the following commands to use the gradle wrapper to build and test the generated application.

Go to the cashcard directory in the Terminal dashboard tab.

[~] $ cd cashcard
[~/cashcard] $
Next, run the ./gradlew build command:

[~/cashcard] $ ./gradlew build
The output shows that the application passed the tests and was successfully built.

[~/cashcard] $ ./gradlew build
Downloading https://services.gradle.org/distributions/gradle-bin.zip
............10%............20%............30%.............40%............50%............60%............70%.............80%............90%............100%

Welcome to Gradle!
...
Starting a Gradle Daemon (subsequent builds will be faster)

> Task :test
...
BUILD SUCCESSFUL in 39s
7 actionable tasks: 7 executed
