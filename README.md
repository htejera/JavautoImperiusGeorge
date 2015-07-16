# Javauto ImperiusGeorge Client

## Introduction

This project is a simple [Javauto](https://github.com/matthewdowney/javauto) [ImperiusGeorge](https://github.com/lookout/ImperiusGeorge) client. Remote-control/execute Java on Android phones via Javauto. It works on Android 4.1+ simply with Android device attached via adb, no need to install anything on Android device.

Powered by [Javauto](http://javauto.org). We welcome all contributions. New to Javauto? Not a problem, Javauto is [easy to learn!](http://javauto.org/docs/getting-started.html)

Website: 

###Example

```groovy
global String app = "appinventor.ai_henrytejera.ImperiusGeorge";
global String mainActivity = "/.Screen1";
global String apk = "ImperiusGeorge.apk";
verbose = true;

func void setup(){
  install("","-r", apk);
  startServer("", "localhost", "1337", "3000");
  startApp(app + mainActivity);
  assertThatCurrentActivityIs("ImperiusGeorge");
}

func void tearDown(){
  stopApp(app);
}

func void testInputs(){
  clickAndWait("Inputs Screen");
  assertThatCurrentActivityIs("InputsScreen");
  enterText("0", "Imperius"); 
  enterText("1", "Password"); 
  pressBack();
  click("Add");
  assertThatTextIsPresent("Ready");
  takeScreenshot("InputScreen");
  click("Back");
  assertThatCurrentActivityIs("ImperiusGeorge");
}

func void testSpinner(){
  clickAndWait("Spinner Screen");
  assertThatCurrentActivityIs("SpinnerScreen");
  click("A");
  click("B");
  takeScreenshot("SpinnerScreen");
  click("Back");
  assertThatCurrentActivityIs("ImperiusGeorge");
}

func void testListScreen(){
  clickAndWait("List picker Screen");
  assertThatCurrentActivityIs("ListPickerScreen");
  click("ListPicker");
  scrollDown(20 ,20);
  click("Edwin (1464*) Abel");
  takeScreenshot("ListPickerScreen");
  assertThatTextIsPresent("Edwin (1464*) Abel");
  click("Back");
  assertThatCurrentActivityIs("ImperiusGeorge");
}

setup();
  testInputs();
  testSpinner();
  testListScreen();
tearDown();
```
