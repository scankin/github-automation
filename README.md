# github-automation
Repository to hold automation scripts, workflows for github and related documentation

## Current Library
All workflows can be found within the `.github/workflows` directory. Documentation for the workflows can be found in the `docs/` directory with the following naming convention `<pipeline-name>-README.md`
- generate-release-type.yml: Is used to determine whether a release is of type 'major', 'minor' or 'patch'
- create-release.yml: Generates a new release number based off previous releases and creates a new release for the repository
