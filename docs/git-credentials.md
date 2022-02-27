![Logo](https://red-van-workshop.s3.us-east-1.amazonaws.com/logo.png "Logo")

:arrow_backward: **[BACK](./prerequisites.md#prerequisites)**

Git Credentials
===

> Before you get too far into things, let's get your local developer machine ready to work with containers:

**NOTE:** These instructions are just the most common requirements that should meed _most_ developers needs, and are likely _already_ setup on your machine. See [Sharing Git credentials with your container](https://code.visualstudio.com/docs/remote/containers#_sharing-git-credentials-with-your-container) for more specific setup requirements.  If you have not already created SSH Keys, follow the instructions on [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) or [BitBucket](https://support.atlassian.com/bitbucket-cloud/docs/set-up-an-ssh-key/).

**OS Specific Instructions:**

* [All Platforms](#all-platforms)
* [macOS](#macos)
* [Windows](#windows)
* [Linux](#linux)

All Platforms
---

In order to have consistent commit authors, you'll want to set some global info about yourself. If you do not set your username and email, it's possible you you will have different git commit authors for your Local machine and your Container, even though they are using the same SSH Keys.

You can check what your current Global Git Config settings are by running the following:

```bash
git config --global user.name
git config --global user.email
git config --global pull.rebase
```

If either of these failed to return results, you can set them by running the following:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@address"
# Container will ask you to specify this before you can use `git pull`
# hint: git config pull.rebase false  # merge (the default strategy)
# hint: git config pull.rebase true   # rebase
# hint: git config pull.ff only       # fast-forward only
git config --global pull.rebase false
```

IMPORTANT: You will want to perform this task with the exact same values on BOTH your Local machine, and the Developer Container.

macOS
---

For macOS you just need to make sure your SSH Keys are added to your SSH Agent.

**STEP 1. Adding SSH Keys to SSH Agent:**

```bash
eval "$(ssh-agent -s)"

# Use this line if you have an `id_rsa` SSH Key
ssh-add ~/.ssh/id_rsa

# Use this line if you have an `id_ed25519` SSH Key
ssh-add ~/.ssh/id_ed25519
```

**STEP 2. Signing Git Commits:**

In order to Sign Commit Messages, you will need to install [GPG Suite](https://gpgtools.org/).

Windows
---

Regardless if you are using PowerShell or Windows Subsystem for Linux (WSL), you will still need to use the instructions for PowerShell.  Well cover WSL specific instructions as well.

NOTE: If you do not already use [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701), it makes switching back and forth between PowerShell & WSL terminal windows.

**STEP 1. PowerShell Setup:**

Open **PowerShell** as an **Administrator** and run:

```bash
Set-Service ssh-agent -StartupType Automatic
Start-Service ssh-agent
Get-Service ssh-agent
```

**STEP 2. WSL Setup:**

If you are using WSL, you will need to take these additional steps inside a WSL terminal window:

```bash
sudo apt install socat
eval "$(ssh-agent -s)"
```

Then you will need to add these lines to either your `~/.bash_profile` or `~/.zprofile` (for Zsh) so it starts on login:

```bash
if [ -z "$SSH_AUTH_SOCK" ]; then
   # Check for a currently running instance of the agent
   RUNNING_AGENT="`ps -ax | grep 'ssh-agent -s' | grep -v grep | wc -l | tr -d '[:space:]'`"
   if [ "$RUNNING_AGENT" = "0" ]; then
        # Launch a new instance of the agent
        ssh-agent -s &> $HOME/.ssh/ssh-agent
   fi
   eval `cat $HOME/.ssh/ssh-agent`
fi
```

**STEP 3. Adding SSH Keys to SSH Agent:**

Now you can add your SSH Key to your SSH Agent:

```bash
# Use this line if you have an `id_rsa` SSH Key
ssh-add ~/.ssh/id_rsa

# Use this line if you have an `id_ed25519` SSH Key
ssh-add ~/.ssh/id_ed25519
```

**STEP 4. Signing Git Commits:**

In order to Sign Commit Messages, you will need to install [Gpg4win](https://www.gpg4win.org/).

If you are using WSL, you will also want to run the following command inside a WSL terminal window.

```bash
sudo apt install gpg
mkdir -p ~/.gnupg
touch ~/.gnupg/gpg-agent.conf
echo pinentry-program /mnt/c/Program\ Files\ \(x86\)/Gpg4win/bin/pinentry.exe > ~/.gnupg/gpg-agent.conf
```

Linux
---

For Linux you just need to make sure your SSH Keys are added to your SSH Agent.

**STEP 1. Adding SSH Keys to SSH Agent:**

```bash
eval "$(ssh-agent -s)"

# Use this line if you have an `id_rsa` SSH Key
ssh-add ~/.ssh/id_rsa

# Use this line if you have an `id_ed25519` SSH Key
ssh-add ~/.ssh/id_ed25519
```

Then you will need to add these lines to either your `~/.bash_profile` or `~/.zprofile` (for Zsh) so it starts on login:

```bash
if [ -z "$SSH_AUTH_SOCK" ]; then
   # Check for a currently running instance of the agent
   RUNNING_AGENT="`ps -ax | grep 'ssh-agent -s' | grep -v grep | wc -l | tr -d '[:space:]'`"
   if [ "$RUNNING_AGENT" = "0" ]; then
        # Launch a new instance of the agent
        ssh-agent -s &> $HOME/.ssh/ssh-agent
   fi
   eval `cat $HOME/.ssh/ssh-agent`
fi
```

**STEP 2. Signing Git Commits:**

In order to Sign Commit Messages, you will need to install the `gnupg2` package:

```bash
sudo apt-get update && sudo apt-get install gnupg2 -y
```

Up Next
---

[![Up Next](https://img.shields.io/badge/Next-Usage_Instructions-blue.svg?style=for-the-badge&logo=github&logoColor=ffffff&logoWidth=16)](./usage-instructions.md#usage-instructions)
