---
tags: Java ChangeLog LTS Licensing News
---
Java 11 has been released for general use in september 2018. Let's see what changed in this version.
## New release schedule

Since Java 9, Java is released at a 6 month frequency. With a LTS version 
(Long term support) every 3 versions. With each new version, the previous one stops 
to receive public updates.

# Java 11 is LTS

Java 11 is the first LTS since the 2 last versions.

## New licensing system

Java 11 comes with a new licence system. Stephen Colebourn warns that Oracle's JDK has been 
deliberately or accidentally setup as a 'trap for users'. He says that the developpers who will
download the commercial JDK from Oracle and use it in production (because they are use to do it as an habit). And they may not know that the licence has changed. 

They may experience to be called later by Oracle salesforces asking for a lot of money. If they
don't read the JDK's terms and conditions, they won't realize that it is a commercial JDK.
And they will have to pay for Java.

There is an alternative : use OpenJDK. In addition to the commercial JDK, Oracle proposes an
OpenJDK build under GPL licence. It is available at [jdk.java.net](https://jdk.java.net/).
Some other implementations of OpenJDK will be available too.

Java SE 8 free updates will continue until january 2019. Then, you will need to switch to another
version of the SDK (OpenJdk is an alternative) or consent to acquire a commercial license, or
only use non commercial features. Though Oracle commercial JDK and OpenJDK are almost identical,
[they are different on a few aspects](https://blogs.oracle.com/java-platform-group/oracle-jdk-releases-for-java-11-and-later).

## New HTTP Api stabilized

`java.net.http`

## Unicode 9.0.0 & 10.0.0 support

### Unicode 9.0.0
Support of [Unicode 9.0.0](https://unicode.org/versions/Unicode9.0.0/).

Main improvements includes : 
* 7500 new characters
* 6 new scripts (Osage, Nepal Bhasa, Fulani and other African languages, Bravanese dialect of Swahili, Warsh orthography for Arabic, Tangut)
* [72 new emoji characters](http://www.unicode.org/emoji/charts/emoji-versions.html#2016)
* 19 symbols for the new 4K TV standard

### Unicode 10.0.0
Support of [Unicode 10.0.0](https://unicode.org/versions/Unicode10.0.0).

Main improvements includes :
* 8518 new characters
* 4 new scripts (Masaram Gondi, Nushu, Soyombo, Zanabazar Square)
* [56 new emoji characters](http://www.unicode.org/emoji/charts/emoji-versions.html#2017)
* Bitcoin sign, 

## Z garbage collector

Experimental low-latency scalable garbage collector.

Only available on Linux/x64 yet.

## `var` : local variable syntax for lambdas parameters

`var` keyword was introduced in Java 10 for local scoped type inference. 
It can now be used during lambdas formal parameters declaration.

## Security

Java now implements ChaCha20 and Poly1305 encryption algorithms. It also supports TLS 1.3.

## Removal of Apis and tools

Corba has been removed from Java. Java EE Apis have been removed from Java SE and JDK, 
they are available as separate dependencies.

Nashorm javascript engine has been deprecated in Java 11.

`pack200`, `unpack200` tools and Pack200 API from `java.util.jar` are deprecated.

Applets and Web Start deployment platform have been removed in Java 11.

JavaFx is considered "non essential" and is not a part of the JDK anymore. It is now available 
[as a separate dependency](https://openjfx.io/).

## Resources

* [Oracle annonce la sortie officielle de Java 11](https://www.developpez.com/actu/226307/Oracle-annonce-la-sortie-officielle-de-Java-11-tour-d-horizon-des-principales-nouveautes-de-cette-version-LTS/)
* [OpenJDK feature list (JSR)](https://openjdk.java.net/projects/jdk/11/)
[][]
[][]
