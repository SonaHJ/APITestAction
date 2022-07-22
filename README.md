## HCL OneTest API
This action enables you to run HCL OneTest API tests.

## Pre requisites

1. Create a github repository
2. Create a folder named ".github" in the root of the repository
3. Create a folder named "workflows" inside the ".github" folder.
5. Create a .yml file with any name , inside the "workflow" folder and you need to code as following example in that yml file
## Example usage

```yaml
name: HCL OneTest API

on:
    workflow_dispatch:
        inputs:
            selectedConfigType:
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

    WebUI-Action:
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
7. Replace the example input values with your details.
8. Push it into the main branch
9. Go to the Actions section in the repository and select the workflow.
10. Click the Run workflow dropdown and the list of input boxes get displayed.

To configure agent:
1. Go to settings (Repo).
2. Select action -> runner.
3. Click Create self-hosted runner, follow the download and configure instruction

## Inputs

### `projectdir`

Fully qualified path to the HCL OneTest API project directory.

### `projectname`

**Required** The name of the API test project.

### `environment`

**Required** The API Test environment to use for this execution.

### `tests`

Semicolon separated list of tests/suites to run.

### `junitDir`
Specify the folder to export the JUnit reports to.
