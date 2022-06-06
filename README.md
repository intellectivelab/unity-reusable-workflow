# unity-reusable-workflow
Holds Github workflows to be reused in other unity projects

# release_flow.yml
Supports following release types (_type_ input variable):

- Snapshot:
 Trigger same action as merge to a dev branch. Uses snapshot dependencies.
 Creates "snapshot-<timestamp>" tag.
 Does not create release.

- QA Release:          
  Numbered release with snapshot dependencies from dev branch.
  Creates github release with '''qarelease-<releaseversion>-<RC><increment>-<timestamp>''' tag.
  Applied only for dev branch
 
- Release:          
  Numbered release with use the latest versions of dependencies.
  Creates github release with '''wfrelease-<major.minor.increment>-<timestamp>''' tag.

- Patch Release
  Numbered release with use the latest minor versions of dependencies.
  Creates github release with '''wfrelease-<major.minor.increment>-<timestamp>''' tag.

# Note for implementors
Use secrets to hold any sensitive data - urls, usernames, passwords etc.  
