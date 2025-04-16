# OpenHEXA Push Pipeline Github Action Example
Minimal example of how to use the [OpenHEXA Push Pipeline Github Action](https://github.com/BLSQ/openhexa-push-pipeline-action) to push a pipeline to OpenHEXA.

## How to use this action
To use this action, you need to add the following step to your workflow:

```yaml
- name: Push pipeline to OpenHEXA
  uses: blsq/openhexa-push-pipeline-action@v1
  with:
    workspace: <insert-workspace-slug>
    pipeline: <insert-pipeline-code>
    token: ${{ secrets.OH_TOKEN }}
    
    path: <insert-path-to-pipeline> (optional)
    versionName: <insert-version-name> (optional)
    versionDescription: <insert-version-description> (optional)
```

### Required parameters
You have to replace `<insert-workspace-slug>` with the slug of your workspace. 
You can find it in the URL of your workspace: `https://app.openhexa.org/workspaces/<workspace-slug>`. 

You have to replace `<insert-pipeline-code>` with the code of the pipeline you want to push.
You can find the code of the pipeline in the OpenHEXA web interface on `https://app.openhexa.org/workspaces/<workspace-slug>/pipelines/<pipeline-code>`.

You also need to provide a token to authenticate with the OpenHEXA API. 
You can get this token in the OpenHEXA web interface on `https://app.openhexa.org/workspaces/<workspace-slug>/pipelines/`.

### Optional parameters

You can also provide the following optional parameters:

- `path`: The path to the pipeline file. Default is `.`
- `versionName`: The name of the version. Default is no name
- `versionDescription`: The description of the version. Default is no description

