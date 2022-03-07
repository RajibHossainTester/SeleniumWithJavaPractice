# SeleniumWithJavaPractice
package day11;

import java.util.List;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;

public class CreateanAccount {


	public static void main(String[] args) throws InterruptedException {
		//1) Open the Browser9 Chrome/IE/ Firefox)
		System.setProperty("webdriver.chrome.driver", "C:/Users/RHami/Downloads/chromedriver_win32 (2)/chromedriver.exe");
		
		
		WebDriver driver =new ChromeDriver();
		//ChromeDriver if you do not want to use WebDriver
		
		//2. Open URL http://opensource.demo.orangehrmlive.com	
		driver.get("http://automationpractice.com/index.php");
		System.out.println(driver.getTitle());
		driver.manage().window().maximize();
		driver.manage().deleteAllCookies();
		
		
		//Click the Sign in button for a new register
		driver.findElement(By.className("login")).click();
		
		//Input the email address
		driver.findElement(By.xpath("//*[@id='email_create']")).sendKeys("rajib777@yopmail.com");
		//Click the Create an account
		driver.findElement(By.id("SubmitCreate")).click();
		
		Thread.sleep(3000);
		
		
		
		
		
		//Capture title of the home page
		//http://automationpractice.com
		String Actual_url=driver.getCurrentUrl();  //Capture the title of the current page 
		
		String Expected_url="http://automationpractice.com/index.php?controller=authentication&back=my-account#account-creation";
		//Verify the title of the page: automationpractice.com
		
		if(Actual_url.equals(Expected_url))
		{
			System.out.println("Test Passed");
		}
		else{
			System.out.println("Test Failed");
		}
		
		
		
		// Sleep time needs to be added for the 	
		//Click the radio button for male
		
		WebElement radioBtn1= driver.findElement(By.xpath("//input[@type='radio' and @value='1']")); 
		radioBtn1.click();
		System.out.println("Male radio button is selected: "+radioBtn1.isSelected());
		//This is for the Female button
		WebElement radioBtn2= driver.findElement(By.xpath("//input[@type='radio' and @value='2']"));
		//radioBtn2.click();
		System.out.println("Male radio button is selected: "+radioBtn2.isSelected());
	
		Thread.sleep(3000);
		
		
		//Input the name
		
		driver.findElement(By.xpath("//*[@id='customer_firstname']")).sendKeys("Rajib");
		driver.findElement(By.xpath("//*[@id='customer_firstname']")).clear();
	
		Thread.sleep(3000);
		
		
		//Check if the FirstName box is not taking any Numeric Number
		
		WebElement invalidFirstNamewithnumeric=driver.findElement(By.xpath("//*[@id='customer_firstname']"));
		invalidFirstNamewithnumeric.sendKeys("1234");
		System.out.println("Invalid First Name : "+invalidFirstNamewithnumeric.isSelected());
		driver.findElement(By.xpath("//*[@id='customer_firstname']")).clear();
		WebElement invalidFirstNamewithnumericS = driver.findElement(By.xpath("//*[@id='customer_firstname']"));
		System.out.println("Invalid First Name with Special Character : "+invalidFirstNamewithnumericS.isSelected());
		driver.findElement(By.xpath("//*[@id='customer_firstname']")).clear();
		driver.findElement(By.xpath("//*[@id='customer_firstname']")).sendKeys("Rajib");
		
		
		//Check if the LastName box id not tacking any invalid numbers.
		
		WebElement invalidLastNamewithnumeric=driver.findElement(By.xpath("//*[@id='customer_lastname']"));
		invalidLastNamewithnumeric.sendKeys("1234");
		System.out.println("Invalid Last Name : "+invalidLastNamewithnumeric.isSelected());
		driver.findElement(By.xpath("//*[@id='customer_lastname']")).clear();
		
		Thread.sleep(3000);
		
		//Special Character
		
		WebElement invalidLastNamewithnumericS = driver.findElement(By.xpath("//*[@id='customer_lastname']"));
		System.out.println("Invalid Last Name with Special Character : "+invalidLastNamewithnumericS.isSelected());
		driver.findElement(By.xpath("//*[@id='customer_lastname']")).clear();
		driver.findElement(By.xpath("//*[@id='customer_lastname']")).sendKeys("Hossain");
		Thread.sleep(3000);
		
		
		//Special Character in the Password input box
		
		driver.findElement(By.xpath("//*[@id='passwd']")).sendKeys("Test1234");
		
		
		
		//Date of birth drop down menu
		//We will select the date first 
		WebElement element= driver.findElement(By.xpath("//select[@id='days']"));
		Select Date= new Select(element);
		Date.selectByValue("23");
		WebElement FirstElemnt = Date.getFirstSelectedOption();
		System.out.println("First Element = "+FirstElemnt.getText());
		List<WebElement> listOptions = Date.getOptions();
		for (WebElement webElement : listOptions){
		System.out.println("options -"+webElement.getText());
		}
		
		
		//This part will select the Month from the drop down menu
		WebElement element1= driver.findElement(By.xpath("//*[@id='months']"));
		Select month= new Select(element1);
		month.selectByValue("7");
		WebElement FirstElemnt1 = month.getFirstSelectedOption();
		System.out.println("First Element = "+FirstElemnt1.getText());
		List<WebElement> listOptions1 = month.getOptions();
		for (WebElement webElement : listOptions1){
		System.out.println("options -"+webElement.getText());
		}
		
		//This part will click the year drop-down menu
		
		WebElement elementyear= driver.findElement(By.xpath("//*[@id='years']"));
		Select year= new Select(elementyear);
		year.selectByValue("2020");
		WebElement FirstElemntyear = year.getFirstSelectedOption();
		System.out.println("First Element = "+FirstElemntyear.getText());
		List<WebElement> listOptionsyear = month.getOptions();
		for (WebElement webElement : listOptionsyear){
		System.out.println("options -"+webElement.getText());
		}
		
		
		//Move the element to the address element
		WebElement address = driver.findElement(By.xpath("//*[@id='address2']"));
		Actions actions = new Actions(driver);
		actions.moveToElement(address);
		actions.perform();
		
		//Click the check box
			driver.findElement(By.name("newsletter")).click();
			Thread.sleep(2000);
			driver.findElement(By.name("optin")).click();
			Thread.sleep(5000);
		//Un.check the check boxes
			driver.findElement(By.name("newsletter")).click();
			Thread.sleep(2000);
			driver.findElement(By.name("optin")).click();
			
		//Fill the Address Line one 
			driver.findElement(By.xpath("//*[@id='company']")).sendKeys("PurnaTraders");
			//Fill the Address Line Two	
			driver.findElement(By.xpath("//*[@id='address1']")).sendKeys("250 Colony St");
		//Address Text box
			driver.findElement(By.xpath("//*[@id='address2']")).sendKeys("405");
			//Add the city 
		
			driver.findElement(By.xpath("//*[@id='city']")).sendKeys("Vancouver");
			
		//Select State Drop down 
			
			WebElement stateElement = driver.findElement(By.xpath("//*[@id='id_state']"));
			Select state = new Select(stateElement);
			state.selectByValue("10");
			WebElement StateSelect = state.getFirstSelectedOption();
			System.out.println("First Element = "+StateSelect.getText());
			List<WebElement> listOptions11 = Date.getOptions();
			for (WebElement webElement : listOptions11){
			System.out.println("options -"+webElement.getText());
			}
				
		//Postal Code
			driver.findElement(By.xpath("//*[@id='postcode']")).sendKeys("12453");
			
			
			WebElement CountryElement = driver.findElement(By.xpath("//*[@id='id_country']"));
			Select country = new Select(CountryElement);
			country.selectByValue("21");
			WebElement CountrySelect = country.getFirstSelectedOption();
			System.out.println("CountryName = "+CountrySelect.getText());
			List<WebElement> listOptions111 = country.getOptions();
			for (WebElement webElement : listOptions111){
			System.out.println("options -"+webElement.getText());
			}
			
		//Additional information text box
			
		driver.findElement(By.xpath("//*[@id='other']")).sendKeys("This is gonna be the fisrt test case");
		
		//Enter the phone number
		driver.findElement(By.xpath("//*[@id='phone']")).sendKeys("0123456789");
		
		
		//Mandatory Phone Number
		driver.findElement(By.xpath("//*[@id='phone_mobile']")).sendKeys("9874561230");
		
		//Assign an address alias for future reference text box
		//Clear the text box
		driver.findElement(By.xpath("//*[@id='alias']")).clear();
		driver.findElement(By.xpath("//*[@id='alias']")).sendKeys("9874561230");
		
		driver.findElement(By.xpath("//*[@id='submitAccount']")).click();
		
		
		//Click the home button
		driver.findElement(By.xpath("//*[@id='center_column']/ul/li/a")).click();
		Thread.sleep(3000);
		//Click the sign out Button
		driver.findElement(By.xpath("//*[@id='header']/div[2]/div/div/nav/div[2]/a")).click();
		
		
		
		
		
		//Close the browser
		driver.close();//Will close the current browser
		
	}
}
