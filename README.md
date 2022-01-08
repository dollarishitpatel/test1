ClassName nameOfAnObject = new ClassName();                                        //for creating an object for a classname
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
WebDriver driver = new ChromeDriver();                                             //Webdriver is interface, driver is object, new is an operator, ChromeDriver() is Class nameOfAnObject
 ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
System.setProperty("webdriver.chrome.driver", "C://Users//chromedriver.exe");      //setProperty is method, webdriver.chrome.driver is key, C://users is   path
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
""  must be used to tell java that this is a string and it will simply print it. If you are decalring a variable then you need NOT have to use "" 

"" inside "" is not accepted. use\" or ' .
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
; - All Java statements ends with ; we just dont use ; for loops.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Variables should not be placed in double quotes""
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ is used to join string and a variable                     // system.out.println("Sum is" +c);
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Classobject.methodname();                

ClassName Classobject = new ClassName();
Classobject.methodname(); 

syntax to access method from a different class. Both Class name and method should be of another class which you want to access.
I am defining ClassObject of another class in a variable m so that whenever we want to access another class we can just wrrite m.

Basics2 m = new Basics2();
m.ValidateHeader();
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Selenium supports below locaters by default:

ID
Name
Classname
linkText
partialLinkText
Xpath
CSS

ID is always unique. Dont use ALPHANUMERIC ID. They may vary with every refresh.

linkText - Selenium can understand any link on a webpage but just providing Text of that link.To confirm if it is a link or not you have to see HTML. All the Links will have tag 'a'.Confirm the link object with anchor/tag name 'a'.

ClassName should NOT have spaces. if they have spaces then provide . between

XPATH - When XPATH starts from HTML it is not reliable. 

XPATH Validation in chrome console: $x("//input[@id='value']") 
CSS Validation in chrome console: $("input[id='value'")

Xpath Syntax: //tagname[@attribute='value']  
              //*[@attribute='value']        -- To skip tag name 

CSS Syntax: tagName[attribute='value']
            [attribute='value']             -- To skip tag name
			tagName#value                   -- To skip attribute    
			tagName.ClassNameValue          -- When you have to use Class Name ( just provide .classnamevalue )
			
			
Regular Expression:

Xpath:  //tagName[contains(@Attribute, 'PartialValue')]
CSS:    tagNAme[attribute* = 'partialvalue']

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Parent-Child Travel Xpath Relationship: 
//div[@class = '1st-c']/div/div[2]/div/input

div[@class = '1st-c']  : This came from parent 
div: child of above parent 
div[2]: grand child of above parent and 2 in [] means second child in case if there are more than 2 child in one parent
div: Grand grand child
input: tagName of the child we want


---------------------------------------------------------------
Parent Child relationship xpath Locator to idetify objects:+

//tagname[@classname = 'Value'] //tagname[@classname = 'Value']

First xpath is xpath of parent
Space
Second xpath is xpath of child which you wnat to select 



Parent Child CSS:
tagname[classname = 'value'] tagname
------------------------------------------------------------------------------
 int checkBox = driver.findElements(By.xpath("//table[@id='BodyContentPlaceHolder_pAvailableAcctsTable'] //input[@type='checkbox']")).size();
        for (int k=1; k<=checkBox;k++) {
            driver.findElement(By.xpath("(//td[@class='CheckBox'])[" + k + "]")).click();
            WebElement accountNumberText= driver.findElement(By.xpath("(//td[@class='AccountNumber HighlightedColumn'])[" + k + "]"));
            String accountNumberValue = accountNumberText.getText();
            if(accountNumberValue.startsWith("5")) {
                driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("Checking");
            }
            if(accountNumberValue.startsWith("4")){
                driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("Savings");
            }
            if(accountNumberValue.startsWith("6")){
                driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("CD");
            }
        }
-------------------------------------------------------------------------------
	boolean hasNextPage = true;
        while (hasNextPage) {
            List<WebElement> enabledNextPage = driver.findElements(By.xpath("//div[@class= 'pgNext pagination_right_sngl  ']"));
            List<WebElement> disabledNextPage = driver.findElements(By.xpath("//div[@class= 'pgNext pagination_right_sngl  disabled']"));

            if (enabledNextPage.size() > 0) {
                Thread.sleep(100L);
                int acctSvcsAccess = driver.findElements(By.xpath("//select[contains(@id, 'acctSvcsAccess')]")).size();
                Thread.sleep(100L);
                for (int i = 0; i < acctSvcsAccess; i++) {
                    Thread.sleep(100L);
                    driver.findElement(By.xpath("//option[@id='acctSvcsAccess_" + i + "__" + accessLevelDropdownValue + "']")).click();
                    Thread.sleep(100L);
                }
                Thread.sleep(100L);
                driver.findElement(By.xpath("//img[@alt='Go to next page']")).click();

            } else if (disabledNextPage.size() > 0) {
                break;
            }
	
		
---------------------------------------------------------------------
Sibiling:
//*[@attribute='Value']/following-sibling::attribute[2]           //attribute in second position is attribute of a sibling and [2] means second sibling






--------------------------------------------------------------------------------------
Child Parent:

//*[@attribute='value']/parent::attribute    // second attribute is an attribute of a parent.


//*[@attribute='Value'/preceding-sibling::attribute[2]      // If you want to go from sibiling 3 to sibling 1 use this. first attribute is an attribute of sibling and second attribute is attribute of sibiling 1. [2] means going back 2 places.




driver.findElement(By.xpath("//*[normalize-space(text())='"+nameOfEntity+"']/parent::tr/td[1]/input")).click();

	in this Xpath I am first going to parent from a child- 2 and then I am going to a child -1 from a common parent.


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Text based XPATH:

//tagName[text() = 'Value']
//*[text()=' Value ']

//id[text()='Text on your website']

make sure you give space beofre and after Value as per the source code




driver.findElement(By.xpath("//*[contains(text(), 'Account Activity')]")).click();

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Static Dropdown:

SELECT tag dropdown -- Class in selenium to use static dropdown

WebElement staticDropDown = driver.findElement(By.id("sdasd"));                     ---Need to give knowledge to selenium where the static dropdown is present in my whenever
Select dropdown = new Select();                                                     ---Creating dropdown object for Select() class                          
dropdown.                                                                           ---dropdown. will give methods of select class

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Loop:

While Loop: Below loop will run 4 times. It will run until the condition you give in brackets becomes false. Initalize, Compare and increment.
-----------
Syntax:

int i=1;
while(i < 5)
{
selenium codes
i++;
}

Foor Loop: 
-----------
Syntax:

for(int i=1; i<5; i++)
{
Selenium codes
}

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Xpath Index: (Dynamic dropdown)

[2] This will select 2nd node instead of first. Useful when two matching xpath are found and I want to select 2nd xpath.

Syntax: Driver.findElement(By.xpath("(//tagname[@attribute = 'value'])[2]")).click();

ChroPath syntax: (//tagname[@attribute = 'value'])[2]

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
find.elements when multiple values needs to be selected

-------------------------------------------------------------------------------------------------
Enhance For Loop: for selecting particular value from a autosuggestive dropdown ( Video number 54)

List<WebElement> options = driver.findElement(By.Css("adasdad"));

For(WebElemtn option : options)
{
   if(option.getText().equals("India"));
  {
   option.click();
   break;
   
  }
 
}

-----------------------------------------------------------------------------------------------------------------

Assert.assert(false)
Assert.assert(True)
Assert.assert("Actula" , "Expected")

----------------------------------------------------------------------------------------------------------------------

.size() will get me number of checkboxes in page. make sure to put elements in driver.findelements

-------------------------------------------------------------------------------------------------------------------

if(driver.findElement(By.id("div 1")).getAttribute("style").conatins("1"))
{
assert.Assert(True);
}

else
{
assert.Assertfalse(false)
}


-----------------------------------------------------------------------------------------------------------------------------

String text = "value";
driver.findElement(By.id("name")).sendKeys(text);

----------------------------------------------------------------------------------------------------------------------------
Handle alerts on browser:

driver.switchTo().alert().accept();  //will click ok button

driver.switchTO().alert().dismiss();  // Will click on Cancel button

-------------------------------------------------------------------------------------------------------------------------
Declaring variables in For loop:

List<WebElement> products = driver.findElement(By.cssSelector(""));

for(i=0 ; i < products ; i++)

{
String name = products.get(i).getText();

if (name.contains("cucumber"))
    {
	  driver.findElements(By.xpath("")).get(i).click();
	  break; 
	}  
}

---------------------------------------------------------------------------------------------------------------------------
Array:

Declare Array: String[] arrayName = {"value1","Value2"};
               int[]  arrayName ={value1,value2};  
			   
String is a return type 
[] Telling java that the value in curly brackets are array
name= name of your variable


How to convert array to arrayList:
List arrayListName = Arrays.aslist(arrayName);


if (arrayListName.contains(arrayName))
    {
	  driver.findElements(By.xpath("")).get(i).click();
	  
	}  
	
	
cant use break;

To use break; do following:



int j = 0;
if (arrayListName.contains(arrayName))
    {
	  j++;
	  driver.findElements(By.xpath("")).get(i).click();
	  if(j==3)
	  {
	  break;
	  }
	}  
	

(j == nameOfArray.length)

length method is used to get size of array
size() method is used to get size of Array List.


---------------------------------------------------------------------------------------------------------------------------------------
Trim the text getting from HTML: Seprate two strings


//cabbage -1 kg
String[] name = products.get(i).getText().split("-");

name[0] = cabbage   //has space after word

String formatted name = name[0].trim();

name[1] = -1 kg

-----------------------------------------------------------------------------------------------------------------------------------------------------------------
How to declare variable in XPATH:

// Make sure value of i is in double quotes.
for (i=2; i<3; i++)
{
 driver.findElement(By.xpath("//table[@id='CompanyAccountsTable']/tbody/tr["+i+"]/td/input")).click();
}	


String nameOfEntity =  "RODNEY JERMANN";
nameOfEntity = nameOfEntity.trim();

    driver.findElement(By.xpath("//td[text() = '"+nameOfEntity+"']")).click();
	
	
	
driver.findElement(By.xpath("//*[normalize-space(text())='"+nameOfEntity+"']/parent::tr/td[1]/input")).click();	
	
	normalize-space will trim out allspaces before and after
	'"+nameOfEntity"' is a variable define in string
	
	in this Xpath I am first going to parent from a child- 2 and then I am going to a child -1 from a common parent.
	


String xPathWithVariable = "(//a[contains(@href, 'EditCompanyAccount')])" + "['+i+']";
           driver.findElement(By.xpath(xPathWithVariable)).click();	
	
	
	
	
	
	
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
For each loop:

for ( variableName : arrayName {
Lines of codes              
}	


int[] myArray = {1,2,3}
for (int i : myArray ){
driver.findelement(By.id("TaxId").sendKeys(String.valueof(i));   //String value of i because i is int and not a string.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Storing value in a variable which was found on a particular xpath:

int numberOfCompanies = driver.findElements(By.xpath("//a[contains(@href, 'EditCompanyAccount')]")).size();
        for (int i = 1; i <= numberOfCompanies; i++) {
		
		
WebElemet nameOfCompany = driver.findElement(By.css(""));



 WebElement test = driver.findElement(By.xpath("(//input[@name='accountId'])[4]"));
        System.out.println(test.getAttribute("value"));
        if(test.getAttribute("value").startsWith("4")){
            System.out.println("Hello");
        }else{
            System.out.println("World");
		
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
convert string to integer:

int total = Integer.parseInt(driver.findElement(By.cssSelector(".totalAmount").getText().split(":")[1].trim());

-----------------------------------------------------------------------------------------------------------------------------	
Soft Assertion:

SoftAsset a = new SoftAssert();
{
a.assertTrue(respcode <400, "This link with Tezt"+link.getText()+"is Broken with code"+respcode)

}
a.assertAll();

-----------------------------------------------------------------------------------------------------------------------------------
If webelemt does not have any unique element:

WEbElement dateOfBirth = driver.findelemt(By.cssSelector(""));
driver.findElement(withTagName("input").below(dateOfBirth)).sendkeys("");
                                       .toLeftOf
                                       .toRightOf
                                       .above									   


-------------------------------------------------------------------------------------------------------------------------------
TestNg Annotations:

Before suite and beforetest are used at package level.

If there are 3 class in one project and 1 class has beforetest then it will execute first before any testcase of any class will execute.

before class is executed at class level. If 3 class and beforeclass is given in 2nd class then 1st class will exeecute--before class of 2nd will execute--all class test cases form 2nd class will execute--3rd class will execute 

BeforeSuite
'   BeforeTest
'   '   BeforeClass (for particular class)
'   '   '   BeforeMethod (will be executed before each test case)
'   '   '   '   myTestMethod3
'   '   '   AfterMethod
'   '   '   BeforeMethod
'   '   '   '   myTestMethod4
'   '   '   AfterMethod
'   '   AfterClass
'   AfterTest
'   BeforeTest
'   '   BeforeClass
'   '   '   BeforeMethod
'   '   '   '   myTestMethod1
'   '   '   AfterMethod
'   '   '   BeforeMethod
'   '   '   '   myTestMethod2
'   '   '   AfterMethod
'   '   AfterClass
'   '   BeforeClass
'   '   '   BeforeMethod
'   '   '   '   myTestMethod3
'   '   '   AfterMethod
'   '   '   BeforeMethod
'   '   '   '   myTestMethod4
'   '   '   AfterMethod
'   '   AfterClass
'   AfterTest
AfterSuite

-----------------------------------------------------------


@Test
public void usecase1 () {
//my codes

}


<suite name="Suite">
  <test  name="module name">
    <classes>
      <class name="packagename.classname">
	  <methods>
	    <include name = "usecase1"/>
		<exclude name = "usecase1"/>
		</class>
		<class name ="packagename.classname2"/>
    </classes>
  </test>
<test name ="modulename2">
<classes>
<class name = "packagename.classname3">
<methods>
<exclude name = "API.*"/>
</methods>
</class>
</classes> 
</suite> 



give below for sequential run:
<test>
<classess></classes>
</test>
<test>
<classes></classes>
</test>


---------------------------------------------------------
TestNg Groups:

To pick a particular use case from classes. 1 use case from class1, 4th use case from class 22 etc.

define tagname:


//Class1
@Test(groups={"Smoke"})
public void usecase1 () {
//my codes
}

//Class2
@Test(groups={"Smoke"})
public void usecase2 () {
//my codes
}


In Xml file



<suite name="Suite">
  <test  name="regression">
  <groups>
  <run>
  <include name="Smoke"/>
  </run>
  </groups>
  
    <classes>
      <class name="packagename.classname"/>
	  <class name ="packagename.classname2"/>
    </classes>
  </test>
  </suite> 
  
------------------------------------------------------------------------------------------
dependsOnMethod = will run the given method first before it ever execute tht particular method.


//Class1
@Test
public void usecase1 () {
//my codes
}


@Test(dependsOnMethod={"usecase1","usecase0"})
public void usecase2 () {
//my codes
}

-----------------------------------------------------------------------------------------------
@Test(enabled=false) -- TestNG will skip it from execution.

----------------------------------------------------------------------------------------------
@Test(timeOut = 4000) -- Thread.sleep. It will not fail for 40 seconds even though implicit wait time is given.

-------------------------------------------------------------------------------------------------------------------
@DataProvider: parametriezing with multiple data set while running test with multiple combination

@DateProvider
public Object[][] getData()
{
Object[][] data= new object [3][2];  //3 is rows and 2 is coloum. Multidimensanal object array.
data[0][0] = "firstusername";
data[0][1] = "firstpassword";
data[1][0]="";
data[1][1]="";
data[2][0]="";
data[2][1]="";
return data;
}

@Test(dataProvider="getData")
public void usecase1(String username, String password) 
{
//mycodes
}


-----------------------------------------------------------------------------------------------------------
TestNG listeners:

Create a new class listerners.java

public class Listeners implements ITestListerner {
  
  public void onTestFailure(ITestResult result){
  
  system.out.println(result.getName());    //print failed usecase name
  }

 }
 
 
 XML file update:
 
 <suite name="Suite">
 <listeners>
 <listner class-name= "packagename.classnameoflisteners"/>
 
 
 </listeners>
 
  <test  name="regression">
  <groups>
  <run>
  <include name="Smoke"/>
  </run>
  </groups>
  
    <classes>
      <class name="packagename.classname"/>
	  <class name ="packagename.classname2"/>
    </classes>
  </test>
  </suite> 

-----------------------------------------------------------------------------------------------
Running test parallely with TestNG:

<suite name="module name" parallel="tests" thread-count = "6" >  //first 6 test will run from xml file
-------------------------------------------------------------------------------------------------------------------------------------------------------
 To run in sequesntial order:
 @test(priority=0)

function1()
{}


---------------------------------------------------------------------
how to drive global environment from external soucre:

create a file data.properties


Public class GlobalValuesDrive{
 public static void main() {
 Properties prop = new Properties();
 FileInputStream fis = new FileInputStream("path of data.properties");
 prop.load(fis);
 prop.setProperty("browser", "firefox");
  FileOutputStream fos = new FileOutputStream("path of data.properties");
  prop.store(fos,null);
  
  }
  }
  
------------------------------------------------------------------------------------
MAVEN:

At the end of each JAVA class File Give Test so that maven understand it and able to run it

  Add surefire plugin, This plugin will execute all test cases
  Add TestNg dependencies
  Add Selenium dependencies
------------
mvn compaile on cmd prompat will look for all syntax mistake
mvn clean will clean code
mvn test will run test
--------  
  
 <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>3.0.0-M5</version>
        <configuration>
          <suiteXmlFiles>
            <suiteXmlFile>testng.xml</suiteXmlFile>  //testng.xml will be your xml file you want ot run it through maven
          </suiteXmlFiles>
        </configuration>
      </plugin>  
	  
mvn -test now will run only testng.xml file


to run a single class: mvn -Dtest= testcircle test // testcircle is name of class name file you want to run.


-----------------
Maven profiling:

<profiles>
<profile>
<id>regression</id>

  <build>
  
  
    <pluginManagement><!-- lock down plugins versions to avoid using Maven defaults (may be moved to parent pom) -->
      <plugins>
        <!-- clean lifecycle, see https://maven.apache.org/ref/current/maven-core/lifecycles.html#clean_Lifecycle -->
        <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-surefire-plugin</artifactId>
          <version>3.0.0-M5</version>
		  <configuration>
          <suiteXmlFiles>
            <suiteXmlFile>tesng.xml</suiteXmlFile>  //testng.xml will be your xml file you want ot run it through maven
          </suiteXmlFiles>
        </configuration>
        </plugin>
        <plugin>
          <artifactId>maven-clean-plugin</artifactId>
          <version>3.1.0</version>
        </plugin>
        <!-- default lifecycle, jar packaging: see https://maven.apache.org/ref/current/maven-core/default-bindings.html#Plugin_bindings_for_jar_packaging -->
        <plugin>
          <artifactId>maven-resources-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.8.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-surefire-plugin</artifactId>
          <version>2.22.1</version>
        </plugin>
        <plugin>
          <artifactId>maven-jar-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-install-plugin</artifactId>
          <version>2.5.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-deploy-plugin</artifactId>
          <version>2.8.2</version>
        </plugin>
        <!-- site lifecycle, see https://maven.apache.org/ref/current/maven-core/lifecycles.html#site_Lifecycle -->
        <plugin>
          <artifactId>maven-site-plugin</artifactId>
          <version>3.7.1</version>
        </plugin>
        <plugin>
          <artifactId>maven-project-info-reports-plugin</artifactId>
          <version>3.0.0</version>
        </plugin>
      </plugins>
    </pluginManagement>
  </build>
	 
	 
cmd prompt: mvn test -PRegression //Regression is name of your id from above codes


test folder is for test cases
main folder is for utilites

----------------------------------------------------------------------------------------
Jenkins:
Automated test cases. Continuous integration tool
--------------------------------------------------------

Data driven:
reading coloumns:
Excel:
heading1|heading2|
heading2|value1
heading3|value2
Socialsecurity|123456799, 987654321

Code:
public class datadriven3 {


    DataFormatter formatter = new DataFormatter();

    @Test(dataProvider="drivedata", priority=1)
    public void testcase(String CompanyName, String Division, String AccountNumber, String socialsecurtiy) {

        String[] ssn=socialsecurtiy.split(", ");
        int social= ssn.length;
        System.out.println(social);
        for(int i=0;i<social;i++){
            String security = ssn[i];
            System.out.println(security);

        }
    }


    @DataProvider(name="drivedata")
    public Object[][] getData() throws IOException {

        FileInputStream fis= new FileInputStream("C:\\Users\\10001926\\eclipse-workspace\\testdata.xlsx");
        XSSFWorkbook workbook = new XSSFWorkbook(fis);
        XSSFSheet sheet = workbook.getSheetAt(0);
        int rowCount = sheet.getPhysicalNumberOfRows();
        XSSFRow row = sheet.getRow(0);
        int colCount=row.getLastCellNum();

        Object data[][] = new Object[colCount-1][rowCount-1];
        for(int i=0;i<rowCount-1;i++) {
            row=sheet.getRow(i+1);
            for(int j=0;j<colCount-1;j++) {
                XSSFCell cell = row.getCell(j+1);
                data[j][i] = formatter.formatCellValue(cell);


            }
        }
        return data;

    }

}


New logic:
int n=0;
        String[] placeHolderName =placeHolder.split(", ");
        String[] nickNameName =nickName.split(", ");

        for(String l: placeHolderName) {
            driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "']")).click();
            driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "']")).click();
            driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "TXT']")).clear();
            driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "TXT']")).sendKeys(nickNameName[n]);
            n++;
        }



For reading rows:
header1|header2|header3
value1|value1.1|value1.2
Value2|Value2.1|Value2.2

	DataFormatter formatter= new DataFormatter();
	
	@Test(dataProvider="drivetest")
	public void main(String Username, String Password, String Address, String Phone) {
 
		System.out.println(Username);
		System.out.println(Password);
		System.out.println(Address);
		//long a = Long.parseLong(Phone);
		System.out.println(Phone);
		
		
		
		//System.out.println(Phone);
		
		
		
	}
    
	@DataProvider(name="drivetest")
	public Object[][] getData() throws IOException {
		FileInputStream fis = new FileInputStream("C:\\Users\\10001926\\eclipse-workspace\\testdata.xlsx");
    	XSSFWorkbook workBook = new XSSFWorkbook(fis);
		XSSFSheet sheet = workBook.getSheet("Sheet1");
		int rowCount = sheet.getPhysicalNumberOfRows();
		XSSFRow row= sheet.getRow(0);
		int coloumnCount = row.getLastCellNum();
    	
		Object data[][] = new Object[rowCount-1][coloumnCount];
		for(int i=0;i<rowCount-1;i++) {
			row=sheet.getRow(i+1);
			for(int j=0;j<coloumnCount;j++) {
				
				XSSFCell cell = row.getCell(j);
				
				data [i][j] = formatter.formatCellValue(cell);			
			}
		}
		return data;



Easy peasy logic:

FileInputStream fis = new FileInputStream("C:\\Users\\10001926\\eclipse-workspace\\testdata.xlsx");
    	XSSFWorkbook workBook = new XSSFWorkbook(fis);
    	XSSFSheet sheet = workBook.getSheet("Sheet1");
    	int noOfColoumns = sheet.getRow(0).getLastCellNum();
    	String[] Headers = new String[noOfColoumns];
    	for(int j=0;j<noOfColoumns;j++) {
    		Headers[j] = sheet.getRow(0).getCell(j).getStringCellValue();
    	}
    	
    	int b = 1;
    	
    	for(int a=0;a<noOfColoumns;a++) {
    		if(Headers[a].equals("Username")) {
    			System.out.println(sheet.getRow(b).getCell(a).getStringCellValue());
    		    
    		}
    		if(Headers[a].equals("Password")) {
    			System.out.println(sheet.getRow(b).getCell(a).getStringCellValue());
    		    
    		}	
    		if(Headers[a].equals("Address")) {
    			System.out.println(sheet.getRow(b).getCell(a).getStringCellValue());
    		    
    		}
    		if(Headers[a].equals("Phone")) {
    			System.out.println(sheet.getRow(b).getCell(a).getStringCellValue());
    		    
    		}
        	b++;
    	}
    		

		
	}
--------------------------------------------------------------------------------------------------------------------------------------------
extend base from end to end testing tutorial video
---------------------------------------------------

					
					
					
					
					
					
					
					
					
					
					
					
					
					
	import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.concurrent.TimeUnit;

public class datadriven {


    public static void main(String[] args) throws IOException, FileNotFoundException {
        System.setProperty("webdriver.chrome.driver", "C:\\Users\\10001926\\JavaDependencies\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
        driver.get("https://test.casso.dollarbank.com/Admin/AdministrativeLogon/AdministrativeLogon.aspx");



        FileInputStream fis = new FileInputStream("C:\\Users\\10001926\\eclipse-workspace\\testdata.xlsx");
        XSSFWorkbook workBook = new XSSFWorkbook(fis);
        XSSFSheet sheet = workBook.getSheet("Sheet1");
        int noOfColoumns = sheet.getRow(0).getLastCellNum();
        String[] Headers = new String[noOfColoumns];
        for(int j=0;j<noOfColoumns;j++) {
            Headers[j] = sheet.getRow(0).getCell(j).getStringCellValue();
        }

        int noOfRows = sheet.getLastRowNum();
        for(int k=1;k<=noOfRows;k++) {
          for (int a = 0; a < noOfColoumns; a++) {
              if (Headers[a].equals("Username")) {
                 sheet.getRow(k).getCell(a).getNumericCellValue();
                  driver.findElement(By.xpath("//input[@name='ctl00$BodyContentPlaceHolder$pUserID']")).sendKeys(sheet.getRow(k).getCell(a).getStringCellValue());
                  driver.findElement(By.xpath("//input[@name='ctl00$BodyContentPlaceHolder$pUserID']")).clear();
              }
              if (Headers[a].equals("Password")) {
                  driver.findElement(By.xpath("//input[@name='ctl00$BodyContentPlaceHolder$pPassword']")).sendKeys(sheet.getRow(k).getCell(a).getStringCellValue());
                  driver.findElement(By.xpath("//input[@name='ctl00$BodyContentPlaceHolder$pPassword']")).clear();


              }
              if (Headers[a].equals("Address")) {
                  String Address = sheet.getRow(k).getCell(a).getStringCellValue();

              }
              if (Headers[a].equals("Phone")) {
                  String Phone = sheet.getRow(k).getCell(a).getStringCellValue();

              }




              /* Login */
                                      //Enter Username

          }
      }




    }

}				
	
	
	
	
	
	
	
	
`````````````````````````````````````````````````````````````````````````````````````````````````
	package com.dollarbank;

import org.apache.commons.io.FileUtils;
import org.apache.poi.ss.usermodel.DataFormatter;
import org.apache.poi.xssf.usermodel.XSSFCell;
import org.apache.poi.xssf.usermodel.XSSFRow;
import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.ITestResult;
import org.testng.annotations.*;

import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;

import java.util.Arrays;
import java.util.concurrent.TimeUnit;

public class ACIAdminPlayGround {

    DataFormatter formatter = new DataFormatter();
    String driverPath = "C:\\Users\\10001926\\JavaDependencies\\chromedriver.exe";
    public WebDriver driver;



    @Test(dataProvider="drivedata")
    public void testcase(String masterCompanyAccountNumber, String socialSecurityArray, String companyName, String companyDivision, String accountName, String userID, String userName, String userEmail, String userMobileNumber, String nameOfEntity, String placeHolder, String nickName) throws InterruptedException {
        //long masterCompanyAccountNumber = 52671243293L;  5 for checking account and 4 for savings account
       //int[] socialSecurityArray = {208840076,251068614,256001017};
        // String companyName = "Patels Automation60";
       // String accountName = "Checking60";
      //  String userID = "automate60";
     //   String userName = "automate60";
     //   String userEmail = "ipatel744@dollarbank.com";
    //    String userMobileNumber = "4122610000";
   //     String[] nameOfEntity = {"CAMOSUN COLLEGE","HERITAGE WOODS SECONDARY SCHOOL","SOLUTIA"};         // Name of company if one SSN is given to more than one company
      //  int companyDivision = 1;                                       //1 = Pittsburgh , 2= Ohio
       // int[] modifyAccountsAlerts = {0};
    //    long[] placeHolder = {52670857574L, 52671243293L};                    // account number to for a company nickname
     //   String[] nickName = {"MyName","YourName"};                            //nickname to a company


        System.setProperty("webdriver.chrome.driver", driverPath);
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
        driver.get("https://test.casso.dollarbank.com/Admin/AdministrativeLogon/AdministrativeLogon.aspx");

        driver.findElement(By.xpath("//input[@name='ctl00$BodyContentPlaceHolder$pUserID']")).sendKeys("Ishit");
        driver.findElement(By.xpath("//input[@name='ctl00$BodyContentPlaceHolder$pPassword']")).sendKeys("Ishit@2021");
        driver.findElement(By.xpath("//input[@name = 'ctl00$BodyContentPlaceHolder$pSubmit']")).click();
        Assert.assertEquals(driver.findElement(By.id("PageHeader-Title")).getText(), "Welcome to the CashANALYZER Administration Site");

        driver.findElement(By.xpath("//*[@id=\"CompanyMaintenance-Tab\"]/span")).click();                                                                 //COMPANY Tab in upper module
        Assert.assertEquals("Company Maintenance", "Company Maintenance");                                                                                // Company Tab
        driver.findElement(By.cssSelector("input[name ='ctl00$BodyContentPlaceHolder$AddButton']")).click();                                              //Enroll Company
        /* Company Overview */
        Assert.assertEquals("Company Maintenance - Enroll Company Screen", "Company Maintenance - Enroll Company Screen");                               //Company Enrollment page
        driver.findElement(By.cssSelector("input[name = 'ctl00$BodyContentPlaceHolder$pCompanyName']")).sendKeys(companyName);                           //Adding Company Name
        driver.findElement(By.xpath("//input[@id = 'BodyContentPlaceHolder_pCompanyDivision" + companyDivision + "']")).click();                                         //Selecting Pittsburgh or Ohio Radio Button
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pMasterProfileAccount']")).sendKeys(masterCompanyAccountNumber);     //Master Profile Account number must include 5 or 4 in the beginning
        /* CashAnalyzer Product Access */
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pAlertsAccess']")).click();                                        //Alerts
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pBusinessCdAccess']")).click();                                    //Business Cds
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pCorporateVisaAccess']")).click();                                 //Corporate Credit Card
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pAccountReconcilementAccess']")).click();                          //Reconcilement
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pRemoteDepositAccess']")).click();                                 //Remote Deposit
        /* CashAnalyzer Multipurpose SSO Access */
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$ssoOptions']")).click();                                           //Multipurpose SSO
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$loanActivity']")).click();                                         //Loan Activity
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$consolidatedReports']")).click();                                  //Consolidated Reports
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$availableHolds']")).click();                                       //Available Holds
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$ContinueButton']")).click();                                       //Submit Company
        /* Company maintenance review screen */
        Assert.assertEquals("Company Maintenance - Review Screen", "Company Maintenance - Review Screen");                                             //Verifying Review Screen
        driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$ReviewCompanyButton']")).click();                                  //Submit Review Button
        /* Verifying if company is created or not */
        driver.findElement(By.id("BodyContentPlaceHolder_mSortByName")).click();                                                                       //Sort By Company Name
        driver.findElement(By.id("BodyContentPlaceHolder_cbCompany_cbCompany_TextBox")).click();                                                       //Selecting checkbox
        driver.findElement(By.id("BodyContentPlaceHolder_cbCompany_cbCompany_TextBox")).sendKeys(companyName);                                         //Entering CompanyName
        driver.findElement(By.id("PageBody")).click();                                                                                                 //Clicking somewhere on page to select company
        Assert.assertEquals(masterCompanyAccountNumber, masterCompanyAccountNumber);                                                                   //Verifying if company is created or not

        driver.findElement(By.xpath("//*[@id=\"TaxID-Tab\"]/span")).click();                                                                            // Click on Tax ID Tab
        Assert.assertEquals(companyName, companyName);                                                                                                  // Verifying company name

        int p=0;
        String[] nameOfEntityName =nameOfEntity.split(", ");
        String[] ssn=socialSecurityArray.split(", ");
        int social= ssn.length;
       // for(String i:ssn) {
        //}
        for(int i=0;i<social;i++){
            driver.findElement(By.id("BodyContentPlaceHolder_pTaxId")).sendKeys(ssn[i]);                                                    // Sending SSN Number in form of i
            driver.findElement(By.id("BodyContentPlaceHolder_pCanDisplayBusinessCD_0")).click();                                                       // Business CD yes
            driver.findElement(By.id("BodyContentPlaceHolder_pAddButton")).click();                                                                    // Submit button
            //for (String j : nameOfEntity)
            if (driver.getCurrentUrl().equals("https://test.casso.dollarbank.com/Admin/TaxIdMaintenance/SelectTaxEntity.aspx")) {
                driver.findElement(By.xpath("//*[normalize-space(text())='" + nameOfEntityName[p] + "']/parent::tr/td[1]/input")).click();                 //normalize-space is to remove spaces and name of entity is a name of Company which user wants to select from a list
                driver.findElement(By.id("BodyContentPlaceHolder_pAddButton")).click();
                Assert.assertEquals("Tax ID Add Was Successful.", "Tax ID Add Was Successful.");
                driver.findElement(By.id("BodyContentPlaceHolder_pCloseButton")).click();

            } else {
                Assert.assertEquals("Tax ID Add Was Successful.", "Tax ID Add Was Successful.");                                                       //Verification of TaxID
            }
            p++;


        }


        driver.findElement(By.xpath("//*[@id=\"Accounts-Tab\"]/span")).click();                                                                        // Click on Accounts Tab
        driver.findElement(By.id("BodyContentPlaceHolder_pSetupAccountsButton")).click();                                                              // Setup Accounts
        int checkBox = driver.findElements(By.xpath("//table[@id='BodyContentPlaceHolder_pAvailableAcctsTable'] //input[@type='checkbox']")).size();
        for (int k=1; k<=checkBox;k++) {
            driver.findElement(By.xpath("(//td[@class='CheckBox'])[" + k + "]")).click();
            WebElement accountNumberText= driver.findElement(By.xpath("(//td[@class='AccountNumber HighlightedColumn'])[" + k + "]"));
            String accountNumberValue = accountNumberText.getText();
            if(accountNumberValue.startsWith("5")) {
                driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("Checking");
            }
            if(accountNumberValue.startsWith("4")){
                driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("Savings");
            }
            if(accountNumberValue.startsWith("6")){
                driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("CD");
            }
        }
        int n=0;
        String[] placeHolderName =placeHolder.split(", ");
        String[] nickNameName =nickName.split(", ");

        for(String l: placeHolderName) {
            driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "']")).click();
            driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "']")).click();
            driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "TXT']")).clear();
            driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "TXT']")).sendKeys(nickNameName[n]);
            n++;
        }
        driver.findElement(By.id("BodyContentPlaceHolder_pAddAccountsButton")).click();                                                                // Add selected accounts
        driver.findElement(By.id("BodyContentPlaceHolder_pConfirmAddAccountsButton")).click();                                                         // Confirm Add
        Assert.assertEquals("Account Add Was Successful.", "Account Add Was Successful.");                                                             // Verification

        driver.findElement(By.xpath("//*[@id=\"Users-Tab\"]/span")).click();
        Assert.assertEquals("User Maintenance - Create New User", "User Maintenance - Create New User");
        driver.findElement(By.id("BodyContentPlaceHolder_btnAddNewUser")).click();                                                                      // Add new user button
        driver.findElement(By.id("BodyContentPlaceHolder_pUserId")).sendKeys(userID);                                                                   // Entering userID
        driver.findElement(By.id("BodyContentPlaceHolder_pUserName")).sendKeys(userName);                                                               // Entering userName
        driver.findElement(By.id("BodyContentPlaceHolder_pUserEmail")).sendKeys(userEmail);                                                             // Entering user email
        driver.findElement(By.id("BodyContentPlaceHolder_mobileNumber")).sendKeys(userMobileNumber);                                                    // Entering user phone number
        driver.findElement(By.id("BodyContentPlaceHolder_pTokenModel_2")).click();                                                                      // Non token radio button
        driver.findElement(By.id("BodyContentPlaceHolder_pBusinessCDAccess")).click();                                                                  // Business CDs
        driver.findElement(By.id("BodyContentPlaceHolder_pCorporateVisaAccess")).click();                                                               // Corporate Credit Card
        driver.findElement(By.id("BodyContentPlaceHolder_ssoAccess")).click();                                                                          // Multi purpose login
        driver.findElement(By.id("BodyContentPlaceHolder_pARP")).click();                                                                               // Account Reconcilement
        driver.findElement(By.id("BodyContentPlaceHolder_pAlerts")).click();                                                                            // Alerts
        driver.findElement(By.id("BodyContentPlaceHolder_btnAddContinue")).click();                                                                     // Continue button
        Assert.assertEquals("User Maintenance - Approve User Changes", "User Maintenance - Approve User Changes");                                      // Verify Approve user changes
        driver.findElement(By.id("BodyContentPlaceHolder_btnAppContinue")).click();                                                                     // Continue button
        Assert.assertEquals("Welcome Letter Generated.", "Welcome Letter Generated.");                                                                  // Verifying user created or not
        driver.findElement(By.id("BodyContentPlaceHolder_pCloseButton")).click();                                                                       // Close button

        driver.findElement(By.xpath("//*[@id=\"Accounts-Tab\"]/span")).click();                                                                         // Clicking on Accounts Tab
        int numberOfCheckboxes = driver.findElements(By.xpath("//input[@type='checkbox']")).size();
        for (int j = 2; j < numberOfCheckboxes; j++) {
            driver.findElement(By.xpath("//table[@id='BodyContentPlaceHolder_pCompanyAccountsTable']/tbody/tr["+j+"]/td/input")).click();
            Thread.sleep(100L);
            driver.findElement(By.id("BodyContentPlaceHolder_pEditAccountButton")).click();                                                                 // Modify Account
          /*  for(int alerts : modifyAccountsAlerts){
                if(alerts == 1){
                                                                                       // Alerts
                }
            } */
            driver.findElement(By.id("BodyContentPlaceHolder_pAlerts")).click();
            driver.findElement(By.id("BodyContentPlaceHolder_pBusinessCD")).click();                                                                        // Business Cds
            driver.findElement(By.id("BodyContentPlaceHolder_reconcilements")).click();                                                                     // Reconcilement
            driver.findElement(By.id("BodyContentPlaceHolder_pMultipurposeEdit")).click();                                                                  // Multi purpose SSO
            driver.findElement(By.id("BodyContentPlaceHolder_pLoanActivityEdit")).click();                                                                  // Loan Activity
            driver.findElement(By.id("BodyContentPlaceHolder_pAvailableHoldsEdit")).click();                                                                // Available holds
            driver.findElement(By.id("BodyContentPlaceHolder_pConsolidatedReportsEdit")).click();                                                           // Consolidated reports
            driver.findElement(By.id("BodyContentPlaceHolder_pContinue")).click();                                                                          // Continue button
            driver.findElement(By.id("BodyContentPlaceHolder_pConfirm")).click();                                                                           // Confirm button
            Assert.assertEquals("Account Access Edit Was Successful.", "Account Access Edit Was Successful.");                                              // Verification
            driver.findElement(By.id("BodyContentPlaceHolder_pCancel")).click();                                                                            // Cancel button
        }

        driver.findElement(By.xpath("//*[@id=\"Accounts-Tab\"]/span")).click();
        Assert.assertEquals("Account Maintenance", "Account Maintenance");
        for (int j = 2; j < numberOfCheckboxes; j++) {
            driver.findElement(By.xpath("//table[@id='BodyContentPlaceHolder_pCompanyAccountsTable']/tbody/tr[" +j+ "]/td/input")).click();
            Thread.sleep(100L);
            driver.findElement(By.id("BodyContentPlaceHolder_pEditAccountAccessButton")).click();
            driver.findElement(By.name("ctl00$BodyContentPlaceHolder$AccountRepeater$ctl00$UserGroup")).click();
            driver.findElement(By.id("BodyContentPlaceHolder_AccountRepeater_addSelUser_0")).click();                                                    // Clicking on selected users
            driver.findElement(By.id("BodyContentPlaceHolder_AccountRepeater_confirmAddSelUser_0")).click();                                             // Confirming add user
            driver.findElement(By.name("ctl00$BodyContentPlaceHolder$AccountRepeater$ctl00$UserGroup")).click();                                         // Selecting radio button again
            driver.findElement(By.id("BodyContentPlaceHolder_AccountRepeater_changeUserAccess_0")).click();                                              // Change user Access button
            driver.findElement(By.id("BodyContentPlaceHolder_pARP")).click();                                                                            // Account reconcilement (ARP)
            driver.findElement(By.id("BodyContentPlaceHolder_pARPInputIssue")).click();                                                                  // ARP Create single issue
            driver.findElement(By.id("BodyContentPlaceHolder_pARPEditIssue")).click();                                                                   // Arp Edit Issue
            driver.findElement(By.id("BodyContentPlaceHolder_pAlerts")).click();                                                                         // Alerts
            driver.findElement(By.id("BodyContentPlaceHolder_pBusinessCDPurchase")).click();                                                             // Business CD Purchase
            driver.findElement(By.id("BodyContentPlaceHolder_pMultipurposeEdit")).click();                                                               // Multi purpose SSO
            driver.findElement(By.id("BodyContentPlaceHolder_pLoanActivityEdit")).click();                                                               // Loan Activity
            driver.findElement(By.id("BodyContentPlaceHolder_pAvailableHoldsEdit")).click();                                                             // Available holds
            driver.findElement(By.id("BodyContentPlaceHolder_pConsolidatedReportsEdit")).click();                                                        // Consolidated reports
            driver.findElement(By.id("BodyContentPlaceHolder_pContinue")).click();
            driver.findElement(By.id("BodyContentPlaceHolder_pConfirm")).click();
            Assert.assertEquals("User Account Permissions Successfully Updated.", "User Account Permissions Successfully Updated.");
            driver.findElement(By.id("BodyContentPlaceHolder_pCloseButton")).click();
            driver.findElement(By.id("BodyContentPlaceHolder_cancel")).click();  // Cancel button
        }

    }








    @DataProvider(name="drivedata")
    public Object[][] getData() throws IOException {

        FileInputStream fis= new FileInputStream("C:\\Users\\10001926\\eclipse-workspace\\testdata.xlsx");
        XSSFWorkbook workbook = new XSSFWorkbook(fis);
        XSSFSheet sheet = workbook.getSheetAt(0);
        int rowCount = sheet.getPhysicalNumberOfRows();
        XSSFRow row = sheet.getRow(0);
        int colCount=row.getLastCellNum();

        Object data[][] = new Object[colCount-1][rowCount-1];
        for(int i=0;i<rowCount-1;i++) {
            row=sheet.getRow(i+1);
            for(int j=0;j<colCount-1;j++) {
                XSSFCell cell = row.getCell(j+1);
                data[j][i] = formatter.formatCellValue(cell);


            }
        }
        return data;

    }

    @AfterMethod
    public void takeScreenShotOnFailure(ITestResult testResult) throws IOException {
        if (testResult.getStatus() == ITestResult.FAILURE) {
            System.out.println(testResult.getStatus());
            File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
            FileUtils.copyFile(scrFile, new File("errorScreenshots\\" + testResult.getName() +  ".jpg"));
        }
    }


    }





/*
package com.dollarbank;

import org.apache.commons.io.FileUtils;
import org.apache.poi.ss.usermodel.DataFormatter;
import org.apache.poi.xssf.usermodel.XSSFCell;
import org.apache.poi.xssf.usermodel.XSSFRow;
import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.ITestResult;
import org.testng.annotations.*;

import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;

import java.util.Arrays;
import java.util.concurrent.TimeUnit;

public class ACIAdminPlayGround {

    DataFormatter formatter = new DataFormatter();
    String driverPath = "C:\\Users\\10001926\\JavaDependencies\\chromedriver.exe";
    public WebDriver driver;



    @Test(dataProvider="drivedata")
    public void testcase(String masterCompanyAccountNumber, String socialSecurityArray, String companyName, String companyDivision, String accountName, String userID, String userName, String userEmail, String userMobileNumber, String nameOfEntity, String placeHolder, String nickName) throws InterruptedException {
        //long masterCompanyAccountNumber = 52671243293L;  5 for checking account and 4 for savings account
       //int[] socialSecurityArray = {208840076,251068614,256001017};
        // String companyName = "Patels Automation60";
       // String accountName = "Checking60";
      //  String userID = "automate60";
     //   String userName = "automate60";
     //   String userEmail = "ipatel744@dollarbank.com";
    //    String userMobileNumber = "4122610000";
   //     String[] nameOfEntity = {"CAMOSUN COLLEGE","HERITAGE WOODS SECONDARY SCHOOL","SOLUTIA"};         // Name of company if one SSN is given to more than one company
      //  int companyDivision = 1;                                       //1 = Pittsburgh , 2= Ohio
       // int[] modifyAccountsAlerts = {0};
    //    long[] placeHolder = {52670857574L, 52671243293L};                    // account number to for a company nickname
     //   String[] nickName = {"MyName","YourName"};                            //nickname to a company


        System.setProperty("webdriver.chrome.driver", driverPath);
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
        driver.get("https://test.casso.dollarbank.com/Admin/AdministrativeLogon/AdministrativeLogon.aspx");

        driver.findElement(By.xpath("//input[@name='ctl00$BodyContentPlaceHolder$pUserID']")).sendKeys("Ishit");
        driver.findElement(By.xpath("//input[@name='ctl00$BodyContentPlaceHolder$pPassword']")).sendKeys("Ishit@2021");
        driver.findElement(By.xpath("//input[@name = 'ctl00$BodyContentPlaceHolder$pSubmit']")).click();
        Assert.assertEquals(driver.findElement(By.id("PageHeader-Title")).getText(), "Welcome to the CashANALYZER Administration Site");

        driver.findElement(By.xpath("//*[@id=\"CompanyMaintenance-Tab\"]/span")).click();                                                                 //COMPANY Tab in upper module
        Assert.assertEquals("Company Maintenance", "Company Maintenance");                                                                                // Company Tab
        driver.findElement(By.cssSelector("input[name ='ctl00$BodyContentPlaceHolder$AddButton']")).click();                                              //Enroll Company

        Assert.assertEquals("Company Maintenance - Enroll Company Screen", "Company Maintenance - Enroll Company Screen");                               //Company Enrollment page
                driver.findElement(By.cssSelector("input[name = 'ctl00$BodyContentPlaceHolder$pCompanyName']")).sendKeys(companyName);                           //Adding Company Name
                driver.findElement(By.xpath("//input[@id = 'BodyContentPlaceHolder_pCompanyDivision" + companyDivision + "']")).click();                                         //Selecting Pittsburgh or Ohio Radio Button
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pMasterProfileAccount']")).sendKeys(masterCompanyAccountNumber);     //Master Profile Account number must include 5 or 4 in the beginning
                /* CashAnalyzer Product Access
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pAlertsAccess']")).click();                                        //Alerts
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pBusinessCdAccess']")).click();                                    //Business Cds
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pCorporateVisaAccess']")).click();                                 //Corporate Credit Card
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pAccountReconcilementAccess']")).click();                          //Reconcilement
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$pRemoteDepositAccess']")).click();                                 //Remote Deposit
                /* CashAnalyzer Multipurpose SSO Access
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$ssoOptions']")).click();                                           //Multipurpose SSO
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$loanActivity']")).click();                                         //Loan Activity
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$consolidatedReports']")).click();                                  //Consolidated Reports
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$availableHolds']")).click();                                       //Available Holds
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$ContinueButton']")).click();                                       //Submit Company
                /* Company maintenance review screen
                Assert.assertEquals("Company Maintenance - Review Screen", "Company Maintenance - Review Screen");                                             //Verifying Review Screen
                driver.findElement(By.cssSelector("input[name='ctl00$BodyContentPlaceHolder$ReviewCompanyButton']")).click();                                  //Submit Review Button
                /* Verifying if company is created or not
                driver.findElement(By.id("BodyContentPlaceHolder_mSortByName")).click();                                                                       //Sort By Company Name
                driver.findElement(By.id("BodyContentPlaceHolder_cbCompany_cbCompany_TextBox")).click();                                                       //Selecting checkbox
                driver.findElement(By.id("BodyContentPlaceHolder_cbCompany_cbCompany_TextBox")).sendKeys(companyName);                                         //Entering CompanyName
                driver.findElement(By.id("PageBody")).click();                                                                                                 //Clicking somewhere on page to select company
                Assert.assertEquals(masterCompanyAccountNumber, masterCompanyAccountNumber);                                                                   //Verifying if company is created or not

                driver.findElement(By.xpath("//*[@id=\"TaxID-Tab\"]/span")).click();                                                                            // Click on Tax ID Tab
                Assert.assertEquals(companyName, companyName);                                                                                                  // Verifying company name

                int p=0;
                String[] nameOfEntityName =nameOfEntity.split(", ");
                String[] ssn=socialSecurityArray.split(", ");
                int social= ssn.length;
                // for(String i:ssn) {
                //}
                for(int i=0;i<social;i++){
        driver.findElement(By.id("BodyContentPlaceHolder_pTaxId")).sendKeys(ssn[i]);                                                    // Sending SSN Number in form of i
        driver.findElement(By.id("BodyContentPlaceHolder_pCanDisplayBusinessCD_0")).click();                                                       // Business CD yes
        driver.findElement(By.id("BodyContentPlaceHolder_pAddButton")).click();                                                                    // Submit button
        //for (String j : nameOfEntity)
        if (driver.getCurrentUrl().equals("https://test.casso.dollarbank.com/Admin/TaxIdMaintenance/SelectTaxEntity.aspx")) {
        driver.findElement(By.xpath("//*[normalize-space(text())='" + nameOfEntityName[p] + "']/parent::tr/td[1]/input")).click();                 //normalize-space is to remove spaces and name of entity is a name of Company which user wants to select from a list
        driver.findElement(By.id("BodyContentPlaceHolder_pAddButton")).click();
        Assert.assertEquals("Tax ID Add Was Successful.", "Tax ID Add Was Successful.");
        driver.findElement(By.id("BodyContentPlaceHolder_pCloseButton")).click();

        } else {
        Assert.assertEquals("Tax ID Add Was Successful.", "Tax ID Add Was Successful.");                                                       //Verification of TaxID
        }
        p++;


        }


        driver.findElement(By.xpath("//*[@id=\"Accounts-Tab\"]/span")).click();                                                                        // Click on Accounts Tab
        driver.findElement(By.id("BodyContentPlaceHolder_pSetupAccountsButton")).click();                                                              // Setup Accounts
        int checkBox = driver.findElements(By.xpath("//table[@id='BodyContentPlaceHolder_pAvailableAcctsTable'] //input[@type='checkbox']")).size();
        for (int k=1; k<=checkBox;k++) {
        driver.findElement(By.xpath("(//td[@class='CheckBox'])[" + k + "]")).click();
        WebElement accountNumberText= driver.findElement(By.xpath("(//td[@class='AccountNumber HighlightedColumn'])[" + k + "]"));
        String accountNumberValue = accountNumberText.getText();
        if(accountNumberValue.startsWith("5")) {
        driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("Checking");
        }
        if(accountNumberValue.startsWith("4")){
        driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("Savings");
        }
        if(accountNumberValue.startsWith("6")){
        driver.findElement(By.xpath("(//input[@type='text'])[" + k + "]")).sendKeys("CD");
        }
        }
        int n=0;
        String[] placeHolderName =placeHolder.split(", ");
        String[] nickNameName =nickName.split(", ");

        for(String l: placeHolderName) {
        driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "']")).click();
        driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "']")).click();
        driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "TXT']")).clear();
        driver.findElement(By.xpath("//input[@name= 'ctl00$BodyContentPlaceHolder$" + l + "TXT']")).sendKeys(nickNameName[n]);
        n++;
        }
        driver.findElement(By.id("BodyContentPlaceHolder_pAddAccountsButton")).click();                                                                // Add selected accounts
        driver.findElement(By.id("BodyContentPlaceHolder_pConfirmAddAccountsButton")).click();                                                         // Confirm Add
        Assert.assertEquals("Account Add Was Successful.", "Account Add Was Successful.");                                                             // Verification

        driver.findElement(By.xpath("//*[@id=\"Users-Tab\"]/span")).click();
        Assert.assertEquals("User Maintenance - Create New User", "User Maintenance - Create New User");
        driver.findElement(By.id("BodyContentPlaceHolder_btnAddNewUser")).click();                                                                      // Add new user button
        driver.findElement(By.id("BodyContentPlaceHolder_pUserId")).sendKeys(userID);                                                                   // Entering userID
        driver.findElement(By.id("BodyContentPlaceHolder_pUserName")).sendKeys(userName);                                                               // Entering userName
        driver.findElement(By.id("BodyContentPlaceHolder_pUserEmail")).sendKeys(userEmail);                                                             // Entering user email
        driver.findElement(By.id("BodyContentPlaceHolder_mobileNumber")).sendKeys(userMobileNumber);                                                    // Entering user phone number
        driver.findElement(By.id("BodyContentPlaceHolder_pTokenModel_2")).click();                                                                      // Non token radio button
        driver.findElement(By.id("BodyContentPlaceHolder_pBusinessCDAccess")).click();                                                                  // Business CDs
        driver.findElement(By.id("BodyContentPlaceHolder_pCorporateVisaAccess")).click();                                                               // Corporate Credit Card
        driver.findElement(By.id("BodyContentPlaceHolder_ssoAccess")).click();                                                                          // Multi purpose login
        driver.findElement(By.id("BodyContentPlaceHolder_pARP")).click();                                                                               // Account Reconcilement
        driver.findElement(By.id("BodyContentPlaceHolder_pAlerts")).click();                                                                            // Alerts
        driver.findElement(By.id("BodyContentPlaceHolder_btnAddContinue")).click();                                                                     // Continue button
        Assert.assertEquals("User Maintenance - Approve User Changes", "User Maintenance - Approve User Changes");                                      // Verify Approve user changes
        driver.findElement(By.id("BodyContentPlaceHolder_btnAppContinue")).click();                                                                     // Continue button
        Assert.assertEquals("Welcome Letter Generated.", "Welcome Letter Generated.");                                                                  // Verifying user created or not
        driver.findElement(By.id("BodyContentPlaceHolder_pCloseButton")).click();                                                                       // Close button

        driver.findElement(By.xpath("//*[@id=\"Accounts-Tab\"]/span")).click();                                                                         // Clicking on Accounts Tab
        int numberOfCheckboxes = driver.findElements(By.xpath("//input[@type='checkbox']")).size();
        for (int j = 2; j < numberOfCheckboxes; j++) {
        driver.findElement(By.xpath("//table[@id='BodyContentPlaceHolder_pCompanyAccountsTable']/tbody/tr["+j+"]/td/input")).click();
        Thread.sleep(100L);
        driver.findElement(By.id("BodyContentPlaceHolder_pEditAccountButton")).click();                                                                 // Modify Account
          /*  for(int alerts : modifyAccountsAlerts){
                if(alerts == 1){
                                                                                       // Alerts
                }
            }
        driver.findElement(By.id("BodyContentPlaceHolder_pAlerts")).click();
        driver.findElement(By.id("BodyContentPlaceHolder_pBusinessCD")).click();                                                                        // Business Cds
        driver.findElement(By.id("BodyContentPlaceHolder_reconcilements")).click();                                                                     // Reconcilement
        driver.findElement(By.id("BodyContentPlaceHolder_pMultipurposeEdit")).click();                                                                  // Multi purpose SSO
        driver.findElement(By.id("BodyContentPlaceHolder_pLoanActivityEdit")).click();                                                                  // Loan Activity
        driver.findElement(By.id("BodyContentPlaceHolder_pAvailableHoldsEdit")).click();                                                                // Available holds
        driver.findElement(By.id("BodyContentPlaceHolder_pConsolidatedReportsEdit")).click();                                                           // Consolidated reports
        driver.findElement(By.id("BodyContentPlaceHolder_pContinue")).click();                                                                          // Continue button
        driver.findElement(By.id("BodyContentPlaceHolder_pConfirm")).click();                                                                           // Confirm button
        Assert.assertEquals("Account Access Edit Was Successful.", "Account Access Edit Was Successful.");                                              // Verification
        driver.findElement(By.id("BodyContentPlaceHolder_pCancel")).click();                                                                            // Cancel button
        }

        driver.findElement(By.xpath("//*[@id=\"Accounts-Tab\"]/span")).click();
        Assert.assertEquals("Account Maintenance", "Account Maintenance");
        for (int j = 2; j < numberOfCheckboxes; j++) {
        driver.findElement(By.xpath("//table[@id='BodyContentPlaceHolder_pCompanyAccountsTable']/tbody/tr[" +j+ "]/td/input")).click();
        Thread.sleep(100L);
        driver.findElement(By.id("BodyContentPlaceHolder_pEditAccountAccessButton")).click();
        driver.findElement(By.name("ctl00$BodyContentPlaceHolder$AccountRepeater$ctl00$UserGroup")).click();
        driver.findElement(By.id("BodyContentPlaceHolder_AccountRepeater_addSelUser_0")).click();                                                    // Clicking on selected users
        driver.findElement(By.id("BodyContentPlaceHolder_AccountRepeater_confirmAddSelUser_0")).click();                                             // Confirming add user
        driver.findElement(By.name("ctl00$BodyContentPlaceHolder$AccountRepeater$ctl00$UserGroup")).click();                                         // Selecting radio button again
        driver.findElement(By.id("BodyContentPlaceHolder_AccountRepeater_changeUserAccess_0")).click();                                              // Change user Access button
        driver.findElement(By.id("BodyContentPlaceHolder_pARP")).click();                                                                            // Account reconcilement (ARP)
        driver.findElement(By.id("BodyContentPlaceHolder_pARPInputIssue")).click();                                                                  // ARP Create single issue
        driver.findElement(By.id("BodyContentPlaceHolder_pARPEditIssue")).click();                                                                   // Arp Edit Issue
        driver.findElement(By.id("BodyContentPlaceHolder_pAlerts")).click();                                                                         // Alerts
        driver.findElement(By.id("BodyContentPlaceHolder_pBusinessCDPurchase")).click();                                                             // Business CD Purchase
        driver.findElement(By.id("BodyContentPlaceHolder_pMultipurposeEdit")).click();                                                               // Multi purpose SSO
        driver.findElement(By.id("BodyContentPlaceHolder_pLoanActivityEdit")).click();                                                               // Loan Activity
        driver.findElement(By.id("BodyContentPlaceHolder_pAvailableHoldsEdit")).click();                                                             // Available holds
        driver.findElement(By.id("BodyContentPlaceHolder_pConsolidatedReportsEdit")).click();                                                        // Consolidated reports
        driver.findElement(By.id("BodyContentPlaceHolder_pContinue")).click();
        driver.findElement(By.id("BodyContentPlaceHolder_pConfirm")).click();
        Assert.assertEquals("User Account Permissions Successfully Updated.", "User Account Permissions Successfully Updated.");
        driver.findElement(By.id("BodyContentPlaceHolder_pCloseButton")).click();
        driver.findElement(By.id("BodyContentPlaceHolder_cancel")).click();  // Cancel button
        }

        }








@DataProvider(name="drivedata")
public Object[][] getData() throws IOException {

        FileInputStream fis= new FileInputStream("C:\\Users\\10001926\\eclipse-workspace\\testdata.xlsx");
        XSSFWorkbook workbook = new XSSFWorkbook(fis);
        XSSFSheet sheet = workbook.getSheetAt(0);
        int rowCount = sheet.getPhysicalNumberOfRows();
        XSSFRow row = sheet.getRow(0);
        int colCount=row.getLastCellNum();

        Object data[][] = new Object[colCount-1][rowCount-1];
        for(int i=0;i<rowCount-1;i++) {
        row=sheet.getRow(i+1);
        for(int j=0;j<colCount-1;j++) {
        XSSFCell cell = row.getCell(j+1);
        data[j][i] = formatter.formatCellValue(cell);


        }
        }
        return data;

        }

@AfterMethod
public void takeScreenShotOnFailure(ITestResult testResult) throws IOException {
        if (testResult.getStatus() == ITestResult.FAILURE) {
        System.out.println(testResult.getStatus());
        File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
        FileUtils.copyFile(scrFile, new File("errorScreenshots\\" + testResult.getName() +  ".jpg"));
        }
        }


        }


 */









	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
					
