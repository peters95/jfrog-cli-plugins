# rb-gen

## About this plugin

This plugin is designed to simplify interaction with release bundles, by
generating them from other formats. Currently, it can generate release bundles
from Helm charts.

## Installation with JFrog CLI

Installing the latest version:

`$ jfrog plugin install rb-gen`

Installing a specific version:

`$ jfrog plugin install rb-gen@version`

Uninstalling a plugin

`$ jfrog plugin uninstall rb-gen`

## Usage

### Commands

- from-chart
  - Arguments:
    - bundle-name: The name of the new release bundle
    - bundle-version: The version of the new release bundle
  - Flags:
    - chart-path: The path (in Artifactory) of the Helm chart from which to
      generate the release bundle. All dependency Helm charts should be
      available in the same repository.
    - docker-repo: The name of a Docker repository in Artifactory. All
      dependency Docker images should be available in this repository.
  - Example:
    ``` shell
    jfrog rb-gen from-chart --chart-path=<chart path> --docker-repo=<Docker repo name> <bundle name> <bundle version>
    ```

Note that if Helm or Docker dependencies are found in a remote repository, they
must be cached. Otherwise, they won't show up in the release bundle. After
generating a release bundle, the generator will output which dependencies were
and were not found; missing dependencies are not listed in the bundle.

## Release Notes
The release notes are available [here](RELEASE.md).