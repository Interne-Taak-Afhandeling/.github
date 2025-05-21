Decision-record
===============

Het datamodel staat niet toe dat een contactmoment (klantcontact) dat voortkomt uit een contactverzoek (interne taak) wordt gekoppeld aan die interne taak.
Het contactmoment kan alleen, via een onderwerp object, gekoppeld worden aan een eerder contactmoment. Daarbij hebben we twee keuzes moeten maken. (gerelateerd aan issue #13)

probleem: Er kan niet op het aanleidinggevende klantcontact gezocht wordt (daar is een issue voor aangemaakt op de backlog van OpenKlant).
keuze: We slaan de benodigde gegevens op in de onderwerpobjectidentificator velden. Daar kan wel op gezocht worden.
overwegingen: Wachten op aanpassing van de OpenKlant api duurt te lang. Het zou ook opgelost kunnen worden door de benodigde gegevens apart op te slaan in een soort logboek van de interne taak. Zoiets staat op de planning, maar was een te omvangrijk ingreep om dit probleem nu mee op te lossen.

probleem: We zouden het nieuwe contactmoment altijd kunnen koppelen aan het eerste contactmoment, of aan het laatste. 
keuze: We hebben gekozen voor het laatste, omdat op die manier een keten te maken is waarbij de volgorde klopt. 
overwegingen: We hadden erop kunnen gokken dat de items altijd door de API in de zelfde volgorde van moment van aanmaken geretourneerd worden, maar daar worden geeen garanties voor gegeven. Of we zouden kunnen sorteren op datum, maar aangezien de datum geen verplicht veld is leek dat ook geen stabiele betrouwbare oplossing. de gekozen oplossing is omslachtig, maar lijkt wel de veiligste oplossing.


