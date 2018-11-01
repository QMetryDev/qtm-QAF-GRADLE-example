# qtm-QAF-GRADLE-example

This is automation project skeleton to start with using Gradle. Please refer [documentaion](https://qmetry.github.io/qaf/) for more help.


This is sample project with Gradle directory structure:
 
The 'config' directory contains testng.xml file, and is a place holder for configuration files.

The 'resources' directory contains all required resources including properties files and data files, and is a place holder for other resources.

The 'src' directory contains all java files and is a place holder for other java files.

The 'test-results' directory contains result files.

The 'scenarios' directory is the default place holder for all the scenario files. 

Note: This sample project uses chrome driver and it requires chrome driver binary.
You need to download and set webdriver.chrome.driver property in application.properties file with driver binary path.

Please refer https://qmetry.github.io/qaf/

## How to integrate QTMGradlePlugin?

- Step 1 Add QTMGradlePlugin to upload test-result files to QMetry Test Management.
To add QTMGradlePlugin in the project add following code in `build.gradle`
```
plugins
{
    id 'com.qmetry.QTMGradlePlugin' version '1.0'
}
 
qtmConfig 
{ 
	qtmUrl = 'https://testmanagement.qmetry.com' 
	qtmAutomationApiKey = 'cwmtmB6WYXo7Sj0YEchpJYiZgt3nd8TZCmtsDwD' 
	automationFramework='QAS' 
	testResultFilePath='../test-results'
	project='Demo Project'
	testSuiteId='STR-TS-01'
	platform='Chrome' 
	release='Demo Release'
	cycle='Demo Cycle'
	build='Demo Build' 
	
}
```
Please refer https://github.com/qmetry/qmetry-test-management-gradle-plugin for more information

- Step 2 To run the project, from command prompt go to project home and run 
```
gradle test qtmUploadResults
```

- Step 3 Response
```
----------------------------------------------------------------
QMetry Test Management Gradle Plugin : Starting Post Build Action
-----------------------------------------------------------------
QMetry Test Management Gradle Plugin : Reading result files from Directory 'D:/Gradle Plugin/qtm-QAF-GRADLE-example/build/../test-results'
QMetry Test Management Gradle Plugin : Creating zip file...
QMetry Test Management Gradle Plugin : Reading result file 'D:/Gradle Plugin/qtm-QAF-GRADLE-example/build/../test-results/01_Nov_2018_12_46_PM/testresult.zip'
QMetry Test Management Gradle Plugin : Uploading result file...
QMetry Test Management Gradle Plugin : TestSuiteId : STR-TS-01
QMetry Test Management Gradle Plugin : Project : Demo project
QMetry Test Management Gradle Plugin : Release : Demo Release
QMetry Test Management Gradle Plugin : Cycle : Demo Cycle
QMetry Test Management Gradle Plugin : Build : Demo Build
QMetry Test Management Gradle Plugin : Platform : Chrome
QMetry Test Management Gradle Plugin : Response : {"success":true,"code":"CO.IMPORT_SCHEDULED","data":[{"id":27670,"buildID":7150,"platformID":4808,"dropID":1407,"testsuiteId":"STR-TS-01","entityURL":"https://testmanagement.qmetry.com/#/test-suite/92558"}]}
QMetry Test Management Gradle Plugin : Result file successfully uploaded!
QMetry Test Management Gradle Plugin : Finished Post Build Action!
```

- Step 4 View results in QMetry Test Management
To view result login to QMetry Test Management and go to this url `https://testmanagement.qmetry.com/#/test-suite/92558` 
![Test Results](img/qtm-result.png?raw=true "Title")
