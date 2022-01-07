## Deploy using Azure Cloud Shell

- `az extension add --name azure-batch-cli-extensions`

- `git clone https://github.com/jomit/TelemetryLogsGeneratorAndBenchmark.git`

- `cd TelemetryLogsGeneratorAndBenchmark\Infrastructure\ARM`

- `az deployment group create --resource-group DataAtScale --template-file template.json --parameters  parameters.json`

- `cd TelemetryLogsGeneratorAndBenchmark`

- `dotnet publish -r win-x64 -c Release --self-contained true`

- `cd ./bin/Release/netcoreapp3.1/win-x64`

- `zip -r publish.zip publish`

- `az batch application package create --application-name GENERATOR --name adxbenchmarkbatch --package-file publish.zip --resource-group DataAtScale --version-name 1.0`

- `cd TelemetryLogsGeneratorAndBenchmark/Infrastructure/AzureBatchTemplates`

- `az batch account login --resource-group DataAtScale --name adxbenchmarkbatch --shared-key-auth`

- `az batch pool create --template generator-pool.json`

- `az batch job create --template generator-job.json`