***************
Decision-record
***************

Notificeren van nieuwe contactverzoeken
---------------------------------------------
Een poller controleert periodiek (momenteel een keer per minuut) of er nieuwe contactverzoeken zijn. Alle toegewezen actoren waarvan een e-mailadres achterhaald kan worden, ontvangen per contactverzoek een e-mail.


In een interne database wordt bijgehouden wat de aanmaak datum/tijd is van het contactverzoek (InterneTaak) dat als laatste verwerkt is. De poller haalt steeds de nieuwste items op en gaat door totdat er geen items meer zijn die nieuwer zijn dan de bijgehouden datum/tijd. Er wordt niet uitgegaan van het id, maar van het tijdstip, omdat het item in de bron verwijderd zou kunnen worden, waarna we niet meer zouden kunnen bepalen welke items al verwerkt zijn. Er is voor gekozen om niet gebruik te maken van het statusveld in OpenKlant om bij te houden voor welke items al een notificatie is verstuurd. De toegestane waardes zijn daarvoor niet toereikend.  

Er is voor gekozen om (voorlopig) geen gebruik te maken van de notificatie mogelijkheden in OpenKlant als alternatief voor de poller. De reden daarvoor was dat de mogelijkheden en beperkingen van het notificeren vanuit OpenKlant niet tijdig voldoende helder gemaakt konden worden.  

Koppelen van contactmomenten bij contactverzoeken
-------------------------------------------------

Het datamodel staat niet toe dat een contactmoment (klantcontact) dat voortkomt uit een contactverzoek (interne taak) wordt gekoppeld aan die interne taak.
Het contactmoment kan alleen, via een onderwerpobject, gekoppeld worden aan een eerder contactmoment. Daarbij hebben we twee keuzes moeten maken. (gerelateerd aan issue #13)

**Probleem**: Er kan niet op het aanleidinggevende klantcontact gezocht wordt (daar is een issue voor aangemaakt op de backlog van OpenKlant).

* Keuze: We slaan de benodigde gegevens op in de onderwerpobjectidentificator velden. Daar kan wel op gezocht worden.
* Overwegingen: Wachten op aanpassing van de OpenKlant api duurt te lang. Het zou ook opgelost kunnen worden door de benodigde gegevens apart op te slaan in een soort logboek van de interne taak. Zoiets staat op de planning, maar was een te omvangrijk ingreep om dit probleem nu mee op te lossen.

**Probleem**: We zouden het nieuwe contactmoment altijd kunnen koppelen aan het eerste contactmoment, of aan het laatste. 

* Keuze: We hebben gekozen voor het laatste, omdat op die manier een keten te maken is waarbij de volgorde klopt. 
* Overwegingen: We hadden erop kunnen gokken dat de items altijd door de API in de zelfde volgorde van moment van aanmaken geretourneerd worden, maar daar worden geen garanties voor gegeven. Of we zouden kunnen sorteren op datum, maar aangezien de datum geen verplicht veld is leek dat ook geen stabiele betrouwbare oplossing. de gekozen oplossing is omslachtig, maar lijkt wel de veiligste oplossing.


Koppelen van zaken bij contactverzoeken
---------------------------------------------

Het OpenKlant-model staat in principe toe dat er meer dan één Zaak gekoppeld is aan een Contactverzoek (via een ``onderwerpobject`` bij het ``klantcontact`` van het Contactverzoek). ITA ondersteunt dit op dit moment niet. De kans dat dit voorkomt is zeer klein. In de oorspronkelijke opzet van Klantinteracties was het idee dat elke ``klantcontact`` één Onderwerp heeft. Dit maakt meerdere ``onderwerpobjecten`` onwaarschijnlijk. 

Dus bij het koppelen van een Zaak aan een Contactverzoek hebben we gekozen voor:

* Als een gebruiker een Zaak koppelt aan een Contactverzoek, creëert ITA een ``onderwerpobject``
* Als er al een Zaak gekoppeld is, dan vervangt ITA de eerder gekoppelde Zaak door de nieuw gekoppelde Zaak
* Als het voorkomt dat er al 2 of meer Zaken zijn gekoppeld aan een Contactverzoek, dan is het niet mogelijk om een Zaakkoppeling te leggen of aan te passen. In dat geval verschijnt er een melding: "Er is een fout opgetreden bij het koppelen van de zaak: Het koppelen van een nieuwe zaak wordt niet ondersteund omdat er al meerdere zaken gekoppeld zijn aan dit contactverzoek."


Tonen van digitale adressen
---------------------------------

Bij een Contactverzoek worden de contactgegevens van de klant opgeslagen in ``digitaleAdressen`` die verstrekt zijn door de betrokkene van het Klantcontact. 
De interface van ITA gaat uit van 1 of 2 telefoonnummers, en 1 e-mailadres. 
Omdat bij de telefoonnummers, zeker een tweede telefoonnummer, een omschrijving opgeslagen kan zijn die door de klant is doorgegeven, gebruiken we voor de labels van telefoonnummers de waarde van ``digitaalAdres.omschrijving``. Voor het e-mailadres doen we dat niet.  


Contactverzoek sluiten
---------------------------------------------

**Probleem**: Er is nog geen duidelijke visie op wat een gebruiker zou moeten kunnen doen met met een afgesloten contactverzoek. Ook niet op welk type gebruiker dit zou mogen doen.

* Keuze: Het contactverzoek krijgt, bij het afsluiten m.b.v. de knop "Opslaan & afronden", de status ``verwerkt``. Het verdwijnt daarmee uit alle lijsten van openstaande contactverzoeken. Als men het op een andere manier benadert (rechtstreeks via de url, of uit een lijst met gesloten contactverzoeken), dan kan je er op dit moment precies hetzelfde mee als met een openstaand contactverzoek.

* Overwegingen: Scenario's waarbij men bijvoorbeeld per ongeluk het verkeerde contactmoment sluit, vergeet nog iets toe te voegen, achteraf een fout ontdekt, etc, zijn reëel. Het zou zeer onpraktisch zijn als men geen mogelijk had om een gesloten contactverzoek nog te kunnen bewerken.

Tonen van de contactverzoeken die zijn toegewezen aan de ingelogde gebruiker
----------------------------------------------------------------------------
**Probleem**: Paginering is niet mogelijk. Een contactverzoek kan op meerdere manieren zijn toegewezen, waardoor er meerdere actoren kunnen bestaan voor de ingelogde gebruiker. De klantinteracties api biedt alleen de mogelijkheid om internetaken op te vragen op basis van één actor. We zouden dus apart per actor alle pagina's met internetaken op moeten halen en die lijsten samen moeten voegen en ordenen om daar vervolgens de gewenste pagina met contactverzoeken uit te destilleren. Dat zou de applicatie zeer traag maken.

* Keuze: Voor nu halen we slechts de eerste pagina internetaken op per actor en maken daar een gecombineerde lijst van. Derhalve worden alleen de eerste honderd contactverzoeken per actor getoond. 

* Overwegingen: Dit is een voorlopige oplossing in afwachting van en uitbreiding van de api. Voor openstaande contactverzoeken verwachten we niet dat het een probleem zal zijn. Het is onwaarschijnlijk dat iemand meer dan honderd openstaande contactverzoeken heeft. Voor het overzicht van afgeronde contactverzoeken is het mogelijk in de praktijk wel een beperking, maar dat is minder belangrijke data. Hoe ouder een afgerond Contactverzoek, hoe kleiner de kans dat men dat nog moet inzien. Tenslotte is de kans zeer groot dat er óók een Afdeling of Groep aan een Contactverzoek hangt (vanuit KISS bijv. wordt een contactverzoek altijd minimaal aan een Afdeling of Groep toegewezen). Daarmee zijn oudere afgeronden contactverzoeken zeer waarschijnlijk wel in te zien via de afgesloten Contactverzoeken van die Afdeling of Groep.

