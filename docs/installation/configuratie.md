.. _config_omgevingsvariabelen:

Omgevingsvariabelen
===================


Notificatie settings
---------------------------------

| **Variabele**                      | **Waarde**                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| Email_SmtpSettings_Host            | Adres van uw mailserver                                                                                  |
| Email_SmtpSettings_Port            | De poort waarover van uw mailserver benaderbaar is                                                      |
| Email_SmtpSettings_Username        | Credentials voor toegang tot uw mailserver                                                               |
| Email_SmtpSettings_Password        | Credentials voor toegang tot uw mailserver                                                               |
| Email_SmtpSettings_EnableSsl       | true/false                                                                                                |
| Email_SmtpSettings_FromEmail       | Afzenderadres voor mails die door ITA verstuurd worden                                                   |
| InternetakenNotifier_HourThreshold | Uurgrens voor meldingen. Contactverzoeken jonger dan deze waarde (in uren) krijgen periodiek notificaties |

 
Koppelingen met externe registers
---------------------------------

ITA gaat ervan uit dat emailadressen van medewerkers en organisatorische eenheden in een overige objecten registratie te vinden zijn en voldoen aan deze formats:
- medewerker: https://github.com/open-objecten/objecttypes/blob/main/community-concepts/Medewerker/medewerker-schema.json
- groep: https://github.com/open-objecten/objecttypes/blob/main/community-concepts/Afdeling%20en%20Groep/groep-schema.json
- afdeling:  https://github.com/open-objecten/objecttypes/blob/main/community-concepts/Afdeling%20en%20Groep/afdeling-schema.json

| **Variabele**                      | **Waarde**                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| ObjectApi_BaseUrl | https://uw-overige-objecten-adres.nl/api/v2/  |
| ObjectApi_ApiKey | min. 32 karakters  |
| OpenKlantApi_BaseUrl | https://uw-openklant-adres/klantinteracties/api/v1/  |
| OpenKlantApi_ApiKey | min. 32 karakters  |
| ZaakSysteem_BaseUrl |  https://uw-zaaksysteem-adres.nl |
| ZaakSysteem_ClientId |   |
| ZaakSysteem_Key |  min. 32 karakters |


Database configuratie
---------------------------------
| **Variabele**                      | **Waarde**                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| Database_Name            | Naam van de database voor ITA                                                         |
| Database_Username        | Gebruikersnaam voor toegang tot de database                                           |
| Database_Password        | Wachtwoord voor toegang tot de database                                               |
| Database_Host            | Hostnaam van de database server *(optioneel - alleen nodig als `postgresql.enabled=false`)* |

Theming
------------------

| Variabele                       | Omschrijving |
|--------------------------------|--------------|
| LOGO_URL          | Publiek URL waar het logo van de gemeente beschikbaar is, bijvoorbeeld: `https://www.mijn-gemeente.nl/logo.svg` |
| FAVICON_URL       | Publiek URL waar het favicon van de gemeente beschikbaar is, bijvoorbeeld: `https://www.mijn-gemeente.nl/favicon.ico` |
| DESIGN_TOKENS_URL  | Publiek URL waar het CSS-bestand met NL Design System tokens beschikbaar is, om de applicatie te stylen in gemeentehuisstijl, bijvoorbeeld: `https://unpkg.com/@gemeente/design-tokens/dist/index.css` |
| WEB_FONT_SOURCES   | Publiek URL – of meerdere door spaties gescheiden publieke URL's – als verwijzing naar web-font-bestand(en) horend bij de gemeentehuisstijl, bijvoorbeeld: `https://fonts.mijn-gemeente.nl/custom-regular-font.woff2 https://fonts.mijn-gemeente.nl/custom-bold-font.woff2`. Een enkele verwijzing naar de locatie waar alle font-style-bestanden staan kan ook: `https://fonts.mijn-gemeente.nl/custom-font/`. **Let op:** deze configuratie is alleen bedoeld om de font-bestanden onder CORS te kunnen inladen. Verwijzingen naar bestanden zullen ook in de theme styling onder een `@font-face` ruleset gespecificeerd moeten worden. |


Deze theming variabelen zijn allemaal optioneel.
