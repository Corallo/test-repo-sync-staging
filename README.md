# test-repo-sync

This is an example of how the automatic sync should work
If something is pushed in master a github action in the public repo creates new branch in the staging repo with the changes, an human has to start the PR, approve and merge.
The same will happen in the opposite direction.

## Sync loop
There shouldn't be sync loop between the staging and the public, as in case a merge is done without changes, the git merge commands returns an error and the push is skipped.

## Possible improvements
- Automatically start PR in both direction
- Consider if the sync needs to pass in a branch in both directions, instead of going directly into main
- Use a github "bot-account" token instead of a developer token.

## Notes
To avoid branch collision if more than one sync happens the same day, it is reccomanded to enable the "Automatic delete branch on merge" setting.
It is also needed to put an authorized token into the repository secrets.


## Why syncing to main would be better
Pushing directly to main will spare a lot of problems in case we have multiple sync per day,
besides in the current state for every change in the code we have two Pull request and review, one that goes from the staging new branch to the staging main, and then one that goes from the synced-branch in the public repo, to the public main.
The second is reduntant, could be skipped making the automatation more smooth.

