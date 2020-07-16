# Endpoint Documentation

Every endpoint on a standard instance is prefixed by `/api/v1`.

All JSON responses on a standard instance follow a common, defined format.

Responses which only return plain text follow no enforced format and can contain any values. When a request body is present in documentation, it is more often than not JSON.

The "common, defined" format:

```json
{
  "status": 000,
  "payload": {
    ... 
  },
  "error": ""
}
```

**Properties:**
* `status (Number)`: An always present number containing the request's HTTP status code.
* `payload (Object)`: When a request succeeds this field contains any information returned by the request.
* `error (String)`: If present, a string which includes a message describing the error.

## `GET /document/<id>`

### Route Parameters

* `id (String)`: ID of the document you are requesting.

### Response Body

The body returned by this request is the same of the document in the database.

```json
{
  "id": "...",
  "content": "...",
  "dateCreated": "1970-01-01T05:00:00.000Z",
  "extension": "..."
}
```

* `id (String)`: The unique identifier of the document.
* `content (String)`: The content of the document.
* `dateCreated (ISO Date)`: The date in ISO format of when the document was created.
* `extension (String)`: The file format/extension the document's **content** is. Most commonly `text`.

## `GET /document/<id>/verify`

**Warning:** This endpoint may soon be removed, in favor of just making a GET document request.

### Route Parameters

* `id (String)`: The unique identifier of the document you are requesting.

### Response Body

```json
{
  "exists": true | false
}
```

* `exists (Boolean)`: Whether the document exists or not. true if exists, false if it doesn't.

## `GET /document/<id>/raw`

### Route Parameters

* `id (String)`: ID of the document you are requesting.

### Response Text

The plain text **content** with the document, including new lines.

## `POST /document/`

### Request Body

```json
{
	"content": "..."
}
```

* `content (String)`: The content of the document to insert. Newlines must be replaced with the string `\n` as to preserve JSON validity.

### Response JSON Body

```json
{
  "id": "...",
  "contentHash": "..."
}
```

* `id (String)`: The ID of the document inserted.
* `contentHash (String)`: A base 64 hash of the document's content.
