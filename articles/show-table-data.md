# Show Table Data
Sometimes it is useful while debugging a test to see the record(s) that have been created in a table.

![](..\images\show-table-data.gif)

AL Test Runner adds a context menu item to ```Show Table Data```. Place the cursor somewhere in the name of Record variable that you want to view then select ```Show Table Data``` from the right click menu.

The extension will call find the variable declaration and call the Test Runner Service extension to find the id of this table. Your default browser will then be opened to the table.

## Setup
The [Test Runner Service](test-runner-service.md) extension must be installed and configured in your container.