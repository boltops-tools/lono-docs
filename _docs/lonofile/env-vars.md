---
title: Env Vars
---

There is one notable env var that allows you to affect the `git clone` command that `lono bundle` calls.

    LB_GIT_CLONE_ARGS

This allows you to add extra arguments to the `git clone` command. IE:

    export LB_GIT_CLONE_ARGS='-c http.extraheader="AUTHORIZATION: Basic"'
    lono bundle
