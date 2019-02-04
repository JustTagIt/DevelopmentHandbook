# Version Bumps

## When to Bump
It is important to make sure we are continuously bumping the version of our applications. By versioning our application, we can track the current state, determine what features are available, and understand what has changed

Version bumps should happen __after__ a release branch is merged into master. Once that is done then master's version should be bumped.

## How To Bump The Version
The version of an application gets managed with changes done to the `VERSION` file located at the root of a project, a new [git tags](https://git-scm.com/book/en/v2/Git-Basics-Tagging), and a Bump Version commit message (All On Master).

### Automated Script
Luckily we have a script we can utilize to handle versioning for us. You can also run the [bump version script](/bump_version.sh) and it should handle it for you.

1. The script will look for a VERSIONS File, if it dne then it will create one from scratch
2. It will stage the VERSIONS file
3. If your application has a `package.json`, it will bump the version using `npm version [given version]`. This change will be staged ad well.
4. At this point the script will commit the changes with a version specific message.
5. Finally it will create a tag for you and push that immediately to github. You can go to the github repo and view the code according to that tag.

__First Time Running__

Script will version application as `0.1.0`
```
➜  adpnyc git:(master) ✗ ./bump_version.sh
! Could not find a VERSION file.
? Do you want to create a version file and start from scratch? [y]: y
? Now you can make adjustments to CHANGELOG.md. Then press enter to continue.

❯ Pushing new version to the origin...
Bumping version on package.json
{ 'gatsby-starter-semantic-ui': '0.1.0',
  npm: '5.6.0',
  ares: '1.10.1-DEV',
  cldr: '32.0',
  http_parser: '2.8.0',
  icu: '60.1',
  modules: '57',
  napi: '3',
  nghttp2: '1.32.0',
  node: '8.11.3',
  openssl: '1.0.2o',
  tz: '2017c',
  unicode: '10.0',
  uv: '1.19.1',
  v8: '6.2.414.54',
  zlib: '1.2.11' }
[master 7596de8] Add VERSION and CHANGELOG.md files, Bump version to v0.1.0.
 2 files changed, 40 insertions(+)
 create mode 100644 CHANGELOG.md
 create mode 100644 VERSION
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 1002 bytes | 1002.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:Bedrock02/adpnyc.git
 * [new tag]         v0.1.0 -> v0.1.0
❯ Finished.
```
__After First Time Running__

Script will version application as the input given
```
adpnyc git:(master) ✗ ./bump_version.sh
❯ Current version: 0.1.0
❯ Latest commit hash: c59b451
? Enter a version number [0.2.0]: 1.0.0
❯ Will set new version to be 1.0.0
....
....
```
### Post Script
After you have successfully bumped the version you must make sure that you `push` your changes to `origin master`. The script only pushes the tags up to github and stages/commits the changes done to VERSION, CHANGELOG.md, and package.json (if it applies).

Also, don't forget to merge master into develop so that develop can also have the version bumped. You can do this via the console, a pull request isn't needed.

```
git checkout develop
git merge master
git push origin develop
```
