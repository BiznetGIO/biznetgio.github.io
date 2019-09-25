# Developer Standadrd

---

## Style Guide

### Python

We use [black](https://github.com/psf/black) for code formatter, and
[pre-commit](https://pre-commit.com/) for it's
[automation](https://github.com/psf/black#version-control-integration)

To enforce PEP-08 standard we use [flake8](http://flake8.pycqa.org/en/latest/),
and integrate it's plugin to our code editor.

In near future we will automate this process in our CI/CD step.

## Commit Message Guide

We use the pattern bellow for commit message:

``` bash
Add: <your commit message>
Drop: <your commit message>
Fix: <your commit message>
... : <your commit message>
```
Some other keyword we use: `Bump`, `Refactor`, `Reformat`, and `Reword`

## Code standard

We adhere to clean code ideology. So we avoid things like:

- meaningless / ambigous variable name: `x`, `y`, `ymdstr`.
