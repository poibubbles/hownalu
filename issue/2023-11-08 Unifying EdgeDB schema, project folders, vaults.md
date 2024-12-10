To the extent that the basis of operations is project-based management and the DB schema intends to support project-based management, the actions supported by the DB schema should support, enhance, or map to a folder-based structure.

The goal is to unify the following:
* folder structure in `hownalu` and other vaults
* folder structure in `upena/doc/`
* folder structures for PMP-style management
* the `upena` [[EdgeDB]] database objects

So far the gist looks like this:
* folders are good for easy access to durable deliverables
* databases are good for structured transactions

```
project term        db object

activity            activity
component           asset
history             event
issue               issue (IBIS)
jargon              exposition
question            issue (IBIS)
resource            resource
role                endorsement
todo                imperative (IBIS)

upena doc

administration
citations
guide
model
purpose
resource
standard
terminology
todo

PMP model?
```

I really wanna move from 'elements' and 'compounds' to something like 'facets' and "use-case specific term for the object thingee." Because the point is that the facets are all the dimensions we have to express/capture the all the potential object thingees, and the object thingees themselves just constrain inter-object capabilities.