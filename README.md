# unity-reusable-workflow
Holds Github workflows to be reused in other unity projects

# release_flow.yml
Supports following release types (_type_ input variable):

- Snapshot:
 Trigger same action as merge to a dev branch. Uses snapshot dependencies.

 Creates "snapshot-<timestamp>" tag. 

 Does not create release. 

 Applied only for dev branch.

- QA Release:          
  Numbered release with snapshot dependencies from dev branch.

  Creates github release with '''qarelease-<NextReleaseVersion>-<RC><increment>-<timestamp>''' tag.

  Applied only for dev branch
 
- Release:          
  Numbered release with use the latest versions of dependencies.
  
  Creates github release with '''wfrelease-<major.minor.increment>-<timestamp>''' tag. 
  
  Increments '''minor''' number by one. Set all dependencies for unity artifacts to latest released version.
  
  Push pom changes to git.

- Patch Release
  Numbered release with use the latest minor versions of dependencies.

  Creates github release with '''wfrelease-<major.minor.increment>-<timestamp>''' tag.

## initial tags
To start working with flow one need to define initial wfrelease tag:
```
wfrelease-<major.minor.increment>-<timestamp>
```
Where <timestamp> has date format like below:
```2022-06-06T14_59_23Z```

Manually push initial tag:
```
TS=$(TZ=GMT date +"%Y-%m-%dT%H_%M_%SZ")
git tag "wfrelease-${INITAL_VERSION}-${TS}"
git push --tags
```

# Note for implementors
Use secrets to hold any sensitive data - urls, usernames, passwords etc.  
