# Developer Standard

---

## Style Guide

### Python

We use [black](https://github.com/psf/black) for code formatter, and
[pre-commit](https://pre-commit.com/) for it's
[automation](https://github.com/psf/black#version-control-integration). Read
[Black editor integration](https://github.com/psf/black#editor-integration) for
more information.

To enforce PEP-08 standard we use [flake8](http://flake8.pycqa.org/en/latest/),
and integrate it's plugin to our code editor.

## Commit Message Guide

We use the pattern bellow for commit message:

``` bash
Add: <your commit message>
Update: <your commit message>
Remove: <your commit message>
Fix: <your commit message>
```
- `Add`: for feature additions.
- `Update`: for feature update.
- `Remove`: for feature dropping, etc.
- `Fix`: for bug fixing, style, etc.

## Code standard

We adhere to [clean code](https://www.oreilly.com/library/view/clean-code/9780136083238/)
ideology. Most common things such as:

- meaningless / ambigous variable name: `x`, `y`, `ymdstr`.
