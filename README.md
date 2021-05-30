# Wiki

> 📖🚀 **The Spacebin Wiki** powered by mdBook

## Building

**Prerequisites**

* [`Rust`](https://www.rust-lang.org/)
* [`mdBook`](https://crates.io/crates/mdbook)

```sh
$ rm -rf book  # Cleans output directories.
$ mdbook build # Builds static files for usage in production environments.
$ mdbook serve # Rebuilds on file change & runs a local server on port 3000. Useful when developing.
```

## `assets/` Folder

The project's asset folder contains all of the graphical resources used by Spacebin in it's projects and official sites.

Like the wiki itself, everything in this folder is available under Creative Commons Attribution-ShareAlike 4.0. For more information see [Licensing & Copyright](#licensing--copyright).

You may have noticed the `github-banner.png` file in the `spacebin-text-logo` folder. This image is to be used for official header images of Spacebin repositories. The only difference between it and other logo images with text is its padding.

## Contributors

* [Luke Whrit <lukewhrit@pm.me>](https://github.com/lukewhrit)

## Licensing & Copyright

This wiki and all of it's content are available under the Creative Commons Attribution-ShareAlike 4.0 license. A copy of the license can be found in the [`LICENSE`](LICENSE) text file in the root of this repository.
