<img src="/uploads/logos/github-logo.png" align="right" />

# GitHub
##### How to use git efficiently as a team

GitHub is a cloud-based Git version control repository service.

![Github Icon](/uploads/icons/github-icon.png "Github Icon") [GitHub Repository](https://github.com/JoMedia)

<img src="/uploads/logos/github-flow-icon.png" align="right" />

## Development Process

Using the right flow when developing new features or fixing bugs is critical to keep merging and deployment issues at a minimum.

A standard process is to create a main branch (master) and optionally a dev branch (develop):
- **master** branch: The stable version of the code, usually the one currently in production. Is always ready for deployment.
- **develop** branch *(optional)*: The upcoming version of the code, currently under development. Code will be pushed to the master branch when stable and ready for deployment.

Developers should never work directly on the project repository. A fork of the master/develop branch should be made into the developer's personal account.

In most cases, developers should create a copy of the dev's master/develop branch for every feature or hotfix they are working on. This method allows developers to work on multiple features/fixes without affecting one or another. It's also easier to rollback in case of an issue discovered later in the flow.

#### Without dev branch
![Github Fork Pr Flow Simple](/uploads/diagrams/github-fork-pr-flow-simple.png "Github Fork Pr Flow Simple")

#### With dev branch
![Github Fork Pr Flow](/uploads/diagrams/github-fork-pr-flow.png "Github Fork Pr Flow")

## Semantic Commit Messages

Use the following format when writing commit messages:

```
feat: add hat wobble
^--^  ^------------^
|     |
|     +-> Summary in present tense.
|
+-------> Type: chore, docs, feat, fix, refactor, style, or test.
```

Examples:

- chore: add Oyster build script
- docs: explain hat wobble
- feat: add beta sequence
- fix: remove broken confirmation message
- refactor: share logic between 4d3d3d3 and flarhgunnstow
- style: convert tabs to spaces
- test: ensure Tayne retains clothing

## How-to
### Fork a branch
From the project repository, click on the **Fork** button to make a copy to your personnal account:

![Github Fork](/uploads/screenshots/github-fork.png "Github Fork")

### Create a Repository
From scratch -- Create a new local repository named **my_project**  
`$ git init my_project`

Download from an existing repository located at **my_url**  
`$ git clone my_url`

### Observe your Repository
List new or modified files not yet committed  
`$ git status`

Show the changes to files not yet staged  
`$ git diff`

Show the changes to staged files  
`$ git diff --cached`

Show all staged and unstaged file changes  
`$ git diff HEAD`

Show the changes between two commit ids  
`$ git diff commit1 commit2`

List the change dates and authors for a file  
`$ git blame [file]`

Show the file changes for a commit id and/or file  
`$ git show [commit]:[file]`

Show full change history  
`$ git log`

Show change history for file/directory including diffs  
`$ git log -p [file/directory]`

### Working with Branches
List all local branches  
`$ git branch`

List all branches, local and remote  
`$ git branch -av`

Switch to a branch, **my_branch**, and update working directory  
`$ git checkout my_branch`

Create a new branch called **new_branch**  
`$ git branch new_branch`

Delete the branch called **my_branch**  
`$ git branch -d my_branch`

Merge **branch_a** into **branch_b**  
`$ git checkout branch_b`
`$ git merge branch_a`

Tag the current commit **my_tag**  
`$ git tag my_tag`

### Making a Change
Stages the file, ready for commit  
`$ git add [file]`

Stage all changed files, ready for commit  
`$ git add .`

Commit all staged files to versioned history  
`$ git commit -m "commit message"`

Commit all your tracked files to versioned history  
`$ git commit -am "commit message"`

Unstages file, keeping the file changes  
`$ git reset [file]`

Revert everything to the last commit  
`$ git reset --hard`

### Synchronize
Get the latest changes from origin (no merge)  
`$ git fetch`

Fetch the latest changes from origin and merge  
`$ git pull`

Fetch the latest changes from origin and rebase  
`$ git pull --rebase`

Push local changes to the origin  
`$ git push`
