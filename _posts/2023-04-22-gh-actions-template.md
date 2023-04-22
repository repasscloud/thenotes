---
title: gh-actions Template
author: danijeljw-rpc
date: 2023-04-22 00:00:00 +1000
categories: [git, GitHub]
tags: [cli, git, github]
math: true
mermaid: true 
image:
  path: https://github.githubassets.com/images/modules/open_graph/github-octocat.png
  alt: github Octocat
---

Template for all development branches:

> The default `GITHUB_TOKEN` value is `secrets.PAT`
{: .prompt-info }

```yaml
name: Development
on:
  push:
    branches: [ "dev" ]
  pull_request:
    branches: [ "dev" ]
permissions:
  contents: read
jobs:
  dev-build:
    runs-on: ubuntu-latest
    steps:
    - name: CHeckout
    - uses: actions/checkout@v3
    - name: Set up X
      uses: actions/setup-X@Y
      with:
        X-version: "X.Y.Z"
    - name: Install dependencies
      run: |
        # do something
  check-pr:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3
      - name: Get PR numbers
        run: |
          sudo apt-get -y install jq
          ticket_number=$(gh pr list --repo <user>/<repo> --json number | jq '.[].number')
          if [ -n "$ticket_number" ]; then
            echo "PR numbers exist: $ticket_number"
            gh pr close "$ticket_number" --repo <user>/<repo>
          else
            echo "No PR numbers exist"
            # Do nothing
          fi
        shell: bash
        env:
          GITHUB_TOKEN: ${{ secrets.PAT }}
  auto-pr:
    needs:
      - check-pr
      - dev-build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Create pull request
        run: gh pr create -B main -H dev --title 'Auto PR dev into main' --body 'Automatically created by gh-actions.'
        env:
          GITHUB_TOKEN: ${{ secrets.PAT }}
  auto-merge:
    needs: [ "auto-pr" ]
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: merge pull request
        run: gh pr merge --merge --admin
        env:
          GITHUB_TOKEN: ${{ secrets.PAT }}
```