# Installing the CLI

Installing the Spacebin CLI is very easy. You have two options for your install method:

* Via Cargo (Recommended)
* From Source

## Installing via Cargo (Recommended)

**Requires:**
* Rust tool chain

Simply type the following:

```console
$ cargo install spacebin-cli
```

After running, (providing everything went correctly) the Spacebin CLI will now be available in your terminal under `space`. Feel free to test by running `space -v`.

## Compiling from source

**Requires:**
* Git
* Rust tool chain

```console
$ git clone https://github.com/spacebin-org/cli.git spacebin-cli
$ cd spacebin-cli
$ cargo install --path .
```

When running `space -V`, you should now get something similar to the following:

```
spacebin-cli 0.2.2
```
