# GitHub Actions for nodenv

This repo provides multiple nodenv-related GitHub Actions.

## setup-nodenv

This action sets up nodenv such that it is available in subsequent steps.

```yml
steps:
  - uses: nodenv/actions/setup-nodenv
```

## node-version

Determines node version via `nodenv local` and sets it as an output for use in subsequent steps.

```yml
steps:
  - uses: nodenv/actions/node-version
```

### usage with setup-node

Example demonstrating combined use with GitHub's own setup-node action:

```yml
steps:
  - uses: nodenv/actions/node-version
    id: nodenv
  - uses: actions/setup-node@v1
    with:
      node-version: '${{ steps.nodenv.outputs.node-version }}'
  - run: node -v
```
