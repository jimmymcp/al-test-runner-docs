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
# Config File