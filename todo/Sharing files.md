## Steps

* Sync Upena jargon and Upena structure (`include/class.uml` classes).
	* Jargon is supreme. Unique. Unambiguous.
	* Area|Folder > Class|Object|Folder > Object|File > Element|Dimension
* Sync Upena documentation with Upena structure.
* Determine if/how this conforms to a 10x10 JD structure.
* Constrain Upena structure to 2-tier area/category relations. Use stub areas if needed.
* Sync Upena types and HKA JD to determine top 10 JD areas.

## Things to fold into each other

* Obsidian vault project/template/ with HKA J.D 00-99 folders.
* Obsidian folders with HKA J.D 00-99 folders.
* Upena/doc/files with above.
* Upena UML structure with above.
* Project docs (Dibs, etc.) with above.
* Role-based (admin, development, marketing, compliance) requirements with above.
* PMP requirements with above.
* Whatever other use cases.

## ..resulting in

* UML logical structure (suitable for database) that can be flattened into..
* J.D categories

## Goals

* Each format should be able to support a project.
* A single project should be able to incorporate every format.
* Each format should be transferable to every other format.

## Constraints

Projects assume:
* Unique project-based ID across all initial collaborators
* Project ID is used as the entry point for a project, and doesn't need to be all over the place within the project.

## Notes

* Integrity is just easier to impose in a database and harder to impose on generic files; you could  always forego constraints in a database and crawl files to maintain integrity.
* Distinguish the information from who needs access to it and why. Because the who and the why (employees, roles, responsibilities assigned to roles) are expected to change and the information that they refer to must remain uniform and accessible across those changes.

For the sake of normalization and accessibility and to help expose complexity, I prefer to categorize information based on the type of information

With respect to the [Johnny.Decimal example](https://johnnydecimal.com/10-19-concepts/11-core/11.02-areas-and-categories/) regarding competing hierarchies:

	ex1: Insurance > Car    Insurance > House 
	ex2: Car > Insurance    House > Insurance

..I'd prefer something like:

	ex3: Asset > Car        Asset > House
	ex4: Insurance > Car    Insurance > House

If the relations above were organized as `Folder > File` types, then the Johnny.Decimal example would 

focus on the types of information instances (documents, spreadsheets, images) type-based structure to a task-based structure. PMI doctrines and Johnny.Decimal are typically organized in terms of roles, responsibilities, and interests.

Since the same types (activities, components, employees, etc.) can obviously serve multiple goals and since type composition is not as dynamic as the goals they serve, it makes more sense to arrange tasks and phases “on top of” the types they depend on rather than the other way around.

Specific example:  A ‘deliverable’ can capture aspects of quality, procurement, and scheduling that are inextricably bound to the same thing being delivered. Isolate the deliverable and leave whoever is in charge of quality, procurement, and scheduling to coordinate their efforts with respect to that deliverable accordingly.


## Cases

* Management, planning, scheduling
	* Projects characterized by..
		* At least one lead having read access to all files.
		* A lead understanding the necessity and dependency of all areas and categories (JD terminology). If there is too much information for a single person to manage or understand, break into smaller projects and define project interfaces.
		* All files being related to a particular collaborative effort.
* Exchanging, sharing, trading
* Assessing and evaluating

## Aspects

* Packaging
	* Individual
		* Email attachment
		* Text message attachment
		* Physical drive (USB, etc.)
		* URL
	* Group
		* Obsidian vault
		* Repository (Distributed)
		* Repository (Shared)
		* Shared folder
			* Apple iCloud folders
			* Dropbox
			* Google Drive folders
			* Google Workspace shared drive
		* Zipped, then handled individually or by group
* Formats
	* Apple office doctypes - Pages, Numbers
	* Apple Notes
	* Google office doctypes - Docs, Sheets
	* Google Keep
	* Google Tasks
	* Microsoft office doctypes - Word, Excel
	* Plain text
		* CSV
		* Graphviz
		* HTML
		* INI
		* JSON
		* Markdown
		* PlantUML
		* ReStructuredText
		* YAML
	* PDF
* Devices
	* PC app
	* PC web
	* tablet app
	* tablet web
	* phone app
	* phone web
* Authentication
	* PC account
	* PC group
	* Cloud account
	* Cloud group
	* Enterprise account
	* Enterprise group
* Deliverable
	* Native format (per format and device)
	* Slide show
	* Printed publication
	* Website

Authority
* Shared folder
	* Obsidian vault
		* ! therefore a shared/periphery JD type
	* Repository
		* ! therefore a shared/periphery JD type
	* Individual file

## J.D common issues

*"Not enough room, need more numbers/letters/etc.."* If you use J.D to manage collaborative efforts, then those different efforts will probably require different access.

Folders are the most common (and probably easiest) method for controlling access to information. Therefore consider access
Dependencies are not likely to nest nicely - they're probably going to form a multi-tree.

*"Nesting is too deep/ugly."* Expose category folders in one common folder (put all 00-99 categories into a single folder). Put links to the category folders in the 0-9 areas folders. Exposure *shouldn't* be taxing for the most part because you're probably not filling out all your areas and you probably don't have 10 areas in the first place. Also, with respect to project management, exposing complexity is a good thing. If you actually need 100 folders to run a project, you should know what they all are. Nesting categories in areas is really just a trade-off between scrolling through potentially 100 folders to get to the ones at the bottom vs. clicking on an area first.

*"I don't like/want to remember the IDs."* The usefulness of the IDs is that you can (a) effectively rename the file (the text following the ID) and retain (b) the persistent and unambiguous identification across documents, emails, texts, napkins, etc.. You'll remember the IDs you use the most, making access to those a little easier.

*"What if a file should go in two places?"* Folders, if determined by type (rather than purpose), should not compete for the same file. If so, the folder names are too ambiguous. If a file really really needs to be in two places, flip a coin and put a link or reference (perhaps in a stub document) in one folder that points to a file in another.

## Propaganda

* A dynamic workforce requires a stable foundation.
* Your solution is our problem.
