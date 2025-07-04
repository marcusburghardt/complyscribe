# The complyscribe command line sync-cac-content Tutorial

This tutorial provides how to use `complyscribe sync-cac-content` transform [Cac content](https://github.com/ComplianceAsCode/content) to OSCAL models.
This command has two sub-commands `component-definition` and `profile`

## component-definition

This command is to create OSCAL Component Definitions by transforming CaC content control files.

The CLI performs the following transformations:

- Populate CaC product information to OSCAL component title and description
- Ensure OSCAL component control mappings are populated with rule and rule parameter data from CaC control files
- Create a validation component from SSG rules to check mappings
- Ensure OSCAL Component Definition implemented requirements are populated from control notes in the control file
- Ensure implementation status of an implemented requirement in OSCAL Component Definitions are populated with the status from CaC control files

### 1. Prerequisites

- Initialize the [complyscribe workspace](../tutorials/github.md#3-initialize-complyscribe-workspace).

- Pull the [CacContent repository](https://github.com/ComplianceAsCode/content).

### 2. Run the CLI sync-cac-content component-definition
```shell
poetry run complyscribe sync-cac-content component-definition \
  --repo-path $complyscribe_workspace_directory \
  --branch main \
  --cac-content-root ~/content \
  --cac-profile $high-rev-4 \
  --oscal-profile $OSCAL-profile-name \
  --committer-email test@redhat.com \
  --committer-name tester \
  --product $productname \
  --dry-run \
  --component-definition-type $type
```

For more details about these options and additional flags, you can use the `--help` flag:
`poetry run complyscribe sync-cac-content component-definition --help`
This will display a full list of available options and their descriptions.

After running the CLI with the right options, you would successfully generate an OSCAL Component Definition under $complyscribe_workplace_directory/component-definitions/$product_name/$OSCAL-profile-name.

## profile

This command is to generate OSCAL Profile according to content policy 

### 1. Prerequisites

- Initialize the [complyscribe workspace](../tutorials/github.md#3-initialize-complyscribe-workspace) if you do not have one.

- Pull the [CacContent repository](https://github.com/ComplianceAsCode/content).

### 2. Run the CLI sync-cac-content profile
```shell
poetry run complyscribe sync-cac-content profile \ 
--repo-path ~/complyscribe-workspace \
--dry-run \
--cac-content-root ~/content \
--product ocp4 \ 
--oscal-catalog nist_rev5_800_53 \
--cac-policy-id nist_ocp4 \ 
--committer-email test@redhat.com \
--committer-name test \
--branch main
```

For more details about these options and additional flags, you can use the `--help` flag:
`poetry run complyscribe sync-cac-content profile --help`
This will display a full list of available options and their descriptions.

After running the CLI with the right options, you would successfully generate an OSCAL Profile under $complyscribe_workplace_directory/profiles.
