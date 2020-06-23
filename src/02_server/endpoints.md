# Endpoint Documentation

Every endpoint on a standard instance is prefixed by `/api/v1`.

All requests are JSON, therefore they must all include a `Content-Type` header with a value of `application/json`.

## `GET /document/<id>`

### Request Parameters

* `id (type: String)`
	* **Description**: ID associated with document.
	* **Required:** True
	* **Length:** Set in Config (Default: 12)

### Response Body

```json
{
	"id": "...",
	"content": "...",
	"dateCreated": "..."
}
```

* `id (type: String)`
	* **Description:** ID associated with document.
	* **Length:** Set in Config (Default: 12 chars)
	* **Notes:** Will always be the same as the key parameter in request body.
* `content (type: String)`
	* **Description:** The content of the requested document.
	* **Max Length:** Set in Config (Default: 400,000 chars)
	* **Min Length:** 2 chars
	* **Notes:** New lines are encoded with a `\n`
* `dateCreated (type: String/Date)`
	* **Description:** The timestamp the document was created.

## `POST /document`

### Request Body

```json
{
	"content": "..."
}
```

* `content (type: String)`
	* **Description:** The content of the requested document.
	* **Max Length:** Set in Config (Default: 400,000 chars)
	* **Min Length:** 2 chars

### Response Body

```json
{
	"id": "...",
	"content": "..."
}
```

* `id (type: String)`
	* **Description:** Key/id associated with document.
	* **Length:** Set in Config (Default: 12 chars)
* `content (type: String)`
	* **Description:** The content of the requested document.
	* **Max Length:** Set in Config (Default: 400,000 chars)
	* **Min Length:** 2 chars
	* **Notes:** New lines are encoded with a `\n`. Will always be the same as the key parameter in request body.

## `POST /verify`

Returns status code 200 or 404 depending on if the `id` parameter exists in the database.

### Request Body

```json
{
	"id": "..."
}
```

* `id (type: String)`
	* **Description:** ID associated with document.
	* **Length:** Set in Config (Default: 12 chars)
	* **Notes:** Will always be the same as the key parameter in request body.

### Response Body

None.

## `POST /document/<id>/raw`

Returns the Plain Text content of a document object with the id `<id>`

### Request Parameters

* `id (type: String)`
	* **Description:** ID associated with document.
	* **Length:** Set in Config (Default: 12 chars)
	* **Notes:** Will always be the same as the key parameter in request body.

### Response Body

Returns the `Plain Text` variant of a document's content field.
