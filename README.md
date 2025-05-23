# Test Renovate

The project is just an experiment to test RenovateBot via workflow.

## Problem

By default, we can just install RenovateBot App to the repository, add a bare minimum renovate.json config file, and it should work by doing:

- Create a new PR
- Updates package.json with updated dependency version
- Updates package-lock.json accordingly

However, updating the lock file only worked for npm (default). If you use non-npm package managers like pnpm, renovate bot doesn't update the `pnpm-lock.yaml` file in the PR (it only updates `package.json` file).

## Solution

We'll need to use [postUpgradeTasks](https://docs.renovatebot.com/configuration-options/#postupgradetasks), but it is only available for self-hosted instances. This means we have to manually run it in our Github workflow.

## Memo

(unverified) Dependency Dashboard ("dependencyDashboard": true) only works with RenovateBot Github App. Using the CI way means that the dashboard won't work.

