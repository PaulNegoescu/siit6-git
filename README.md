# Git workflow cheatsheet

## After installing git, only FIRST TIME EVER, configure git
- `git config --global user.name "Paul Negoescu"` - configure the username for future commits in all repos
- `git config --global user.email paul.negoescu@scoalainformala.ro` - Same but for email
- `git config --global core.autocrlf false` - checkout "as-is" commit "as-is"

## Start a project from scratch only locally

### Only the FIRST TIME ON EACH PROJECT
- `git init` - Initialize an empty repo

### For EVERY TIME we want to record changes as a new version
- `git add <path>` - Track files
- `git commit -m "<message>"` - Actually record the change (create a version)

### Other useful commands
- `git status` - See the current status

## Move our local project online to be used by others

### Only the FIRST TIME ON EACH PROJECT
- `git remote add <remote-name(usually-origin)> <remote-url(usually-grabbed-from-github)>` - hook up a remote repository to use as a central repository
- `git push -u <remote-name> <branch-name>` - send the branch online and set up the local branch to track the remote branch

### On EACH subsequent update that we want to publish
- `git pull` - grab all changes from remote first
- `git push` - send all content of the current branch to the remote tracking branch

## Start a project from an existing one on a remote like github

### Only the FIRST TIME
- `git clone <remote-url> [<path-to-clone-to>]` - copy entire repo locally

### EVERY TIME we want to record changes (AS OFTEN AS POSSIBLE)
- `git add <path>`
- `git commit -m <path>`

### EVERY TIME we want to publish local changes (AT LEAST ONCE A DAY)
- `git pull`
- `git push`

## Git branch workflow

### Common Branch Names
- `master` - Production branch (only commits that make it live)
- `develop` - Development branch (used by everyone)
    - `feature/<feature-name>` - Personal development branch (used by team developing a certain feature)

### Workflow

#### Start a new feature
Starting from develop
- `git switch -c feature/<feature-name>` - create a new branch and switch to it
- `git push -u <remote-name> feature/<feature-name>`

#### Work on it (as many times as necessary)
- `git add`
- `git commit`

#### At least once a day
- `git switch develop`
- `git pull`
- `git switch feature/<feature-name>`
- `git merge develop`
- test that the code still works
- `git push`

#### When we want to merge our changes into develop
- repeat the steps above for once a day
- `git switch develop`
- `git merge feature/<feature-name>`
- `git push`
