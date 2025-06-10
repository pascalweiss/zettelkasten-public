#public
In contrast to Zettel links, a tag is not used for content wise relations. Instead they are used for organizing and managing notes. The following tags are recommended: 

#### for documents in input folder
- `#article`: an article or a blog post, with the corresponding link
- `#video`: e.g. a YouTube video
- `#course`: e.g. a Udemy course
- `#consume`: these are resources in the `input`folder that weren’t consumed, yet. If a resource was consumed, the tag should be removed
- `#private`: for Zettels, that should/must be excluded from potential publication

#### for Zettels in the Zettelkasten 
- `#public`: Notes that can be published in public
- `#private`: Notes that can not be published in public

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

