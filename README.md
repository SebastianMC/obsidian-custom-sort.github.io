# obsidian-custom-sort.github.io

Documentation for obsidian-custom-sort plugin for Obsidian.md

# Project repository structure

- `/docs/`
  - documentation website generated by [Material for MkDocs](https://squidfunk.github.io/mkdocs-material)
  - Github Pages exposes this as the www root of [documentation website](https://obsidian-custom-sort.info)
  - `/docs/CNAME`
    - github requires this file ar part of thw website when exposed under custom domain
- `/src/`
  - source and configuration for [Material for MkDocs](https://squidfunk.github.io/mkdocs-material)
  - `/src/mkdocs.yml`
    - configuration for [MkDocs](https://www.mkdocs.org) generator
  - `/src/docs/`
    - source documents for the documentation consumed by [MkDocs](https://www.mkdocs.org) generator
    - `/src/docs/CNAME`
      - the `CNAME` file in source location, it is copied as-is to the documentation website during generation.
        This file is required (in the root of the documentation website) by github pages, when they are exposed under a custom domain 
# Building the documentation

Using docker `squidfunk/mkdocs-material` instead of local installation

- source of documentation exits in `/src` of this repository
  - this local folder is mapped onto `/docs` in the docker container - MkDocs expects source in that location
- target documentation site is generated to `/docs` of this repository
  - Github Pages expects this exact location to be the root of website to be published Github Pages
  - the docker container folder `/generated-site` is mapped onto the `/docs` local (repository) folder
- the command to build documentation with the above setup is, when invoked from the repository root folder is:
  - `obsidian-custom-sort-docs % docker run --rm -it -v ${PWD}/src:/docs -v${PWD}/docs:/generated-site squidfunk/mkdocs-material build --site-dir /generated-site`

# Viewing the generated site in browser

Simply open the `/docs/index.html` in local webserver or use live preview (below)

## Live preview (useful for development)

After issuing the command:

`docker run --rm -it -p 8000:8000 -v ${PWD}/src:/docs squidfunk/mkdocs-material`

the on-the-fly generated site is exposed at `http://localhost:8000`

# References

- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material)
- [MkDocs](https://www.mkdocs.org)
- 
