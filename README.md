# import-git-files

![import-git-files](https://github.com/michaeltneylon/import-git-files/workflows/import-git-files%20CI/badge.svg)
[![Documentation Status](https://readthedocs.org/projects/import-git-files/badge/?version=latest)](https://import-git-files.readthedocs.io/en/latest/?badge=latest)

[Read The Docs](https://import-git-files.readthedocs.io/)

`import-git-files` enables defining file imports from 1 or more git repositories (public or private) to local destinations.

This supports use of polyrepos that may be related. Each repository may follow release definitions that the repository should only contain 
what is released together, yet it may be a sub-project or related project to other repositories. This import tool allows defining imports 
into other projects which can include commit shas, tags, and releases.

## Installation

Requires Python 3.6+ and either OS X or Linux. 
It is not tested or supported on Windows. This is only developed and tested
against GitHub repositories, but may work elsewhere.

`pip install import-git-files`

## Usage

```commandline
usage: import-git-files [-h] [--version] [-v] [-t TEMPORARY_DIRECTORY_PARENT]
                        [--ssh-key SSH_KEY]
                        input

Import files from other repositories. Define the imports in a JSON file and
pass as input argument. If the repositories are private and require
authentication but you do not have cached credentials and are using it in a
non-interactive way, you can either define a Personal Access Token in your
Environment under variable GITHUB_TOKEN or you can specify a path to an SSH
Deploy Key.

positional arguments:
  input                 The input json with a hash of repo URLs and their
                        value being hash of source path and destination path.
                        Source path should be relative to root of repository
                        and the destination path can be absolute or it can be
                        relative to the PWD.

optional arguments:
  -h, --help            show this help message and exit
  --version             show program's version number and exit
  -v, --verbose         Set logging to verbose
  -t TEMPORARY_DIRECTORY_PARENT, --temporary-directory-parent TEMPORARY_DIRECTORY_PARENT
                        Optionally set the parent directory for temporary
                        directories or else will use system tmp default.
  --ssh-key SSH_KEY     Path to an SSH Key with access to the repository. This
                        file needs 600 permissions. This cannot be defined in
                        combination with GITHUB_TOKEN environment variable.
```

note: When needing to setup non-interactive authentication methods, 
SSH deploy key is preferred over Personal Access Token. If using a PAT, avoid
setting verbose logging as it may expose the token.

You can also use `import_git_files` module in your project and the included 
context manager, `GitExtractedFiles`. See the [docs](https://import-git-files.readthedocs.io/) 
for more information.
