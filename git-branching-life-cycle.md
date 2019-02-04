# Git Branching Lifecycle
Keeping branches and commits organizes sets up a team for success. With a good git model, we can make development faster and safe at the same time.

This write up has been inspired by the following [article](https://nvie.com/posts/a-successful-git-branching-model/)

### Main Branches
- master
- develop

`Master` and `Develop` are the two main branches that will hold the source of truth.

The `HEAD` of `master` should always represent a production ready state. The `HEAD` of `develop` should represent the latest finished features that will be pushed to master via the next release.

### Supporting Branches
- Feature branches
- Release branches
- Hotfix branches

These branches are short lived branches used to work on new features, fix bugs, set up release-ready code, and handle hotfixes.

#### Feature Branches
Feature branches are branched off develop and represents a new feature. After the code changes are approved by a developer it is then merged into develop.

#### Release Branches
Release branches are branched off develop and represents a potential ready to go version of the application.

##### 1. Create The Release Branch
`git checkout -b release-1.2 develop`

##### 2. QA The Release Branch
Before releasing new code, QA should be making sure that all tickets in the release should be QA'd on the staging environment that holds the release code.

__[ NOTE: The Following Steps (3-5) Should be done by the D&T tech lead or "code guardian"]__

##### 3. Version Bump
After everything checks out, the version should be bumped.
```
./bump-version.sh 1.2 (can be done manually too)
$ git commit -a -m "Bumped version number to 1.2"
```

##### 4. Merge Release Into Master
```
git checkout master
git merge --no-ff release-1.2
```

##### 5. Tag New Version
```
git tag -a 1.2
```

#### Hotfix Branches
Hotfix branches are branched off from master. After a hotfix is merged back into master and production is stable, then master is merged back into develop to bring any hotfix changes into develop.

##### 1. Create The Hotfix Branch
Create hotfix branch off current master.
```
git checkout master
git checkout -b hotfix-1.2.1
```
##### 2. Commit Changes
```
git commit -m "Hotfix change"
```
##### 3. Version Bump
After everything checks out, the version should be bumped using a [script](/bump_version.sh) or done manually.
```
./bump-version.sh 1.2.1 (can be done manually too)
git commit -a -m "Bumped version number to 1.2.1"
```
##### 4. Merge Release Into Master
```
git checkout master
git merge --no-ff release-1.2.1
```

##### 5. Merge Master into Develop
```
git checkout develop
git merge master
```
