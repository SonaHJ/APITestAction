## HCL OneTest API
This action enables you to run HCL OneTest API tests.

## Pre requisites

1. Create a github repository
2. Create a folder named ".github/workflows" in the root of the repository
3. Create a .yml file with any name, inside the ".github/workflows" folder and you need to code as detailed below in that yml file

## Example usage

```yaml
name: HCL OneTest API

on:
    workflow_dispatch:
        inputs:
            configurationType:
                description: 'Configuration Type'
                required: true
            productpath:
                description: 'Product Path'
                required: true
            projectdir:
                description: 'Project Directory'
                required: true
            projectname:
                description: 'Project Name'
                required: true
            environment:
                description: 'Environment'
                required: true
            tests:
                description: 'Test(s) to run'
                required: true
            junitDir:
                description: 'JunitDir'
                required: false

jobs:

    API-Action:
        runs-on: self-hosted
        name: HCL OneTest API
        steps:
         - name: HCL OneTest API
           uses: SonaHJ/APIAction@main
           with:
            selectedConfigType: '${{ github.event.inputs.selectedConfigType }}'
            productpath: '${{ github.event.inputs.productpath }}'
            projectdir: '${{ github.event.inputs.projectdir }}'
            projectname: '${{ github.event.inputs.projectname }}'
            environment: '${{ github.event.inputs.environment }}'
            tests: '${{ github.event.inputs.tests }}'
            junitDir: '${{ github.event.inputs.junitDir }}'
```
4. Push the new yml file into the main branch
5. The you will have to configure agent:
    1. Go to settings (Repo).
    2. Select action -> runner.
    3. Click Create self-hosted runner, follow the download and configure instructions.

6. Go to the Actions section in the repository and select the workflow.
7. Click the Run workflow dropdown and the list of input boxes get displayed.

## Inputs

### `configurationType`

**Required** Type of the test to execute

### `projectdir`

**Required** Fully qualified path to the HCL OneTest API project directory.

### `projectname`

**Required** The name of the API test project.

### `environment`

**Required** The API Test environment to use for this execution.

### `tests`

**Required** Semicolon separated list of tests/suites to run.

### `junitDir`
**Optional** Specify the folder to export the JUnit reports to.
