#  CI/CD Setup: GitHub Actions — Public vs Private Runners

This repository demonstrates two common ways to run GitHub Actions workflows:

-  **GitHub-hosted runners** — best for public, open source projects.
-  **Self-hosted runners** — better for private projects that need more control and security.

---

##  GitHub-hosted runner

A GitHub-hosted runner is a virtual machine provided by GitHub.

**Ideal for:**
- Public and open source projects
- Quick setup with no extra configuration
- Automatic updates and maintenance handled by GitHub

**Example workflow:**
```yaml
# .github/workflows/ci.yml
name: Simple CI

on:
  push:
    branches: 
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Setup Nodejs
      uses: actions/setup-node@v4
      with:
        node-version: '18'

    - name: Install dependencies
      run: npm install

    - name: Run tests
      run: npm test
```
## Benefits
- Free for public repositories (with generous limits)
- Easy to set up and scale
- Managed environment with automatic updates

## Drawbacks
- Less control over the environment
- Not ideal for sensitive or private code

##  Self-hosted runner
A self-hosted runner is your own machine registered with GitHub Actions.

**Ideal for:**
- Private or enterprise projects requiring more security
- Projects needing specific hardware or custom software environments

```yaml
name: Simple CI

on:
  push:
    branches: 
      - main

jobs:
  build:
    runs-on: self-hosted

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Setup Nodejs
      uses: actions/setup-node@v4
      with:
        node-version: '18'

    - name: Install dependencies
      run: npm install

    - name: Run tests
      run: npm test

```

## Benefits
- Full control over software, tools, and configuration
- Better suited for sensitive, private projects
- Can run inside your network or behind a firewall
  
## Drawbacks
- You’re responsible for maintenance and security updates
- Limited scalability unless you add more machines
- Higher operational effort




