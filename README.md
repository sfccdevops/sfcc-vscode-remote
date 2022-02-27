![Logo](https://red-van-workshop.s3.us-east-1.amazonaws.com/logo.png "Logo")

SFCC › VS Code › Remote Development Container
===

> VS Code Remote Development Container for SFCC Teams as [Recommended by Salesforce](https://developer.salesforce.com/tools/vscode/en/user-guide/remote-development).

**Created _for_ SFCC Developers _by_ SFCC Developers:**

- [X] Cross-Platform Virtual Environment for SFCC Developers
- [X] Customized VS Code with Your Teams Settings & Extensions
- [X] Pair Programming and Audio Chat for Entire Team
- [X] Run Custom DevOps Scripts directly in VS Code
- [X] Customizable Environmental Dotfiles

[![Get Started](https://img.shields.io/badge/Let's_Get_Started-blue.svg?style=for-the-badge&logo=github&logoColor=ffffff&logoWidth=16)](#getting-started)

**Not your first time here?**

[![Get Started](https://img.shields.io/badge/Download-gray.svg?style=for-the-badge&logo=github&logoColor=ffffff&logoWidth=16)](https://github.com/redvanworkshop/sfcc-vscode-remote/archive/refs/heads/develop.zip)

Demo Video
---

> Want a quick walkthough on how to use our Remote Container?

[![Play Demo Video](https://via.placeholder.com/480x270?text=Demo+Video)](# "Play Demo Video")

Getting Started
---

### Organization Setup

1. [Repository Setup](docs/repository-setup.md#repository-setup)

### Developer Setup

1. [Prerequisites](docs/prerequisites.md#prerequisites)
2. [Git Credentials](docs/git-credentials.md#git-credentials)
3. [Usage Instructions](docs/usage-instructions.md#usage-instructions)

> If you got stuck along the way, checkout our Troubleshooting document.

[![Troubleshooting](https://img.shields.io/badge/Need_help-Troubleshooting-orange.svg?style=for-the-badge&logo=github&logoColor=ffffff&logoWidth=16)](docs/troubleshooting.md#troubleshooting)

Benefits
---

<details><summary>Remote Container is Version Controlled</summary>
<br>

> **This means you can Version Control your teams Dev Environment.**
>
> Need to work on updating to a new version of Node? Need to update your Team's Linter or Code Formatting Rules? Maybe you want to try out a new VS Code Extension with your entire Team? No problem! Make a branch, change some settings in the container config, and VS Code will prompt anyone switching to that branch to rebuild their Dev Environment. When they switch back, their environment can as well.

</details>
<details><summary>Cross-Platform Virtual Environment</summary>
<br>

> **Not everyone works on macOS laptops!**
>
> With our setup, you will be able to launch VS Code with a Virtual Environment to allow your Windows, macOS, and Linux Coders to access a consistent Dev Environment built explicitly for SFCC Projects.  There are no weird issues with cross-platform dependencies, managing different versions of Node, etc.

</details>
<details><summary>Pair Programming for Entire Team</summary>
<br>

> **Pair Programming and Group Chat Already Installed.**
>
> Getting VS Code's Live Share & Live Share Audio to play well on one machine can be a challenge on its own, let alone your entire dev team.  With our Remote Container, we have everything set up for you.  We've also built-in better security than what is enabled by default.  So team members don't have to worry about anonymous guests joining a pair programming session.

</details>
<details><summary>Run Custom DevOps Scripts</summary>
<br>

> **Executing Commands on your Dev Environment from VS Code.**
>
> There is always someone on your Dev Team creating handy DevOps tools to automate specific tasks.  Sometimes you want to remove all the node_modules folders and start life over.  We get it, and that's why we've baked in support for collecting your DevOps scripts and making them accessible via VS Code right from the Task Bar.

</details>
<details><summary>Easy to Customize for Your Team</summary>
<br>

> **Not every Dev Team works the same way, and that's OK.**
>
> We've already sorted out the basics to ensure everything you need to do SFCC Dev Work is supported, but we realize every team is different. We've documented everything you need to know to customize which VS Code Extensions are best for your team and how to configure Linters and Code Formatters for your teams' needs.

</details>

Frequently Asked Questions
---

<details><summary>What's the Difference?</summary>
<br>

> **That's a Great Question, and an important one to consider for your Team.**
>
> The first significant change is that VS Code will spin up your Dev Environment in a Virtual Machine. This method means each Dev Environment will be using the same OS ( Linux Debian 11 ) with identical versions of Node, NPM, etc. VS Code launches from within these containers ( not your local OS's version of VS Code ). VS Code Extensions or custom settings you have on your local instance of VS Code will not be installed in the Container ( unless you configured them to be in the Dev Container Settings ).

</details>
<details><summary>What about my Custom Theme?</summary>
<br>

> **Each Developer has their style, and there's no need to change that.**
>
> VS Code put a lot of thought into this regarding Virtual Dev Environments. When you spin up a Remote Development Container, VS Code will automatically pull in your Visual Settings. So your custom theme, fonts, icons, etc., should be just the way you had them in your native VS Code instance. The only exception is if your Remote Developer Container Settings set an override for this. That might be handy for teams that want a consistent VS Code theme with custom colors and fonts. If you wanted to do that with these containers, you 100% could.

</details>
<details><summary>Will my SSH Keys Still Work?</summary>
<br>

> **Remote Containers will be hard to use on a team if they don't.**
>
> Yes, VS Code already thought of this and has added support for using your development machines SSH Keys within your Remote Development Container. You will be able to use your IDE's terminal window to connect to GitHub or BitBucket without any issues.

</details>
<details><summary>Will Signed Commit Messages Work?</summary>
<br>

> **Some Dev Teams will need to make sure Git Commits can be signed.**
>
> Yes, we have added support for this into the Docker container. This setting is not enabled by default for VS Code Remote Containers, as you would need to add Operating System support for the Virtual Machine. So we took care of that in this project.

</details>
<details><summary>Can we Configure the Container?</summary>
<br>

> **Not every Dev Team will want the same thing.**
>
> Yes, anything that you can typically configure in VS Code can also be configured for your containers. Some teams make `.code-workspace` files for this very reason. However, that method does not solve the Operating System issues addressed using Remote Developer Containers.

</details>

About Us
---

[Red Van Workshop](https://redvanworkshop.com/) works with Digital Commerce Retailers who want to get things done.  Our developers enjoy publishing [Open Source](https://github.com/redvanworkshop) solutions to everyday problems.
