#public

My public Zettelkasten notes from [[My Zettelkasten]] are going to be hosted as static website in my homelab (see [[My homelab]]) with quartz. And maybe on some public domain, as well. But we'll see

Domain: http://digital-garden.homelab.lan
Repository: http://git.homelab.lan/homelab/digital-garden

#### Static website generation
For generating the website, I use quartz (see [[quartz - static websites with markdown]]). Therefore I forked the original quartz repo to [[repo - digital garden]].

#### Content integration
The content is going to be the set of markdown files, that I write with Obsidian in form of a Zettelkasten. This data is versioned via git, here: [[repo - zettelkasten public]]. It is integrated into the [[repo - digital garden]] as a submodule, lying in `<repo-root>/content`. This way I can easily work on my Zettelkasten, while having the digital-garden in sync. 


#### Docker image build
The docker image is built in the ci pipeline. 


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

