# Diligence Fuzzing GitHub Action
A simple wrapper around Diligence Fuzzing CLI that can be used directly from GitHub Actions!

## What is Diligence Fuzzing?
Easy to use and powerful, Fuzzing as a Service enables users to find bugs immediately after writing their first specification!
Smart contracts are increasingly complex programs that often hold and manage large amounts of assets. 
Developers should use tools to analyze their smart contracts before deploying them to find vulnerabilities open to exploitation.

If you're new to the Diligence Fuzzing tool or want to learn more about its capabilities, the :octocat: [Fuzzing CLI](https://github.com/ConsenSys/diligence-fuzzing) and 📚 [Fuzzing Docs](https://fuzzing-docs.diligence.tools/) are great resources to get started.

# Usage

Add this Action as a step to your project's GitHub Action Workflow file:

   ```yaml
         - uses: ConsenSys/diligence-fuzzing-github-action@v0.0.2
           with:
             # Flag to control if the action should check out your repository using actions/checkout@v3.
             # Default: true
             checkout: ''

             # Flag to control if the action should install Foundry using foundry-rs/foundry-toolchain@v1.
             # Default: true
             install_foundry: ''
             
             # The API key used to submit campaigns to the Diligence Fuzzing API.
             # Should be added as a secret under repository settings and named FUZZ_API_KEY
             fuzz_api_key: ${{ secrets.FUZZ_API_KEY }}
             
             # The name of the project to add submitted campaigns to.
             # Default: ${{ github.repository }}
             fuzz_project: YOUR_PROJECT_NAME

             # The time limit for each individual fuzzing job (e.g., 10m, 1h, 30s).
             # Default: 1h
             fuzz_time_limit: ''
   ```

## Configuration
Configuration can be provided via the with: section of this Action.

### Inputs

| Variable          | Default Value            | Required | Description                                                                                 |
|-------------------|--------------------------|----------|---------------------------------------------------------------------------------------------|
| `checkout`        | `true`                   | No       | Flag to control if the action should check out your repository using actions/checkout@v3.   |
| `install_foundry` | `true`                   | No       | Flag to control if the action should install Foundry using foundry-rs/foundry-toolchain@v1. |
| `fuzz_api_key`    | -                        | Yes      | The API key used to submit campaigns to the Diligence Fuzzing API.                          |
| `fuzz_project`    | ${{ github.repository }} | No       | The name of the project to add submitted campaigns to.                                      |
| `fuzz_time_limit` | `1h`                     | No       | The time limit for each individual fuzzing job (e.g., 10m, 1h, 30s).                        |
