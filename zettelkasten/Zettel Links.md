---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public
Zettel links are for connecting Zettels by their content. Since the Titel of a Zettel might change over time, it is recommended to not use the title of the link as part of the sentence. Instead a sentence with a link should have the following format: 
`<some text> here: [[the link]]`

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

