.. _config_omgevingsvariabelen:

Omgevingsvariabelen
===================

OpenID Connect settings
---------------------------------
| **Variabele**                      | **Waarde**                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| internetaakafhandeling-web.config.oidc.authority            | URL van de OpenID Connect Identity Provider <details> <summary>Meer informatie </summary>Bijvoorbeeld: `https://login.microsoftonline.com/ce1a3f2d-2265-4517-a8b4-3e4f381461ab/v2.0` </details>         |
| internetaakafhandeling-web.config.oidc.clientId            | Voor toegang tot de OpenID Connect Identity Provider <details> <summary>Meer informatie </summary>Bijvoorbeeld: `54f66f54-71e5-45f1-8634-9158c41f602a` </details>  |
| internetaakafhandeling-web.config.oidc.clientSecret            | Secret voor de OpenID Connect Identity Provider <details> <summary>Meer informatie </summary>Bijvoorbeeld: `VM2B!ccnebNe.M*gxH63*NXc8iTiAGhp` </details>    |
| internetaakafhandeling-web.config.oidc.itaSystemAccessRole            | De waarde van de role claim in het JWT token van de OpenID Connect Provider voor toegang tot ITA <details> <summary>Meer informatie </summary>Bijvoorbeeld: `ITA-Gebruiker` </details>     |
| internetaakafhandeling-web.config.oidc.nameClaimType            | De naam van de claim in het JWT token van de OpenID Connect Provider waarin de volledige naam van de ingelogde gebruiker staat <br/> (default waarde is `name`) |
| internetaakafhandeling-web.config.oidc.roleClaimType            | De naam van de claim in het JWT token van de OpenID Connect Provider waarin de rollen van de ingelogde gebruiker staan. <br/> (default waarde is `roles`)  |
| internetaakafhandeling-web.config.oidc.idClaimType            | De naam van de claim in het JWT token van de OpenID Connect Provider waarin de unieke identificatie van de ingelogde gebruiker staat. <br/> (default waarde is `preferred_username` met een fallback op `email`)   |

Notificatie settings
---------------------------------

| **Variabele**                      | **Waarde**                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| internetaakafhandeling-poller.config.smtp.host            | Adres van uw mailserver                                                                                  |
| internetaakafhandeling-poller.config.smtp.port            | De poort waarover van uw mailserver benaderbaar is                                                      |
| internetaakafhandeling-poller.config.smtp.username        | Credentials voor toegang tot uw mailserver                                                               |
| internetaakafhandeling-poller.config.smtp.password        | Credentials voor toegang tot uw mailserver                                                               |
| internetaakafhandeling-poller.config.smtp.enableSsl       | true/false                                                                                                |
| internetaakafhandeling-poller.config.smtp.fromEmail       | Afzenderadres voor mails die door ITA verstuurd worden                                                   |

 
Koppelingen met externe registers
---------------------------------

ITA gaat ervan uit dat emailadressen van medewerkers en organisatorische eenheden in een overige objecten registratie te vinden zijn en voldoen aan deze formats:
- medewerker: https://github.com/open-objecten/objecttypes/blob/main/community-concepts/Medewerker/medewerker-schema.json
- groep: https://github.com/open-objecten/objecttypes/blob/main/community-concepts/Afdeling%20en%20Groep/groep-schema.json
- afdeling:  https://github.com/open-objecten/objecttypes/blob/main/community-concepts/Afdeling%20en%20Groep/afdeling-schema.json

| **Variabele**                      | **Waarde**                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| config.objectApi.baseUrl | https://uw-overige-objecten-adres.nl/api/v2/  |
| secrets.objectApiKey | min. 32 karakters  |
| config.openKlantApi.baseUrl | https://uw-openklant-adres/klantinteracties/api/v1/  |
| secrets.openKlantApiKey | min. 32 karakters  |
| config.zaakSysteem.baseUrl |  https://uw-zaaksysteem-adres.nl |
| config.zaakSysteem.clientId |   |
| secrets.zaakSysteemKey |  min. 32 karakters |


Database configuratie
---------------------------------
| **Variabele**                      | **Waarde**                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| config.database.name            | Naam van de database voor ITA                                                         |
| config.database.username        | Gebruikersnaam voor toegang tot de database                                           |
| secrets.databasePassword        | Wachtwoord voor toegang tot de database                                               |
| config.database.host            | Hostnaam van de database server *(optioneel - alleen nodig als `postgresql.enabled=false`)* |

Theming
------------------

| Variabele                       | Omschrijving |
|--------------------------------|--------------|
| internetaakafhandeling-web.config.resources.logoUrl          | Publiek URL waar het logo van de gemeente beschikbaar is, bijvoorbeeld: `https://www.mijn-gemeente.nl/logo.svg` |
| internetaakafhandeling-web.config.resources.faviconUrl       | Publiek URL waar het favicon van de gemeente beschikbaar is, bijvoorbeeld: `https://www.mijn-gemeente.nl/favicon.ico` |
| internetaakafhandeling-web.config.resources.designTokensUrl  | Publiek URL waar het CSS-bestand met NL Design System tokens beschikbaar is, om de applicatie te stylen in gemeentehuisstijl, bijvoorbeeld: `https://unpkg.com/@gemeente/design-tokens/dist/index.css` |
| internetaakafhandeling-web.config.resources.webFontSources   | Publiek URL – of meerdere door spaties gescheiden publieke URL's – als verwijzing naar web-font-bestand(en) horend bij de gemeentehuisstijl, bijvoorbeeld: `https://fonts.mijn-gemeente.nl/custom-regular-font.woff2 https://fonts.mijn-gemeente.nl/custom-bold-font.woff2`. Een enkele verwijzing naar de locatie waar alle font-style-bestanden staan kan ook: `https://fonts.mijn-gemeente.nl/custom-font/`. **Let op:** deze configuratie is alleen bedoeld om de font-bestanden onder CORS te kunnen inladen. Verwijzingen naar bestanden zullen ook in de theme styling onder een `@font-face` ruleset gespecificeerd moeten worden. |


Deze theming variabelen zijn allemaal optioneel.
