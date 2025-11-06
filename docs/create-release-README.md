# Create Release Workflow
The following workflow is used to create github releases for a chosen repository.

## Assumptions
Knowledge in the following:
- Github Actions Workflows
- Github CLI

### Calling this Workflow
Sample code to call this workflow is the following.
```YAML
  create_release:
    name: Create Release
    uses: scankin/github-automation/.github/workflows/create-release.yml@1.0.0
    with:
      repository_name: '<ORG>/<REPO-NAME>'
      release_type: 'minor'
    secrets:
      GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Inputs
The following inputs are designed to be as unperscriptive as possible. 

| Name | Type | Required | Description | 
| ---- | ---- | ---------| ----------- |
| repository_name | `string` | Y | The name of the repository to create the release |
| release_type | `string` | Y | Type of release in terms of semantic versioning i.e. 'major', 'minor' or 'patch' |

### Secrets
| Name | Required | Description | 
| ----  | ---------| ----------- |
| GH_TOKEN | Y | The credentials of your GH Actions token - needs "write" permissions [See Authenticating To Azure](#authenticating-to-azure) for more information.|


### Jobs
#### Deploy
Job which is composed of all steps to create a new release in github
##### Generate New Release Number
This task generates the new release number, incrementing the previous release in terms of semantic versioning.
##### Create New Release
This task uses the github cli `gh release create` command to create the release within the repository, using the release number generated in the previous task.

### Resources
- [Semantic Versioning Documentation](https://semver.org/)