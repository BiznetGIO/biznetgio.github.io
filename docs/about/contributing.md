# Contributing to BiznetGio Docs

---

## Quickstart

- install mkdocs and related depedencies

``` python
pip install mkdoc mdx_gh_links 
```
- clone the repository then make your desired changes

- review your changes with

``` python
mkdocs serve
```

- make the pull request.


## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

## Pushing Compiled Docs

``` python
mkdocs gh-deploy --config-file ./mkdocs.yml --remote-branch master
```

