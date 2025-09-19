package runner;

import java.io.FileInputStream;
import java.io.IOException;
import java.net.MalformedURLException;

import org.apache.poi.ss.usermodel.Row;
import org.apache.poi.ss.usermodel.Sheet;
import org.apache.poi.ss.usermodel.Workbook;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;
import org.openqa.selenium.By;
import org.testng.annotations.AfterClass;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.Test;

import com.aventstack.extentreports.ExtentReports;

import utils.Base;
import utils.ExcelReader;
import utils.LoggerHandler;
import utils.Reporter;
import utils.Screenshot;

public class TestRunner extends Base {
   ExtentReports reports;
   Reporter reporter;
   @BeforeClass
   public void generateReport()
   {
    reports=Reporter.generateExtentReport();
   }
    @BeforeMethod
    public void launchBrowser() throws IOException {
        // launch your browser
        openBrowser();

    }
    @Test
    public void testone() throws IOException
    {
        String username=ExcelReader.readdata("testdata/testdata.xlsx", "Sheet1", 0, 0);
        driver.findElement(By.xpath("//input[@name='username']")).sendKeys(username);
        String pass=ExcelReader.readdata("testdata/testdata.xlsx", "Sheet1", 0, 1);
        driver.findElement(By.xpath("//input[@name='password']")).sendKeys(pass);
        driver.findElement(By.xpath("//button[@class='oxd-button oxd-button--medium oxd-button--main orangehrm-login-button']")).click();
        LoggerHandler.logInfo("clicked");
        Screenshot.getScreenShot(driver, "screenshot");
    }
    @AfterMethod
    public void tearDown() {
        // quit the driver here
        driver.quit();
    }
    @AfterClass
    public void finish()
    {
        reports.flush();
    }
}

//Screenshot(gvn seprately)
@Test 
public void test() throws IOException

{
    String Path = "screenshots/myscreenshot.png";
    File src=((TakesScreenshot)driver).getScrenshotsAs(OutputType.FILE);
    File desc=new File(Path);
    File Utils.copyFile(src,desc);
}

//If didn't work
import org.apache.commons.io.FileUtils;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;

TakesScreenshot ts = (TakesScreenshot) driver;
File source =  ts.getScreenshotAs(OutputType.FILE);
String destination = "screenshots/myscreenshot.png";
FileUtils.copyFile(source, new File(destination));


//Screenshot if utils gvn 
Screenshot.getScrenshot(driver,"screenshot");

//Alertbox

Alert alert = driver.switchTo().alert();
alert.accept();
Alert alert1=driver.switchTo().alert();
alert1.dismiss();

// Title contains "hello"
Assert.assertTrue(driver.getTitle().contains("hello"));

// Element text contains "Welcome"
WebElement element = driver.findElement(By.id("message"));
Assert.assertTrue(element.getText().contains("Welcome"));

//browser
executiontype = remote
browsername = chrome
gridurl = http://localhost:4444
url = 

//click
WebElement input = driver.findElement(By.id("searchBox"));
input.sendKeys("Selenium");
input.sendKeys(Keys.ENTER);

//Reading data from excel file (given seprately)
@Test
public void test()
{
    FileInputStream fis=new FileInputStream("path");
    Workbook wb=new XSSFWorkbook(fis);
    Sheet sh=wb.getSheetAt(0);
    Row row=sh.getRow(0);
    String ss=row.getCell(0).getStringCellValue();
    driver.findElement(By.xpath("")).sendKeys(ss);
    wb.close();
    fis.close();
}

//excel if utils gvn
Excel
Create testdata folder
Data.xlsx file in it
String username=ExcelReader.readdata("testdata/data.xlsx","Sheet1",0,0);
driver.findElement(By.xpath()).sendKeys(username);

//hover
import org.openqa.selenium.interactions.Actions;

WebElement menu = driver.findElement(By.id("menu"));
Actions actions = new Actions(driver);
actions.moveToElement(menu).perform();

//Define the root logger with the DailyRollingFileAppender
log4j.rootLogger=DEBUG, RollingAppender

// Configure the DailyRollingFileAppender
log4j.appender.RollingAppender=org.apache.log4j.DailyRollingFileAppender
log4j.appender.RollingAppender.File=logs/a.log
log4j.appender.RollingAppender.DatePattern='.'yyyy-MM-dd_HH-mm-ss
log4j.appender.RollingAppender.layout=org.apache.log4j.PatternLayout
log4j.appender.RollingAppender.layout.ConversionPattern=[%d{yyyy-MM-dd HH:mm:ss}] [%p] %c %M - %m%n

//log4j.properties

WebElement element = driver.findElement(By.id("footer"));
((JavascriptExecutor) driver).executeScript("arguments[0].scrollIntoView(true);", element);

//helper 
WebdriverHelper helper;

WebElement user = driver.findElement(By.id("user"));
helper.javascriptscroll(user);

//switch

String parent = driver.getWindowHandle();
Set<String> windows = driver.getWindowHandles();

for (String win : windows) {
    if (!win.equals(parent)) {
        driver.switchTo().window(win);
    }
}
