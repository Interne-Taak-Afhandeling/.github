***************
Decision-record
***************

Notificeren van nieuwe contactverzoeken
---------------
Een poller controleert periodiek (momenteel een keer per minuut) of er nieuwe contactverzoeken zijn. Alle toegewezen actoren waarvan een e-mailadres achterhaald kan worden, ontvangen per contactverzoek een e-mail.


In een interne database wordt bijgehouden wat de aanmaak datum/tijd is van het contactverzoek (InterneTaak) dat als laatste verwerkt is. De poller haalt steeds de nieuwste items op en gaat door totdat er geen items meer zijn die nieuwer zijn dan de bijgehouden datum/tijd. Er wordt niet uitgegaan van het id, maar van het tijdstip, omdat het item in de bron verwijderd zou kunnen worden, waarna we niet meer zouden kunnen bepalen welke items al verwerkt zijn. Er is voor gekozen om niet gebruik te maken van het statusveld in OpenKlant om bij te houden voor welke items al een notificatie is verstuurd. De toegestane waardes zijn daarvoor niet toereikend.  

Er is voor gekozen om (voorlopig) geen gebruik te maken van de notificatie mogelijkheden in OpenKlant als alternatief voor de poller. De reden daarvoor was dat de mogelijkheden en beperkingen van het notificeren vanuit OpenKlant niet tijdig voldoende helder gemaakt konden worden.  

Koppelen van contactmomenten bij contactverzoeken
=================================================

Het datamodel staat niet toe dat een contactmoment (klantcontact) dat voortkomt uit een contactverzoek (interne taak) wordt gekoppeld aan die interne taak.
Het contactmoment kan alleen, via een onderwerpobject, gekoppeld worden aan een eerder contactmoment. Daarbij hebben we twee keuzes moeten maken. (gerelateerd aan issue #13)

Probleem: Er kan niet op het aanleidinggevende klantcontact gezocht wordt (daar is een issue voor aangemaakt op de backlog van OpenKlant).
Keuze: We slaan de benodigde gegevens op in de onderwerpobjectidentificator velden. Daar kan wel op gezocht worden.
Overwegingen: Wachten op aanpassing van de OpenKlant api duurt te lang. Het zou ook opgelost kunnen worden door de benodigde gegevens apart op te slaan in een soort logboek van de interne taak. Zoiets staat op de planning, maar was een te omvangrijk ingreep om dit probleem nu mee op te lossen.

Probleem: We zouden het nieuwe contactmoment altijd kunnen koppelen aan het eerste contactmoment, of aan het laatste. 
Keuze: We hebben gekozen voor het laatste, omdat op die manier een keten te maken is waarbij de volgorde klopt. 
Overwegingen: We hadden erop kunnen gokken dat de items altijd door de API in de zelfde volgorde van moment van aanmaken geretourneerd worden, maar daar worden geen garanties voor gegeven. Of we zouden kunnen sorteren op datum, maar aangezien de datum geen verplicht veld is leek dat ook geen stabiele betrouwbare oplossing. de gekozen oplossing is omslachtig, maar lijkt wel de veiligste oplossing.


Tonen van digitale adressen
=================================================

Bij een Contactverzoek worden de contactgegevens van de klant opgeslagen in ``digitaleAdressen`` die verstrekt zijn door de betrokkene van het Klantcontact. 
De interface van ITA gaat uit van 1 of 2 telefoonnummers, en 1 e-mailadres. 
Omdat bij de telefoonnummers, zeker een tweede telefoonnummer, een omschrijving opgeslagen kan zijn die door de klant is doorgegeven, gebruiken we voor de labels van telefoonnummers de waarde van ``digitaalAdres.omschrijving``. Voor het e-mailadres doen we dat niet.  

