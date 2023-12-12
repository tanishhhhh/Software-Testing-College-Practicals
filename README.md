# Practical 02

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class SeleniumTest {

    static WebDriver driver;

    public static void main(String[] args) throws InterruptedException {
        System.setProperty("webdriver.chrome.driver", "D:\\chromedriver.exe");

        // Creating a single driver instance for both websites
        driver = new ChromeDriver();

        // First website (Gmail)
        driver.get("https://www.gmail.com");
        driver.manage().window().maximize();
        Thread.sleep(3000); // Consider using WebDriverWait instead

        // Second website (mycontactform.com)
        driver.get("https://www.mycontactform.com");
        driver.manage().window().maximize();

        // Locate elements
        WebElement username = driver.findElement(By.id("user"));
        WebElement password = driver.findElement(By.id("pass"));
        WebElement login = driver.findElement(By.name("btnSubmit"));

        // Enter credentials
        username.sendKeys("your_)email");
        password.sendKeys("your_password"); // Provide the actual password

        // Click login
        login.click();

        try {
            System.out.println("Test Case Pass");
        } catch (Exception e) {
            System.out.print("Test Case Failed");
        } finally {
            driver.quit();
        }
    }
}

```
#Practical 03

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class Test1 {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "D:\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        driver.get("https://accounts.google.com/ServiceLogin?");
        
        driver.findElement(By.id("identifierId")).sendKeys("your_email");
        driver.findElement(By.id("identifierNext")).click();

        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        driver.findElement(By.name("password")).sendKeys("xxx");
        ((WebElement) driver.findElements(By.id("passwordNext"))).click();

        String title = driver.getTitle();
        
        if (title.equals("GoogleAccounts")) {
            System.out.print("\"Login Successful");
        } else {
            System.out.print("Login Failed");
        }

        driver.quit();
    }
}

```
#Practical 05

```html
<!DOCTYPE html>
<html>

<head>
    <title>Program to calculate gcd of 2 numbers</title>
    <script type="text/javascript">
        function gcd() {
            var x, y;
            x = parseInt(document.myform.n1.value);
            y = parseInt(document.myform.n2.value);
            while (x !== y) {
                if (x > y)
                    x = x - y;
                else
                    y = y - x;
            }
            document.myform.result.value = x;
        }
    </script>
</head>

<body>
    <h1>Program to calculate gcd of 2 numbers</h1>
    <p>Enter Two numbers:</p>

    <form name="myform">
        Number 1: <input type="text" name="n1" value="">
        <br><br>
        Number 2: <input type="text" name="n2" value="">
        <br><br>
        <input type="button" value="get GCD" onClick="gcd()" id="calculateButton">
        <br><br>
        GCD is: <input type="text" name="result" value="">
    </form>
</body>

</html>

java:
package package3;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class Gcd {
    public static void main(String args[]) {
        System.setProperty("webdriver.chrome.driver", "C://Users//HP//Downloads//chromedriver.exe");

        WebDriver driver = new ChromeDriver();
        driver.get("C://Users//HP//Downloads//LcmGcd.html");
        driver.manage().window().maximize();

        driver.findElement(By.name("n1")).sendKeys("20");
        driver.findElement(By.name("n2")).sendKeys("40");
        driver.findElement(By.id("calculateButton")).click();

        String result = driver.findElement(By.id("result")).getText();
        System.out.println("Result is: " + result);

        driver.quit();
    }
}

```
#Practical 06

```java
package practical7;

import java.util.List;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class Object {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "E:\\practical7\\chromedriver (2).exe");

        WebDriver driver = new ChromeDriver();
        driver.get("https://www.google.com");

        List<WebElement> mylist = driver.findElements(By.xpath("//a"));
        System.out.println("Number of objects = " + mylist.size());

        driver.quit();
    }
}

```
#Practical 07

```html
<!DOCTYPE html>
<html>

<head>
    <title>RadioButton and Checkbox Test</title>
</head>

<body>
    <form>
        <h2>Radio Button Test</h2>
        <input type="radio" name="gender" value="Male" checked> Male
        <br>
        <input type="radio" name="gender" value="Female"> Female
        <br>
        <input type="radio" name="gender" value="Others"> Others
        <br>
        <br>
        <h2>Checkbox Test</h2>
        <input type="checkbox" name="lang" value="C" checked="checked"> C
        <br>
        <input type="checkbox" name="lang" value="C++" checked="checked"> C++
        <br>
        <input type="checkbox" name="lang" value="C#"> C#
        <br>
        <input type="submit" value="Submit">
    </form>

    <!-- Include Java code or description here -->
</body>

</html>

java :
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class Practice {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "D://chromedriver.exe");

        WebDriver driver = new ChromeDriver();
        driver.get("C://Users//hp//Downloads//PP1.html");

        int chk = 0;
        int unchk = 0;
        int rchk = 0;
        int runchk = 0;

        // Checkboxes
        for (int i = 1; i <= 3; i++) {
            WebElement checkbox = driver.findElement(By.xpath("(//input[@type='checkbox'])[" + i + "]"));
            if (checkbox.isSelected() || "true".equals(checkbox.getAttribute("checked"))) {
                chk++;
            } else {
                unchk++;
            }
        }

        // Radio buttons
        for (int i = 1; i <= 3; i++) {
            WebElement radioButton = driver.findElement(By.xpath("(//input[@type='radio'])[" + i + "]"));
            if (radioButton.isSelected() || "true".equals(radioButton.getAttribute("checked"))) {
                rchk++;
            } else {
                runchk++;
            }
        }

        System.out.println("Checked Checkboxes are: " + chk);
        System.out.println("Unchecked Checkboxes are: " + unchk);
        System.out.println("Checked Radio Buttons are: " + rchk);
        System.out.println("Unchecked Radio Buttons are: " + runchk);

        // Close the browser
        driver.quit();
    }
}

```
#Practical 08

```java
package practical51;

import java.io.File;
import java.io.IOException;
import java.util.Locale;
import jxl.CellView;
import jxl.Workbook;
import jxl.WorkbookSettings;
import jxl.format.UnderlineStyle;
import jxl.write.Formula;
import jxl.write.Label;
import jxl.write.Number;
import jxl.write.WritableCellFormat;
import jxl.write.WritableFont;
import jxl.write.WritableWorkbook;
import jxl.write.WritableSheet;
import jxl.write.WriteException;
import jxl.write.biff.RowsExceededException;

public class StudentRecord {
    private WritableCellFormat timeBoldUnderline;
    private WritableCellFormat times;
    private String inputFile;

    public void setOutputFile(String inputFile) {
        this.inputFile = inputFile;
    }

    public void write() throws IOException, WriteException {
        File file = new File(inputFile);
        WorkbookSettings wbSettings = new WorkbookSettings();
        wbSettings.setLocale(new Locale("en", "EN"));
        WritableWorkbook workbook = Workbook.createWorkbook(file, wbSettings);
        workbook.createSheet("Report", 0);
        WritableSheet excelSheet = workbook.getSheet(0);
        createLabel(excelSheet);
        createContent(excelSheet);
        workbook.write();
        workbook.close();
    }

    private void createLabel(WritableSheet sheet) throws WriteException {
        WritableFont time10pt = new WritableFont(WritableFont.TIMES, 10);
        times = new WritableCellFormat(time10pt);
        times.setWrap(true);
        WritableFont times10ptBoldUnderline = new WritableFont(WritableFont.TIMES, 10, WritableFont.BOLD, false,
                UnderlineStyle.SINGLE);
        timeBoldUnderline = new WritableCellFormat(times10ptBoldUnderline);
        timeBoldUnderline.setWrap(true);
        CellView cv = new CellView();
        cv.setFormat(times);
        cv.setFormat(timeBoldUnderline);
        addCaption(sheet, 0, 0, "Student Name");
        addCaption(sheet, 1, 0, "Subject 1");
        addCaption(sheet, 2, 0, "Subject 2");
        addCaption(sheet, 3, 0, "Subject 3");
    }

    private void createContent(WritableSheet sheet) throws WriteException, RowsExceededException {
        for (int i = 1; i < 10; i++) {
            addLabel(sheet, 0, i, "Student " + i);
            addNumber(sheet, 1, i, ((i * i) + 10));
            addNumber(sheet, 2, i, ((i * i) + 4));
            addNumber(sheet, 3, i, ((i * i) + 3));
        }
    }

    private void addCaption(WritableSheet sheet, int column, int row, String s)
            throws RowsExceededException, WriteException {
        Label label;
        label = new Label(column, row, s, timeBoldUnderline);
        sheet.addCell(label);
    }

    private void addNumber(WritableSheet sheet, int column, int row, Integer integer)
            throws RowsExceededException, WriteException {
        Number number;
        number = new Number(column, row, integer, times);
        sheet.addCell(number);
    }

    private void addLabel(WritableSheet sheet, int column, int row, String s)
            throws RowsExceededException, WriteException {
        Label label;
        label = new Label(column, row, s, times);
        sheet.addCell(label);
    }

    public static void main(String[] args) throws WriteException, IOException {
        StudentRecord test = new StudentRecord();
        test.setOutputFile("E:\\excel\\Student.xls");
        test.write();
        System.out.println("Please check the result file under C:\\excel");
    }
}
