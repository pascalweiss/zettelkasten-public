---
created: 2025-03-03T08:00
updated: 2025-06-12T23:45
---
#public
An index points to entries to the various topics. Such an index in my Zettelkasten is here `zettelkasten/Index`. This index is also the root of the Zettelkasten. It may also be required to have sub indices that are organized in a tree-structure to simplify navigation.

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

