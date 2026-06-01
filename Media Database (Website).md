---
tags:
  - meta
---

# Folder Structure
- Subtypes (e.g. for music, track/album/artist), will be represented by tags
```js
  > 'Media'
    > 'Books'
    > 'Creators'
    > 'Movies'
    > 'Music'
    > 'Shows'
    > 'Games'
```

---
# Common Attributes
## Title
- Each entry note's title should be the primary name by which the piece of media is known
## Tags
All entries must be tagged with **#media** and **#media/web** to appear in the database on Nate's site!
## YAML Properties
### **tags** (*list[string]*) - required
- [[Media Database (Website)#Tags|See 'Tags' above]] for common tags across all entries
- Additional tags based on type(s) & subtype(s) of media
### **url** (*string*) - required
- A URL linking to the entry
	- This should be one primary link; other links (e.g. Wikipedia) should be added to the note body
- See each type's URL property for data sources
### **image** (*string*) - required
- Ideally, a URL pointing to an image associated with the entry (to save website storage space)
	- Alternatively, a link to a file within `Meta/Attachments` 
- This shows up in the base's card view to make it pretty
### **creators** (*list[string]*) - required<span style="color: #92795A">*</span>
- <span style="color: #92795A"> * Not required for the entries of</span> [[Media Database#../Templates/Media/Creator (Empty Template) Creator|creators themselves]]
- Who (artistically) created the entry—i.e. author, band, director, artist
- Formatted as a list to allow multiple artists per entry
- These can be `[[WikiLinks]]` to the creators' entries, but they will not show up on the graph view. Include WikiLinks within a section in the note so the [[Linker brigade|graph is pretty]] %% TODO: any way to improve the creator tag? subtypes for individual & group perhaps?  %%
### **type** (*string*) - required
- The type of media that the entry belongs to
- For sorting purposes in the base views of types
### **genres** (*list[string]*)
- What genre(s) does the entry fall under?
- *?* Formatted as a list to allow multiple genres per entry
### **release_date** (*date*)
- When was this entry first published?
	- **!!** NOT the date it was added to the database
### **aliases** (*list[string]*)
- A list of alternate names that the entry may be known by and found under
### **subtype** (*string*)
- The subtype of media that the entry belongs to
	- For [[Media Database#Templates Media Creator Empty Template Creator|creators]], this property should be `creator`, to sort them in their respective category 
- For sorting purposes in the base views of types w/ subtypes

---
# Types
## Creator
- This type is a little unique
	- **Does not require the [[Media Database#creators** (*list[string]*) - required*|`creators` property]]**
	- Goes into their own folder (`Media/Creators`), not the type of media
- Does not have subtypes
	- But should be tagged with the primary type of media they create
### Tags
- [[Media Database#Tags|Common media tags]]
- #media/creator
- The top-level tag of the type(s) of media they create
### Properties
 - [[Media Database#YAML Properties|Common media properties]]
	 - except [[Media Database#**creators** (*list[string]*) - required*|`creators`]]
## Music
### Common Attributes
#### Tags
- [[Media Database (Website)#Tags|Common media tags]]
- #media/music 
#### Properties
- [[Media Database (Website)#Common Attributes|Common media properties]]
### Subtypes
#### Album
##### Tags
- Common music tags
- #media/music/album 
##### Properties
- Common music tags
###### **url** (*string*) - required
- An [album.link](https://odesli.co/) URL to the album
	- See the script [[Track (Inline) 1]] for an example on how to use the [Spotify API](obsidian://show-plugin?id=spotify-api) to search for songs & use the song.link API to fetch the URL
		- **TODO:** script to fetch album links
#### [[../Templates/Media/Track (Empty Template)|Track]]
##### Tags
- Common music tags
- #media/music/track 
##### Properties
- Common music properties
###### **url** (*string*) - required
- A [song.link](https://odesli.co/) URL to the track
	- See the script [[Track (Spotify Script)]] for an example on how to use the [Spotify API](obsidian://show-plugin?id=spotify-api) to search for songs & use the song.link API to fetch the URL
###### **album** (*string*)
- The album the track is from
	- If the track is from a single, this can be omitted
- This can be a `[[WikiLink]]`, but the connection from a property will not appear on the graph view.
	- Add a WikiLink to a Links section within the note to make that connection