---
layout: post
title:  "Simple github action workflow of npm execution (basic workflow)"
date:   2020-01-06 14:50:00 +0900
categories: github npm git-action
---

As recently `github` announced some very useful feature, automatic workflow execution which can simplify project life cycle and forever running CI/CD.
That you can achieve with running `action` in project building process.

If you'd like to read more about actions, please read from here [github-action](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/about-github-actions).

Following example I've provided simple `npm` project workflow execution, such as `npm install` and `npm audit`. If any vulnerabilities found, it will update the dependencies (packages) and create pull request for merging to master branch and assign to some people.

{% highlight yaml %}
name: Example action flow 
# name of the action

on:
# trigger that workflow can start
pull_request:
    types: [opened, reopened]
push:
branches:
    - master

jobs:
# job execution
    build:
        runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1 
      - name: install dependencies
        run: npm install
      - name: audit fix
        run : npm audit fix
      - name: run test
        run: npm test 
      - name: Create PR for merging to master
        uses:  peter-evans/create-pull-request@v2
        with:
            token: ${{ secrets.GITHUB_TOKEN }}
            commit-message: this is auto generated PR by action
            title: Auto generated PR
            body: This is an auto-generated PR, please review it.
            branch: master
            branch-suffix: none
            reviewers: azaa13
{% endhighlight %}

**Action or workflow explanation:**

File type (workflow) or extension: `.yaml`, `.yml` in .github/workflows folder \\
File location: `.github/workflows` folder 

Writing flow is not so complicated, as you've seen, name, jobs, steps need to be defined and it should have proper indentation.

We can have different type of triggers (`on:`), such as push branch, open PR, even defined paths.
Please read more from here [config-workflow](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/configuring-a-workflow).

For `jobs:`, first we need to explicitly describe on which environment workflow can run. For that `runs-on: ubuntu-latest` this part says it'll run on ubuntu latest version.
Ubuntu specific version can be described as well such as `ubuntu-16.04`.

After having env to run, need to prepare our repo to fetch source files, such as package.json or lock files. For that  `- uses: actions/checkout@v1 ` this part simply organizing  repo related all execution such as fetch/clone, checkout branch. Note that here exec keyword is `-uses:` which means we're using this repo or packages to operate the execution.

Then we can run `npm commands` and after that any updates/changes found, we should create PR and someone should do review.
For that `uses:  peter-evans/create-pull-request@v2` this part is used, simply it's using repo or package to create PR, and we have to provide `GITHUB_TOKEN` and some entries if you'd like such as title, body, branch, reviewers etc.,

I'm providing some useful repos to look up similar cases below.
 - <https://github.com/actions>
 - <https://github.com/actions/starter-workflows>
