# tools
This repository contains reusable GitHub Actions workflows that can be utilized in various repositories within the [hellocoop](https://github.com/hellocoop) organization.

## Reusable Workflows (`./github/workflows/*`)
> Worflows prefixed with `content-` are used by the content repos ([www.hello.coop](https://github.com/hellocoop/www.hello.coop), [hello.dev](https://github.com/hellocoop/hello.dev), etc)
### `content-merge.yml`  
**Purpose:** This workflow is responsible for checking if a Pull Request (PR) is ready to be merged into the `main` branch.  
**How it works:** It accomplishes this by fetching all the latest changes in the `main` branch and running tests on the PR to ensure it meets the necessary criteria for merging.  
**Usage:**  
```yml
uses: hellocoop/tools/.github/workflows/content-merge.yml@main
```

### `content-sync.yml`
**Purpose:** This workflow is responsible for synchronizing the built content with the associated S3 bucket and perform cache invalidation.
**How it works:** This workflow requires a `STACK` name argument as part of the AWS CloudFormation. The workflow builds the content using the npm run build command in the repository, which creates content in an S3 directory. This content is then copied to its associated S3 bucket, and finally, it invalidates the CloudFront cache.  
**Usage:**  
```yml
uses: hellocoop/tools/.github/workflows/content-sync.yml@main
with:
  STACK: <stack-name> #type: string, required: true
```
