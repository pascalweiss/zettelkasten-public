---
created: 2025-03-19T23:18
updated: 2025-06-12T23:45
---
### Basic requirements
- It is a web app, that runs in the browser
- It has responsive design, so that it has a good look on both, desktop and phone
- It is deployed has helm release in the kubernetes cluster of my homelab (see [[My homelab]])
- It has the domain `activity.homelab.lan`
- Data is written via a simple backend into a postgres database

### Functional requirements
- There is a text field on the bottom, where the user can type in an activity (e.g. "washed the dishes").
- When the user types in an activity, and presses enter, or clicks "submit", then this becomes an entry in a list
- The entry shows the text, that was typed in by the user.
- Next to the entry, there is a counter, which is set to 1, when the activity was created
- When the user did the same activity again, then he can click a button with label +1. This will increase the counter with +1
- There is also a -1 button. This will decrease the counter with -1. 
- If the counter is decreased from 1 to 0, then the entry is removed from the list
- When the user types in a new entry, then this becomes another entry in the list.
- The list items are sorted in chronological order. I.e. the activity that is added first is on top of the list. The activity that is added second is on the second place of the list... and so on

### Meta data of activity entires
Each activity is stored with the following meta data:
- date 
- time (hours, minutes, seconds)
- activity (the value that was written in the text input)

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

