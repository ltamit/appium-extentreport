# LT-appium-java-testng

Sample repo to run app automation on real device on LambdaTest.

**Below is the curl request to upload the app for automation**

```
curl --location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--header 'Authorization: Basic <ENTER_BASIC_AUTH_TOKEN_HERE>' \
--form 'name="lambda1"' \
--form 'appFile=@"/path/to/file"'
```

### **Step-1: Upload your application**

```bash
curl -u "YOUR_LAMBDATEST_USERNAME":"YOUR_LAMBDATEST_ACCESS_KEY" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"'
```

> **Note:**
>
> - If you do not have any **.apk** or **.ipa** file, you can run your sample tests on LambdaTest by using our sample [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
> - Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

### **Step 2: Write Your Automation Script**

Write your automation script in the client language of your choice from the ones [supported by Appium](https://appium.io/downloads.html). In the sample automation script in Java for the sample app downloaded above. Ensure to update the `app_url`, `username` and `accesskey` in the below code.

### **Step 3: Execute Your Test Case**

Debug and run your code. Run iOSApp.java or AndroidApp.java in your editor.

**Android:**

```
mvn test -P android-single
```

```
mvn test -P android-parallel
```

**IOS:**

```
mvn test -P ios-single
```

```
mvn test -P ios-parallel
```

### **Step 4: View Test Execution**

Once you have run your tests, you can view the test execution along with logs. You will be able to see the test cases passing or failing. You can view the same at [LambdaTest Automation](https://accounts.lambdatest.com/login).




### ** Extent Report Explanation **
1. Extent Reports Integration:
We integrated Extent Reports into the AndroidApp.java file to generate detailed test reports. This involved several steps:

Imports: Added necessary imports for Extent Reports.
- Initialization: Initialized the ExtentReports instance and set up the ExtentSparkReporter to generate HTML reports.
- Test Logging: Within the AndroidApp1 test method, created an ExtentTest instance for logging purposes. This instance represents a specific test run in the report.
- Exception Handling: In the event of an exception during the test, captured a screenshot and logged the exception message to the Extent Report.


**2. Screenshot on Exception:**
To capture screenshots when an exception occurs:

- Utilized Appium's screenshot capability via the TakesScreenshot interface.
- Created a helper method named getScreenshot that captures and saves the screenshot to a specified path.
- In the event of an exception, the screenshot is captured and attached to the Extent Report log entry for that specific test run.

**3. Modifications to pom.xml:**
To support Extent Reports and file operations:

- Added dependencies for Extent Reports (extentreports and extentreports-testng-adapter) to the pom.xml.
When you reported the "Cannot resolve symbol 'FileUtils'" error, I realized that the Apache Commons IO library was missing. So, I added the commons-io dependency to the pom.xml.

**4. AndroidApp.java Adjustments:**
To ensure the code worked smoothly:

- Imported the necessary classes, including FileUtils from the Apache Commons IO library.
- Integrated the getScreenshot method to handle screenshot capture and storage.

The goal of these modifications was to ensure that, when running your Appium tests, you'd get a detailed report of the test execution. In cases where a test failed, a screenshot would be captured automatically and embedded in the report for better visualization and debugging.

