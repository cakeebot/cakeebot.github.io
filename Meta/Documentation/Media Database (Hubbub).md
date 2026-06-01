---
tags:
  - hubbub
  - media
---
%% duplicated from The Hubbub's media database %%
# Base Guide
## **-->** [[Media Collection.base]] **<--**
## Views
### [[Media Collection.base#Everything]]
### [[Media Collection.base#Books]]
### [[Media Collection.base#Creators]]
### [[Media Collection.base#Movies]]
### [[Media Collection.base#Music]]
### [[Media Collection.base#Shows]]

---
# Folder Structure
- subtypes, like track/album/artist for music, will be represented by tags

```js
  > 'Media'
    > 'Books'
    > 'Creators'
    > 'Movies'
    > 'Music'
    > 'Shows'
    > 'Games'
```
# Common Note Structure
- Each heading links to an empty template that (should) meet the standards of that type. The template linked above can be used to create new types/subtypes of media.
## Title
- The note title for an entry should be the primary name by which it is known. Alternative names can be put in the [[Media Database (Website)#aliases list string|`aliases`]] field.
## Tags
- #media 
- #hubbub 
#### *+ type tag(s)*
- #media/book 
- #media/creator 
- #media/movie 
- #media/music 
	- #media/music/album 
	- #media/music/track 
- #media/show 
- #media/game
	- #media/game/video 

> [!NOTE]
> All database entry notes must be tagged with #media and #hubbub (to show up in the base & make the graph pretty)
## YAML Properties
### **tags** (*list[string]*) - required
- [[Media Database (Website)#Tags|See 'Tags' above]] for common tags across all entries
- Additional tags based on type(s) & subtype(s) of media
### **url** (*string*) - required
- A URL linking to the entry
	- This should be one primary link; other links (e.g. Wikipedia) should be added to the note body
- [e.g.] for tracks, using [song.link](https://odesli.co/) for cross-platform compatibility
	- Could use IMDB for movies & shows
	- Could use Goodreads or [Library Thing](https://www.librarything.com/) for books
### **image** (*string*) - required
- A link to a file within `The Hubbub/Attachments` or a URL of an image associated with the entry
- This shows up in the base's card view to make it pretty
### **creators** (*list[string]*) - required*
- \* Not required for the entries of [[Media Database (Website)#../Templates/Media/Creator (Empty Template) Creator|creators themselves]]
- Who (artistically) created the entry—i.e. author, band, director, artist
	- **!!** NOT who added the entry to the database- use [[Media Database Documentation#**added_by** (*string*)|added_by]]
- Formatted as a list to allow multiple artists per entry
- These can be `[[WikiLinks]]` to the creators' entries, but they will not show up on the graph view. Include WikiLinks within a section in the note so the [[Linker brigade|graph is pretty]]
### **type** (*string*) - required
- The type of media that the entry belongs to
- For sorting purposes in the base views of types
	%% i can't find a good way to group them by tag, so this redundancy is the best solution for now %%
### **genres** (*list[string]*)
- What genre(s) does the entry fall under?
- Formatted as a list to allow multiple genres per entry
### **release_date** (*date*)
- When was this entry first published?
	- **!!** NOT the date it was added to the database
### **added_by** (*string*)
- Who added this entry to the database?
	- Add your name here if you want credit for the media discovery
### **aliases** (*list[string]*)
- A list of alternate names that the entry may be known by and found under
### **subtype** (*string*)
- The subtype of media that the entry belongs to
	- For [[Media Database (Website)#Templates Media Creator Empty Template Creator|creators]], this property should be `creator`, to sort them in their respective category 
- For sorting purposes in the base views of types w/ subtypes

---

# Types
- top-level types should correspond with a folder in `The Hubbub/Media`
## [[The Hubbub.nosync/Templates/Media/Book (Empty Template)|Book]]
### Tags
- [[Media Database (Website)#Tags|Common media tags]]
- #media/book 
### Properties
- [[Media Database (Website)#YAML Properties|Common media properties]]
#### **url** (*string*) - required
- A link to the Goodreads (or other book database) page for the movie.
### Subtypes
- None at the moment—if you have ideas on how to sub-categorize books please add them!
## [[The Hubbub.nosync/Templates/Media/Creator (Empty Template)|Creator]]
- This type is a little unique
	- **Does not require the [[Media Database#creators** (*list[string]*) - required*|`creators` property]]**
	- Goes into their own folder (`Media/Creators`), not the type of media
- Does not have subtypes
	- But should be tagged with the primary type of media they create
### Tags
- [[Media Database (Website)#Tags|Common media tags]]
- #media/creator
- The top-level tag of the type(s) of media they create
### Properties
 - [[Media Database (Website)#YAML Properties|Common media properties]]
	 - except [[Media Database (Website)#**creators** (*list[string]*) - required*|`creators`]]
#### **url** (*string*) - required
- A link to a website associated with the creator.
	- If available, I recommend linking to their Wikipedia article
	- Other links can be put within the note's body
## [[The Hubbub.nosync/Templates/Media/Movie (Empty Template)|Movie]]
### Common Attributes
#### Tags
- [[Media Database (Website)#Tags|Common media tags]]
- #media/movie 
#### Properties
- [[Media Database (Website)#YAML Properties|Common media properties]]
###### **url** (*string*) - required
- A link to the IMDB (or other movie database) page for the movie.
### Subtypes
- None at the moment—if you have ideas on how to sub-categorize movies please add them!
## Music
### Common Attributes
#### Tags
- [[Media Database (Website)#Tags|Common media tags]]
- #media/music 
### Subtypes
#### [[The Hubbub.nosync/Templates/Media/Album (Empty Template)|Album]]
##### Tags
- Common music tags
- #media/music/album 
##### Properties
- Common music tags
###### **url** (*string*) - required
- An [album.link](https://odesli.co/) URL to the album
	- See the script [[Track (Inline) 1]] for an example on how to use the [Spotify API](obsidian://show-plugin?id=spotify-api) to search for songs & use the song.link API to fetch the URL
		- **TODO:** script to fetch album links
#### [[The Hubbub.nosync/Templates/Media/Track (Empty Template)|Track]]
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
## [[The Hubbub.nosync/Templates/Media/Show (Empty Template)|Show]]
### Common Attributes
#### Tags
- [[Media Database (Website)#Tags|Common media tags]]
- #media/show 
#### Properties
- [[Media Database (Website)#YAML Properties|Common media properties]]
###### **url** (*string*) - required
- A link to the IMDB (or other database) page for the show.
### Subtypes
- None at the moment—if you have ideas on how to sub-categorize shows please add them!
## Game
### Common Attributes
#### Tags
- [[Media Database (Website)#Tags|Common media tags]]
- #media/game
#### Properties
- [[Media Database (Website)#YAML Properties|Common media properties]]
###### **url** (*string*) - required
- A link to a database or store page for the game.
### Subtypes
#### Video Game
##### Tags
- Common game tags
- #media/game/video
##### Properties
- Common game properties
###### \*\***url** (*string*) - required
- A link to the Steam (or other storefront) page for the game
###### **platform** (*string*)
- What platform(s) can the game be played on?