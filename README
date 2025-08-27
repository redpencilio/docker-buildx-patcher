# Docker Buildx Patcher

This repository provides patches for the [Docker Buildx Woodpecker CI plugin](https://woodpecker-ci.org/plugins/docker-buildx) to centralize and simplify multi-architecture builds and registry mirror configuration in Woodpecker CI workflows. Changes to builders can now be made in one place, rather than updating many repositories individually.

## Features

- **Default Builders:** Automatically sets default builders, enabling multi-arch builds without requiring explicit configuration in every workflow.
- **Default Registry Mirror:** Sets a default Docker registry mirror.
- **Per-Server Overrides:** Allows overriding default builder and registry mirror settings for individual Woodpecker servers.
- **Drop-in replacement**: Works as a drop-in replacement for the existing Docker Buildx plugin.

## Images

Patched images are built daily using Woodpecker CI and have the same version as label as the original plugin.

## Example workflow

An SSH key with access to the builders is required.

```diff
 steps:
   build:
-    image: woodpeckerci/plugin-docker-buildx:latest
+    image: redpencil/plugin-docker-buildx:latest
     settings:
       repo: "${CI_REPO_OWNER}/${CI_REPO_NAME}"
       tags: latest
+      platforms: linux/amd64,linux/arm64
       username:
         from_secret: docker_username
       password:
         from_secret: docker_password
+      ssh_key:
+        from_secret: ssh_key
 when:
   - event: push
     branch: [master, main]
```
