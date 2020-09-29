# Endpoint Documentation

Every endpoint on a standard instance is prefixed by `/api/v1`.

All JSON responses on a standard instance follow a common, defined format and are snake_cased.

Responses which only return plain text follow no enforced format and can contain any values. When a request body is present in documentation, it is more often than not JSON.

The format:

```json
{
  "status": 000, // HTTP status code.
  "payload": {
    // The response's content, null if an error is present.
    ...
  },
  "error": "" // Error message.
}
```

All keys in the response will be snake_cased.

## POST `/documents/`

### Request

```json
{
  "content": "...", // The document's content.
  "extension": "...", // The document's file type/extension.
}
```

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
