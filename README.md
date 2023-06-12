[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=mathworks/Simple-Code-Analyzer-Configuration&file=GettingStarted.mlx)

# Simple Code Analzyer Configuration

This repository provides a simple Code Analyzer configuration example that increases the strictness of the Code Analyzer in MATLAB®.

The Code Analyzer:
* checks your code for code violations and suggestions for improvement
* runs continuously as you type in the MATLAB Editor
* can be used interactively with the [Code Analyzer Report](https://www.mathworks.com/help/matlab/matlab_prog/matlab-code-analyzer-report.html)
* can be used programmatically with the [`codeIssues`](https://www.mathworks.com/help/matlab/ref/codeissues.html) function
<br/><br/><br/>


## How to use the simple Code Analyzer configuration
To get started with the Code Analyzer configuration:
* Copy the `codeAnalyzerConfiguration.json` file to the "`resources`" folder at the root of your codebase
  * Note: If the root of your codebase does not have a "`resources`" folder, you will need to create one
* Analyze your codebase for issues using:
  * Code Analyzer app (`codeAnalyzer`), or
  * `codeIssues` function
<br/><br/><br/>


## Trying out the simple Code Analyzer configuration in MATLAB Online™
* Click on the "Open in MATLAB Online" badge at the top of this README.md
  * This will automatically clone this repository to your MATLAB Online account and open the `GettingStarted.mlx` file
* Walk through the `GettingStarted.mlx` file
  * Analyze the codebase before applying the simple Code Analyzer configuration
  * Copy the `codeAnalyzerConfiguration.json` file to the "`resources`" folder
  * Execute `matlab.codeanalysis.refreshConfiguration` for the JSON file to take effect
  * Analyze the codebase again after applying the simple Code Analyzer configuration

Disclaimer:
* Code Analyzer app is not yet supported in MATLAB Online
* For now, please use the `codeIssues` function in MATLAB Online to see code analysis results using the Code Analyzer configuration
<br/><br/><br/>


## Details of the checks configured by this simple Code Analyzer configuration
The table below lists all of the Code Analyzer checks that are enabled or modified by this simple Code Analyzer configuration.

| Check ID     | Issue Being Identified           | Limit           | Severity                     | Reasoning                                                                                                                                                                                                                                                                 |
|--------------|----------------------------------|:---------------:|:----------------------------:|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DISALLOWEVAL | All uses of "eval" and "evalc"   |                 | Error                        | "eval" and "evalc" are inefficient, make code difficult to understand and maintain, are hard to debug, and can lead to security concerns if untrusted user code is passed to them.                                                                                       |
| FCNLL        | Very long functions              | 2000 lines      | Error                        | Long functions make code more difficult to understand and maintain. It is helpful to refactor long functions into several smaller functions that are called by one main function.                                                                                         |
| LLMNC        | Very long lines                  | 1000 characters | Error                        | Long lines make code more difficult to understand and maintain. It is helpful to break long lines into multiple simpler statements, or into a single statement split across several shorter lines.                                                                        |
| MNCSN        | Deeply nested control statements | 10 levels       | Error                        | Deeply nested control statements make code difficult to understand and maintain.                                                                                                                                                                                          |
| FCNIL        | Too many input arguments         | 10 arguments    | Warning                      | Too many input arguments make functions difficult to understand and maintain. In these cases, it can be beneficial to create several simpler functions to accomplish all of the tasks of the original more complicated function.                                          |
| FCNOL        | Too many output arguments        | 10 arguments    | Warning                      | Too many output arguments make functions difficult to understand and maintain. In these cases, it can be beneficial to return a single output or a few outputs containing multiple pieces of data (such a struct/table/object containing multiple results).               |
| GVMIS        | Global variable usage            |                 | Raised from warning to error | Global variables are inefficient and make errors difficult to diagnose.                                                                                                                                                                                                   |
| EVLCS        | All uses of "eval" and "evalc"   |                 | Raised from warning to error | Built-in Code Analyzer check warning that "eval" and "evalc" are inefficient, make code difficult to understand and maintain, are hard to debug, and can lead to security concerns if untrusted user code is passed to them.                                             |
| NOANS        | Use of "ans" as a variable       |                 | Raised from warning to error | Using "ans" as a variable is not recommended as "ans" is frequently overwritten by MATLAB.                                                                                                                                                                                |
| CHAIN        | Chained logical operations       |                 | Raised from warning to error | Expressions like a > b > c are often a bug because they are interpreted as (a > b) > c, instead of as a comparison to ensure b is between a and c. To test a > b > c mathematically, use (a > b) && (b > c) for numeric scalars, or (a > b) & (b > c) for numeric arrays. |


Copyright 2023 The MathWorks, Inc.
