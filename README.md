# ai-dedicated-workflows
Reusable workflows for AI

# implemented at
See [AI-workflow network dependants](../../network/dependents)
and [localAGI Profile](https://github.com/localagi)

------------------------------
------------------------------
# Template for Service Model Card about built service
------------------------------
------------------------------

# Service-name-docker

Sophisticated docker builds for parent project [**This-project**](https://github.com/**This-project**). 

![example workflow](https://github.com/localagi/ai-dedicated-workflows/actions/workflows/publish-docker.yml/badge.svg)

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

When there is a new version of **This-project** or you require the latest main build, feel free to open an issue

## Problems?

Open an issue on the [Issue Tracker](../../issues)

## Limitations
We cannot support issues regarding the base software. Please refer to the main project page mentioned in the second line of this card.
