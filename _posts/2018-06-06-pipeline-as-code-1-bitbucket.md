---
title: "Installer bitbucket server avec docker (french)"
tags: How-To Docker Bitbucket French
---
Mettre en place bitbucket avec docker

* https://bitbucket.org/atlassian/docker-atlassian-bitbucket-server

```
%> docker volume create --name bitbucketVolume
$> docker run -v bitbucketVolume:/var/atlassian/application-data/bitbucket --name="bitbucket" -d -p 7990:7990 -p 7999:7999 atlassian/bitbucket-server:5.5
```

Bitbucket est disponible à l'adresse [http://localhost:7990](http://localhost:7990).

Créer une license d'évaluation et configurer le serveur

Bitbucket est installé!

TODO : à déplacer dans le post 2
<iframe width="560" height="315" src="https://www.youtube.com/embed/k_fVlU1FwP4?cc_load_policy=1&hl=fr&rel=0&version=3&cc_lang_pref=fr" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
