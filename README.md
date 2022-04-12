# FitNesseAction
Demo GitHub Action to run FitNesse with FitSharp using the [fitnesse-composite-action](../../../fitnesse-composite-action).

It uses .NET Core 5.0, so should be platform independent. It was tested only on GitHub hosted Linux runners.

Check out [fitnesse-run.yml](.github/workflows/fitnesse-run.yml) for the action script.

## How it works:
* Prepare the Wiki test pages in the [FitNesseRoot](FitNesseRoot) folder. 
* Create [config.xml](fixtures/config.xml) in the fixtures folder, pointing to all relevant assemblies.
* In the action script, download the required fixtures. Make sure they end up in the location that config.xml refers to.
* Call essenius/fitnesse-composite-action, specifying at least test-spec (which test or suite to execute) and fixture-folder.

## Test spec:
Use the relative URL that you would use in FitNesse to run the test:
* Execute a suite called GameManagmentSuite: `GameManagementSuite?suite`
* Execute a test called FibonacciTest: `FibonacciTest?test`

# Contribute
Enter an [issue](../../issues) or provide a [pull request](../../pulls). 
