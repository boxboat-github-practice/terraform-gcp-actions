# Reusable Terraform Actions for GCP

An action that can be used to deploy to GCP with Terraform.

Create a workflow from your repository that looks like this. 

``` yaml
jobs:
  terraform:
    runs-on: ubuntu-latest
    name: Terraform
    environment: canary # if you want to use secrets tied to an environment, define an environment in your repository (e.g. 'canary')
    steps:
      - uses: actions/checkout@v3
      - uses: boxboat-github-practice/terraform-gcp-actions@v1.0.0
        with:
          GOOGLE_CREDENTIALS: {{ secrets.GOOGLE_CREDENTIALS }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          terraform-version: 1.1.9
```

Make sure you add the following permissions in the GitHub workflow.

``` yaml
permissions:
  contents: read
  pull-requests: write
```
