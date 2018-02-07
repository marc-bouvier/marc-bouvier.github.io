---
layout: post
title: "Delivery app from food-truck during event"
tags: innovation branding partnership ios android
published: false
date: 2018-02-06
---

With [Davidson Consulting Strasbourg](https://www.davidson.fr/), we have been partner 
of ["La nuit de l'info"](https://www.nuitdelinfo.com/) which is a student software contest. It occurs each year and take place
during one evening and one night. The students must choose challenges proposed by sponsor companies and are given a
subject as a main guideline.

Each company propose with it's challenge money prizes for the winners of the challenge. It is an opportunity for 
sponsor companies to gain more visibility about them. It allows them to spot future talents.

We want to make a good impression next year by providing a food truck for the night. In order to help the students 
get their food, we can deliver it to them directly. A delivery app just for the occasion can be made.

## Registering

Students must provide a key if they want to use the app. We give them a key at the beginning of the event. And 
they log in with it when they want to order. When they finish their order the transaction is finished and we provide a number to follow the 
order. That way, several students can order with the same device. They can go back to their order by typing their user ID or order ID.
That way we can also limit number of orders by person.

## Queuing engine

Queue orders and localization.
We must know at least where will the goods be delivered. I will be attached to the ID that will be given to the student.
We may have to feed the data store with localisation at the start of the event.
Then, when an order is made by a student, it is queued. The queue of orders is accessible by the foodtruck which can prepare the order. When the order is finished, it is passed to an available delivery person. The delivery person localizes the student with the Order ID and bring food to them.

Problems we may encounter : 
- everybody may order at the same time : not allowing ordering until enough delivery men are available and when order queue is to big?
- order for later? order in advance for a due time (partitionning order queue in split of time?)

## Payment

No payment : it will be open-bar. But we must track how many has been delivered. We may allow only one order per student.

## Non functional requirements

PWA : Progressive Web App. Should be accessible as an app everywhere and easy to install.
At least must be available as a web site accessible from wifi of the event.

Might be nice if it is on android and apple store

# My stack

- hosted on a raspberry pi 3
- socket.io for bidirectional communication
- nodejs as frontend api
- emberjs for frontend
- nodejs server
- mongodb for sharing state in backend
- try jhipster or yeoman generator?
- https://spring.io/guides/gs/messaging-stomp-websocket/
- CQRS?
- Event sourcing?
- DDD?
- SpringBoot 2 + Spring WebFlux (reactive stream) : https://www.infoq.com/presentations/spring-kotlin-boot


