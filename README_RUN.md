- `az extension add --name azure-batch-cli-extensions`

- `cd TelemetryLogsGeneratorAndBenchmark\Infrastructure\ARM`

- `az deployment group create --resource-group DataAtScale --template-file template.json --parameters  parameters.json`

- `dotnet publish -r win-x64 -c Release --self-contained true`

- Manually zip the `publish` folder

- `az batch application package create --application-name GENERATOR --name adxbenchmarkbatch --package-file publish.zip --resource-group DataAtScale --version-name 1.0`

- `az batch pool create --template generator-pool.json`

- `az batch job create --template generator-job.json`