---

---

Dans Bitbucket créer un projet et un dépôt.

```
git clone http://Admin@localhost:7990/scm/tes/pipeline-as-code.git
```

Ajouter des sources
Pour l'exemple je génère un projet maven à partir d'un archetype
```
mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-simple -DarchetypeVersion=1.3
Define value for property 'groupId': fr.bouvier.marc
Define value for property 'artifactId': pipeline-as-code
Define value for property 'version' 1.0-SNAPSHOT: : 
Define value for property 'package' fr.bouvier.marc: : 
```
... et un fichier `Jenkinsfile`
Voici un exemple de configuration de pipeline à plusieurs étapes qui ne fait rien d'autre que écrire des messages dans la console.
```
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
```

Aller sur [http://localhost:8080/blue/organizations/jenkins/pipelines](http://localhost:8080/blue/organizations/jenkins/pipelines)

Where do you store your code : Bitbucket server

TODO : screens

ifconfig pour connaître l'adresse IP de docker (ici : 172.17.0.1)
```
$> ifconfig
docker0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        inet6 fe80::42:9dff:fe59:c59  prefixlen 64  scopeid 0x20<link>
        ether 02:42:9d:59:0c:59  txqueuelen 0  (Ethernet)
        RX packets 39977  bytes 14070252 (14.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 64327  bytes 90338990 (90.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```