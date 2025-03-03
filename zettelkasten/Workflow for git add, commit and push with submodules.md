#public
Say that you have various git repositories, and you want to have a higher level repository, that integrates the others. Then it might be handy to work with git submodules. It allows to nest git repositories into each other 

### how to add a submodule


### how to commit
There are two workflows for committing submodules. 
1. Committing is done for each repo separately. I.e. you navigate into each individual submodule and do 
   ```
   git add…
   git commit -m "…"
	```
2. Or you commit all submodules at once
   ```
   git submodule foreach --recursive 'git add . && git commit -m "Update submodule"
   ```
 ### how to push 
Pushing can be done recursively. So all commits in submodules get pushed as well

```
git push --recurse-submodules=on-demand
```

### IntelliJ
IntelliJ provides convenient a workflow for submodules. Here you have to go to go to `Settings > Version Control > Directory Mappings` and reference every submodule. The rest (git add, commit and push) works like without submodules.


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

