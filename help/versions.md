---
title: Adobe Sign-integraties - Productversies en levenscyclus
description: Meer informatie over Adobe Sign Integrations-versies en de levenscyclus van ondersteuning
audience: External
products: Adobe Sign
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: c1f22848-7951-4066-84d4-f8cf6c2f3a6f
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Productversies en levenscyclus {#version}

De versieovereenkomst van Adobe Sign en de steunlevenscyclus voor de geïntegreerde diensten richten zich op andere producten van de Adobe die u met kunt vertrouwd zijn.

## Versienummers

De pakketversie gebruikt een nummeringssysteem met drie delen om het opeenvolgende buildnummer van de vrijgegeven versie en de relatieve import van de upgrade in termen van nieuwe of veranderende inhoud te identificeren.

Het versienummer volgt dit patroon: N.m.p

Waar, N = hoofdversie; m = kleine versie; p = Patchversie.

Zo geeft een integratiepakket versie 23.2.1 een releasestatus aan van:

* Hoofdversie: 23
* Kleine versie: 2
* Patchversie: 1

Terwijl engineers nieuwe &#39;builds&#39; van het pakket ontwikkelen, verhogen ze het versienummer op basis van de aard van de updates van de code.

* Belangrijke wijzigingen van de versie omvatten een belangrijke toevoeging aan functies of een belangrijke wijziging in de kernsystemen.
* Kleine versie-updates bevatten kleinere functie-updates en beveiligingspatches. Adobe Sign kan een upgrade naar de nieuwste patchversie vereisen in het geval van beveiligingsupdates of om een gemeld item te verhelpen.
* Patchversies zijn vrijwel uitsluitend oplossingen voor problemen en UI-aanpassingen

>[!NOTE]
>
>Niet alle versies worden vrijgegeven voor het publiek terwijl het product zich in ontwikkeling herhaalt. Er kunnen dus belangrijke sprongen zijn in de patchversie tussen releases.

De beheerders moeten hun versie up-to-date houden om ervoor te zorgen dat het account volledige toegang heeft tot alle functies en alle bekende beveiligingsproblemen worden gepatcheerd. Adobe Sign kan een upgrade naar de nieuwste patchversie vereisen in het geval van beveiligingsproblemen of om een essentieel systeemprobleem op te lossen.

## Levenscyclus versieondersteuning

De levenscyclus van versieondersteuning van een Adobe Sign-integratieproduct wordt gedefinieerd op basis van de hoofdversie van het pakket en geeft het tijdsbestek aan waarin Adobe Sign de afzonderlijke versie van de integratie actief ondersteunt.

Adobe Sign ondersteunt de huidige versie van een pakket en de vorige twee hoofdversies (inclusief alle bijbehorende kleine en patchupdates). De belangrijkste versies worden als volgt uitgedrukt:

* Huidige versie (N): De nieuwste hoofdversie van het pakket
* Vorige versie (N-1): Eén grote versie achter de nieuwste versie
* Laatste ondersteunde versie (N-2): Twee belangrijke versies achter de huidige versie

Als de huidige beschikbare versie van het pakket bijvoorbeeld 23.2.1 is, geldt het volgende:

* Huidige hoofdversie (N) is 23
* De vorige hoofdversie (N-1) van dit pakket is 22
* Laatste ondersteunde hoofdversie (N-2) van dit pakket is 21
* Elke versie ouder dan 21.0.0 wordt niet ondersteund

![Versiesdiagram](images/version_chart.png)

## Levenscyclus versieservice

De levenscyclus van de versiedienst bepaalt het volledige werkingsgebied van wanneer de dienst bruikbaar is. De tijdlijn komt overeen met de levenscyclus van versieondersteuning en voegt een respijtperiode van 90 dagen toe waarmee klanten hun upgrade kunnen voltooien.

* Tijdens de evaluatieperiode van een niet-ondersteunde versie wordt alleen ondersteuning geboden voor het uitvoeren van een upgrade naar een nieuwere versie, niet voor het onderhouden van een niet-ondersteunde versie
* Na de respijtperiode is de versie niet meer beschikbaar

* Adobe Sign accepteert geen aanvragen van versies die niet meer in gebruik zijn
* Zodra de integratie is bijgewerkt naar de huidige versie, worden de communicatie tussen Adobe Sign en de integratie normaal hervat

![Afsluitperiode](images/shutdown_period.png)

Neem contact op met uw leverancier of klantenondersteuning als u vragen hebt.
