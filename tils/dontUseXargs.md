---
title: Don't use xargs, use a for loop instead
date: 2020-05-13
tags:
  - shell
layout: layouts/post.njk
---

If you want to run a command on all the files in a folder, use this command:

```shell
for f in * ; do echo "$f" ; done
```

> (Replace `echo "$f"` with whatever command you want to run)

Don't use xargs, since its input format is not support by most common tools, and it doesn't support filenames with whitespaces or special characters
