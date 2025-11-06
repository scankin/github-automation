# Create Release Workflow
The following workflow is used to determine the type of release. This is perscriptive in terms of my own convention. Merges which branch name contains the name "release" will result in a major change, branches containing "feature" will result in a minor change and those containing "patch" will result in a patch version change.

## Assumptions
Knowledge in the following:
- Github Actions Workflows

### Calling this Workflow
Sample code to call this workflow is the following.
```YAML
  generate_release_type:
    uses: scankin/github-automation/.github/workflows/generate-release-type.yml@feature/adding-release-workflow
    with:
      repository_name: '<ORG>/<REPOSITORY-NAME>'
    secrets:
      GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Inputs
The following inputs are designed to be as unperscriptive as possible. 

| Name | Type | Required | Description | 
| ---- | ---- | ---------| ----------- |
| repository_name | `string` | Y | The name of the repository to create the release |

### Secrets
| Name | Required | Description | 
| ----  | ---------| ----------- |
| GH_TOKEN | Y | The credentials of your GH Actions token - needs "write" permissions [See Authenticating To Azure](#authenticating-to-azure) for more information.|


### Jobs
#### Deploy
Job which is composed of all steps to generate the type of release
##### Get Merged Branch Name
This task gets the branch name from the most recent pull request which has been merged. This value is set to the outputs and used in the next step.
##### Generate Release Type
This task generates the release type of the merge. Merges which branch name contains the name "release" will result in a major change, branches containing "feature" will result in a minor change and those containing "patch" will result in a patch version change. Feel free to edit along with your own convention.

### Resources
- [Semantic Versioning Documentation](https://semver.org/)