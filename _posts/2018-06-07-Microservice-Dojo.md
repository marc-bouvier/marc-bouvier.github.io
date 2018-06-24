---
published: false
--- 
Kata microservices et eventual consistency

A : client front
B : Api CQRS
* Recoit des commandes, résultat de l'appel REST = résultat de la commande 
  * KO + id de corrélation
  * OK + id de corrélation -> quand la commande est traitée -> émission d'un événement
     * Event OK : 
       * écouté par B pour mettre à jour la partie query
       * écouté par autres services pour poursuivre les traitement sur d'autres domaines
       * écouté par A pour éventuel feedback utilisateur (A peut aussi écouter les événement déclenchés en cascade par l'activation des autres service : besoin de garder l'id de corrélation)
       * écoute 
     * Event KO : écouté pour éventuel mécanisme de compensation fonctionnelle
C : API CQRS (idem)
  * Recoit l'événement OK de B
    * Emet une commande
      * Event KO
        * B doit compenser l'echec de C pour revenir à l'état initial (par ex. )


## Resources

* [Compensating transactions](https://docs.microsoft.com/en-us/azure/architecture/patterns/compensating-transaction)