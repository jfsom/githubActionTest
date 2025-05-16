# GitHub Actions Basic Tutorial

This guide provides a basic introduction to setting up GitHub Actions for your project.

## 1. Create a Simple Workflow

1. In your GitHub repository, create a `.github/workflows` directory
2. Create a new file called `main.yml` in that directory

## 2. Basic Workflow Example

```yaml
name: CI Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v2
    
    - name: Run a one-line script
      run: echo "Hello, GitHub Actions!"

    - name: Setup Node.js
      uses: actions/setup-node@v1
      with:
        node-version: '14.x'

    - name: Cache node modules
      uses: actions/cache@v2
      with:
        path: ~/.npm
        key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
        restore-keys: |
          ${{ runner.os }}-node-


