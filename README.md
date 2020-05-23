# Hugo

[![](https://images.microbadger.com/badges/image/klakegg/hugo.svg)](https://microbadger.com/images/klakegg/hugo "Get your own image badge on microbadger.com")
[![Build Status](https://travis-ci.org/klakegg/docker-hugo.svg?branch=master)](https://travis-ci.org/klakegg/docker-hugo)
[![Docker Pulls](https://img.shields.io/docker/pulls/klakegg/hugo.svg)](https://store.docker.com/community/images/klakegg/hugo)

Truly minimal Docker images for [Hugo](http://gohugo.io/) with batteries included.
These images sets `destination` during build and `bind` when started as server, otherwise no magic.


## Latest tags

Default minimal image based upon [Busybox](https://hub.docker.com/r/_/busybox/):
* Aliases: `latest`, `busybox`, `busybox-onbuild`, `onbuild`
* Hugo 0.71.0: `0.71.0-busybox`, `0.71.0`, `0.71.0-busybox-onbuild`, `0.71.0-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.71.0/dist/busybox/Dockerfile-busybox))
* Hugo 0.70.0: `0.70.0-busybox`, `0.70.0`, `0.70.0-busybox-onbuild`, `0.70.0-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.70.0/dist/busybox/Dockerfile-busybox))

Minimal image based upon [Alpine](https://hub.docker.com/r/_/alpine/):
* Aliases: `alpine`, `alpine-onbuild`, `ext-alpine`, `ext-alpine-onbuild`, `ext-nodejs`
* Hugo 0.71.0: `0.71.0-alpine`, `0.71.0-alpine-onbuild`, `0.71.0-ext-alpine`, `0.71.0-ext-alpine-onbuild`, `0.71.0-ext-nodejs` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.71.0/dist/alpine/Dockerfile-alpine))
* Hugo 0.70.0: `0.70.0-alpine`, `0.70.0-alpine-onbuild`, `0.70.0-ext-alpine`, `0.70.0-ext-alpine-onbuild`, `0.70.0-ext-nodejs` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.70.0/dist/alpine/Dockerfile-alpine))

Minimal image based upon [Alpine](https://hub.docker.com/r/_/alpine/) with [Asciidoctor](http://asciidoctor.org/) installed:
* Aliases: `asciidoctor`, `asciidoctor-onbuild`, `ext-asciidoctor`, `ext-asciidoctor-onbuild`
* Hugo 0.71.0: `0.71.0-asciidoctor`, `0.71.0-asciidoctor-onbuild`, `0.71.0-ext-asciidoctor`, `0.71.0-ext-asciidoctor-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.71.0/dist/alpine/Dockerfile-asciidoctor))
* Hugo 0.70.0: `0.70.0-asciidoctor`, `0.70.0-asciidoctor-onbuild`, `0.70.0-ext-asciidoctor`, `0.70.0-ext-asciidoctor-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.70.0/dist/alpine/Dockerfile-asciidoctor))

Minimal image based upon [Alpine](https://hub.docker.com/r/_/alpine/) with [Pandoc](https://pandoc.org/) installed:
* Aliases: `pandoc`, `pandoc-onbuild`, `ext-pandoc`, `ext-pandoc-onbuild`
* Hugo 0.71.0: `0.71.0-pandoc`, `0.71.0-pandoc-onbuild`, `0.71.0-ext-pandoc`, `0.71.0-ext-pandoc-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.71.0/dist/alpine/Dockerfile-pandoc))
* Hugo 0.70.0: `0.70.0-pandoc`, `0.70.0-pandoc-onbuild`, `0.70.0-ext-pandoc`, `0.70.0-ext-pandoc-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.70.0/dist/alpine/Dockerfile-pandoc))

Image based upon [Debian](https://hub.docker.com/r/_/debian/):
* Aliases: `debian`, `debian-onbuild`, `ext`, `latest-ext`, `ext-debian`, `ext-debian-onbuild`, `ext-onbuild`
* Hugo 0.71.0: `0.71.0-debian`, `0.71.0-debian-onbuild`, `0.71.0-ext`, `0.71.0-ext-debian`, `0.71.0-ext-debian-onbuild`, `0.71.0-ext-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.71.0/dist/debian/Dockerfile-debian))
* Hugo 0.70.0: `0.70.0-debian`, `0.70.0-debian-onbuild`, `0.70.0-ext`, `0.70.0-ext-debian`, `0.70.0-ext-debian-onbuild`, `0.70.0-ext-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.70.0/dist/debian/Dockerfile-debian))

Image based upon [Ubuntu](https://hub.docker.com/r/_/ubuntu/):
* Aliases: `ubuntu`, `ubuntu-onbuild`, `ext-ubuntu`, `ext-ubuntu-onbuild`
* Hugo 0.71.0: `0.71.0-ubuntu`, `0.71.0-ubuntu-onbuild`, `0.71.0-ext-ubuntu`, `0.71.0-ext-ubuntu-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.71.0/dist/ubuntu/Dockerfile-ubuntu))
* Hugo 0.70.0: `0.70.0-ubuntu`, `0.70.0-ubuntu-onbuild`, `0.70.0-ext-ubuntu`, `0.70.0-ext-ubuntu-onbuild` ([Dockerfile](https://github.com/klakegg/docker-hugo/blob/0.70.0/dist/ubuntu/Dockerfile-ubuntu))

*Looking for older tags? Please see the [complete list of tags](https://github.com/klakegg/docker-hugo/blob/master/doc/tags.md).*


## Using image

This image does not try to do any fancy.
Users may use Hugo [just as they are used to](https://gohugo.io/documentation/).


### Command line

Normal build:

```shell
docker run --rm -it \
  -v $(pwd):/src \
  klakegg/hugo:0.71.0
```

Run server:

```shell
docker run --rm -it \
  -v $(pwd):/src \
  -p 1313:1313 \
  klakegg/hugo:0.71.0 \
  server
```


### docker-compose

Normal build:

```yaml
  build:
    image: klakegg/hugo:0.71.0
    volumes:
      - ".:/src"
```

Run server:

```yaml
  server:
    image: klakegg/hugo:0.71.0
    command: server
    volumes:
      - ".:/src"
    ports:
      - "1313:1313"
```


### Github Actions

All versions and variants published using this repository may be used in any combination.

Simple configuration for e.g. `.github/workflows/hugo.yml`:

```yaml
name: Hugo

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v1

    - name: hugo
      uses: klakegg/actions-hugo@1.0.0
```

Find out more in [klakegg/actions-hugo](https://github.com/klakegg/actions-hugo).


### Travis CI

Simple configuration for `.travis.yml`:

```yaml
language: bash

services:
- docker

script:
- docker run --rm -i \
    -v $(pwd):/src \
    klakegg/hugo:0.71.0
```

The `bash` environment is used for faster loading before Travis is ready to trigger Docker.


## Hugo shell

A Hugo shell is made available in the Alpine/Debian/Ubuntu images (including Asciidoctor/Pandoc images).
Hugo shell is bash and Hugo completion.

To get into a shell for your site:

```shell
docker run --rm -it \
  -v $(pwd):/src \
  klakegg/hugo:0.71.0-alpine \
  shell
```


## Hugo extended edition

The extended edition is used in those images containing `ext` in the name. Except use of extended edition and additional tools are those images exactly the same as those using the normal edition.

Table of Hugo extention features and the version when images first support the feature:

| Feature       | Alpine | Debian | Ubuntu |
| ------------- | ------ | ------ | ------ |
| Hugo extended | 0.43   | 0.43   | 0.43   |
| PostCSS       | 0.56.0 | 0.43   | 0.43   |
| NodeJS        | 0.54.0 | 0.54.0 | 0.54.0 |
| Yarn          | 0.54.0 | 0.54.0 | 0.54.0 |
| Git           | 0.56.0 | 0.56.0 | 0.56.0 |
| Autoprefixer  | 0.57.0 | 0.57.0 | 0.57.0 |
| Go            | 0.68.0 | 0.68.0 | 0.68.0 |
| Babel         | 0.71.0 | 0.71.0 | 0.71.0 |

Users of [google/docsy](https://github.com/google/docsy) may use the extended images as of version 0.57.2 to build their site.


## Using an ONBUILD image

The onbuild images adds content of the folder of your Dockerfile into `/src` and builds to the `/target` (prior to `0.68.0`: `/onbuild`) folder.

Example Dockerfile for your project where the site is made into an nginx image (Docker 17.05-ce or newer):

```Dockerfile
FROM klakegg/hugo:0.71.0-onbuild AS hugo

FROM nginx
COPY --from=hugo /target /usr/share/nginx/html
```

Available arguments for `docker build`:
* HUGO_CMD - Commands passed to Hugo during build. Default *empty*
* HUGO_DESTINATION_ARG - Location of output folder. Default: `/target`
* HUGO_ENV_ARG - Selecting environment ("DEV"/"production"). Default: `DEV`


## Using Pandoc

Hugo images with Pandoc support are made available for users wanting to use Pandoc in combination with Hugo.

[Hugo triggers Pandoc](https://gohugo.io/content-management/formats/#additional-formats-through-external-helpers) with `pandoc --mathjax`.
Some users may want to use other arguments, so to accommodate such a need is an alias `pandoc` created with the content of `HUGO_PANDOC` (default: `pandoc-default`) upon initiation.
The normal `pandoc` executable is renamed to `pandoc-default` to allow for later introduction of `pandoc-citeproc` if needed.

Example of explicit setting `pandoc` alias:

```shell
docker run --rm -it \
  -v $(pwd):/src \
  -e HUGO_PANDOC="pandoc-default --strip-empty-paragraphs" \
  klakegg/hugo:0.71.0-pandoc
```


## Overriding entrypoint

Those wanting to override entrypoint in the image may easily do so.

Default entrypoint is `hugo`, a small script wrapping the official Hugo software. If you want to use the official software without any wrapping may you use `hugo-official` as entrypoint.

On command line using `--entrypoint`:

```shell
docker run --rm -it \
  -v $(pwd):/src \
  --entrypoint hugo-official \
  klakegg/hugo:0.71.0
```

In docker-compose using `entrypoint`:

```yaml
  build:
    image: klakegg/hugo:0.71.0
    entrypoint: hugo-official
    volumes:
      - ".:/src"
```


## Versions

| Software | Version |
| -------- | ------- |
| Hugo     | 0.71.0  |
| Go       | 1.14.3  |
| NodeJS   | 12.16.3 |
| Pandoc   | 2.9.2.1 |
| Yarn     | 1.22.4  |


## Configuration

Environment variables:
* HUGO_BIND - Bind address for server. Default: `0.0.0.0`
* HUGO_CACHEDIR - Cache directory for modules. Default: `/tmp`
* HUGO_DESTINATION - Location of output folder. Default: `public`
* HUGO_PANDOC - Pandoc command to be triggered. Default: `pandoc-default`
* HUGO_ENV - Selecting environment ("DEV"/"production"). Default: `DEV`
* HUGO_VERSION - Version of Hugo to use. Requires images for Hugo NEXT or newer. Default: *blank*

Ports:
* `1313/tcp`
