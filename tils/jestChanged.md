---
title: Run tests on just your changed files with jest -o
date: 2020-09-15
tags:
  - jest
  - javascript
  - testing
layout: layouts/post.njk
---

You can specify the particular test file you want to run with a pattern, like `jest Layout`, which will run only tests whose file paths contain "Layout". But if you want a general command that will always run just the tests for files you've changed since your last commit, use `jest --onlyChanged`, or `jest -o` for short. Combined with watch, you can use this single command for all your regular development.

```shell
jest -o --watch
```

If you want to run tests for all files changed since a certain commit or branch (e.g. if you're working on a feature branch and want to test all the changed files in that branch), then use `jest --changedSince master`, where `master` is that branch you branched off from.
