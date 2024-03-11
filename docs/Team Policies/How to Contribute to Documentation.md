# How to Contribute to Documentation

We use MKDocs to generate static sites from simple markdown. Simply edit or create new Markdown (`.md`) files as needed. 

(Note: Make sure they have the `.md` extension! Editors like VSCode may detect the formatting in the file and treat them as markdown, but MKDocs does not.)

You don't need to install it, simply pushing to the main branch will trigger a redeploy.

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.