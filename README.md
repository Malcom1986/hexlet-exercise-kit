# hexlet-exercise-kit

[![Main](https://github.com/hexlet/hexlet-exercise-kit/actions/workflows/main.yml/badge.svg)](https://github.com/hexlet/hexlet-exercise-kit/actions/workflows/main.yml)

This is a complete kit for teachers who want to create exercises on the Hexlet platform.

## Requirements

* Docker
* Node.js
* Make
* Ubuntu, macOS or WSL (for Windows)

## Setup

```bash
git clone git@github.com:Hexlet/hexlet-exercise-kit.git

cd hexlet-exercise-kit
make setup
```

If you have access to clone Hexlet repositories:

* create a personal access token on this page: [https://gitlab.hexlet.io/-/profile/personal_access_tokens](https://gitlab.hexlet.io/-/profile/personal_access_tokens)
* add created token to *.env* file

```
GHORG_GITLAB_TOKEN=<token>

# Adjust this value for faster or slower speed of repositories download
PARALLEL=4
```

```bash
make clone

# if your .ssh catalog has specific path:
make clone SSH_KEYS_PATH=/specific/path/to/your/.ssh
```

For pulling into cloned repos:

```bash
make clone
```

## Using hexlet linters

```bash
# install/update all hexlet linters
make update-hexlet-linters
# install/update one hexlet linter. For example, eslint
make update-hexlet-linter L=eslint
```

## Run exercise

```bash
cd <path/to/exercise/catalog>
make build # build exercise container
make start # run exercise and listen port 80
make test # run tests
make lint-js # run linter
make lint-hexlet-js # check exercise with linter, as in production
```

For frontend exercise after `make start` open [http://localhost:80](http://localhost:80) in your browser.

```bash
make stop # stopped container
```

## Copy a course from Code-Basics to Hexlet

```bash
make copy-from-cb I=path-to-source O=path-to-destination
```

## Run markdown linter

Add `Makefile` in the course directory:

```makefile
include ../../../course.mk
```

and run:

```bash
make markdown-lint # view error list
make markdown-lint-fix # fix errors
```

## New stuff

```bash
mkdir -p exercises/ru/course-<name>/<lesson-name>_exercise
```

## Run LanguageTool

* Install LanguageTool for your code editor. For example VS Code [LanguageTool Linter](https://marketplace.visualstudio.com/items?itemName=davidlday.languagetool-linter)
* Set URL of your LanguageTool server. Defaults to localhost on port 8081
* Run LanguageTool server `make start-languagetool`
* Stop LanguageTool server `make stop-languagetool`

## Troubleshooting

```text
Unable to find image 'hexlet/gitlab-downloader:latest' locally
docker: Error response from daemon: pull access denied for hexlet/gitlab-downloader, repository does not exist or may require 'docker login': denied: requested access to the resource is denied.
See 'docker run --help'.
```

Build downloader `make build-downloader` or see [setup](#setup) or fresh installation
