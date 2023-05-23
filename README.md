# AI Pipeline
Reusable github workflows for AI projects

![example workflow](https://github.com/localagi/ai-pipeline/actions/workflows/publish-docker.yml/badge.svg?branch=main)

![example workflow](https://github.com/localagi/ai-pipeline/actions/workflows/test-service.yml/badge.svg?branch=main)

This contains a collection of [reusable workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) crafted for AI projects.

See where it is used at [about localAGI](https://github.com/localagi)

# Supported features

* [Docker build and publish pipeline](#docker)
* [Jupyter notebook test pipeline (TBD)](#jupyter)
 
<a name="docker	"></a>
## Docker build and publish pipeline

Reliably builds and publishes your AI-project wrapped in docker containers on various registries.

`uses: localagi/ai-pipeline/.github/workflows/operation-docker-build-publish.yml@v2`

### Placement of source and dockerfiles

#### Context for docker build
In order of precedence
* `inputs.context` - will be directly mapped to context of `docker/build-push-action`, could be a plain git repo also
* `inputs.context-repository` - git repository of complex remotes. Full support of submodules etc
* `inputs.context-cache` - a cache key to restore files from (untested)

##### git references for remote sources

* `inputs.context` - in form of `https://github.com/my_user/my_repo.git#ref`
* `inputs.context-repository-ref` - use with `inputs.context-repository` in form of `ref`

#### Dockerfile for docker build
Defaults to `Dockerfile`

* `inputs.dockerfile` - can be any relative, absolute or `https://` path

#### Support matrix Dockerfile x context directory

|                       | **local source** `inputs.context` | **remote source** `inputs.context` | **complex remote source** `inputs.context-repository` |
| ---- | ---- | ---- | ---- |
| **local Dockerfile  `inputs.dockerfile`** | :ballot_box_with_check:          | :ballot_box_with_check:             | :ballot_box_with_check: |
| **remote Dockerfile `inputs.dockerfile`** | :ballot_box_with_check:          | :ballot_box_with_check:             | :ballot_box_with_check: |

### Caching
Defaults to `gha` cache for docker builds
* `inputs.cache-from`
* `inputs.cache-to`

Set to `${{ null }}` to disable

### More build space
Clean up the disk beforehand for large builds

* `inputs.pre-free-disk-space`

Set to `true` to enable


### Docker Registry selection
All enabled by default
* `inputs.registry-dockerhub-enable`
* `inputs.registry-github-enable`

### Custom dockerhub registry README
Defaults to `README.md`
* `inputs.registry-readme`
Supports getting a remote readme from `https://`

<a name="docker	"></a>
## Jupyter test pipeline
Easily test the resulting containers against your test-notebook

`uses: localagi/ai-dedicated-workflows/.github/workflows/operation-test-with-jupyter.yml@v2` - 

**TBD**

### Example
For a service using the test pipeline, see here: [localAGI/AGiXT-docker](https://github.com/localagi/AGiXT-docker)

------------------------------
------------------------------
# Template for Service Model Card about built service
------------------------------
------------------------------

# Service-name-docker

Sophisticated docker builds for parent project [**This-project**](https://github.com/**This-project**). 

![example workflow](https://github.com/localagi/ai-dedicated-workflows/actions/workflows/publish-docker.yml/badge.svg?branch=main)

Easy setup. Compatible. Tweakable. Scaleable.

#### Supported platforms
`amd64`, `arm64`

#### Supported versions
Containers follow the version scheme of the parent project

`main` (default), `0.2.9`, `0.2.5`, etc.

See [Releases](../../releases)

## Prerequisites

* `docker` and `docker compose` are available on your system

##### NVIDIA card required
These containers require `nvidia-container-toolkit` installed and reboot

## Run

Short description what it does
The following wil get all **This-project** images and do something

* get `docker-compose.yml` (clone repo, copy or else) 
* Run `docker compose up`
* wait for model download (~7GB)
* open/refresh `http://localhost:3000` 

### Runtime options
Environment variables to set for the specific service

#### version selection `PROJECT_VERSION`
Prepend, e.g. `PROJECT_VERSION=1.2.3`

#### Another runtime option

foo bar baz

### Get the latest builds / update
`docker compose pull`

### Cleanup
`docker compose rm`

## Contributing

When there is a new version and there is need of builds or you require the latest main build, feel free to open an issue

## Problems?

Open an issue on the [Issue Tracker](../../issues)

## Limitations
We cannot support issues regarding the base software. Please refer to the main project page mentioned in the second line of this card.
