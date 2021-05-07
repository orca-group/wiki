# Endpoint Documentation

Every endpoint on a standard instance is prefixed by `/api/v1`.

All JSON responses on a standard instance follow a common format and are snake_cased.

On `spaceb.in` &mdash;the Spacebin official instance&mdash;, API routes are available at `spaceb.in/api/v1` (including prefix).

Responses which only return plain text follow no enforced format and can contain any values. When a request body is present in documentation, it is more often than not JSON.

The format:

```json
{
  "status": 000, // HTTP status code.
  "payload": {
    // The response's content, is an empty object if an error is present.
    ...
  },
  "error": "" // Error message.
}
```

## POST `/documents/`

### Request

```json
{
  "content": "...", // The document's content.
  "extension": "...", // The document's file type/extension.
}
```

#### Content field

The value of the `content` field corresponds to the value of the paste and is required in all requests.

Additionally, instances set a max length for this value. By default and on `spaceb.in` the max length is set to 400,000 bytes or ~390KB. Contact your instance's administrator or consult it's documentation to find the value of the max length of documents on it.

#### Extension Field

The `extension` field is used to set the file type of the paste and is required in all requests. Since this field will often be used for syntax highlighting purposes it is important that the value passed accurately corresponds to the format of the text in the file. 

The value of this field must follow a specific value, that being one of the following:

* `python`
* `javascript`, `jsx`
* `typescript`, `tsx`
* `go`
* `kotlin`
* `cpp`, `csharp`, `c`, `objc`
* `sql`
* `scala`
* `haskell`
* `shell-session`
* `bash`
* `powershell`
* `php`
* `asm6502`
* `julia`
* `perl`
* `crystal`
* `json`, `yaml`, `toml`
* `rust`
* `ruby`
* `java`
* `markdown`
* `markup` (Catch-all for `html`, `xml`, `svg`, `atom`, `rss`, `mathml`, `ssml`)
* `css`

Additionally, a value of `none` may be used for any paste that does not have/want an extension.

### Response

```json
{
  "status": 201,
  "payload": {
    "id": "...", // The unique ID of the document.
    "content_hash": "...", // A base64 representation of the document's content. Useful for content validation.
  },
  "error": ""
}
```

## GET `/documents/:id/`

### Request

* `:id`: The document's unique ID.

### Response

```json
{
  "status": 201,
  "payload": {
    "id": "...", // The document's unique ID.
    "content": "...", // The document's content.
    "extension": "...", // The document's file type/extension.
    "created_at": 0000000000, // The UNIX timestamp at the time the document was created.
    "updated_at": 0000000000 // The UNIX timestamp at the time the document was last updated, usually the same as `created_at`.
  },
  "error": ""
}
```

## GET `/documents/:id/raw`

### Request

* `:id`: The document's unique ID.

### Response

The response of this endpoint is just the plain text content of the document. If an error occurs while retrieving the document a JSON response will be sent back instead with the `error` field populated.
