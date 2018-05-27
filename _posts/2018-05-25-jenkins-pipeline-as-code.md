---
layout: post
title: "Pipeline as code with Jenkins (french)"
tags: Jenkins Continuous-Integration Build French
published: false
---

## Intérêt des pipelines

* Enchainer des builds
* paralléliser des builds (compilation, tests, test intégration, e2e)
* Affichage sympa BlueOcean
* Configuration as code (Jenkinsfile) -> création automatique d'un job lors de la création d'une branche

## Ressources

* https://jenkins.io/doc/book/pipeline/getting-started/#defining-a-pipeline-in-scm
* https://jenkins.io/doc/book/pipeline/jenkinsfile/
* https://github.com/jenkinsci/docker/blob/master/README.md
* [Blue Ocean](https://jenkins.io/projects/blueocean/) (démo pipeline visuel)
* https://plugins.jenkins.io/bitbucket
* https://bjurr.com//building-atlassian-stash-pull-requests-in-jenkins/
* https://bjurr.com/continuous-integration-with-bitbucket-server-and-jenkins/

## Installation

Avec docker
```
# docker pull jenkins/jenkins:lts
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```
this will automatically create a 'jenkins_home' docker volume on the host machine, that will survive the container stop/restart/deletion.
# Demo
