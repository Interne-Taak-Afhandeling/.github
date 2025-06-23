===========
Objecttypen
===========

ITA slaat de history rondom de afhandeling van een internetaak op in de Objecten API.
Hiertoe wordt het onderstaande Logboek objecttype gebruikt. 
Bij de installatie van ITA moet men ervoor zorgen dat dit objecttype aanwezig is in een Objecttypen API en dat deze correct geregistreerd is in de Objecten API. 
Zie de documentatie (https://objects-and-objecttypes-api.readthedocs.io/en/latest/) voor instructies. 

Logboek objecttype
------------------

.. code-block:: json

    {
      "type": "object",
      "title": "activiteitenlog",
      "$schema": "http://json-schema.org/draft-07/schema#",
      "examples": [],
      "required": [
        "heeftBetrekkingOp",
        "activiteiten"
      ],
      "properties": {
        "activiteiten": {
          "type": "array",
          "items": {
            "type": "object",
            "title": "Activiteit",
            "required": [
              "datum",
              "type",
              "omschrijving"
            ],
            "properties": {
              "type": {
                "type": "string",
                "title": "Type",
                "description": "Vaste waardes waarmee verschillende de soorten activiteiten herkend kunnen worden. Bijvoorbeeld: 'afsluiting' of 'toewijzing'"
              },
              "actor": {
                "type": "object",
                "title": "Actor",
                "required": [
                  "codeRegister",
                  "codeObjecttype",
                  "codeSoortObjectId",
                  "objectId"
                ],
                "properties": {
                  "objectId": {
                    "type": "string",
                    "description": "De waarde van het veld, bijvoorbeeld: 'een.naam@degemeente.nl"
                  },
                  "codeRegister": {
                    "type": "string",
                    "title": "De naam van het register",
                    "description": "Naam van het register waarin het object is geregistreerd, bijvoorbeeld: 'entraId'"
                  },
                  "codeObjecttype": {
                    "type": "string",
                    "title": "De naam van het soort object in het register",
                    "description": "Type van het object: bijvoorbeeld: 'user'"
                  },
                  "codeSoortObjectId": {
                    "type": "string",
                    "title": "De naam van het veld van het object",
                    "description": "Naam van het identificerende veld in het object, bijvoorbeeld: 'Id'."
                  }
                },
                "description": "Verwijzing naar de persoon die dit item aan deze log heeft toegevoegd"
              },
              "datum": {
                "type": "string",
                "title": "Datum",
                "format": "date-time",
                "description": "De datum waarop dit item is toegevoegd aan de log."
              },
              "notitie": {
                "type": "string",
                "title": "Notitie",
                "description": "Informatie over deze activiteit"
              },
              "omschrijving": {
                "type": "string",
                "title": "Omschrijving",
                "description": "Gebruiksvriendelijke informatieve omschrijving van de soort activiteit."
              },
              "heeftBetrekkingOp": {
                "type": "array",
                "items": {
                  "type": "object",
                  "title": "Object",
                  "required": [
                    "codeRegister",
                    "codeObjecttype",
                    "codeSoortObjectId",
                    "objectId"
                  ],
                  "properties": {
                    "objectId": {
                      "type": "string",
                      "description": "De waarde van het veld"
                    },
                    "codeRegister": {
                      "type": "string",
                      "title": "De naam van het register",
                      "description": "Naam van het register waarin het object is geregistreerd, bijvoorbeeld: 'OpenKlant-v2'"
                    },
                    "codeObjecttype": {
                      "type": "string",
                      "title": "De naam van het soort object in het register",
                      "description": "Type van het object, bijvoorbeeld Klantcontact"
                    },
                    "codeSoortObjectId": {
                      "type": "string",
                      "title": "De naam van het veld van het object",
                      "description": "Naam van het identificerende veld in het object, bijvoorbeeld: 'id'."
                    }
                  },
                  "description": "Verwijzing naar een object waar deze activiteit betrekking op heeft. Bijvoorbeeld een klantcontact of een medewerker"
                },
                "title": "heeftBetrekking op",
                "description": "Lijst van objecten waar deze activiteit betrekking op heeft. Bijvoorbeeld een klantcontacten en medewerkers"
              }
            },
            "description": "Activiteit"
          },
          "title": "Activiteiten",
          "description": "Lijst van activiteiten"
        },
        "heeftBetrekkingOp": {
          "type": "object",
          "title": "Het object waar deze activiteitenlog betrekking op heeft",
          "required": [
            "codeRegister",
            "codeObjecttype",
            "codeSoortObjectId",
            "objectId"
          ],
          "properties": {
            "objectId": {
              "type": "string",
              "title": "De waarde in het bij codeSoortObjectId aangeduide veld ",
              "description": "De waarde van het veld, bijvoorbeeld: '575fc9e4-a73c-495b-a8a1-1e718656e847'"
            },
            "codeRegister": {
              "type": "string",
              "title": "De naam van het register",
              "description": "Naam van het register waarin het object is geregistreerd, bijvoorbeeld: 'OpenKlant'"
            },
            "codeObjecttype": {
              "type": "string",
              "title": "De naam van het soort object in het register",
              "description": "Type van het object, bijvoorbeeld: internetaak"
            },
            "codeSoortObjectId": {
              "type": "string",
              "title": "De naam van het veld in het objecttype",
              "description": "Naam van het identificerende veld in het object, bijvoorbeeld: 'uuid'"
            }
          },
          "description": "Dit is een referentie naar het object waar deze activiteitenlog betrekking op heeft, bijvoorbeeld een interne taak"
        }
      }
    }  

                     
