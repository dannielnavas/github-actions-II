# Triggers

- [ ] push
- [ ] pull_request
- [ ] issues
- [ ] issue_comment
- [ ] workflow_dispatch
- [ ] schedule

## Push

on:
    push:
        branches:
            - 'main'
            - 'releases/**'
        paths:
            - '**.js'

## pull_request

on:
    pull_request:
        types:
            - [opened, labeled]
        paths:
            - '**.js'

## issues

on:
    issues:
        types: [openend, edited, closed]

## issue_comment

on:
    issue_comment:
        types: [created, deleted]

on: issue_comment
    jobs:
        pr_comment:
            name: PR comment
            if: ${{ github.event.essue.pull_request }}

## workflow_dispatch

on:
    workflow_dispatch:
        inputs:
            alerta:
                description: 'nivel'
                required: true
                default: 'medio'
                type: choice
                options:
                    - 'bajo'
                    - 'medio'

## schedule

on:
    schedule:
        - cron: '0 0 ** *'
