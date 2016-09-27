---
tags: containers
---

## Pushing multiple tags

You can push multiple tags for your container to a registry by defining
them as follows in your `internal/docker-push` step:

```
internal/docker-push:
    repository: $REPO
    tag: latest, foo, bar
    username: $DOCKER_USERNAME
    password: $DOCKER_PASSWORD
```

A good best practice is to use the `commit` and `branch` [environment variables](/docs/environment-variables/index.html) 
available in your Wercker pipelines such as:

```
internal/docker-push:
    repository: $REPO
    tag: latest, $WERCKER_GIT_COMMIT, $WERCKER_GIT_BRANCH
    username: $DOCKER_USERNAME
    password: $DOCKER_PASSWORD
```

This allows for a good versioning scheme for your containers enabling easy look-up when things break.
