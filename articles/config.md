# Configuration
The settings for the extension are split between a [configuration file](#config-file) (.altestrunner/config.json) - mostly used by the PowerShell module and [extension settings](#extension-settings) in Visual Studio Code (mostly used by the typescript).

# Config File
The config file will be created automatically when required and is stored in the .altestrunner folder and is called config.json. You can also open (and create if it is doesn't already exist) the file with the ```Open Config File``` command in VS Code.

Most of the values in this file are set automatically, but you will need to update them for [debugging](debugging-tests.md) and [code coverage](code-coverage.md) (which use the [test runner service](test-runner-service.md) app).

## containerResultPath
The local path which test results can be saved to by the container. Needs to be a folder which is shared with the container. Should be set automatically.

## launchConfigName
If your test project has multiple launch configurations you will be asked to select the one that you want to use with AL Test Runner. Your selection is saved here and values read from the configuration in launch.json.

## securePassword, userName
The UserPassword credentials used to authenticate with the container.

## companyName
The company to excute tests in. If your container has more than one company you will be prompted to select which one to use and the result is saved here.

## testSuiteName
Only required for BC14. The name of the test suite to execute.

## vmUserName, vmSecurePassword
The credentials used to create a PS remoting session on a remote docker host.

## remoteContainerName
When working with a remote docker host typically the server setting in your launch.json file will be the name of the host machine and not the name of the container. This setting holds the name of the container to execute remote PowerShell commands against.

## dockerHost
The name of the remote docker host machine. Leaving this blank indicates that docker is running locally i.e. on the same machine as the terminal hosted by VS Code.

## newPSSessionOptions
If using PS remoting you can use this setting to hold additional paramters and switches which should be used by the ```New-PSSession``` command to open a new PowerShell session on the remote machine.

## testRunnerServiceUrl
The OData endpoint of the [test runner service](test-runner-service.md). Should be in the format http://containername:7048/BC/ODataV4/TestRunner?company=My%20Company&tenant=default. Include the company name (which should match the [companyName](#companyname) setting) and the tenant (if the container is multi-tenant).

## codeCoveragePath
The path that the code coverage JSON file is downloaded to. Defaults to .altestrunner/codecoverage.json. It is not normally necessary to change this.

# Extension Settings

## Test Decoration
### Decorate Test Methods
Determines whether the names of test methods are decorated in the editor. Colors are defined in RGBA format and can be edited in the settings.json file.
### Passing Tests Color
The color to highlight tests which are passing in the editor.
### Failing Tests Color
The color to highlight tests which are failing in the editor.
### Untested Tests Color
The color to highlight tests with no results in the editor.
### Highlight Failing Line
Determines whether the line of a failing test which led to an error is highlighted in the editor (according to the Failing Line Decoration setting).
### Failing Line Decoration
The CSS to decorate the line of a failing test which led to the error.
### Test Output Location
Determines where the test results are output to. Choose between ```Output``` (the AL Test Runner output channel) or ```Editor``` (results are displayed in a new editor window).
### Code Lens
Determines whether ```Run Test``` and ```Debug Test``` Code Lens actions are displayed above test methods.
## Publishing Options
The following settings control if and how the test app is published to your container before tests are run.
### Publish Before Tests
Select from ```Publish```, ```Rapid application publishing``` or ```None```. The corresponding command from the AL Language extension will be run on the test project before the test(s) are executed.

This allows you to publish your test app to your container before running tests automatically.
### Enable Publishing from PowerShell
(**Experimental**) Rather than publishing through the AL Language extension commands, enable this setting to publish from PowerShell with the bccontianerhelper module. This option gives AL Test Runner better control over how the test run behaves if the test app fails to compile or publish.
### Publish Timeout
The time (in milliseconds) to wait before assuming that the test app failed to compile and/or publish into the container.
## Test Folder Name
When publishing apps from PowerShell this setting must be set. Enter the name of the folder in the workspace which contains your test project.
### Pre/Post Test Command
A PowerShell command to execute in the terminal before or after the tests have been run. See the commands which are available in the ALTestRunner module with ```Get-Command -Module ALTestRunner```
## Code Coverage
The following settings are used by the [code coverage](code-coverage.md) features of AL Test Runner.
### Enable Code Coverage
Determines whether code coverage statistics are calculated and displayed after running tests.

### Code Coverage Exclude Files
This is a regular expression to define files in your project which should be excluded from the code coverage statistics. Typically this would be used to exclude files in your test project.

Any files whose paths match this setting will be excluded from code coverage.

For example, if your test codeunits are contained in a folder named "tests" then set this setting to ```tests```.

### Code Coverage Path
Typically this setting can be left blank. AL Test Runner will automatically discover the codeCoverage.json file.

The purpose of this setting is to hold the relative path from your project file to the codeCoverage.json file which is downloaded when calculating code coverage.
