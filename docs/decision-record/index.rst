Decision-record
===============

Notificeren van nieuwe contactverzoeken
---------------
Een poller controleert periodiek (momenteel een keer per minuut) of er nieuwe contactverzoeken zijn. Alle toegewezen actoren waarvan en emailadres achterhaald kan worden ontvangen per contactverzoek een email.
In een interne database wordt bijgehouden wat de aanmaak datum/tijd is van het contactverzoek (InterneTaak) dat als laatste verwerkt is. De poller haalt steeds de nieuwste items op en gaat door totdat er geen items meer zijn die nieuwer zijn dan de bijgehouden datum/tijd. Er wordt niet uitgegaan van het id, maar van het tijdstip, omdat het item in de bron verwijderd zou kunnen worden, waarna we niet meer zouden kunnen bepalen welke items al verwerkt zijn. Er is voor gekozen om niet gebruik te maken van het status veld in OpenKlant om bij te houden voor welke items al een notificatie is verstuurd. De toegestane waardes zijn daarvoor niet toereikend.  Er is voor gekozen om (voorlopig) geen gebruik te maken van de notificatie mogelijkheden in OpenKlant als alternatief voor de poller. De reden daarvoor was dat de mogelijkheden en beperkingen van het notificeren vanuit OpenKlant niet tijdig voldoende helder gemaakt konden worden.  
