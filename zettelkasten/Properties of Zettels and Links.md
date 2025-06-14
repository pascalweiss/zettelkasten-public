---
created: 2025-03-03T08:00
updated: 2025-06-14T21:20
---
#public
# Content
A Zettel is a single document, that represents a certain thought or idea. It should be concisely written in own words. It should be clearly understandable by itself (For specialized topics it may be required, that the reader has some background information). 

Remember: [[A Zettel should be publishable]] - If this is given, then you are good


# Relations
There are two types of relations between Zettels.
### Links
Like in a wiki, Zettels are interconnected with links to each other. These links represent a contentwise relation. A subset of Zettels with many interconnections can be interpreted as a cluster. See [[Zettel clustering]] 

### Tags
It may also be helpful to have technical relations between Zettels. This can be done with tags. Tags should be used for maintaining and organizing the Zettels. They may represent a **state** or a **type** of a Zettel. While they may be useful, they should be used sparingly and wisely

You may also want look into the following: [[Connection Rules for Zettels]]

### ### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

