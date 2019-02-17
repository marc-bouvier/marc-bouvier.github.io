---
tags: Sonar How-To Docker
---
```
docker pull sonarqube:lts
```

```
docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube:lts
```

Generate a token. I named it `sonar-token`
```
sonar-token: 0309b3dc4d0ca5a4fc35d0f18428499c818616c6

```
mvn sonar:sonar \
  -Dsonar.host.url=http://172.17.0.1:9000 \
  -Dsonar.login=0309b3dc4d0ca5a4fc35d0f18428499c818616c6
```

Use the token to configure Jenkins 
̀ 0309b3dc4d0ca5a4fc35d0f18428499c818616c6` 