# Air_Bnb
package com.selenium;

import java.awt.AWTException;
import java.awt.Robot;
import java.awt.Toolkit;
import java.awt.datatransfer.StringSelection;
import java.awt.event.KeyEvent;
import java.util.ArrayList;
import java.util.Set;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

import io.github.bonigarcia.wdm.WebDriverManager;

public class Air_Bnb {
	public static void main(String[] args) throws AWTException, InterruptedException {
		WebDriverManager.chromedriver().setup();
		WebDriver driver = new ChromeDriver();
		driver.manage().window().maximize();
		driver.get("https://www.airbnb.co.in/");
		driver.manage().timeouts().implicitlyWait(70, TimeUnit.SECONDS);
		driver.findElement(By.xpath("(//button[@aria-expanded='false'])[2]")).click();
		Robot r = new Robot();
		r.keyPress(KeyEvent.VK_DOWN);
		r.keyRelease(KeyEvent.VK_DOWN);
		r.keyPress(KeyEvent.VK_DOWN);
		r.keyRelease(KeyEvent.VK_DOWN);
		r.keyPress(KeyEvent.VK_ENTER);
     	r.keyPress(KeyEvent.VK_ENTER);
     	Thread.sleep(3000);
     	JavascriptExecutor js = (JavascriptExecutor)driver;
		WebElement ck = driver.findElement(By.xpath("//div[text()='Continue with email']")); 
		js.executeScript("arguments[0].click();", ck);
		driver.findElement(By.id("email-login-email")).sendKeys("shyamalasai29@gmail.com");
		driver.findElement(By.xpath("//span[@class='t1dqvypu dir dir-ltr']")).click();
		driver.findElement(By.id("email-signup-password")).sendKeys("Airbnb@2023");
		Thread.sleep(3000);
		WebElement ckl = driver.findElement(By.xpath("//span[text()='Log in']"));
		js.executeScript("arguments[0].click();", ckl);
		driver.findElement(By.xpath("//div[text()='Switch to hosting']")).click();
    	driver.findElement(By.linkText("Complete your listing")).click();
    	ArrayList<String> windowHandles = new ArrayList<>(driver.getWindowHandles());
    	driver.switchTo().window(windowHandles.get(1));
     	driver.findElement(By.xpath("//button[text()='Next']")).click();
    	Thread.sleep(3000);
     	driver.findElement(By.xpath("//button[text()='Upload from your device']")).click();
     	r.delay(2000);
     	StringSelection ss = new StringSelection("Downloads\\h 1.jpg");
     	Toolkit.getDefaultToolkit().getSystemClipboard().setContents(ss, null);
     	r.keyPress(KeyEvent.VK_CONTROL);
     	r.keyPress(KeyEvent.VK_V);
     	r.keyRelease(KeyEvent.VK_CONTROL);
     	r.keyRelease(KeyEvent.VK_V);
     	r.keyPress(KeyEvent.VK_ENTER);
     	r.keyRelease(KeyEvent.VK_ENTER);
    	Thread.sleep(3000);
     	driver.findElement(By.xpath("//button[text()='Upload from your device']")).click();
     	r.delay(2000);
     	StringSelection s = new StringSelection("C:\\Users\\yuvaa\\OneDrive\\Pictures\\Screenshots\\h 2.jpg");
     	Toolkit.getDefaultToolkit().getSystemClipboard().setContents(s, null);
     	r.keyPress(KeyEvent.VK_CONTROL);
     	r.keyPress(KeyEvent.VK_V);
     	r.keyRelease(KeyEvent.VK_CONTROL);
     	r.keyRelease(KeyEvent.VK_V);
     	r.keyPress(KeyEvent.VK_ENTER);
     	r.keyRelease(KeyEvent.VK_ENTER);
     	driver.findElement(By.xpath("(//div[@role='button'])[1]")).click();
	}
}
