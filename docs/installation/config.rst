.. _config_omgevingsvariabelen:

Omgevingsvariabelen
===================


Theming variabelen
------------------

* ``RESOURCES:LOGO_URL`` : publiek URL waar het logo van de gemeente beschikbaar is, bijvoorbeeld: ``https://www.mijn-gemeente.nl/logo.svg``
* ``RESOURCES:FAVICON_URL`` : publiek URL waar het favicon van de gemeente beschikbaar is, bijvoorbeeld: ``https://www.mijn-gemeente.nl/favicon.ico``
* ``RESOURCES:DESIGN_TOKENS_URL`` : publiek URL waar het css-bestand met NL Design System tokens beschikbaar is, om de applicatie te stylen in gemeentehuisstijl, bijvoorbeeld: ``https://unpkg.com/@gemeente/design-tokens/dist/index.css``
* ``RESOURCES:WEB_FONT_SOURCES`` : publiek URL - of meerdere door spaties gescheiden publieke URL's - als verwijzing naar web-font-bestand(en) horend bij de gemeentehuisstijl, bijvoorbeeld: ``https://fonts.mijn-gemeente.nl/custom-regular-font.woff2 https://fonts.mijn-gemeente.nl/custom-bold-font.woff2``. Een enkele verwijzing naar de locatie waar alle font-style-bestanden staan kan ook: ``https://fonts.mijn-gemeente.nl/custom-font/``. **Let op:** deze configuratie is alleen bedoeld om de font-bestanden onder CORS te kunnen inladen. Verwijzingen naar bestanden zullen ook in de theme styling onder een @font-face ruleset gespecificeerd moeten worden.

* Deze theming variabelen zijn allemaal optioneel.
