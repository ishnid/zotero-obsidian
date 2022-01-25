# zotero-obsidian

# What's the point?
I started my first research degree in 2003, and I have *never* had a workflow that I'm satisfied with for reading papers, taking notes and manging my thoughts properly. Until now...

Firstly, huge credit to [Bryan Jenks](https://github.com/tallguyjenks), who writes and YouTubes about this a lot. The workflow below is largely based on his, with my own flavour in places.

This workflow ...

- ... uses [Zotero](https://www.zotero.org/) as the central dispatch point:
	- Add papers to Zotero in the usual way (through DOI import/[Zotero Connector](https://www.zotero.org/download/connectors))
	- Send papers to my tablet (iPad in my case) so that I can read/annotate them wherever (like, in a coffee shop when that's possible again<sup name="a1">[1](#f1)</sup>).
	- Take the papers back from the tablet once the annotations are complete.
	- Export to an Obsidian note, after extracting the annotations and highlighted passages.
- ... uses [Obsidian](https://obsidian.md/) as the place to organise my thoughts.
	- Easily write surveys/literature reviews (in Markdown) by referring to papers only by their citation key (e.g. "[[Lillis2021]]").
	- To remind myself of the contents of a paper, I can just click the resulting link (or by hovering I can see the paper title and authors).
		- The Obsidian note contains the paper's metadata, the extracted annotations/highlights and any notes I've taken. It also has a link to open the paper within Zotero, or within Zotero's web interface.
		- If I want to see the PDF, that's one further click (including clicking on a particular annotation/highlight, which takes me to the correct page within the PDF too).
		- In the past I had to open *at least* one other application to do *any* of the above, or do any cross-referencing (I suspect I wasn't the only Computer Science grad student who wrote his own reference manager).
	- If I use the same referencing syntax within the annotations that I write on my tablet (e.g. "[[Lillis2021]]"), that will also become a link within Obsidian when it has been exported.
- ... has one or two caveats :-(
	- It's not *fully* automated, so I do need to actually *click* on things (🤮) to perform these actions (send to tablet, get from tablet, export to Obsidian).
	- If you are writing your literature review in Obsidian in Markdown, there'll be some extra steps required when you switch to LaTeX. On the plus side, since you're already using Zotero citation keys, converting your Markdown links into LaTeX \cite{...} commands will be straightforward.
	- The iPad-based annotations are limited to highlighting passages and adding text notes. Handwritten annotations won't be picked up for export to Obsidian. They will, however, still be visible in the PDF that's stored in Zotero if that's helpful for adding an extra level of detail to your annotations.
	- There are quite a few steps to set it up, but it's, like, *totally* worth it.

<b id="f1">[1]</b> #TODO remember to remove this whenever the pandemic is over. [↩](#a1)


# You will need

**Software**

- [Obsidian](https://obsidian.md/) - a "second brain" notetaking app. Free of charge for personal use, though not free software. However, all notes are in ordinary Markdown files, so there is no proprietary file type.
- [Zotero](https://www.zotero.org/) - a reference manager that is available as free software.

**Zotero Plugins**

- [BetterBibTeX](https://retorque.re/zotero-better-bibtex/) - manage citation keys.
- [Zotfile](http://zotfile.com/) - send/get to/from tablet and extract annotations.
- [Mdnotes](https://github.com/argenos/zotero-mdnotes) - export notes as Markdown.

# Before we start (citation keys)

- The citation key that is generated within Zotero will be the name of the note that appears in Obsidian. It's not crucial that you change this, but I find it easier to use a short, snappy name for each note (e.g. "Lillis2021"). That way I can link to the note within Obsidian by simply writing "[[Lillis2021]]". It also means that if I write that in my PDF annotation notes it will ultimately become a link within Obsidian too.
	- In Zotero, open the preferences window and select the `Better BibTex` panel.
	- Set the "Citation key format" to "[auth:capitalize][year]".

# Annotate on Tablet

- In Zotero, open `Tools` → `ZotFile Preferences` → `Tablet Settings`.
- Enable "Use ZotFile to send and get files from tablet".
- Choose a "Base Folder" that your tablet can access (within Dropbox/Google Drive/OneDrive/Nextcloud/etc.).
- Other default options are OK.
- To send a paper to your tablet, right-click a paper in your library and select `Manage Attachments` → `Send to tablet` (you can now see any papers that have been sent to the tablet in the "Tablet Files" collection).
- On your tablet, add notes and highlighting in your favourite PDF editor (I use [PDF Expert](https://pdfexpert.com/ios) on the iPad). *Note:* Handwritten annotations won't be captured by the process: it supports highlighting passages and adding notes.
- When you have finished editing, back in Zotero, right-click the paper again and select `Manage Attachments` → `Get from tablet`. Any such papers will be visible in the "Tablet Files (modified)" collection.
- If everything is working correctly, you should (after a brief delay) see a note entitled "Extracted Annotations (dd/mm/yyyy, hh:mm:ss)" appear with the paper. This is what will be exported to Obsidian later.

# Set up Obsidian

- Start Obsidian and create a new vault (anywhere) - this is the folder in which Obsidian will store everything.
- If you want to customise what goes in the notes, within Obsidian create a new folder called `templates`. You can do without this if you are happy with the defaults.
	- If you want to start with my templates, copy the files from the [templates](templates/) directory in this repository into the `templates` directory.
	- Alternatively, the default Mdnotes templates are [here](https://argentinaos.com/zotero-mdnotes/docs/advanced/templates/defaults). You should be most interested in the "Mdnotes Default Template" and "Zotero Note Template" templates. The former is for the main note for each paper. The second is for the extracted annotations.

# Configure Zotero to export to Obsidian

- In Zotero, open `Tools` → `Mdnotes Preferences`.
- Under "File organization", choose "Single file".
- Set the "Export directory" to be the directory that your Obsidian vault is in.
- If you created a `templates` directory in Obsidian, set the "Template folder" to be this one. If you are happy to start with the default templates, you can leave this blank.

# Now you're ready to export a paper from Zotero to Obsidian!

- In your Zotero library, right click on the paper and then choose `Mdnotes` → `Create full export note`.
- You will be given the option to choose the export folder. It will default to your Obsidian vault folder (if you've completed the above steps correctly), so you can just click "Open".

# OK so what happened?

- There is now a note in your Obsidian vault. Its name is the citation key of the paper.
- **Caution**: If you edit this note directly in Obsidian, your changes will be lost if you ever re-export from Zotero.
	- To solve this, my template (see above) contains a link within the "My Notes" section. If you click on that it will create a separate note (which will not be overwritten by a Zotero export) that is displayed within the main note.
- **Caution**: If you habitually create notes that have the same pattern as your citations keys, these may be overwritten accidentally if there's a clash. If this is an issue, you could create a `papers` subfolder (for example) to store your exported Zotero notes.
- Now you can link to this note from anywhere using the "[[Lillis2021]]" syntax. Better still, if you hover over such a link you will see the title and authors without having to click into it.
	- Additionally, if you create a [[Lillis2021]]-style link before you have a note by that name, it will point to the exported Zotero note once you have performed the export.
