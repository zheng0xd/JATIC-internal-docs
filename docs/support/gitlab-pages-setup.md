# Gitlab Pages Setup Guide

The Gitlab Pages functionality allows a project in Gitlab to generate a static website. 

It's possible to generate static websites with many different packages, but the process described here specifically focuses on using `mkdocs`.

!!! example 

    This site is generated with Gitlab Pages from the `internal-docs` project  on Gitlab. You can find the project using the top right "Gitlab" link.

## Steps to set up pages

### 1. Enable CI/CD for the Project
1. In the Project, on the left side of the page go to Settings.
1. Expand "Visibility, project features, permissions".
1. Enable CI/CD (click the toggle) and click Apply at the end of the list of items. The page will refresh, showing new options.
1. On the left, select CI/CD.
1. Expand "Runners".
1. Ensure that the are available runners to execute the job.

### 2. Create `requirements.txt`, `mkdocs.yml`, and `.gitlab-ci.yml`
1. Create a new file in the project root called `requirements.txt` and copy the followingCopy the following into a new file named 
```
mkdocs>=1.1.2
mkdocs-material>=5.4.0
mkdocs-awesome-pages-plugin>=2.8.0
```
1. Create a new file in the project root called `mkdocs.yml` and copy the following
```
site_name: SITE NAME # your name here
site_url: https://jatic.pages.jatic.net/location # your pages url here
repo_url: https://gitlab.jatic.net/jatic/location # your repo url here
site_dir: public
docs_dir: docs
theme: # select a theme you prefer
#    name: readthedocs
    name: material
plugins:
    - search
    - awesome-pages
nav: # You can either list each file seperately, or use "..." to auto-add, or a mix
    - Home: README.md
    - ...
```
1. Create a new file in the project root called `.gitlab-ci.yml` and copy the following
```
image: python:3.8-buster

before_script:
  - pip install -r requirements.txt

test:
  stage: test
  script:
  - mkdocs build --verbose --site-dir test -f mkdocs.yml
  artifacts:
    paths:
    - test
  rules:
    - if: $CI_COMMIT_REF_NAME != $CI_DEFAULT_BRANCH

pages:
  stage: deploy
  script:
  - mkdir docs
  - cp *md ./docs
  - mkdocs build --verbose -f mkdocs.yml
  artifacts:
    paths:
    - public
  rules:
    - if: $CI_COMMIT_REF_NAME == $CI_DEFAULT_BRANCH
```

At this point, the runner should automatically run and build the website which includes all of the `.md` files from the project.

For more information on customizing documentation or advanced setup, see the MkDocs [Getting Started Tutorial](https://www.mkdocs.org/getting-started/) or Material for MkDocs [Getting Started Page](https://squidfunk.github.io/mkdocs-material/creating-your-site/).
