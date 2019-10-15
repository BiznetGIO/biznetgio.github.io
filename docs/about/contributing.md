# Contributing to BiznetGio Docs

---

## Quickstart

- Install dependencies

    ``` python
    pip install -r requirements.txt
    ```

- Make your desired changes

- Review your changes with

    ``` python
    mkdocs serve
    ```

- Make pull request


## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

## Deploy documentation

!!! info
    We use two branch. `source` to hold all the source contents, and `master` for
    compiled contents.

``` python
mkdocs gh-deploy --config-file ./mkdocs.yml --remote-branch master
```

Or you can use CI automation:

``` yaml
deploy:
    provider: pages
    skip_cleanup: true
    github_token: $github_token
    local_dir: site
    target_branch: master
    on:
        branch: source
```

`$github_token` is the token than you generate from Github with the scope of
`public_repo` and `repo_deployment`. Then put that token into your CI platform
(such as Travis).
