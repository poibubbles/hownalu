https://flet.dev/docs/guides/python/large-lists#batch-updates

It looks like `page.update()` is keeping track of how many controls have been added between `update()`s. So scrollability seems to be a consequence of `update()` batch sizes, and that scrolling calls to stage an upcoming or nearby batch from an existing cache that was (already) populated during the `for` loop.

Or something.