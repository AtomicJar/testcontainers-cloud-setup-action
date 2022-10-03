# Testcontainers Cloud action

This action downloads and run the agent. `TC_CLOUD_TOKEN` environment variable is required.

## Example usage

```yaml
name: Java CI with Maven

on:
  push:
    branches: [ main ]

permissions:
  contents: read

env:
  TC_CLOUD_TOKEN: ${{ secrets.TC_CLOUD_TOKEN }}

jobs:
  build:
    name: "Run checks"
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v3
      - name: Setup testcontainers-cloud
        uses: atomicjar/testcontainers-cloud-setup-action@main
      - uses: actions/setup-java@v3
        with:
          java-version: '8.0.345'
          distribution: temurin
      - name: Build with Maven
        run: mvn -V -B verify
```

### Define the Operative System
```
    - name: Setup testcontainers-cloud
        uses: atomicjar/testcontainers-cloud-setup-action@main
        with:
          os: windows
        
```