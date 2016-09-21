# octane-cucumber-jvm
The ALM Octane cucumber-jvm formatter plugin enables uploading cucumber-jvm tests into ALM Octane.

## Workflow
1. Use ALM Octane cucumber-jvm formatter in your JUnit cucumber tests. See the instructions below.
2. When running the tests, the plugin outputs a file named gherkinNGAResults.xml_ with the results.
3. The ALM Octane plugin for Jenkins reads this file and uploads the results to ALM Octane. For details how to configure the ALM Octane Jenkins plugin, see the ALM Octane online help.
4. View the results in your Gherkin test in ALM Octane

## Prerequisites
* Use Java and the cucumber-jvm library to develop cucumber tests.
* Use Junit Runner to run the cucumber-jvm library. For details, see https://cucumber.io/docs/reference/jvm#junit-runner.

The JUnit runner uses the JUnit framework to run Cucumber. 
The default configuration requires a single empty class with an annotation that looks like this:
```java
package mypackage;
import cucumber.api.junit.Cucumber;
import org.junit.runner.RunWith;

@RunWith(Cucumber.class)
public class RunCukesTest {

}
```

## To configure the octane-cucumber-jvm in your project
1. Add a dependency in your POM file:
```xml
<dependencies>
    <dependency>
        <groupId>com.hpe.alm.octane</groupId>
        <artifactId>octane-cucumber-jvm</artifactId>
        <version>12.53.8</version>
    </dependency>
</dependencies>
```

2. Import the cucumber-jvm formatter into the Junit Runner class. For example:
```java
import com.hpe.alm.octane.OctaneCucumber;
```

3. Change the cucumber.class to OctaneCucumber.class. For example:
```java
Package feature.manualRunner;

Import com.hpe.alm.octane.OctaneCucumber;
Import cucumber.api.CucumberOptions;
Import org.junit.runner.RunWith;

@RunWith(OctaneCucumber.class)
@CucumberOptions(plugin={"junit:junitResult.xml"},
    features="src/test/resources/feature/manualRunner")
Public class ManualRunnerTest{

}
```

