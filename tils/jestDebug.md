---
title: Is jest not printing the entire DOM on test failure? Increase DEBUG_PRINT_LIMIT
date: 2020-09-15
tags:
  - jest
  - javascript
  - testing
  - testing-library
layout: layouts/post.njk
---

DEBUG_PRINT_LIMIT is an environment variable used by [testing-library](https://testing-library.com/docs/dom-testing-library/api-helpers#debugging) to limit the maximum length of DOM content that's printed to the terminal when a test fails (It's not used by jest, it's just testing-library). This is useful because the DOM can be pretty large, and you don't always want to see the entire DOM. But, if you find that you do need to see more of the DOM, you can increase the DEBUG_PRINT_LIMIT from the default of 7000.

```shell
DEBUG_PRINT_LIMIT=10000 npm test
```
