## TEAM 5458 Git Usage

Reference repo on the usage of Git on FRC Team 5458 systems. 

All commands should be run via Git Bash. 

***
### Configuring Global Git Settings
```bash
git config --global init.defaultBranch main
git config --global core.autocrlf true
git config --global core.safecrlf warn
git config --global user.name "FRC5458"
git config --global user.email FRC5458@wjusd.edu
```
### Creating SSH Key
```bash
# Create SSH folder if needed
mkdir -p ~/.ssh

# Navigate to SSH Folder
cd ~/.ssh

# Create SSH Key to Use with Project Repo Only. Don't Set Password on Key
ssh-keygen -t ed25519 -f {project_name} -C "{project_comment}"
```
### Creating SSH Config file
```bash
# Create SSH Config 
vim ~/.ssh/config

# Each project will need an entry in the SSH Config file

#===== ~/.ssh/config ==========
# Host github-{project_name} 
#   HostName ssh.github.com
#   Port 443
#   User git
#   IdentityFile ~/.ssh/{project_name}
#   IdentitiesOnly yes
#

# Set Required Permissons on Config
chmod 600 ~/.ssh/config
```
### Add Public Key to Repo
An Admin of our GitHub organization will have to complete this step. Currently, only mentors are admins. 

**Github Repo -> Settings -> Deploy keys -> Add Deploy key**

```bash
cat ~/.ssh/{project_name}.pub
```
### Add Public Keys of Github
```bash
ssh-keyscan github.com >> ~/.ssh/known_hosts
# Only Run from SSH Enabled Network
```
### Initalize Git for New Local Project
```bash
# Navigate to New Local Project Folder
cd {project_path}

# Initialize Git
git init

# Add Remote Repo
git remote add origin git@github-{project_name}:FRCTeam5458DigitalMinds/{repo_name}.git
```
### Stage and Push to GitHub
```bash
# Stage Changes 
git add --all

# Commit Changes
git commit -m '{commit comment}' 

# View Remote Name (Default should be 'origin')
git remote -v

# Push to Github
git push origin --all
```
### Clone Repo
```bash
# Clone Repo From Code Already in GitHub
git clone git@github-{project_name}:FRCTeam5458DigitalMinds/{repo_name}.git
```


