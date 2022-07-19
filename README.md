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

on: workflow_dispatch

jobs:

    RPT-Action:
        runs-on: self-hosted
        name: HCL OneTest API
        steps:
         - name: HCL OneTest API
           uses: SonaHJ/UIAction@UI_Release
          with:
            projectdir: C:\Program Files\HCL\HCLProducts\API
            selectedConfigType: simple
            projectname: TestAPI
            environment: COMP-1604-1
            tests: test
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
