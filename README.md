# Manifest

## Dispatch

You can sent by POST three modes with data JSON for to replace image in the kustomizes

### Simple JSON

A simple dispath to sent params to edit a kustomize file

```json
{
    "event_type": "change_image",
    "client_payload": {
        "repository": "<REPOSSITORY_NAME>",
        "branch": "<BRANCH>",
        "image": "luuna/<REPOSSITORY_NAME>:<TAG_IMAGE>",
        "actor": "<COMMIT_AUTHOR>"
    }
}
```

Params:
- repository: name repository
- branch: branch
- image: new image built
- actor: who editing repository

### With Specific PATH to Image

In this case you can set an absoulte path to define to replace image in kustomize file.
Path is optional, if it's not defined, the default path is by default 

```json
{
    "event_type": "change_image",
    "client_payload": {
        "repository": "<REPOSSITORY_NAME>",
        "branch": "<BRANCH>",
        "image": "luuna/<REPOSSITORY_NAME>:<TAG_IMAGE>",
        "actor": "<COMMIT_AUTHOR>",
        "path": "<ABSOLUTE_PATH_KUSTOMIZE_FILE>"
    }
}
```

Params:
- repository: name repository
- branch: branch
- image: new image built
- actor: who editing repository
- path: absolute path, any path within manifests repo 

Example case: Client-API

### Multi images with JSON

In this case you can set multi images with param images, this params is a JSON.

```json
{
    "event_type": "change_image",
    "client_payload": {
        "repository": "<REPOSSITORY_NAME>",
        "branch": "<BRANCH>",
        "images": "{\"<TAG>\": \"<IMAGE>\", \"<TAG>\": \"<IMAGE>\"}",
        "actor": "<COMMIT_AUTHOR>",
        "path": "<ABSOLUTE_PATH_KUSTOMIZE_FILE>" #THIS IS OPTONAL
    }
}
```

### With Specific Brand into Image

In this case you can set special brand to define to replace into image in kustomize file.
Brand is optional, if it's not defined, this will not considered

```json
{
    "event_type": "change_image",
    "client_payload": {
        "repository": "<REPOSSITORY_NAME>",
        "branch": "<BRANCH>",
        "image": "luuna/<REPOSSITORY_NAME>-<BRAND>:<TAG_IMAGE>",
        "actor": "<COMMIT_AUTHOR>",
        "brand": "<SEPECIAL_BRAND>"
    }
}
```

Params:
- repository: name repository
- branch: branch
- image: new image built
- actor: who editing repository
- brand: specify name of deploy image

Example case: Web-Client

## Repository Dispatch

You can sent by POST with data JSON for to replace annotation for deployments in the kustomizes

```json
{
    "event_type": "restart_deploy",
    "client_payload": {
        "repository": "<REPOSSITORY_NAME>",
        "branch": "<CURRENT_BRANCH>",
        "repo_from": "<REPOSSITORY_DESTINATION>",
        "restarted": "<RESTARTED_TIME>",
        "actor": "<COMMIT_AUTHOR>"
    }
}
```

Params:
- repository: name repository
- branch: branch
- repo_from: repository destination to replace annotation with timestamp
- restarted: timestamp to execute job
- actor: who editing repository

Example case: MS-Client-Zecore to Redeploy to Gateway