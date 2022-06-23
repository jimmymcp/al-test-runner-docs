# Test Runner Service
Test Runner Service is a Business Central app which needs to be installed into your container for AL Test Runner to be able to debug tests and use the [Show Table Data](./show-table-data.md) function.

For a local container you should be able to install the app with the ```Install Test Runner Service``` command in Visual Studio Code.

For remote containers you will need to download the app from GitHub at [https://github.com/jimmymcp/test-runner-service/raw/master/James%20Pearson_Test%20Runner%20Service.app](https://github.com/jimmymcp/test-runner-service/raw/master/James%20Pearson_Test%20Runner%20Service.app).

### testRunnerServiceUrl

Once you have installed the app you need to set the URL that the REST endpoint can be reached at.

Open the config.json file in the .altestrunner folder (or use the ```Open Config File``` command from the command palette). Set the correct URL for the service in the **testRunnerServiceUrl** key.

Note that the URL must include both the company name and the tenant (if your container was creating in multi-tenant mode). As example of the URL is:

```
http://containername:7048/BC/ODataV4/TestRunner?company=My%20Company&tenant=default
```

Replace ```containername``` with the name of your container. For a remote container (hosted on a different machine) this URL will be different and you will need to ensure that the OData services port is accessible.

For more details on configuring Business Central for OData services [see here](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/administration/configure-server-instance#ODataServices).