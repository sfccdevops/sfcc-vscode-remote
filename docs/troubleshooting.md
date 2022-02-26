![Logo](https://red-van-workshop.s3.us-east-1.amazonaws.com/logo.png "Logo")

:arrow_backward: **[BACK](../README.md)**

Troubleshooting
===

This document will contain a list of known issues, and how to solve them.

SSH Keys
---

VS Code Remove Developer Containers require that SSH Keys installed on the host computer be added to the `ssh-agent` so VS Code can access them from the Docker Virtual Machine.  When this goes wrong, you can see a few errors.

### GitHub

`git@github.com: Permission denied (publickey)`

If you are seeing this kind of error, you'll need to make sure you review [Sharing Git credentials with your container](https://code.visualstudio.com/docs/remote/containers#_sharing-git-credentials-with-your-container)

Docker
---

Having Docker issues? It happens to the best of us.  I find going nuclear is the best option sometimes.  This command will clean everything and allow you to do a clean install ( without it trying to use some random hidden cache ).

**WARNING:** If you are using docker for anything else, maybe don't use this and contact someone for help.

```bash
docker system prune -a
```

Live Share
---

The quickest way to tell if Live Share is broken ( sadly, it happens more than it should ), you can check your status bar in the footer of VS Code.  If you do not see `Live Share` in the status bar, then it broke.

### Here is how to fix the issue:

1. Press <kbd>F1</kbd> to open the Command Palette
2. Select `Live Share: Repair Installation` and let it run
