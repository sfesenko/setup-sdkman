# Setup Sdkman Action
A simple Github action, that makes [Sdkman](https://sdkman.io)'s managed SDKs available for your GitHub actions workflow.
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

# Notes

- Action must be used only once per workflow