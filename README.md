# Major Tagging Action

## Purpose

GitHub action to move a major tag (e.g. v0, v1, ...) to the latest tag.

For example, when v2.0.3 is created and pushed the v2 tag will be moved from v2.0.2 tag commit to the commit of v2.0.3 tag. If it doesn't exist, major tag will be created.

It's especially useful for GitHub reusable workflow versioning ou GitHub Action versioning last major tag will always point on last tag.

## Howto use

If your version is prefixed with a 'v':

```yaml
name: Move a major tag to the latest release

on:
  push:
    tags:
      - v[0-9]+.[0-9]+.[0-9]+

jobs:
  tag:
    name: Move major tag
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: lupise/major-tagging-action@v1
```

If your version has no prefix:

```yaml
name: Move a major tag to the latest release

on:
  push:
    tags:
      - [0-9]+.[0-9]+.[0-9]+

jobs:
  tag:
    name: Move major tag
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: lupise/major-tagging-action@v1
```
