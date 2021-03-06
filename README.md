[![Test](https://github.com/sfesenko/setup-sdkman/actions/workflows/test-action.yaml/badge.svg)](https://github.com/sfesenko/setup-sdkman/actions/workflows/test-action.yaml)
[![Test-self-hosted](https://github.com/sfesenko/setup-sdkman/actions/workflows/test-action-selfhosted.yaml/badge.svg)](https://github.com/sfesenko/setup-sdkman/actions/workflows/test-action-selfhosted.yaml)
# Setup Sdkman Action
A simple Github action, that makes [Sdkman](https://sdkman.io)'s managed SDKs available for your GitHub actions workflow.

Installed dependencies are cached via `actions/cache`, however, it is used for gihub-hosted runner only, because for a self-hosted runner it works pretty slow.

# Usage

```yml
on: [pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v2
      - name: setup kscript
        uses: sfesenko/setup-sdkman@v0
          deps: kscript
      - name: run kscript
        run: kscript 'println("Hello, world!")'
```

All installed sdks will be added to `$PATH` automatically, but in order to make `sdk` command available, sdkman's init script must be referenced explicitly:
```yml
jobs:
  my-job:
    runs-on: ubuntu-latest
    steps:
      - uses: sfesenko/setup-sdkman@v0
      - run: |
          source ~/.sdkman/bin/sdkman-init.sh
          sdk version
```
