#public 

Sometimes you might have to rewrite the author and committer in the git log. To do this, do:
```bash
 git filter-branch --env-filter '
OLD_EMAIL="pascal.weiss@debtvision.de"
NEW_NAME="pascalweiss"
NEW_EMAIL="paweiss.sub@gmail.com"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$NEW_NAME"
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$NEW_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

Make sure that you have a backup.

### Change contributors on github
If you changed the author of commits for removing somebody from githubs contributos list (e.g. if you commited with the wrong git user), you can follow the steps, here https://github.com/orgs/community/discussions/49813#discussioncomment-10194924

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

