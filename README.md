# Essential tutorial bits for developers
This document is a collection of tutorial bits that I gather over time from
topics ranging from simple bash commands and git gems to creating self-signed
certifcates. It helps to have a common place to store these gems which can be
easily searched.

## Git
- List branches that contain a given commit
```bash
# search within a local branch
$ git branch --contains <commit>
# search across local and remote branches
$ git branch -r --contains <commit>
```

- List all commits in the current branch that are not in the remote branch
```bash
git cherry -v
```

- For a given file, find what commits were added to master relative to the local
  branch
```bash
git log --oneline HEAD..master -- <file>
```

- Change the author
```bash
git commit --amend --author="<Author Name> <email@address.com>"
```

- Show git root directory
```bash
git rev-parse --show-toplevel
```
