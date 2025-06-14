---
created: 2025-03-03T08:00
updated: 2025-06-14T21:20
---
#public

As of now (2024-11-11) when you load a repo with submodules into IntelliJ (or other Jetbrains IDEs), it does not handle submodules correctly, out of the box. 

To fix this, you have to go to 

`Settings > Version Control > Directory Mappings`

There you have to add a mapping for each submodule to the corresponding path. The rest should work as expected.

### Source
https://www.stevestreeting.com/2022/09/20/git-submodules-tips-for-jetbrains-ides/


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

- [x] 