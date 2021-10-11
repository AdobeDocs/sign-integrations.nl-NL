---
title: Opmerkingen bij de release van Adobe Sign for NetSuite
description: Lees meer over de nieuwe functies en wijzigingen die zijn opgenomen in de huidige versie van de Adobe Sign-integratie voor NetSuite.
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 6317723e-447a-4506-a621-4d967bdd6561
source-git-commit: f8d0bc748872e675dc1c638eb4050efe9e3147ef
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 5%

---

# Opmerkingen bij de release van Adobe Sign for NetSuite

## Bijwerken naar pakket v4.0.4

4.0.4 is volledig aangepast aan het gebruik van accountspecifieke domeinen voor alle nieuw gegenereerd verkeer.

Het Adobe Sign-pictogram is bijgewerkt naar de nieuwe afbeelding.

## Vorige versies

### Adobe Sign for NetSuite 4.0.4

4.0.4 is volledig aangepast aan het gebruik van accountspecifieke domeinen voor alle nieuw gegenereerd verkeer.

Het Adobe Sign-pictogram is bijgewerkt naar de nieuwe afbeelding.

### Adobe Sign for NetSuite 4.0.2

Opnieuw gebrandd tot **Adobe Sign** (van *Adobe Document Cloud eSign-services*)\
U ziet nu *Adobe Sign* waar u eerder *eSign Services voor Adobe hebt gezien* als bewijs van de herbranding.

### Adobe Sign for NetSuite 4.0.1

Vanwege een API-regressiefout die is geïntroduceerd toen NetSuite de platformupdate uitvoerde, is een nieuw pakket (v4.0.1) uitgebracht.

Klanten worden aangeraden om de update naar het nieuwste pakket uit te voeren.

### Adobe Sign for NetSuite 4.0

**Automatische provisioning van gebruikers toegevoegd via NetSuite**

Er is een nieuwe aangepaste voorkeur toegevoegd voor v4.0. Als deze optie is ingeschakeld, worden gebruikers die overeenkomsten verzenden in NetSuite automatisch toegewezen aan een gebruikersaccount voor de Adobe Document Cloud eSign-services.

**Gecertificeerd met &#39;Built for NetSuite&#39;**

Deze versie heeft de certificering &#39;Built for NetSuite&#39; behaald en voldoet aan de nieuwste best practices voor het ontwerp van NetSuite.

**Opnieuw gebrandmerkt naar eSign-services van Adobe Document Cloud (vanuit EchoSign)**

U ziet nu Adobe Document Cloud eSign Services (of Adobe eSign Services voor kort), waar u Adobe EchoSign eerder als bewijs van de herbranding zag.

**Uitgebreide beveiliging met OAuth**

Om de gegevensbeveiliging te verbeteren, maken eSign-services nu gebruik van OAuth 2.0 om uw Adobe Document Cloud eSign-serviceaccount binnen NetSuite te verifiëren. Met dit nieuwe protocol kan NetSuite communiceren met eSign-services zonder dat u een wachtwoord voor uw eSign-services hoeft in te voeren. Aangezien gevoelige informatie niet rechtstreeks tussen de apps gedeeld wordt, is het minder waarschijnlijk dat derden toegang tot uw account krijgen. Deze verbetering heeft geen invloed op uw implementatie, maar u moet wel een eenmalige installatie uitvoeren om uw NetSuite-pakket te autoriseren voor communicatie met de Adobe Document Cloud. Dit gebeurt tijdens het installatieproces. Voor klanten die een upgrade uitvoeren vanaf een eerdere versie van het pakket, v3.5.9 en ouder, wordt de eerder gebruikte API-sleutel vervangen door een OAuth-token dat tijdens het autorisatieproces wordt gegenereerd.

**De eSign-services zijn gemigreerd van SOAP-API&#39;s naar REST-API&#39;s**

Om de efficiëntie, flexibiliteit en verwerkingssnelheid te verbeteren, zijn de eSign-services van Adobe Document Cloud, en daarmee de v4.0-integratie voor NetSuite, overgestapt van SOAP-gebaseerde naar REST-gebaseerde API&#39;s.

### Adobe Sign for NetSuite 3.0

**Geavanceerde deelnemersrollen - fiatteur**

* Een of meer ontvangers kunnen worden gemarkeerd als fiatteur(s) in een overeenkomst
* Fiatteurs moeten het document reviseren en goedkeuren
* Fiatteurs kunnen ook worden verplicht gegevens in te vullen in de overeenkomst voordat ze deze goedkeuren

**Documentvoorbeeld weergeven of formuliervelden slepen en neerzetten voordat ze worden verzonden**

Voorbeeld van overeenkomst bekijken of formuliervelden slepen en neerzetten voordat deze ter ondertekening worden verzonden

**Herinnering verzenden naar huidige ondertekenaar**

Directe herinnering verzenden aan huidige ondertekenaar

**Geavanceerd handtekeningverificatiebeleid**

* **Verificatie op basis van kennis:vragen** beantwoorden om identiteit van ondertekenaar te verifiëren
   * Ondertekenaars moeten hun identiteit bewijzen door vragen te beantwoorden uit honderden openbare en commerciële databases
   * Naam ter ondertekening is overgenomen van de geverifieerde naam van de gebruiker en kan niet worden gewijzigd op het moment van ondertekening
   * Aangedreven door RSA
   * Het KBA-gebruik is beperkt per account, per maand. Neem contact op met Sales voor meer informatie.

* **Webidentiteit:** Meld u aan met Facebook, LinkedIn, Google of een andere externe webservice voordat u zich aanmeldt.

   * Ondertekenaars kunnen alleen ondertekenen nadat ze hun identiteit hebben geverifieerd met een webservice van derden.
   * Naam ter ondertekening is afkomstig van de webservice-professional van de gebruiker!le en kan niet worden gewijzigd op het moment van ondertekening
   * Audittrail legt identiteitsverificatiedetails vast

* **Eenmalig wachtwoord**
   * Pas verificatiemethoden toe voor interne of externe ondertekenaars of alle ondertekenaars. Externe ondertekenaars moeten een wachtwoord gebruiken of verificatie op basis van kennis gebruiken, terwijl interne ondertekenaars dat niet doen

**Aanvullende aangepaste voorkeuren**

* Ondertekende PDF toevoegen als een koppeling naar de URL of als bijlage die wordt gehost in NetSuite
* Audittrail toevoegen aan overeenkomstrecord a$er-overeenkomst is ondertekend
* Gebruik de transactiecontacten standaard als ondertekenaar, in plaats van de e-mail van de klant
* Afzenders de optie geven om ontvangers te markeren als fiatteurs

**Transactiebestanden**

U kunt bestanden die u wilt bijvoegen, selecteren in de huidige transactie met de nieuwe vervolgkeuzelijst Transactiebestanden.

**Adobe PDF-certificatie voor alle EchoSign-documenten**

* Alle PDF-bestanden die vanuit EchoSign worden verzonden of gedownload, zijn gecertificeerd met een Adobe EchoSign Digital Certificate
* Acrobat of Reader geeft de certificering weer die garandeert dat er niet met het document is geknoeid om het vertrouwen en de gemoedsrust te vergroten

**Ondersteunende documenten verzamelen**

* Afzenders kunnen tijdens de ondertekening aanvullende ondersteunende documenten van ondertekenaars verzamelen, zoals een rijbewijs, bedrijfscertificaat en meer.
* Verzamelde documenten worden onderdeel van de officiële record van de ondertekende overeenkomst

**Voorwaardelijke gegevensvelden**

* Voorwaardelijke logica voor overeenkomstvelden definiëren
* Voorwaarden kunnen worden gebaseerd op waarden voor een of meer velden in de overeenkomst
* Voorwaarden kunnen worden uitgeschakeld via de gebruikersinterface voor het schrijven van formulieren via slepen en neerzetten of via tekstlabels
* De ondertekenaar krijgt de juiste velden te zien wanneer hij een document ondertekent op basis van de &#39;de!ned&#39;-voorwaarden

**Overige verbeteringen in EchoSign-formuliervelden**

* Vervolgkeuzemenu&#39;s
* Veldmaskering
* Keuzerondjes
* Korte tekstcodes maken om de documentstructuur te behouden
