# CI/CD Pipeline with GitHub Actions

## Overview

This repository demonstrates the implementation of a CI/CD pipeline using GitHub Actions. The pipeline ensures code quality by running Cypress component tests on Pull Requests to the `develop` branch and automates deployment to Render when code is merged from the `develop` branch to the `main` branch.

## User Story

```markdown
AS A developer looking to integrate a pipeline in a codebase for continuous integration and deployment,
I WANT to create a GitHub Action that will follow best practices by running test cases when a Pull Request is made to the develop branch
SO THAT I can ensure that all code integrations are clean and pass the proper requirements.

AS A developer looking to deploy the application automatically to Render when code is merged from develop to main,
I WANT to create a GitHub Action that will run when the code is merged to main and automatically deploys to Render
SO THAT the application is constantly updated when major releases are made to the main branch.
```

## Acceptance Criteria 
```
GIVEN a fullstack application for a web developer,
WHEN I upload new features to the application
THEN I should be making Pull Requests to a develop branch first
WHEN I create a Pull Request to a develop branch
THEN I should be executing a GitHub Action that checks the Cypress component tests
WHEN I see that the tests pass on GitHub Action
THEN I should see those test results on GitHub Action and merge the code
WHEN I push the code from the develop branch to the main branch
THEN I should see that another GitHub Action triggers and should automatically deploy to Render
```

## Getting Started
Prerequisites
 - Node.js
 - Git
 - GitHub account
 - Render account


Setup
1. Clone the repository:
   ```
   git clone https://github.com/ashleyxnicolej/GitHubActions-CI-CD_Setup.git
   cd GitHubActions-CI-CD_Setup
   ```
2. Install dependencies:
   ```
   npm install
   ```
  
3. Create branches:
   - Create a develop branch
   ```
   git checkout -b develop
   git push origin develop
   ```

4. Set up Render deployment:
  - Follow the instructions in the Render and MongoDB deployment guide.
  - Turn off Auto-Deploy in Render settings.
  - Copy the Deploy hook URL.

5. Add GitHub Secrets:
  - Go to your repository on GitHub.
  - Navigate to Settings > Secrets > Actions.
  - Add the following secrets:
    - RENDER_API_KEY: Your Render <vscode_annotation details='%5B%7B%22title%22%3A%22hardcoded-credentials%22%2C%22description%22%3A%22Embedding%20credentials%20in%20source%20code%20risks%20unauthorized%20access%22%7D%5D'> key</vscode_annotation>API.
    - RENDER_DEPLOY_HOOK: The Deploy hook URL from Render.

## GitHub Actions Workflows
 1. Cypress Tests Workflow:
- File: .github/workflows/test.yml
- Triggers on Pull Requests to the develop branch.
- Steps: checkout code, set up Node.js, install dependencies, run Cypress tests.

2. Deployment Workflow:

- File: .github/workflows/deploy.yml
- Triggers on pushes to the main branch.
- Steps: checkout code, deploy to Render using the Render Deploy Hook.


## How to Test
1. Create a feature branch:
  ```
  git checkout -b feature/test-branch
  ```

2. Make a change and commit:
  ```
  echo "Test change" >> README.md
  git add README.md
  git commit -m "docs: Update README for testing CI/CD pipeline"
  ```

3. Push the feature branch:
  ```
  git push origin feature/test-branch
  ```

4. Create a Pull Request:
  - Create a Pull Request from feature/test-branch to develop.
  - Verify that the Cypress tests run automatically in the Actions tab.

5. Merge the Pull Request:
  - Once the tests pass, merge the Pull Request into the develop branch.

6. Merge Develop to Main:
 - Create a Pull Request from develop to main.
 - Merge the Pull Request into the main branch.
 - Verify that the deployment to Render is triggered automatically in the Actions tab.

## Resources
 - Render Deploy Hooks
 - Render API Key
 - GitHub Repo Secrets
 - Main and Develop Branches


## License
This project is licensed under the MIT License.

