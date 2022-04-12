# FitNesseAction
Demo GitHub Action to run [FitNesse](http://fitnesse.org) with [FitSharp](https://fitsharp.github.io/) using the [fitnesse-composite-action](../../../fitnesse-composite-action).

It uses .NET Core 5.0, so should be platform independent. It was tested (only) on GitHub hosted Linux runners.

Check out [fitnesse-run.yml](.github/workflows/fitnesse-run.yml) for the action script.

## Setting things up:
* Prepare the Wiki test pages in the [FitNesseRoot](FitNesseRoot) folder. 
* Create [config.xml](fixtures/config.xml) in the fixtures folder, pointing to all relevant assemblies.
* In the action script, download the required fixtures. Make sure they end up in the location that config.xml refers to.
* Call essenius/fitnesse-composite-action, specifying at least test-spec (which test or suite to execute) and fixture-folder.

## Test spec:
Use the relative URL that you would use in FitNesse to run the test:
* Execute a suite called GameManagmentSuite: `GameManagementSuite?suite`
* Execute a test called FibonacciTest: `FibonacciTest?test`

## The results
The action will fail if it cannot run FitNesse, if FitNesse returns an error, and if one of the executed test cases fails.
Details can be found in the artifacts delivered with the test run (see summary page). The zip file contains the following:
* `result.xml`: the result that FitNesse has returned on the output channel
* `error.log`: the message that FitNesse has logged on the error channel
* Two files that are generated from result.xml by the composite action:
  * `DetailedResults.html`: the test log showing the tests that have ran (viewable in a browser). 
  * `results_nunit.xml`: the test results in NUnit3 format.

# Contribute
Enter an [issue](../../issues) or provide a [pull request](../../pulls). 
