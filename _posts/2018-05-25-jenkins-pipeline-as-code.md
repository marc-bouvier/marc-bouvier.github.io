---
layout: post
title: "Pipeline as code with Jenkins (french)"
tags: Jenkins ContinuousIntegration Build French
published: false
---

* https://jenkins.io/doc/book/pipeline/getting-started/#defining-a-pipeline-in-scm

Avec docker
```
# docker pull jenkins/jenkins:lts
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```
this will automatically create a 'jenkins_home' docker volume on the host machine, that will survive the container stop/restart/deletion.
