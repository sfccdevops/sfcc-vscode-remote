![Logo](https://red-van-workshop.s3.us-east-1.amazonaws.com/logo.png "Logo")

**[↤ Developer Overview](../README.md)**

Troubleshooting
===

This document will contain a list of known issues, and how to solve them.

Docker
---

Having Docker issues? It happens to the best of us.  I find going nuclear is the best option sometimes.  This command will clean everything and allow you to do a clean install ( without it trying to use some random hidden cache ).

**WARNING:** If you are using docker for anything else, maybe don't use this and contact someone for help.

```bash
docker system prune -a
```
