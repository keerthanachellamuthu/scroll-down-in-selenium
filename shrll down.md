How to Scroll Down or Up using Selenium Webdriver
By Jash Unadkat, Community Contributor - February 4, 2023

LinkedIn Facebook Twitter WhatsApp
Scrolling is an essential feature for using any web page on the internet. It doesn’t matter what content a web page hosts, it is almost never possible to place all content on the first fold and do away with the scroll bars, both horizontal and vertical.

For QAs to roll out robust and bug-free web applications, they need to ensure that web pages are thoroughly tested. They especially need to verify that every single UI element is functioning as expected. To do so quickly, they use test automation frameworks like Selenium.

Selenium WebDriver is capable of manipulating the Document Object Model (DOM), and hence it doesn’t require scroll to perform certain actions. However, in some cases, there are certain web elements (for example, a submit button) that become visible only once the user has scrolled down. In such cases, automating the scroll operation becomes necessary.

This article will help QAs on automating horizontal and vertical scroll operations with Selenium.

Before starting with Selenium Scroll operations, let’s quickly understand the role of a JavaScriptexecutor in performing the Scroll operation.

A Scroll is a JavaScript method. The JavaScriptExecutor provides an interface that enables QAs to run JavaScript methods from Selenium scripts. Hence, to scroll up or down with Selenium, a JavaScriptExecutor is a must.

Scroll functions can be defined as follows :
```java
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript("window.scrollBy(0,250)", "");
The scrollBy() method involves two parameters, x, and y, that represent the horizontal and vertical pixel values, respectively.
```
Now let’s discuss the Scroll operation in four scenarios:

How to scroll down and up the webpage in Selenium by a specific number of pixels?
How to scroll down to an element until an element becomes visible?
How to scroll down to the bottom of the webpage using Selenium?
How to scroll to an element horizontally on the webpage?
Table of Contents
How to scroll down on a web page in Selenium by defining the number of pixels
How to scroll down to an element in Selenium until it is visible
How to scroll down to the bottom of the webpage using Selenium?
How to scroll horizontally on a web page to a specific web element using Selenium
How to scroll down on a web page in Selenium by defining the number of pixels
Refer to the script below for performing Selenium scroll-down action on the Firefox browser.

```java
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;

public class HandleScroll 
{

 @Test
 public void scrollDown()
         {
          System.setProperty("webdriver.gecko.driver","D://Selenium    Environment//Drivers//geckodriver.exe");
            WebDriver driver = new FirefoxDriver();
            driver.navigate().to("Website URL");

            //to perform Scroll on application using Selenium
            JavascriptExecutor js = (JavascriptExecutor) driver;
            js.executeScript("window.scrollBy(0,350)", "");
         }
}
```
Run Selenium Tests on Real Devices

Output: The code initializes the Geckodriver for Firefox. Then the Firefox browser is launched, and it navigates to the specified website URL. Once the website loads, the browser window is vertically scrolled down by 350 pixels.

People also read: How to run Selenium tests using Firefox Driver

If a user needs to scroll up, they just need to modify the pixel value of the second parameter (in this case 350) to a negative value (-350).

Refer to the script below:

```java
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;

public class HandleScroll
{
     @Test
     public void scrollDown()

  {
      System.setProperty("webdriver.gecko.driver","D://Selenium Environment//Drivers//geckodriver.exe");

      WebDriver driver = new FirefoxDriver();
      driver.navigate().to("Website URL"); // Specify the website URL

       //to perform Scroll on application using Selenium
       JavascriptExecutor js = (JavascriptExecutor) driver;
       js.executeScript("window.scrollBy(0,-350)", "");
   }

}
```
How to scroll down to an element in Selenium until it is visible
Refer to the Selenium script below.
```java
import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.Test;

public class ScrollByVisibleElement {

    WebDriver driver;
    @Test
    public void ByVisibleElement() {
        System.setProperty("webdriver.gecko.driver","D://Selenium Environment//Drivers//geckodriver.exe"); 
        WebDriver driver = new FirefoxDriver();
        JavascriptExecutor js = (JavascriptExecutor) driver;

        //Launch the application		
        driver.get("https://www.browserstack.com/guide/selenium-scroll-tutorial");

        //Locating element by link text and store in variable "Element"        		
        WebElement Element = driver.findElement(By.linkText("Try Selenium Testing For Free"));

        // Scrolling down the page till the element is found		
        js.executeScript("arguments[0].scrollIntoView();", Element);
    }
}
```
Run Selenium Tests on Real Devices

Output: The above code when executed, will launch the Firefox browser, navigate to the defined URL (Selenium scroll tutorial). Further, it will perform the scroll down until the element with text –  Try Selenium Testing For Free is found.

Selenium Scroll to an element
The Javascript method scrollIntoView() performs the scroll down operation until the mentioned element is completely visible.

People also read: How to handle double click, mouse hover actions in Selenium

How to scroll down to the bottom of the webpage using Selenium?
Refer to the Selenium script below.
```java
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;

public class HandleScroll

{
  @Test
  public void scrollDown()

  {

   System.setProperty("webdriver.gecko.driver","D://Selenium Environment//Drivers//geckodriver.exe");

   WebDriver driver = new FirefoxDriver();
   driver.navigate().to("Website URL"); // Specify the Website URL

   //to perform scroll on an application using Selenium

   JavascriptExecutor js = (JavascriptExecutor) driver;
   js.executeScript("window.scrollBy(0,document.body.scrollHeight)");

  }
}
```
Output: The code above will fetch the maximum height of the webpage from the Document Object Model, and then the scrollBy() method scrolls down to the bottom.

Pro Tip: Want to dive deeper into Selenium implementation on BrowserStack with free interactive courses and lab exercises? Visit Test University

How to scroll horizontally on a web page to a specific web element using Selenium
Refer to the Selenium script below:
```java
import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;

public class HandleScroll 
{

     @Test
     public void ScrollHorizontally()

     {

        System.setProperty("webdriver.gecko.driver","D://Selenium Environment//Drivers//geckodriver.exe");
        WebDriver driver = new FirefoxDriver();

        JavascriptExecutor js = (JavascriptExecutor) driver;

         // Launch the application
         driver.get(" Website URL “); // Specify the website URL

         WebElement Element = driver.findElement(By.linkText("Auto Testing"));

         //This will scroll the page Horizontally till the element is found
         js.executeScript("arguments[0].scrollIntoView();", Element);

      }

}
```
Output: The code above starts the Firefox browser and navigates to the specified URL. Once the page loads, Selenium will automatically detect the specified element on the web page and will scroll horizontally until the element is fully visible in the browser window.

Testing the scroll function is non-negotiable, as it is one of the most fundamental features of a web page. Teams prefer platforms like BrowserStack that help them write a number of automated selenium tests, including operations like scrolling in Selenium for testing websites on multiple browsers like Chrome, Firefox, Safari. Using BrowserStack’s Real Device Cloud you can test your website on 3000+ real devices and browsers for a maximum test coverage. It ensures accurate test results by taking real user conditions into account while testing as opposed to testing on Emulators and Simulators that just mimic the device.

Besides BrowserStack also provides integrations with popular CI/CD tools such as Jenkins, CircleCI, Travis, and more. You can also perform cross browser testing at scale by running tests on multiple device-browser combinations simultaneously with parallel testing using BrowserStack’s Cloud Selenium Grid.

Try BrowserStack for Free

Automation Testing Selenium Selenium Webdriver
Was this post useful? 
