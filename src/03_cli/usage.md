# Spacebin CLI Commands

**This document covers version `0.2.2` of the CLI.**

## Flags

* `--debug`: Debugging features
* `-h, --help`: Prints help information
* `-V, --version`: Prints current version

## Options

### `-u, --upload <file>`

Path of the file to upload to the configured instance.

### `-p, --port <port (default: 443)>`

Port on where the server instance is hosted.

### `-i, --instance <url (default: api.spaceb.in)>`

Host address on where the server instance is hosted.

### `--result-url <url (default: spaceb.in)>`

URL returned by the CLI after a successful upload.

### `--spinners <true | false (default: true)>`

Controls whether the CLI shows fancy spinners while uploading.

## Environment Variables

### `SPACEBIN_INSTANCE`

* **CLI Option:** `-i, --instance`
* **Default:** `api.spaceb.in`

Defines the API instance that files will be uploaded to.

### `SPACEBIN_RESULT_URL`

* **CLI Option:** `--result-url`
* **Default**: `spaceb.in`

Defines the URL that will be returned after a successful upload.

### `SPACEBIN_PORT`

* **CLI Option**: `-p, --port`
* **Default:** 443

Defines the TCP port that `space` uses when communicating with an instance. 

### `SPACEBIN_USER_SPINNERS`

* **CLI Option**: `--spinners`
* **Default**: `true`

Changes if the command will display fancy spinners while uploading files.
