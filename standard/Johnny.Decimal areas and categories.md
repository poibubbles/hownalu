Note arxiv.org, Dewey decimal, legal citations, Bible verses.. JD basically distinguishes itself by assuming category boundaries up front so that we can fit um in our brain.

YO. Repositories and vaults and whatnot ARE COMPONENTS.

## Managing folders, files, and outlines


YOYOYOYO the idea is, for publishing purposes, to summarize the rules in a quick list, then link them to sections that briefly state the reason for the rule before going into more detail. FOR EXAMPLE...

Rules for this section:
* Minimize links from one shared file to another.

### Minimize links from one shared file to another

Because file content may be changed by potentially many editors over time..
* many-to-many and circular relations between files should be avoided, and
* one-to-many relations should be used sparingly.

DESCRIBE ABOVE IN DETAIL.






Given that..
* sections within documents is common and useful, and
* distinguishing all potential section content as individual files is pathological

..we need to know when to capture hierarchies as files within folders or sections within files. (Especially considering an outliner's ability to blur the distinction by presenting folders and files as sections in a single, coherent work.)

Johnny.Decimal file IDs primarily benefit collaboration (including with yourself, across time) by providing unique, persistent identifiers.



* If you're using an outliner to organize information, then you've already determined re probably conforming to whatever standards the outliner uses to perform its magic. Therefore, 

Main idea with our Johnny.Decimal scheme is primarily to identify the *types* of documents, files, and records you want to share (as 'categories') and secondarily to group them into larger thematic 'areas'. Such that with respect to any particular jurisdiction, project, ten areas and ten categories per areas should suffice to distinguish different types. Another way,

If you want to have more than ten different categories per area, it's a good indication that you're either not seeing enough similarity between two categories or that you're trying to combine two conceptually different jurisdictions or projects. (Or so we may choose to believe given the 10x10 limitation.)

* Keep the different categories or types uniform across all jurisdictions and projects.
* Subdivide them 
ggkkkkkkkkkkkkkkkk
### Johnny.Decimal implementation

* Limited to 10 (0-9) basic areas of information.
* Reserve X0 for category meta information.
* Reserve files 00-10 (or 000-010) for metadata and indexes that are of a different structure than instance documents.
* The first (x1) category in an area (x1) represents the most generic category in area.
* Keep a unique and persistent ID for every file, prefixed by their category ID.
* File content is intended to be updated (if not, freeze somehow).
* J.D indexes (if you use them) must be shareable.
* Categories are based on types of output rather than roles or purposes.
	* Prefer to expose the complexity of all the types of information needed rather than hide complexity under project roles or functions.
  * Avoid balkanizing information by purpose - instances of information types may serve many (including unforeseen) purposes.
	* Administration, finance, security, etc. are *dynamic* cross-cutting concerns; roles that may be expanded, reduced, combined, or divided to require access to more or fewer categories of information.
* Minimize links - links aren't durable across jurisdictions or environment types.

##### How should we determine what areas we use?
##### How should we determine what categories we use?
##### How should we determine what gets its own file?

## Pillars

J.D layout: `project (jurisdiction) / area (theme) / category (type) / instance`

* Ideally, J.D categories are types and files in those categories are instances of those types.

In the development of all this:
* It's hard to come up with useful areas from the get-go. Similarities and differences between categories become more obvious over time.
* It's relatively easy to distinguish different types, then clump the types, then determine a flow, then see general areas in that flow.
# Standard layout

## Areas and categories

10-19 priorities and schedules; what we want to accomplish and when
20-29 standards and constraints; how we accomplish things, what we work within
30-39 resources and inventory; who and what we employ to accomplish things
40-49 references and library; publications
50-59
60-69 assessments and evaluations;
70-79 reports and events;
80-89 shared (potentially public) information; what needs to be available to others
90-99 archive and cold storage;


In Obsidian, the top ten areas are folders named after the first category (`N1`, `11 mission`, `21 standard`, etc.). The remaining categories are unordered.

* 10-19 priorities and schedules; what we're about, what's going on
	* THIS IS WHERE DECISIONS ARE MANAGED AND ACCOUNTED FOR
	* 11 mission - purpose, markets, use cases, features, services
	* 12 issue
	* 13 deliverable - goals, capabilities, desirable outcomes, objectives
	* 14 schedule - plans, calendars of events (layerable if not distinct)
* 20-29 standards and constraints; methods, how we operate, what we have to work *within*
	* THIS IS STUFF THAT NEW HIRES NEED TO KNOW TO DO THEIR JOB
	* 21 standard - basis for assessment, quality, competency
	* 22 activity - recipes, guides, repeatable tasks
	* 23 contract - consequential agreements
	* XX guide/howto
	* XX model/
	* XX jargon
	* XX role; mapping of capabilities to members, resources, components
* 30-39 resources and inventory; what we have to work *with* (things we can gain or lose)
	* THIS IS WHAT YOU HAVE TO WORK WITH, SCHEDULE, AND MAINTAIN
	* 31 member - participants
	* 32 resource
	* 33 component; assignable mechanism or agent (generic)
	* XX asset - assignable, transferable, composed of components
	* XX asset/equipment
	* XX asset/supply
	* XX asset/material
* 40-49
	
* XX-XX reference; canonical/generic documentation, unlikely to vary between jurisdictions
	* X1 topic? - indexes that organize reference docs
	* XX manual
	* XX protocol
	* XX executable
	* XX path
	* XX map
* 70-79 reports; announcements, events, evaluations
	* THIS IS AN ACCOUNTING OF WHAT'S HAPPENED OR GONNA HAPPEN
	* 71 history
	* 72 meeting
	* XX event - description of planned or completed event
	* XX endorsement
* 80-89 shared; accessed or input by public or transient participants
	* THIS IS LIVE OR ACTIVELY SHARED STUFF
	* 81 share
	* 82 website
	* 83 public input
	* XX survey assessments - results provided by targets
	* XX evaluation - determinations, conclusions based on assessments
* 90-99 basement; end of (the) line
	* THIS IS STORAGE FOR WHATEVER
	* 91 archive

For 20-29, see [the four kinds of documentation](https://www.writethedocs.org/videos/eu/2017/the-four-kinds-of-documentation-and-why-you-need-to-understand-what-they-are-daniele-procida/) at https://www.writethedocs.org/:
- learning-oriented tutorials:`howto` (short example), `guide` (long example)
- goal-oriented how-to guides: `activity` (process, assigned as a `task`)
- understanding-oriented discussions: `concept` (principle)
- information-oriented reference material: `jargon`, `model`

### Changing file IDs
Leave the original file ID+name as is. Remove its content, add its content to the new file ID+name. Put a link or reference in the (now empty) old file to the new file ID+name.

Of course, if you're super duper sure that a file ID+name has not be referenced elsewhere then go ahead and change it.
