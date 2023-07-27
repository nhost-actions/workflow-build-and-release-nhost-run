# workflows

Collection of workflows for github actions. You can use them as is or use them as reference to build your own.

## build-and-release-nhost-run.yaml

This workflow builds a docker image, pushes it to the Nhost registry and deploys an [Nhost Run](https://nhost.io/product/run) service.

For details about supported arguments and secrets check [.github/workflows/build-and-release-nhost-run.yaml](.github/workflows/build-and-release-nhost-run.yaml).

### Example

``` yaml
---
name: "Release to production"
on:
  push:
    branches:
      - 'main'

jobs:
  deploy:
    uses: nhost-actions/workflows/.github/workflows/build-and-release-nhost-run.yaml@v1
    with:
      IMAGE: ${{ vars.IMAGE }}:${{ github.sha }}
      SERVICE_ID: ${{ vars.SERVICE_ID }}
    secrets:
      PAT: ${{ secrets.PAT }}
```

For a more complex example you can head to [https://github.com/nhost/nhost-run-hello-world](https://github.com/nhost/nhost-run-hello-world).
