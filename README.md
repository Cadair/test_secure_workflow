# How authorise a security sensitive workflow on a public repo

Consider the following situation: You have a self-hosted GitHub runner which
you want to run all your public repos' PRs against, but you have listened to
the [security warning](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners#self-hosted-runner-security)
and don't want to automatically run all of this.

This repo attempts to achieve the following:

* On push or label add run a workflow which triggers on `pull_request_target`.
* If the PR has a given label then exit with success.
* If it dosen't exit with fail.
* A second workflow which calls out to your self-hosted runner is triggered on
the `workflow_run` of the previous workflow.
