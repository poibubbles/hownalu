# Databases: transactional integrity
...
# Repositories: collaborative performance
...
# Vaults: linked concepts
...
# Folders: easy access and navigability

For durable deliverables and their manually-managed intermediates. Easy to back-up, synchronize. Most familiar and easiest to adopt.

## Access implies purpose, purpose warrants structure

Long version..

Given some form of ownership over the information stored in a folder, a top-most or root-level folder effectively represents an owner's `jurisdiction`:
```
jurisdiction/...
```

Given that we'll accumulate instances of information as files, we can name folders according to a uniform `type` of information:
```
jurisdiction/.../type/instance
```
No ellipses between `type` and `instance` indicate a tight coupling between `type/instance`.

We can also organize our information based on purpose (or theme or other similar grouping):
```
jurisdiction/.../purpose/.../instance
```

We prefer to organize information as `type/instance` because:

* the many-many relationship between potential purposes that types of information,
* we aren't likely to know, in advance, all the purposes our information will eventually serve and,
* links aren't guaranteed to persist across jurisdictions, environment types, and projects
* for well-determined types, access to instances of those types are likely to be uniform; access to `type/instance-1` likely implies access to `type/instance-2`

**My problem with Johnny.Decimal is the relationship implied by the leading decimals.**  Specifically, it's that files in folders 50-59 ..which may be folders of significantly different type.. are implied to have something in common with respect to being in the 50-59 range. For file `51.01 C` in `50-59 A/51 B/51.01 C`, my problem is that `C` is now bound to context `A`.

`jurisdiction/.../type/instance variant`

Items in a folder should all serve an obviously similar purpose. Preferably, they should share the same structure.

```
2023-10-11 meeting.txt
```

## Purpose implies deliverability
...
## Deliverability implies uniformity
If folder contents are deliverables, they are potential dependencies and should therefore . they should 
## Dependencies are deliverables
...
## Nest for navigation, not inheritance
Folders should be used to navigate toward files from the top down. But files should be organized in folders from the bottom up. Which comes first?

Think "up" from the purpose of your files, not "down" from what you expect to see. We want to navigate what is, not what would be nice.

# Identifiable vs. Sortable

[In Johnny's own words](https://www.reddit.com/r/ObsidianMD/comments/13hibnz/comment/jl2lqbf/):
```
I don’t think Johnny.Decimal is well suited to organising things that are already inherently organised: think a phone book, or your music library. They’re already, by nature, alphabetical. Leave well alone.
```
See [Johnny.Decimal's take on PMP management](https://play.johnnydecimal.com/johnny.decimal/10-19-administration).
Find out more about [Johnny.Decimal](https://johnnydecimal.com/)

# Naming by identity

# Names to sort by importance
Given that default folder listings will sort files by name, alphanumerically from left to right, order components of a file name in importance from left to right.

This convention prioritizes when a meeting occurred and when notes were taken:
```
2023-10-03 agenda.txt
2023-10-03 notes.txt
```

This convention prioritizes the purpose of the files' contents over when they occurred:
```
agenda 2023-10-03.txt
notes 2023-10-03.txt
```

```
tmp/icon-large.jpg
    notes.txt
```


# Files identify, folders group
A file's name should usefully (therefore uniquely) identify its contents or purpose across all files in a project.

It should be easy to determine what folder `filename.ext` belongs in by name alone;  once in its destination folder, `filename.ext` can be updated to follow the folder's convention.
 
Don't sacrifice identifiability of individual files. Identifying by purpose variation alone:
```
image/icon/large.jpg
           small.jpg
	  logo/large.jpg
           small.jpg
```
..is as pathological as identifying by general purpose alone:
```
image/large/icon.jpg
            logo.jpg
	  small/icon.jpg
            logo.jpg
```
`large.jpg`, `small.jpg`, `icon.jpg`, and `logo.jpg` are not named uniquely enough to determine which folders they belong in.

Instead, prefer files named uniquely according to purpose in as flat a folder structure as possible:
```
image/icon-large.jpg
	  icon-small.jpg
	  logo-large.jpg
      logo-small.jpg
```

If many variants of a purpose are anticipated (such that listings become unbearable), add an additional folder but :
```
image/icon/icon-large.jpg
           icon-medium.jpg
           icon-small.jpg
	  logo/logo-large.jpg
           icon-medium.jpg
           logo-small.jpg
```

# Additional thoughts
* https://www.eleanorkonik.com/yet-another-hot-take-on-folders-versus-tags/
* https://fortelabs.com/blog/para/
* https://forum.obsidian.md/t/cataloging-classification-information-science-pkms-and-you/10071