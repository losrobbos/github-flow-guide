# Branching workflow recommendation (Cheatsheet)

## Develop a feature

`git checkout main` // always start your branch from the latest master

`git pull` // make sure you have the lastest version of master

`git checkout -b yourMassiveNewFeature` // create a new branch for your feature

// do your stuff on the branch

`git status` // make sure you do not accidentally add something that you do not wanted to add 

`git add .` // or git add <dirname / filename> for every dir / file to have full control on adding

`git commit -m "Finished feature, yeah"`

`git push` // still on your branch


## Bringing your stuff into main branch

Go to GitHub

Go to the uploaded branch and hit "Create pull request" for merging into master

Perform the merge on GitHub

Now master is updated

Go into your terminal and update your local master, so it has the remote changes:

`git checkout main`

`git pull`

Finished!


## Continue the flow

For the NEXT feature you simply repeat the cycle.

IMPORTANT: ALWAYS ALWAYS ALWAAAAAAAAAAAAAAAAAAAAYS create your branch based on main! 

Never fork off branches from other branches (=> hell guarantee).

So always:

`git checkout -b yourNewBranch main`

Enjoy the merge!
