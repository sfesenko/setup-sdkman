# Setup kscript Action
A simple Github action that makes kscript (and kotlin) available for your GitHub actions workflow.
It uses [sdkman](https://sdkman.io) and doesn't touch the installed JREs.

# Usage

```yml
on: [pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v2
      - name: set up java
        uses: actions/setup-java@v1
        with:
          java-version: 11
      - name: setup kscript
        uses: sfesenko/setup-kscript@v0.0.0
      - name: run kscript
        run: kscript 'println("Hello, world!")'
```
