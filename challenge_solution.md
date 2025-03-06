#Git
Step 1- Download the git from given link: 
        https://git-scm.com/downloads
Step 2- Verify installation by running  following command
        git --version
#Github
#SSH Authentication

#1 Created 2 different accounts on Github
#2 Generate a New SSH Key for the Second Account
 ssh-keygen -t ed25519 -C "nikhilkamode77@gmail.com"

#3 Add the New SSH Key to the SSH Agent
Start the SSH agent:
 eval "$(ssh-agent -s)"

#4 Add the new key:
ssh-add ~/.ssh/id_ed25519_github_second

#5Add the SSH Key to GitHub
1)Copy the SSH key to your clipboard.
  cat ~/.ssh/id_ed25519_github_second.pub
2)Go to GitHub → Settings → SSH and GPG keys → New SSH Key
Paste the key and save it.

#6 Configure SSH for Multiple Accounts
Edit (or create) the SSH config file:
nano ~/.ssh/config

Add the following:
# First GitHub Account
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519

# Second GitHub Account
Host github-second
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github_second

#6 Test SSH Connection
Run:
ssh -T git@github.com
ssh -T git@github-second

You should get a message like:
Hi your-username! You've successfully authenticated.

#7 Use Different SSH Keys in Git
To use the second GitHub account in a specific repository:
git config user.email "nikhilkamode77@gmail.com"
git config user.name "nikkh-dev"

#8 When cloning a repository for the second account, use:
git clone git@github-second:nikkh-dev/repository.git


#Gitlab

# Step 1: Generate an SSH Key
Run the following command in Git Bash or PowerShell:

ssh-keygen -t rsa -b 4096 -C "kamodenikhil@gmail.com"

# Press **Enter** to save the key in the default location (`~/.ssh/id_rsa`).
-# When prompted, you can set a passphrase (or press Enter to skip).


# Step 2: Start the SSH Agent
Run:
eval $(ssh-agent -s)
ssh-add ~/.ssh/id_rsa

# Step 3: Copy Your SSH Key
Run:

cat ~/.ssh/id_rsa.pub

or #in PowerShell:

Get-Content C:\Users\Tech-Nikh\.ssh\id_rsa.pub

Copy the output.

# Step 4: Add SSH Key to GitLab
1. Go to GitLab → Click on your profile picture → Settings.
2. In the left sidebar, click SSH Keys.
3. Paste your copied SSH key into the Key field.
4. Click Add key.

# Step 5: Test the SSH Connection
Run:

ssh -T git@gitlab.com

#If successful, you should see a message like:

Welcome to GitLab, @Tech-Nikh!



