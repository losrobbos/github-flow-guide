## Branching workflow

Develop features in branches - with the GitHub Flow. A typical workflow for companies.

### Develop a feature

We develop our features in branches.

This way we can make sure, our work is isolated from the work of others. So we actually do not change the main project right away when we do changes.

This way all our code is in a "safe place" so to say, on a "sideline" of the project.

#### Pull Requests, Merging & Merge Conflicts

Once we finish our branch, we commit our changes, push the branch upwards and submit a so called "Pull Request" on GitHub. 

GitHub checks for uns then automatically if that branch could be integrated into the "mainline" of our project (=> the "main" branch - earlier called "master" branch)

In case GitHub detects NO conflicts with the existing project code, it will allow us to merge our feature directly into the main branch. And then the feature became part of the project code. 

In case GitHub detects conflicts, it will NOT allow the automatic merging of the branch. For good reasons. It prevents accidental overwriting of others peoples work this way.

The typical scenarios where this happens: Two people have made changes on the same files - at approximately the same lines! Git is smart and can often detect if you made changes at different parts of a file. Then it will smartly merge these file changes together and there will not be a conflict. 

But if you did changes at the same code block(s), if will have a conflict. It doesn't know which change of which person to choose... 

In that case you have to resolve the conflicts manually. I suggest you use the online editor of GitHub in case you are unused to resolve conflicts from the terminal. GitHub supports solving merge conflicts actually quite nicely (see instructions in section "Bring branches together" below)

When people do NOT do changes on the same files, by splitting their work thoughtfully, conflicts typically rarely happen. So it is a good practice to organize our work in a way, that we touch same files rarely (but sometimes it can hardly be avoided, e.g. if all team members include their new components into App.js)

#### Branch creation

Okay. Let's start by creating a branch for our new feature.

First we make sure, we start off with our branch from the LATEST stable version of our project. Which always should be found in the master branch.

```
git checkout main // always start your branch from the latest main
git pull // make sure you have the latest remote version of main
git checkout -b <yourMassiveNewFeature> main // create a new branch for your feature (replace <yourMassiveNewFeature> with your feature name)
// now code your stuff on the branch in vscode
```

#### Frequent commits

Once you're done with a part of your feature and tested if everything works, you can commit the changes.

```
git status // make sure you do not accidentally add something that you do not wanted to add :leichtes_lächeln:
git add . // or git add <dirname / filename> for every dir / file to have full control on adding
git commit -m "I did this and that here, yeah"
```

#### Finishing the branch

Once your done, once more add and commit everything. `git status` command should show you no files, neither red or green.

It is now recommended that you import the latest changes from your colleagues (so the main branch) in your branch to see, if your branch works well together with the work of the others or if it produces any conflicts.

It is adviced to do this in a team meeting or minimum in a pair (two developers of the team).

```
git checkout main // switch over to main branch
git pull // grab latest changes from main branch
git checkout <yourBranch> // change over to your branch (replace <yourBranch> with the name of your branch)
git merge main // merge the latest changes of main into your branch
```

In case there are any conflicts with code from your colleagues, git will tell you right away.

You can see the conflicting files when running `git status`. Usually they will be listed in red as "unmerged paths"

Open the listed files in VsCode, fix the code conflicts, ideally together as a team or pair.

Once all conflicts are solved, try to start the app and see if everything still works. 

Now add and commit the changes.

Now your branch should be ready to get pushed into GitHub and get reviewed and merged there.

#### Branch pushing

Once you're done with your branch and tested if everything works, also together with the latest changes in main branch, you can bring it online

```
git branch // make sure you are on your own branch
git push // copy the line that is created and execute it on the terminal
```

### Bring branches together

After we pushed our branch to the GitHub repository, we can now try to integrate it into our main project line.


- Go to the GitHub repo
  - it should tell you right away that your branch was pushed

- Click the button "Compare & Pull request" for your branch
  - alternative: go to the uploaded branch and hit "Create pull request"

- Check if it says "Able to merge" 
  - if so: Create pull request and...
  - merge right away!

- If you receive "Conflicts - cannot merge" 
  - create the pull request anyway!

- In the created Pull request you now should see a section "Conflicts" instead of "Merge"
  - Check the conflicts listed by clicking the "Resolve conflicts" button
  - You now get into an online editor to resolve the conflicting code blocks 
  - On the left side you see all conflicting files. Click through them one by one
  - Resolve the conflicts line by line in the online editor
  - At the end: Mark conflicted as resolved by clicking the "Resolved" button
  - Repeat the steps for every file
  - Once all files are done
    - Click the "Commit merge" button 
    - this will now update your pushed branch so it has no conflicts anymore with master

- In case you do not know which changes to take...
  - Make a comment in the pull request to start a discussion
  - Ideally: Resolve the issues in the team together, in case of any doubts
    - Or: Slack just the person that you are "conflicting with" (hopefully just in code ;-))

- All conflicts resolved
  - When you are done hit the button "Commit merge" in the editor
  - Your branch will get updated with the changes (the main branch is still untouched!)
  - Now you will get back to the pull request
  - You should be able to merge your "fixed" branch into the main branch
  - The green button "Merge" should appear
  - Perform the merge

DONE! Congratulations!


#### Update local main

Go into your terminal and update your local main, so it has the remote changes:
```
git checkout main
git pull
```

Finished.

#### Continue with next feature

NEXT feature: You repeat the cycle.

Important: 
- <b>Do not reuse your old branch</b>. Always create a new branch for every new feature or error fix.
- ALWAYS ALWAYS ALWAAAAAAAAAAAAAAAAAAAAYS create your branch based on main! Never fork off new features branches from other feature branches (=> ride to hell guarantee!).

So always:

`git checkout -b yourNewBranch main`

to create a new feature branch.

Happy Merging!
