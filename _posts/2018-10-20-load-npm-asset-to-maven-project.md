---
tags: How-To Maven Npm Packaging Java Javascript NodeJs
---
In this article I will show you how to download, unpack and copy assets from an NPM repository (nexus 3.0) and add them into maven project at packaging time.

My current client just upgraded Nexus from 2.x to 3.x. Nexus 3.0 introduces NPM repos in addition to Maven. For some 
architectural reasons, we need to copy some static assets from a javascript application into a SpringBoot application.

We used to package the javascript application wrapped with maven. 

What we want now is to use standard javascript structure and publish it to NPM.

I have a javascript application `my-npm-app` which is already published on a nexus mirror.

In the maven target application, first configure nexus path and the javascript application name and version.
pom.xml
```xml
<properties>
    <my-npm-app.artifact.name>my-npm-app</my-npm-app.artifact.name>
    <!-- at release time you will only have to change version number -->
    <my-npm-app.artifact.version>0.0.3-SNAPSHOT</my-npm-app.artifact.version>
 
    <!-- nexus configuration -->
    <nexus.path>https://my_nexus_url.com/nexus/repository/</nexus.path>
    <nexus.snapshot>npm-snapshots/</nexus.snapshot>
    <nexus.release>npm-releases/</nexus.release>
</properties>
```

Then we can use antRun plugin to download, untar and copie files where we want during any maven build phase.
I did a little more. I added snapshot detection : if version number contains 'SNAPSHOT' the nexus URL changes to snapshot repo, else it uses releases.
We don't have to manually change url anymore in order to release or snapshot.

pom.xml
```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-antrun-plugin</artifactId>
            <version>1.8</version>
            <dependencies>
                <!-- to be able to use <if> whithin ant -->
                <dependency>
                    <groupId>ant-contrib</groupId>
                    <artifactId>ant-contrib</artifactId>
                    <version>1.0b3</version>
                    <exclusions>
                        <exclusion>
                            <groupId>ant</groupId>
                            <artifactId>ant</artifactId>
                        </exclusion>
                    </exclusions>
                </dependency>
            </dependencies>
 
            <executions>
                <!-- Downloads npm artifact from npm (nexus 3.0) -->
                <execution>
                    <id>download-my-npm-app</id>
                    <phase>prepare-package</phase>
                    <goals>
                        <goal>run</goal>
                    </goals>
                    <configuration>
                        <target>
                            <ac:if xmlns:ac="antlib:net.sf.antcontrib">
                                <ac:contains substring="SNAPSHOT" string="${my-npm-app.artifact.version}"/>
                                <!-- If version number contains 'SNAPSHOT' we lookup to snapshots in NPM repo -->
                                <ac:then>
                                    <get src="${nexus.path}${nexus.snapshot}@mynpmgroup/${my-npm-app.artifact.name}/-/${my-npm-app.artifact.name}-${my-npm-app.artifact.version}.tgz"
                                         dest="${project.build.directory}/${my-npm-app.artifact.name}-${my-npm-app.artifact.version}.tgz"
                                         verbose="false"
                                         usetimestamp="true"/>
                                </ac:then>
                                <!-- else we lookup for releases -->
                                <ac:else>
                                    <get src="${nexus.path}${nexus.release}@mynpmgroup/${my-npm-app.artifact.name}/-/${my-npm-app.artifact.name}-${my-npm-app.artifact.version}.tgz"
                                         dest="${project.build.directory}/${my-npm-app.artifact.name}-${my-npm-app.artifact.version}.tgz"
                                         verbose="false"
                                         usetimestamp="true"/>
                                </ac:else>
                            </ac:if>
                        </target>
                    </configuration>
                </execution>
                <!-- untar tgz archive -->
                <execution>
                    <id>unpack-my-npm-app</id>
                    <phase>prepare-package</phase>
                    <goals>
                        <goal>run</goal>
                    </goals>
                    <configuration>
                        <target>
                            <untar src="${project.build.directory}/${my-npm-app.artifact.name}-${my-npm-app.artifact.version}.tgz"
                                   dest="${project.build.directory}/my-npm-app/"
                                   compression="gzip">
                                <patternset >
                                    <include name="package/dist/"/>
                                </patternset>
                            </untar>
                        </target>
                    </configuration>
                </execution>
                <!-- Copy files anywhere we want in the application we are packaging -->
                <execution>
                    <id>copy-my-npm-app</id>
                    <phase>prepare-package</phase>
                    <goals>
                        <goal>run</goal>
                    </goals>
                    <configuration>
                        <target>
                            <copy todir="${project.build.directory}/classes">
                                <fileset dir="${project.build.directory}/my-npm-app/package/dist/" includes="**/*"/>
                            </copy>
                        </target>
                    </configuration>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```
