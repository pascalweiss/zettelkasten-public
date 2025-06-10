#public
An index points to entries to the various topics. Such an index in my Zettelkasten is here `zettelkasten/Index`. This index is also the root of the Zettelkasten. It may also be required to have sub indices that are organized in a tree-structure to simplify navigation.

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

