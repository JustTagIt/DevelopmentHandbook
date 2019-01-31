# Branches & Pull Requests

This readme will cover the following:

- Branches
- Pull Requests


### Branches

During the development process developers should be checking-out new branches off of the `develop` branch. Branches should follow the following pattern:

`<category>/<teamwork-id>-<some-name-here>`

__Category__: Indicates what level of priority or stage the changes are for.

__TeamWork ID__: The teamwork id is a reference to task the code is related to.

```
git checkout develop
git pull origin develop

git checkout -b bug/2345857-broken-link
---------------------------------------------------
git checkout -b feature/2345853-form-button
---------------------------------------------------
git checkout -b UAT/2342235-missing-functionality
---------------------------------------------------
git checkout -b hotfix/2342443-typo-breaking-code
```

### Pull Requests
Pull Request should be as clear as possible. The description on a pull request on Github should include the following:

See [pr-template](www.github.com/somelinkhere)

##### 1. Summary
Context or a summary of the changes introduced. This includes anything removed, added on, or modified.

##### 2. TeamWork Reference
Providing a link to the related Teamwork task provides the reviewer or anyone looking at the code the opportunity to seek more context and information regarding the task.

##### 3. Steps To Reproduce (The Solution)
The code in the pull request should have fixed an existing issue or introduced something new to the codebase.

It is important to lay out a step by step way to reproduce the solution. The last step(s) should be what is expected. With these steps anyone can checkout the branch and follow the steps to test out the code.

##### 4. Checklist
The checklist provided is intended to help the developer review their own code and assure that new code can be merged in the best state possible. Pull requests will not be blocked if things are not checked off, this is to benefit the team and the individual.


### Code Reviews & Release Reviews

##### Feature Pull Request
These pull requests have code changes that reflect work on a single teamwork task.

Feature code reviews can be done by any team member. Developers should never merge their own pull request without an approval from another developer.

##### Release Reviews
Release pull requests should be reviewed by a Dom & Tom Technical Leader. A release pull request should include all changes introduced by approved feature pull requests.