# OpenHEXA Push Pipeline Github Action Example
Minimal example of how to use the [OpenHEXA Push Pipeline Github Action](https://github.com/BLSQ/openhexa-push-pipeline-action) to push a pipeline to OpenHEXA.

## How to start automated pushing of pipelines to OpenHexa

1. Create a new repository on GitHub.
2. Create a new file in the root of your repository called `.github/workflows/push-pipeline.yml`.
3. Copy the following code into the `push-pipeline.yml` file:
```yaml
name: Push pipeline to OpenHEXA
on:
  push:
    branches:
      - main
jobs:
    push-pipeline:
    runs-on: ubuntu-latest

    steps:
      - name: Push pipeline on OpenHEXA
        uses: blsq/openhexa-push-pipeline-action@v1.0.0
        with:
          token: ${{ secrets.OH_TOKEN }}
          workspace: openhexa-push-pipeline-action-example <----- REPLACE WITH YOUR WORKSPACE SLUG
          pipeline: example <----- REPLACE WITH YOUR PIPELINE CODE
```
4. Replace `openhexa-push-pipeline-action-example` with the slug of your OpenHEXA workspace. You can find it in the URL of your workspace: `https://app.openhexa.org/workspaces/<workspace-slug>`.
5. Replace `example` with the code of the pipeline you want to push. You can find the code of the pipeline in the OpenHEXA web interface on `https://app.openhexa.org/workspaces/<workspace-slug>/pipelines/<pipeline-code>`.
6. Create a new secret in your GitHub repository called `OH_TOKEN` and set its value to the token you got from OpenHEXA. You can get this token in the OpenHEXA web interface on `https://app.openhexa.org/workspaces/<workspace-slug>/pipelines/`.
7. Push a first time manually the pipeline to OpenHexa to ensure that a pipeline with the correct code is present in OpenHexa.
8. Any push to the main branch will trigger the workflow and push the pipeline to OpenHEXA.
9. Enjoy the automation!

## Example

This repository contains a minimal example of how to use the OpenHEXA Push Pipeline Github Action.
When pushing a change to the main branch, a new version of the pipeline will be pushed to OpenHEXA.

<img width="1470" alt="Screenshot 2025-04-16 at 16 24 43" src="https://github.com/user-attachments/assets/8f20e519-df87-4484-abb6-376273362f8f" />



A link to the diff commit will be added to the version comment.

<img width="1489" alt="Screenshot 2025-04-16 at 16 24 18" src="https://github.com/user-attachments/assets/9f22c0a1-9b3c-4f7a-8a61-5ce2ec0fcd4a" />


