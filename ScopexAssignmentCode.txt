package org.Scopex;

import org.apache.commons.io.FileUtils;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;
import org.testng.Assert;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

import java.io.File;
import java.io.IOException;
import java.time.Duration;

public class ScopexAssesment
{

    public static WebDriver driver;


    @BeforeTest
    public static void init() {
        System.setProperty("webdriver.chrome.driver", "C:\\Ani\\SeleniumTesting\\chromedriver.exe");
        driver = new ChromeDriver();
        driver.manage().window().maximize(); //To maximize the window

    }


    @Test(description = "TC_001-Visit the web page URL specified as a parameter ", priority = 1)
    public void loginTest()
    {
        driver.get("https://scopex.money/");

    }

    @Test(description = "TC_002-Locate the send money page ", priority = 2)
            public void locateNavigationMenu() throws InterruptedException, IOException {
       // Locate the Send Money on the Navigation Menu

        WebElement sendMoney= driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div/span/nav/div/div/div[2]/div/div/ul/li[1]/a"));
            sendMoney.click();

           String expectedTitle="ScopeX";
           String actualTitle= driver.getTitle();
        System.out.println("actual title " +actualTitle);
        Assert.assertEquals(actualTitle,expectedTitle,"Not in the Send Money Page");


        TakesScreenshot ts = (TakesScreenshot) driver;
        File sourceFile = ts.getScreenshotAs(OutputType.FILE);
        File destFile = new File("Screenshots/" + System.currentTimeMillis()
                + ".png");
        FileUtils.copyFile(sourceFile, destFile);

           WebElement homePage= driver.findElement(By.xpath("/html/body/div/div/form/div/nav/div/div/div[1]/a/img"));
                     homePage.click();
    }

    @Test(description = "TC_003-Locate the FAQs on the  page ", priority = 3)
    public void faqs() throws InterruptedException, IOException {
        // Locate the Send Money on the Navigation Menu

        WebElement faqs= driver.findElement(By.xpath("/html/body/div/div/div[1]/div/span/nav/div/div/div[2]/div/div/ul/li[2]/a"));
        faqs.click();

        WebElement faqFrame= driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/span/div/div/div/div[1]/h3"));
        String actualTitle=faqFrame.getText();


        String expectedTitle="FAQ's";
        System.out.println("actual title " +actualTitle);
        Assert.assertEquals(actualTitle,expectedTitle,"Not in the FAQs Page");

        TakesScreenshot ts = (TakesScreenshot) driver;
        File sourceFile = ts.getScreenshotAs(OutputType.FILE);
        File destFile = new File("Screenshots/" + System.currentTimeMillis()
                + ".png");
        FileUtils.copyFile(sourceFile, destFile);


        WebElement homePage= driver.findElement(By.xpath("/html/body/div/div/nav/div/div/div[1]/a/img"));
        homePage.click();

    }

    @Test(description = "TC_004-Locate the Contactus on the  page ", priority = 4)
    public void Contactus() throws InterruptedException, IOException {
        // Locate the Send Money on the Navigation Menu

        WebElement contactus= driver.findElement(By.xpath("/html/body/div/div/div[1]/div/span/nav/div/div/div[2]/div/div/ul/li[3]/a"));
        contactus.click();

        WebElement contactUs= driver.findElement(By.xpath("/html/body/div/div/form/div/div/div/div[1]/h2"));
        String actualTitle=contactUs.getText();


        String expectedTitle="Contact us";
        System.out.println("actual title " +actualTitle);
        Assert.assertEquals(actualTitle,expectedTitle,"Not in the Contact-us Page");

        TakesScreenshot ts = (TakesScreenshot) driver;
        File sourceFile = ts.getScreenshotAs(OutputType.FILE);
        File destFile = new File("Screenshots/" + System.currentTimeMillis()
                + ".png");
        FileUtils.copyFile(sourceFile, destFile);


        WebElement homePage= driver.findElement(By.xpath("/html/body/div/div/form/div/nav/div/div/div[1]/a/img"));
        homePage.click();

    }



    @Test(description = "TC_005-Go to the Register Page ", priority = 5)
    public void Register() throws InterruptedException, IOException {
        // Locate the Send Money on the Navigation Menu

        WebElement register= driver.findElement(By.xpath("/html/body/div/div/div[1]/div/span/nav/div/div/div[2]/div/div/ul/li[5]/a"));
        register.click();

        WebElement contactUs= driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/h1"));
        String actualTitle=contactUs.getText();


        String expectedTitle="Sign up";
        System.out.println("actual title " +actualTitle);
        Assert.assertEquals(actualTitle,expectedTitle,"Not in the Register Page");

     ////////////////////////////////////////////////////

        WebElement firstName=driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/div[1]/input"));
                   firstName.sendKeys("John");

         WebElement lastName= driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/div[2]/input"));
                     lastName.sendKeys("Doe");

          WebElement email= driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/div[3]/input"));
                      email.sendKeys("abc@gmail.com");





           WebElement countryofResidance= driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/div[4]/div/input"));
                      countryofResidance.click();

                      driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(2000));


             WebElement countryofResidance1=driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/div[4]/datalist/option[1]"));
                  Thread.sleep(2000);
             countryofResidance1.submit();

        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(2000));



          WebElement password= driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/div[5]/input"));
                    password.sendKeys("Qwerty@1234");

          WebElement confirmPassword=driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/div[6]/input")) ;
                              confirmPassword.sendKeys("Qwerty@1234");

          WebElement checkBos= driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/div[7]/input"));
                      checkBos.click();


          WebElement createAccount=driver.findElement(By.xpath("/html/body/div/div/form/div/div[2]/div/div[1]/button"));
                      createAccount.submit();
        //////////////////////////////////////////////////
        TakesScreenshot ts = (TakesScreenshot) driver;
        File sourceFile = ts.getScreenshotAs(OutputType.FILE);
        File destFile = new File("Screenshots/" + System.currentTimeMillis()
                + ".png");
        FileUtils.copyFile(sourceFile, destFile);

        ////////////////////////////////////////////////////

        WebElement homePage= driver.findElement(By.xpath("/html/body/div/div/form/div/div[1]/nav/div/div/div[1]/a/img"));
        homePage.click();

    }



    @Test(description = "TC_006-Go to the LogIn Page ", priority = 6)
    public void LogInPage() throws InterruptedException, IOException {



        WebElement login= driver.findElement(By.xpath("/html/body/div/div/div[1]/div/span/nav/div/div/div[2]/div/div/ul/li[4]/a"));

        login.click();

        WebElement contactUs= driver.findElement(By.xpath("/html/body/div/div/form/div/div/div/div[1]/h2"));
        String actualTitle=contactUs.getText();


        String expectedTitle="Welcome back";
        System.out.println("actual title " +actualTitle);
        Assert.assertEquals(actualTitle,expectedTitle,"Not in the Login Page");


        // Enter the LogIn email address and password

        WebElement logIn= driver.findElement(By.xpath("/html/body/div/div/form/div/div/div/div[2]/div[1]/input"));
                  logIn.sendKeys("abc@gmail.com");


        WebElement password= driver.findElement(By.xpath("/html/body/div/div/form/div/div/div/div[2]/div[2]/div/input"));
        password.sendKeys("Qwerty@1234");



        Thread.sleep(2000);


        WebElement submit=driver.findElement(By.xpath("/html/body/div/div/form/div/div/div/div[4]/button"));
                    submit.click();

        TakesScreenshot ts = (TakesScreenshot) driver;
        File sourceFile = ts.getScreenshotAs(OutputType.FILE);
        File destFile = new File("Screenshots/" + System.currentTimeMillis()
                + ".png");
        FileUtils.copyFile(sourceFile, destFile);


        WebElement homePage= driver.findElement(By.xpath("/html/body/div/div/form/div/nav/div/div/div[1]/a/img"));
        homePage.click();

    }

    @AfterTest
    public static void end()
    {
        driver.quit();
    }

}
