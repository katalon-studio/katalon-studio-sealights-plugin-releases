# katalon-studio-sealights-plugin

## Purpose
This plugin is for integration with Sealights to
- List of excluded test cases that has been analyzed by previous run to reduce the needed to run all test cases.
- Report the test result back to feed for Sealights Test Analysis.

- This plugin does not include installing Sealights agent or code instrument to collect test coverage.

## How to use
1. Install the plugins via Katatan store []
2. Setup plugin configuration

   ![sealights_configuration](./docs/images/sealights_configuration_ui.png)

   - Using Sealights: Enable or disable Sealights Plugin.
   - URL: Your sealights url to connect sealights server.
   - Agent Token: Agent token generated from the SeaLights server 
   - Lab Id: Unique ID for a set of test labs in case multiple labs are running simultaneously.
   - Test Stage: Name of the test stage.
   - Build Session Id: Session ID of configuration created.
   - Session Timeout (seconds): Test session timeout (by default: 14400).
4. Create dynamic test suite.
When creating dynamic test suite. The plugin will get the exclude test case from sealights and generate a list of test cases to run.
5. Execute the created dynamic test suite with either one of two mode below:
    + Inside Katalon Studio:
    It should be only used in testing mode with testing environment do not run this in real environment as it could impact the Sealights Test Analysis for next run.
    + In command-line mode execution
    #### List Syntax Sealights
    Default if you don't pass parameters. Then the default value will be taken from within `Katalon Studio` => `Project` => `Settings` => `Plugins` => `Sealights`
    - `-sealightsUrl` : URL connect to sealights server (Optional).
    - `-sealightsAgentToken`: Agent Token (Optional).
    - `-sealightsLabId`:  Lab Id (Optional).
    - `-sealightsTestStage`: Test Stage (Optional).
    - `-sealightsBSId`: Build Session Id (Optional). 
    - `-sealightsSessionTimeout`: Session Timeout (default value is 14400) (Optional).

    ** If optional value is not set, It will be default to UI configuration value if it is not set.

#### For examples
```
katalonc -noSplash -runMode=console -projectPath="C:\Users\Katalon Studio\Project\YourProject.prj" -retry=0 -testSuitePath="Test Suites/download" -executionProfile="default" -browserType="Chrome" --config -sealightsUrl="your sealights server" -sealightsAgentToken="your sealights agent token"
```


## How to contribute
### Build
Requirements:

- JDK 1.8
- Maven 3.3+

Build

`mvn clean package`

### How to test plugin jar in Katalon Studio

- Checkout or get a build of branch `staging-plugin` of KS
- After KS opens, please click on `Plugin` menu, select `Install Plugin` and choose generated jar file.
- If you want to reload this plugin, please click on `Plugin` menu, select `Uninstall Plugin` then select `Install Plugin` again. 


## Companion products

### Katalon TestOps

[Katalon TestOps](https://analytics.katalon.com) is a web-based application that provides dynamic perspectives and an insightful look at your automation testing data. You can leverage your automation testing data by transforming and visualizing your data; analyzing test results; seamlessly integrating with such tools as Katalon Studio and Jira; maximizing the testing capacity with remote execution.

* Read our [documentation](https://docs.katalon.com/katalon-analytics/docs/overview.html).
* Ask a question on [Forum](https://forum.katalon.com/categories/katalon-analytics).
* Request a new feature on [GitHub](CONTRIBUTING.md).
* Vote for [Popular Feature Requests](https://github.com/katalon-analytics/katalon-analytics/issues?q=is%3Aopen+is%3Aissue+label%3Afeature-request+sort%3Areactions-%2B1-desc).
* File a bug in [GitHub Issues](https://github.com/katalon-analytics/katalon-analytics/issues).

### Katalon Studio
[Katalon Studio](https://www.katalon.com) is a free and complete automation testing solution for Web, Mobile, and API testing with modern methodologies (Data-Driven Testing, TDD/BDD, Page Object Model, etc.) as well as advanced integration (JIRA, qTest, Slack, CI, Katalon TestOps, etc.). Learn more about [Katalon Studio features](https://www.katalon.com/features/).

