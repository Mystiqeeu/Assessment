# Assessment question 1
[TEST CASES.docx](https://github.com/user-attachments/files/15832140/TEST.CASES.docx)

# Assessment question 2

package com.selenium;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.By;

public class Selenium_assessment {

    WebDriver driver;
    
    public static void main(String[] args) {
        Selenium_assessment test = new Selenium_assessment();
        test.setUp();
        test.runTests();
        test.tearDown();
    }
    
    public void setUp() {
        System.setProperty("webdriver.chrome.driver", "Z:\\KERJA\\chromedriver-win64\\chromedriver-win64\\chromedriver.exe");
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get("https://www.xe.com/");
    }
    
    public void runTests() {
        testConvertUSDToMYR();
        testConvertWithEmptyAmountField();
        testConvertGBPToMYRWithLargeAmount();
        testConvertUSDToMYRWithDecimalAmount();
        testConvertUSDToMYRWithSwap();
    }
    
    public void testConvertUSDToMYR() {
        try {
            driver.findElement(By.id("amount")).sendKeys("1.00");
            driver.findElement(By.id("midmarketFromCurrency-descriptiveText")).sendKeys("USD - US Dollar");
            driver.findElement(By.id("midmarketToCurrency-descriptiveText")).sendKeys("MYR - Malaysian Ringgit");
            driver.findElement(By.tagName("button")).click();
            WebElement result = driver.findElement(By.id("conversionResult"));
            if (result.isDisplayed()) {
                System.out.println("testConvertUSDToMYR passed");
            } else {
                System.out.println("testConvertUSDToMYR failed");
            }
        } catch (Exception e) {
            System.out.println("testConvertUSDToMYR failed with exception: " + e.getMessage());
        }
    }
    
    public void testConvertWithEmptyAmountField() {
        try {
            WebElement amountField = driver.findElement(By.id("amount"));
            amountField.clear();
            amountField.sendKeys("0");
            driver.findElement(By.id("midmarketFromCurrency-descriptiveText")).sendKeys("USD - US Dollar");
            driver.findElement(By.id("midmarketToCurrency-descriptiveText")).sendKeys("MYR - Malaysian Ringgit");
            WebElement convertButton = driver.findElement(By.tagName("button"));
            convertButton.click();
            WebElement error = driver.findElement(By.id("errorMessage"));
            if (error.isDisplayed()) {
                System.out.println("testConvertWithEmptyAmountField passed");
            } else {
                System.out.println("testConvertWithEmptyAmountField failed");
            }
        } catch (Exception e) {
            System.out.println("testConvertWithEmptyAmountField failed with exception: " + e.getMessage());
        }
    }
    
    public void testConvertGBPToMYRWithLargeAmount() {
        try {
            driver.findElement(By.id("amount")).sendKeys("10000000.00");
            driver.findElement(By.id("midmarketFromCurrency-descriptiveText")).sendKeys("GBP - British Pound");
            driver.findElement(By.id("midmarketToCurrency-descriptiveText")).sendKeys("MYR - Malaysian Ringgit");
            driver.findElement(By.tagName("button")).click();
            WebElement result = driver.findElement(By.id("conversionResult"));
            if (result.isDisplayed()) {
                System.out.println("testConvertGBPToMYRWithLargeAmount passed");
            } else {
                System.out.println("testConvertGBPToMYRWithLargeAmount failed");
            }
        } catch (Exception e) {
            System.out.println("testConvertGBPToMYRWithLargeAmount failed with exception: " + e.getMessage());
        }
    }
    
    public void testConvertUSDToMYRWithDecimalAmount() {
        try {
            driver.findElement(By.id("amount")).sendKeys("35.67");
            driver.findElement(By.id("midmarketFromCurrency-descriptiveText")).sendKeys("USD - US Dollar");
            driver.findElement(By.id("midmarketToCurrency-descriptiveText")).sendKeys("MYR - Malaysian Ringgit");
            driver.findElement(By.tagName("button")).click();
            WebElement result = driver.findElement(By.id("conversionResult"));
            if (result.isDisplayed()) {
                System.out.println("testConvertUSDToMYRWithDecimalAmount passed");
            } else {
                System.out.println("testConvertUSDToMYRWithDecimalAmount failed");
            }
        } catch (Exception e) {
            System.out.println("testConvertUSDToMYRWithDecimalAmount failed with exception: " + e.getMessage());
        }
    }
    
    public void testConvertUSDToMYRWithSwap() {
        try {
            driver.findElement(By.id("amount")).sendKeys("1.00");
            driver.findElement(By.id("midmarketFromCurrency-descriptiveText")).sendKeys("USD - US Dollar");
            driver.findElement(By.id("midmarketToCurrency-descriptiveText")).sendKeys("MYR - Malaysian Ringgit");
            driver.findElement(By.tagName("button")).click();
            WebElement result = driver.findElement(By.id("conversionResult"));
            if (result.isDisplayed()) {
                System.out.println("testConvertUSDToMYRWithSwap passed (before swap)");
            } else {
                System.out.println("testConvertUSDToMYRWithSwap failed (before swap)");
            }
            driver.findElement(By.cssSelector(".sc-df72c595-0.eNeMob")).click(); // Swap button
            driver.findElement(By.tagName("button")).click();
            WebElement swappedResult = driver.findElement(By.id("conversionResult"));
            if (swappedResult.isDisplayed()) {
                System.out.println("testConvertUSDToMYRWithSwap passed (after swap)");
            } else {
                System.out.println("testConvertUSDToMYRWithSwap failed (after swap)");
            }
        } catch (Exception e) {
            System.out.println("testConvertUSDToMYRWithSwap failed with exception: " + e.getMessage());
        }
    }
    
    public void tearDown() {
        if (driver != null) {
            driver.quit();
        }
    }
}


Assessment question 3

Got a problem with installing Java in my PC, hence, the code i try and error by looking at my Java code from before and seek some knowledge from YouTube on how to use selenium.
