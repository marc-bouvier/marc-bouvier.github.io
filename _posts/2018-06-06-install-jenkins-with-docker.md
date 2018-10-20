---
tags: How-To Jenkins Docker
---

La série d'articles
* Installation de Jenkins avec Docker
* [Installation de Bitbucket avec Docker](/2018/06/06/pipeline-as-code-1-bitbucket/)
* [Pipeline As Code avec Jenkins et Bitbucket](/2018/06/10/Pipeline-as-code-with-Jenkins-and-bitbucket/)

Slides : [Pipelines d'intégration continue avec Jenkis Bitbucket et Sonar](https://slides.com/marcbouvier/jenkins-2-bitbucket#/)


```
  docker pull jenkins/jenkins:lts
  docker run --name myjenkins -p 8080:8080 -p 50000:50000 -v /var/jenkins_home jenkins/jenkins:lts
```

Lire les logs pour noter l'utilisateur et le mote de passe générés pour pouvoir lancer le setup.
```
  *************************************************************
  *************************************************************
  *************************************************************

  *************************************************************
  *************************************************************
  *************************************************************

  Jenkins initial setup is required. An admin user has been created and a password generated.
  Please use the following password to proceed to installation:

  d5567ba0c53b43709e2daae0bf8e6fa9

  This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

  *************************************************************
  *************************************************************
  *************************************************************
```

Terminer l'installation de Jenkins : [http://localhost:8080](http://localhost:8080)

Installer les plugins suggérés

Puis, installer le plugin "Blue Ocean" et "Bitbucket Plugin"

Redémarrer Jenkins

Jenkins est installé pour pouvoir travailler avec des pipelines et Blue Océan.

Installer le plugin ̀Bitbucket Branch Source` et ̀Sonarqube scanner`

Configurer un jdk et maven dans Jenkins
Aller dans Manage Jenkins > Global Tools configuration

Jdk > Jdk installations
Name : jdk8
Install automatically : coché
Run shell command
* label : install open-jdk8
* Command : `sudo apt-get --assume-yes install openjdk-8-jdk`
* Tool Home : `/usr/bin`

Maven > Maven installations
Name : maven-3.5.3
Install automatically : coché
Install from apache : 3.5.3

