---
title: Adobe Sign-integraties - Productversies en levenscyclus
description: Meer informatie over Adobe Sign Integrations-versies en de levenscyclus van ondersteuning
audience: External
products: Adobe Sign
type: Documentation
solution: Acrobat Sign, Adobe Sign
role: User, Developer
topic: Integrations
exl-id: c1f22848-7951-4066-84d4-f8cf6c2f3a6f
source-git-commit: b326a9afa2c16333d390cac3b30a2c7c741a4360
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 40%

---

# Productversies en levenscyclus {#version}

De versieovereenkomst van Adobe Sign en de steunlevenscyclus voor de geïntegreerde diensten richten zich op andere producten van de Adobe die u met kunt vertrouwd zijn.

## Versienummers

De pakketversie geeft aan de hand van een uit drie delen bestaand nummer het sequentiële buildnummer van de uitgebrachte versie en het relatieve belang van de upgrade in termen van nieuwe of veranderde content aan.

Het versienummer volgt dit patroon: N.m.p

Waar, N = hoofdversie; m = kleine versie; p = Patchversie.

Zo geeft een integratiepakket versie 23.2.1 een releasestatus aan van:

* Hoofdversie: 23
* Kleine versie: 2
* Patchversie: 1

Terwijl engineers nieuwe &#39;builds&#39; van het pakket ontwikkelen, verhogen ze het versienummer op basis van de aard van de updates van de code.

* Belangrijke wijzigingen van de versie omvatten een belangrijke toevoeging aan functies of een belangrijke wijziging in de kernsystemen.
* Kleine versie-updates bevatten kleinere functie-updates en beveiligingspatches. Adobe Sign kan een upgrade naar de nieuwste patchversie vereisen in het geval van beveiligingsupdates of om een gemeld item te verhelpen.
* Patchversies bevatten bijna uitsluitend gecorrigeerde bugs en aanpassingen van de interface

>[!NOTE]
>
>Niet alle versies worden vrijgegeven voor het publiek terwijl het product zich in ontwikkeling herhaalt. Er kunnen dus belangrijke sprongen zijn in de patchversie tussen releases.

De beheerders moeten hun versie up-to-date houden om ervoor te zorgen dat het account volledige toegang heeft tot alle functies en alle bekende beveiligingsproblemen worden gepatcheerd. Adobe Sign kan een upgrade naar de nieuwste patchversie vereisen in het geval van beveiligingsproblemen of om een essentieel systeemprobleem op te lossen.

## Levenscyclus versieondersteuning

De levenscyclus van versieondersteuning van een Adobe Sign-integratieproduct wordt gedefinieerd op basis van de hoofdversie van het pakket en geeft het tijdsbestek aan waarin Adobe Sign de afzonderlijke versie van de integratie actief ondersteunt.

Adobe Sign ondersteunt de huidige versie van een pakket en de vorige twee hoofdversies (inclusief alle bijbehorende kleine en patchupdates). Hoofdversies worden als volgt uitgedrukt:

* Huidige versie (N): de nieuwste hoofdversie van het pakket
* Vorige versie (N-1): de hoofdversie voorafgaand aan de huidige versie
* Laatst ondersteunde versie (N-2): de twee hoofdversies voorafgaand aan de huidige versie

Als de huidige beschikbare versie van het pakket bijvoorbeeld 23.2.1 is, geldt het volgende:

* Huidige hoofdversie (N) is 23
* De vorige hoofdversie (N-1) van dit pakket is 22
* De laatste ondersteunde hoofdversie (N-2) van dit pakket is 21
* Versies ouder dan 21.0.0 worden niet ondersteund

![Versiegrafiek](images/version_chart.png)

## Levenscyclus versieservice

De levenscyclus voor de service van een productversie definieert het volledige bereik waarin de service kan worden gebruikt. De tijdlijn komt overeen met de levenscyclus voor de ondersteuning van de productversie, inclusief een coulanceperiode van 90 dagen waarin klanten hun upgrade kunnen voltooien.

* Tijdens de coulanceperiode van een niet-ondersteunde versie, geldt de ondersteuning alleen voor de upgrade naar een nieuwere versie, niet voor onderhoud aan een niet-ondersteunde versie
* Na de respijtperiode is de versie niet meer beschikbaar

* Adobe Sign accepteert geen verzoeken voor versies waarvoor de service niet meer geldt
* Nadat de integratie is bijgewerkt naar de huidige versie, wordt alle communicatie tussen Adobe Sign en de integratie normaal hervat

![Sluitingperiode](images/shutdown_period.png)

Neem bij vragen contact op met uw verkoper of de klantenondersteuning.
