#zettel
#### Debug printout
```
set -x 
```
Next to regular printouts, all executed commands are printed out with a `+` in the beginning of the line. For each nested command in the line, there is an additional `+` stating the corresponding command.


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

