---
title: Stubborn DNS Cache? Use "Empty Cache and Hard Reload"
date: 2020-07-03
tags:
  - cache
  - browser
  - chrome
layout: layouts/post.njk
---

A lot of us have learned by now the <kbd>⌘</kbd>+<kbd>⇧</kbd>+<kbd>R</kbd> or <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>R</kbd> shortcut to hard reload the page, so that assets cached by the browser are fetched from the internet again. But what if your cache is being particularly stubborn, for example a local DNS cache is still serving an old redirect, and you just want to check if the new site works, without clearing all the caches in your system and network?

That's where the "Empty Cache and Hard Reload" in Chrome comes in, so you can clear the cache just for your current URL. You can access the option in three easy steps:

1. Open the chrome developer tools

   (<kbd>⌥</kbd>+<kbd>⇧</kbd>+<kbd>I</kbd> or View → Developer → Developer Tools or Right click → Inspect)

2. Right click the refresh icon
3. Click "Empty Cache and Hard Reload" in the menu that appears

![Refresh menu showing "Empty Cache and Hard Reload"](/img/hardReload.png)

That's it! This (usually) clears all caches, so both theassets cache and the local DNS cache would be emptied, and you don't have to wait for any TTLs to expire!
