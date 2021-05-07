## Commit guidelines

Commits all follow the same basic structure:

```
action(scope): message
```

This structure may seem similar to you if you've ever contributed to: Angular, Spirit, or any other project that follows Conventional Commits.

### `action`

The action can be either `modify`, `rename`, `create`, `delete`.

### `scope`

A path-like string representing the location of the file.

* If it's a document it should follow a similar format to `{chapter}/{document_title}`.
* If it's a document but is not in a chapter, simply call the chapter "book".
* If it's a file that is not a document just include the file name. 
* If it's a github workflow file call the chaper "workflows".

* `message` is a string detailing what changed. 

## Code format

Generally just follow the structure of existing documents

New chapters/folders should be numbered and include the name of the chapter, something like: `04_notes`.
