# Minimal Svelte / Routify / Svelte Material UI SPA template

## What's in the box:

- [Svelte rollup](https://github.com/sveltejs/template) (via `degit`)
- [Routify "Install to existing project"](https://routify.dev/guide/installation/install-to-existing-project)
- [Svelte Material UI](https://sveltematerialui.com/INSTALL.md/)

## Setup notes:

- Rollup has been configured to emit modules (as Routify expects) to `public/modules`.
- Make sure `public/index.html` has the proper css and js import statements
  - Including `modules/main.css`
- To use the material styles within SMUI, you must import components with `/styled` appended to the import source. (This is part of the SMUI "Advanced Styling Method")
  - i.e. `import Button from '@smui/button/styled';` versus `@smui/button`

## Containerization notes:

- You  may wish to create a simple, small, fast container that can run _anywhere_.
- This `Dockerfile` runs a _multistage_ build:
  1. First _(intermediate)_ container uses node to build the app.
  1. Second _(final)_ container copies the output of `npm run bulid` (`public` folder) into a minimal linux distro to run the nginx web server.
- The `nginx-spa.conf`, _configured for an SPA_, is copied into the container. You should review and refine this file to suit your needs.

## To prepare and run your containerized SPA:

1. Install [Docker](https://www.docker.com/) on your system.
1. [Build the docker image](https://docs.docker.com/engine/reference/commandline/build/) following the directives in the Dockerfile `docker build -t johnknapp/spa-template .` Change the tag name as needed.
1. [Run the image you just built](https://docs.docker.com/engine/reference/commandline/run/) in your local development environment. `docker run --rm -p80:8080 johnknapp/spa-template`. _(The --rm flag removes the container upon exit.)_
1. Think about the nginx listenting port and the docker container external:internal ports you use.

## Common docker commands to know:

- `docker help`
- `docker image ls`
- `docker image prune`
- `docker ps -a`
- `docker exec -it <cid> /bin/sh` _(container id)_
- `docker container logs -f <cid>`
- `docker container prune`

## Deployment notes:

- Before you can deploy your containerized SPA, you need to [push your container](https://docs.docker.com/engine/reference/commandline/push/) to a container registry. Registry details for two popular low-cost hosting options:
  - [Heroku Container Registry](https://devcenter.heroku.com/articles/container-registry-and-runtime)
  - [Google Cloud Platform Container Registry](https://cloud.google.com/container-registry)
- You may also choose to push your container to a private container registry you host yourself or use [Docker Hub](https://hub.docker.com/) or a similar service.