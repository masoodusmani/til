---
title: Docker caches based on COPY'd files
date: 2020-05-12
tags:
  - docker
  - cache
layout: layouts/post.njk
---

When running a Dockerfile, docker uses a cached step if all the COPY'd files have the same checksums, otherwise the cache is busted. CMD and RUN steps always use the cached version, unless any previous step busted the cache.
