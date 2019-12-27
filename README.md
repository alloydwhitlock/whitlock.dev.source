# whitlock.dev.source
Source project for whitlock.dev

## Deployment to Production

### Overview

This project is automatically deployed on commit & successful build via CircleCI. The site repository, [alloydwhitlock/whitlock.dev](https://github.com/alloydwhitlock/whitlock.dev/), hosts the final assets used by whitlock.dev

### Configuration

#### Secrets

The CircleCI project contains credentials used to deploy the site from CircleCI to GitHub. These secrets are hidden, referenced by environmental variables. You can see the [CircleCI configuration file](https://github.com/alloydwhitlock/whitlock.dev.source/blob/master/.circleci/config.yml) for an example of how they are called.

#### Process

1. Build the static assets via [Hugo](https://gohugo.io/).
    1. Ensure a specified version of Hugo is used
    1. Avoid using `latest` unless wanting to live on the edge of unknown changes
1. Run `HTMLProofer` to validate the output of the Hugo site artifacts
1. On successful run in the `master` branch, run a deployment to the site repository [alloydwhitlock/whitlock.dev](https://github.com/alloydwhitlock/whitlock.dev/).

The build process leverages a [CircleCI Hugo orb](https://circleci.com/orbs/registry/orb/circleci/hugo) to reduce the number of manual steps specified. 


## How to Build and Test Locally

_Note: Ensure `hugo` is installed locally on your development machine_

1. Checkout repository via `git clone git@github.com:alloydwhitlock/whitlock.dev.source.git`
1. `cd` into the site directory
    1. `cd whitlock.dev.source`
1. Run `hugo server -D` to build and view the site
    1. Web server runs locally at `http://localhost:1313/`
1. Built site output is in `public` folder


## Project Status

![CircleCI](https://img.shields.io/circleci/build/github/alloydwhitlock/whitlock.dev.source?logo=circleci)
![GitHub Last Commit](https://img.shields.io/github/last-commit/alloydwhitlock/whitlock.dev.source?logo=github)
