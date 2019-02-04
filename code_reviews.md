# Code Reviews

## Who Can Review?
### Feature PR
For a feature pr, anyone can review the changes introduced. It is important that at least one other person reviews the code has has approved the changes introduced
### Release PR
For a release pr, the D&T technical lead should be the one reviewing the changes. This pull request should be a comparison of the `release branch` and `master` (with `master` as the base).


## CircleCI
CircleCI must be set up to make sure the application is able to build and deploy with the new changes introduced. The build process must incorporate running tests (if tests are available), running a linter on the codebase, building and deploying a docker image.

If any errors surface from the circleci build, then the author of the PR must fix the issues that have been found via the build.

## Setup & Context
If we follow the PR guide found in [Branches & Pull Requests](branches-and-pull-requests.md) the pull requests should have enough context and details to see what exactly has been changed and what ticket(s) are involved in the Pull Request.

## What To Review or Look For
### 1. Typos
At times typos or comments that may not make sense can sneak into the code. Lets make an effort to write clean and clear documentation.
### 2. Risky Code
Some risky code to keep an eye out are changes that introduce memory leaks, infinite loops, or even security vulnerabilities. Anything that will cause an application to run slow, not scalable or insecure should be pointed out.
### 3. Styling Issues
Although developers should be adhering to linting rules, if there are lint errors, these should be clean up. This should be done from day 1. Following the linting rules will keep the code clean, organized and legible.

### 3. Staying DRY (Don't Repeat Yourself)
Code that repeats across different areas of the application should be turned into a class or module so that it lives in one place.
