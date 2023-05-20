---
title: Workday-installatiegids
description: Installatiehandleiding voor het inschakelen van de Adobe Sign-integratie met Workday
uuid: 56478222-fe66-4fa5-aac3-0ecdf2863197
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 29d55a25-6e2f-4c59-ae7c-c21bb82cecba
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 8f12b524-2123-45d4-98d5-b2b23580a5ea
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 0%

---

# [!DNL Workday] Installatiehandleiding{#workday-installation-guide}

[**Contact opnemen met Adobe Sign-ondersteuning**](https://adobe.com/go/adobesign-support-center)

## Overzicht {#overview}

In dit document wordt uitgelegd hoe u Adobe Sign kunt integreren in uw [!DNL Workday] tenant. Adobe Sign gebruiken in [!DNL Workday], moet u weten hoe u kunt maken en wijzigen [!DNL Workday] items zoals:

* Kader voor bedrijfsprocessen
* Instelling en configuratie van de tenant
* Rapportage en [!DNL Workday] studio-integratie

De stappen op hoog niveau om de integratie te voltooien zijn:

* Activeer uw beheeraccount in Adobe Sign (alleen voor nieuwe klanten)
* Configureer een groep in Adobe Sign die de [!DNL Workday] integratiegebruiker
* De OAuth-relatie tussen [!DNL Workday] en Adobe Sign

## Uw Adobe Sign-account activeren {#activating-your-adobe-sign-account}

Bestaande klanten met een vaste account kunnen overslaan naar de [Adobe Sign configureren voor [!DNL Workday]](#config) onderwerp.

Voor klanten die nog geen ervaring hebben met Adobe Sign en die nog niet eerder zijn aangemeld, kan een Adobe on-boarding-specialist uw account (in Adobe Sign) voorzien van [!DNL Workday]. Na voltooiing ontvangt u een bevestigingsbericht zoals hieronder getoond.

![Afbeelding van de welkomstmail van Adobe Sign](images/welcome-email-2020.png)

U moet de aanwijzingen in de e-mail volgen om uw account te initialiseren en toegang te krijgen tot uw Adobe Sign [!UICONTROL Home] pagina.

![De Adobe Sign-dashboardpagina](images/classic-home.png)

## Adobe Sign configureren voor [!DNL Workday] {#config}

Adobe Sign configureren voor [!DNL Workday]moet u de volgende twee speciale objecten genereren in het Adobe Sign-systeem:

* **A [!DNL Workday] groep**: [!DNL Workday] vereist een speciale &quot;groep&quot; binnen het Adobe Sign-account om integratiefunctionaliteit in te schakelen. De Adobe Sign-groep wordt gebruikt om alleen de [!DNL Workday] gebruik van Adobe Sign. Dit heeft geen invloed op enig ander mogelijk gebruik, zoals Salesforce.com of Arriba. De e-mailmeldingen worden onderdrukt in [!DNL Workday] groep zodat de [!DNL Workday] gebruikers ontvangen alleen meldingen binnen hun [!DNL Workday] inbox.

* **Een verificerende gebruiker die de integratiesleutel vasthoudt**: A [!DNL Workday] de groep moet slechts één beheerder op groepsniveau hebben, die de gezaghebbende houder van de integratiesleutel is. We raden de beheerder aan een functioneel e-mailadres te gebruiken, zoals `HR@MyDomain.com` in plaats van een persoonlijke e-mail om het risico te verminderen dat de gebruiker in de toekomst wordt uitgeschakeld en daardoor de integratie wordt uitgeschakeld.

### Een gebruiker en groep maken in Adobe Sign {#create-a-user-and-group-in-adobe-sign}

Een gebruiker maken in Adobe Sign:

1. Meld u aan bij Adobe Sign als accountbeheerder.
1. Navigeren naar **[!UICONTROL Account]** > **[!UICONTROL Gebruikers]**.
1. Klik op ![afbeelding met plusteken](images/icon_plus.png) om een nieuwe gebruiker te maken.

   ![Afbeelding van het navigatiepad om een nieuwe gebruiker te maken](images/navigate-to-group-unbranded.png)

1. Geef in het dialoogvenster dat wordt geopend de nieuwe gebruikersgegevens op:

   * Geef een functionele e-mail die u kunt openen.
   * Voer de juiste waarde voor Voornaam en Achternaam in.
   * Selecteren **[!UICONTROL Een nieuwe groep maken voor deze gebruiker]** in de gebruikersgroep.
   * Geef de **[!UICONTROL Nieuwe groepsnaam]** met een intuïtieve naam zoals *[!DNL Workday]*.

   ![Het deelvenster Gebruiker maken](images/create-user.png)

1. Klikken **[!UICONTROL Opslaan]**.

   Het brengt je terug naar de [!UICONTROL Gebruikers] pagina met een lijst van de nieuwe gebruiker met een **[!UICONTROL GEMAAKT]** status.

   ![Een weergave van de nieuwe gebruiker](images/post-user-creation.png)

Het e-mailadres van de gebruiker verifiëren met de status &quot;Gemaakt&quot;:

1. Meld u aan bij de e-mail van de nieuwe gebruiker.
2. Zoek de e-mail &quot;Welkom bij Adobe Sign&quot;.
3. Klik op de plaats waar de tekst staat **[!UICONTROL Klik hier om uw wachtwoord in te stellen]**.
4. Stel het wachtwoord in.

Nadat u het e-mailadres hebt geverifieerd, verandert de status van de gebruiker in [!UICONTROL GEMAAKT] aan [!UICONTROL ACTIEF].

![Afbeelding van de nieuwe geactiveerde gebruiker](images/actived-users-575.png)

### De verificatiegebruiker definiëren {#define-the-authenticating-user}

Om de nieuwe gebruiker te promoten in de [!DNL Workday] groep:

1. Navigeer naar de [!UICONTROL Gebruikers] pagina (indien nog niet aanwezig).
2. Dubbelklik op de gebruiker in het dialoogvenster [!DNL Workday] groep.

   Dit opent een [!UICONTROL Bewerken] pagina voor de gebruikersmachtigingen.

3. Controleer de **[!UICONTROL Groepsbeheerder]**.
4. Klikken **[!UICONTROL Opslaan]**.

![](images/user-permissions-edit1-575.png)

## Configureer de [!DNL Workday] huurder {#configure-workday}

Als u de verbinding wilt voltooien tussen de [!DNL Workday] tenant en Adobe Sign, moeten we een vertrouwde relatie tussen de services tot stand brengen. Als u klaar bent, kunt u een stap Document controleren toevoegen waarmee het ondertekeningsproces via Adobe Sign wordt geactiveerd.

>[!NOTE]
>
>Adobe Sign is overal in de [!DNL Workday] milieu.

De vertrouwde relatie tot stand brengen:

1. Meld u aan bij [!DNL Workday] als accountbeheerder.
1. Open de **[!UICONTROL Tenant instellen bewerken - Bedrijfsprocessen]** pagina.
1. Zoek de [!UICONTROL Configuratie van e-handtekeningen] sectie:

   ![](images/esignature_configurations.png)

1. Klikken **[!UICONTROL Verifiëren met Adobe]**.

   Dit begint de OAuth2.0 authentificatiereeks.

1. Geef desgevraagd de gegevens op voor de Adobe Sign Group-beheerder die u eerder hebt gemaakt.
1. Goedkeuren van de toegang tot Adobe Sign.

>[!NOTE]
>
>Zorg ervoor dat u zich volledig afmeldt bij een andere Adobe Sign-instantie voordat u verdergaat.

Nadat de Adobe-configuratie is ingeschakeld, is het selectievakje ingesteld en kunt u Adobe Sign gebruiken met [!DNL Workday].

### De stap Review Document Step configureren {#configure-review}

Het document voor de stap Review Document Step kan een van de volgende zijn:

* Een statisch document
* Een document dat is gegenereerd door een stap Document genereren binnen hetzelfde bedrijfsproces
* Een opgemaakt rapport dat is gemaakt met de [!DNL Workday] Rapportontwerper

U kunt al deze documenten toevoegen met [Adobe-tekstlabels](https://adobe.com/go/adobesign_text_tag_guide) om het uiterlijk en de positie van de specifieke componenten voor ondertekening door de Adobe te bepalen. De documentbron moet worden opgegeven binnen de definitie van het bedrijfsproces. Het is niet mogelijk om een ad-hocdocument te uploaden terwijl het bedrijfsproces wordt uitgevoerd.

Uniek aan het gebruik van Adobe Sign met een stap Document bekijken is de mogelijkheid om ondertekenaarsgroepen met serienummering te hebben. Hiermee kunt u op rollen gebaseerde groepen opgeven die zich op volgorde aanmelden. Adobe Sign ondersteunt geen parallelle ondertekeningsgroepen.

Voor hulp bij het configureren van de stap Review Document Step, raadpleegt u de [Gids Aan de slag](https://adobe.com//go/adobesign_workday_quick_start){target="_blank"}.

## Ondersteuning {#support}

### [!DNL Workday] ondersteuning {#workday-support}

[!DNL Workday] is de eigenaar van de integratie en moet uw eerste contactpunt zijn voor vragen over de reikwijdte van de integratie, functieverzoeken of problemen in het dagelijks functioneren van de integratie.

U kunt naar het volgende verwijzen [!DNL Workday] communityartikelen over het oplossen van problemen met de integratie en het genereren van documenten:

* [Problemen met e-handtekeningintegraties oplossen](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [stap Documenten bekijken](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamisch genereren van documenten](https://community.workday.com/saml/login?destination=/articles/176443)
* [Tips voor het genereren van documenten](https://community.workday.com/node/183242)

### Adobe Sign-ondersteuning {#adobe-sign-support}

Adobe Sign is de integratiepartner en moet worden benaderd als de integratie geen handtekeningen krijgt of als het melden van handtekeningen in behandeling mislukt.

Adobe Sign-klanten moeten contact opnemen met hun Customer Success Manager (CSM) voor ondersteuning. U kunt ook telefonisch bij Technische ondersteuning voor Adobe terecht komen: 1-866-318-4100, wacht op productlijst dan ga binnen: 4 en vervolgens 2 (naar wens).

* [Adobe-tekstcodes toevoegen aan documenten](https://adobe.com/go/adobesign_text_tag_guide)
* [Documentconfiguratie en voorbeelden bekijken](https://www.adobe.com//go/adobesign_workday_quick_start)

## Algemene vragen {#faq}

### Waarom wordt de status niet bijgewerkt binnen [!DNL Workday] zelfs wanneer het document volledig is ondertekend? {#why-is-the-status-not-being-updated-within-workday-even-the-document-is-fully-signed}

De documentstatus in [!DNL Workday] kan niet reflecteren als de kandidaat niet op de knop &quot;[!UICONTROL Verzenden]&#39; na aanmelden in Adobe Sign.

Als [!DNL Workday] taak Status e-handtekening ondertekenen controleren: Om het proces te starten, kan de gebruiker de bijbehorende Inbox-taak verzenden.

Als [!DNL Workday] Ontwikkeling: De oorspronkelijke ondertekening wordt alleen voltooid als de gebruiker de inbox-taak verzendt na ondertekening van het document. Na ondertekening wordt het iframe gesloten en wordt de gebruiker omgeleid naar dezelfde taak waar hij of zij op de knop [!UICONTROL Verzenden] om het proces te voltooien.
