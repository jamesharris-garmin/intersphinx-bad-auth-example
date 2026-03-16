# Welcome!

This is a demo project that uses docker-compose to demonstrate a credential
leak in the sphinx.ext.intersphinx documentation.

It uses a build of the readthedocs-examples/example-sphinx-basic as a remote
project. It hosts the intersphinx remote in a docker image using caddy and a
simple basic_auth from the examples.

## What is the issue?

When intersphinx fails to authenticate to a project using basic-auth, sphinx
will print the full uncensored warning in the file, exposing the authentication
token. This exposes the token to the logs, even if the token is correct but the
server is failing to respond for unrelated reasons. (i.e. we got the wrong URL
and the server thinks we are not authroized for the wrong url.)

## Requirements

* `docker` with the `compose` plugin.
    * [Docker CE instructions](https://docs.docker.com/engine/install/#installation-procedures-for-supported-platforms)
    * [Docker Desktop](https://docs.docker.com/get-started/get-docker/)
* `uv`
    * [uv install instructions](https://docs.astral.sh/uv/#installation)

## Running the example:

To run the example, invoke:

```shell
uv run nox
```
and observe the ouput.
