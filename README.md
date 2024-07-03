# GitHub CLI Extension: Repository Destructor

This GitHub CLI extension is designed to delete GitHub repositories in an organization that were created more than a specified number of days ago. It also generates a CSV file with the list of deleted repositories and their admins.

## Installation

1. Install [GitHub CLI](https://cli.github.com/) on your machine.
2. Install this extension using one of the following commands:
   ```shell
   gh extension install homeles/gh-repo-destructor
   ```

or 

```
gh extension install https://github.com/homeles/gh-repo-destructor
```

## Usage

### GitHub Token
To execute this script, your GitHub token will need the following permissions:

- `repo:Full control of private repositories`. This is necessary to delete repositories.
- `admin:org`: Full control of orgs and teams, read and write org projects. This is necessary to manage organization membership and team membership.

### Required Parameters
- `-o`: The name of the GitHub organization.
- `-p`: The period in days. Repositories created more than this number of days ago will be deleted.
- `-d`: Dry run. If this option is provided, the script will not actually delete the repositories.
- `-f`: Force. If this option is provided, the script will not ask for confirmation before deleting the repositories.

### Command
To delete all repositories in an organization that were created more than a specified number of days ago, execute the following command:

```
gh repo-destructor -o ORG_NAME -p PERIOD [-d] [-f]
```

Replace ORG_NAME with the name of your organization and PERIOD with the number of days. Use -d for a dry run and -f to force deletion without confirmation.

### Example

#### Dry-run, just get the list
Get list of repos created more than 180 days ago.
```
gh repo-destructor -o sandbox -p 180 -d
```

#### Delete repos
Deleting repos created more than 180 days ago.
```
gh repo-destructor -o sandbox -p 180 -f
```

## Note
Please use this extension responsibly. Deleting repositories is a destructive action.