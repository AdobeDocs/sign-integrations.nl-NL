---
title: Installatiegids Workday
description: Installatiegids voor het inschakelen van de integratie van Adobe Sign met Workday
uuid: 56478222-fe66-4fa5-aac3-0ecdf2863197
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 29d55a25-6e2f-4c59-ae7c-c21bb82cecba
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8f12b524-2123-45d4-98d5-b2b23580a5ea
source-git-commit: d462ccf41fa5483cfa02f5eaf154c23f26157a1e
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 25%

---

# [!DNL Workday] Installatiegids{#workday-installation-guide}

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://adobe.com/go/adobesign-support-center_nl)

## Overzicht {#overview}

In dit document wordt uitgelegd hoe u Adobe Sign kunt integreren in uw [!DNL Workday] tenant. Als u Adobe Sign wilt gebruiken binnen [!DNL Workday], moet u weten hoe u [!DNL Workday]-items kunt maken en wijzigen, zoals:

* Kader voor bedrijfsprocessen
* Instelling en configuratie van de tenant
* Rapportage en studio-integratie [!DNL Workday]

De stappen op hoog niveau om de integratie te voltooien zijn:

* Activeer uw beheeraccount in Adobe Sign (alleen voor nieuwe klanten)
* Configureer een groep in Adobe Sign om de integratiegebruiker [!DNL Workday] vast te houden
* De OAuth-relatie tussen [!DNL Workday] en Adobe Sign tot stand brengen

## Uw Adobe Sign-account activeren {#activating-your-adobe-sign-account}

Bestaande klanten met een accountsysteem kunnen het [Adobe Sign configureren voor het onderwerp  [!DNL Workday]](#config) overslaan.

Voor klanten die nog geen ervaring hebben met Adobe Sign en die nog niet eerder zijn aangemeld, kan een Adobe on-boarding specialist uw account (in Adobe Sign) voorzien voor [!DNL Workday]. Na voltooiing ontvangt u een bevestigingsbericht zoals hieronder getoond.

![Afbeelding van de welkomste-mail van Adobe Sign](images/welcome-email-2020.png)

U moet de aanwijzingen in de e-mail volgen om uw account te initialiseren en toegang te krijgen tot uw Adobe Sign [!UICONTROL startpagina].

![De pagina met het dashboard van Adobe Sign](images/classic-home.png)

## Adobe Sign configureren voor [!DNL Workday] {#config}

Als u Adobe Sign wilt configureren voor [!DNL Workday], moet u de volgende twee speciale objecten genereren in het Adobe Sign-systeem:

* **Een  [!DNL Workday] groep**:  [!DNL Workday] vereist een speciale &quot;groep&quot; binnen het Adobe Sign-account om integratiefunctionaliteit in te schakelen. De Adobe Sign-groep wordt gebruikt om alleen het [!DNL Workday]-gebruik van Adobe Sign te beheren. Dit heeft geen invloed op enig ander mogelijk gebruik, zoals Salesforce.com of Arriba. De e-mailmeldingen worden onderdrukt in de [!DNL Workday]-groep, zodat de [!DNL Workday]-gebruikers alleen meldingen ontvangen binnen hun [!DNL Workday]-postvak.

* **Een verificerende gebruiker die de integratiesleutel** vasthoudt: Een  [!DNL Workday] groep moet slechts één beheerder op groepsniveau hebben, die de gezaghebbende houder van de integratiesleutel is. We raden de beheerder aan een functioneel e-mailadres zoals `HR@MyDomain.com` te gebruiken in plaats van een persoonlijke e-mail om het risico te verkleinen dat de gebruiker in de toekomst wordt uitgeschakeld en daardoor de integratie wordt uitgeschakeld.

### Een gebruiker en groep maken in Adobe Sign {#create-a-user-and-group-in-adobe-sign}

Een gebruiker maken in Adobe Sign:

1. Meld u als accountbeheerder aan bij Adobe Sign.
1. Navigeer naar **[!UICONTROL Account]** > **[!UICONTROL Gebruikers]**.
1. Klik op de ![afbeelding met het plusteken](images/icon_plus.png) om een nieuwe gebruiker te maken.

   ![Afbeelding van het navigatiepad voor het maken van een nieuwe gebruiker](images/navigate-to-group-unbranded.png)

1. Geef in het dialoogvenster dat wordt geopend de nieuwe gebruikersgegevens op:

   * Geef een functionele e-mail die u kunt openen.
   * Voer een toepasselijke waarde in voor de voor- en achternaam.
   * Selecteer **[!UICONTROL Een nieuwe groep maken voor deze gebruiker]** in de gebruikersgroep.
   * Geef de **[!UICONTROL Nieuwe groepsnaam]** een intuïtieve naam, zoals *[!DNL Workday]*.

   ![Het deelvenster Gebruiker maken](images/create-user.png)

1. Klik op **[!UICONTROL Opslaan]**.

   Hiermee keert u terug naar de pagina [!UICONTROL Users] waarin de nieuwe gebruiker met de status **[!UICONTROL CREATED]** wordt vermeld.

   ![Een weergave van de nieuwe gebruiker](images/post-user-creation.png)

Het e-mailadres van de gebruiker verifiëren met de status &quot;Gemaakt&quot;:

1. Meld u aan bij de e-mail van de nieuwe gebruiker.
2. Zoek de e-mail &quot;Welkom bij Adobe Sign&quot;.
3. Klik op **[!UICONTROL Klik hier om uw wachtwoord in te stellen]**.
4. Het wachtwoord instellen.

Nadat u het e-mailadres hebt geverifieerd, verandert de status van de gebruiker van [!UICONTROL CREATED] in [!UICONTROL ACTIVE].

![Afbeelding van de nieuwe geactiveerde gebruiker](images/actived-users-575.png)

### De verificatiegebruiker definiëren {#define-the-authenticating-user}

De nieuwe gebruiker promoveren in de groep [!DNL Workday]:

1. Navigeer naar de pagina [!UICONTROL Gebruikers] (als deze nog niet wordt afgebeeld).
2. Dubbelklik op de gebruiker in de groep [!DNL Workday].

   Hiermee opent u een [!UICONTROL pagina Bewerken] voor de gebruikersmachtigingen.

3. Controleer **[!UICONTROL Groepsbeheerder]**.
4. Klik op **[!UICONTROL Opslaan]**.

![](images/user-permissions-edit1-575.png)

## Configureer de [!DNL Workday] tenant {#configure-workday}

Om de verbinding tussen de [!DNL Workday] tenant en Adobe Sign te voltooien, moeten we een vertrouwde relatie tussen de services tot stand brengen. Als u klaar bent, kunt u een stap Document controleren toevoegen waarmee het ondertekeningsproces via Adobe Sign wordt geactiveerd.

>[!NOTE]
>
>Adobe Sign is in de gehele [!DNL Workday]-omgeving voorzien van het merk Adobe Document Cloud.

De vertrouwde relatie tot stand brengen:

1. Meld u bij [!DNL Workday] aan als accountbeheerder.
1. Open de pagina **[!UICONTROL Tenant instellen bewerken - Bedrijfsprocessen]**.
1. Zoek de sectie [!UICONTROL Configuratie elektronische handtekening]:

   ![](images/esignature_configurations.png)

1. Klik op **[!UICONTROL Verifiëren met Adobe]**.

   Dit begint de OAuth2.0 authentificatiereeks.

1. Geef desgevraagd de gegevens op voor de Adobe Sign Group-beheerder die u eerder hebt gemaakt.
1. Goedkeuren van de toegang tot Adobe Sign.

>[!NOTE]
>
>Zorg ervoor dat u zich volledig afmeldt bij een andere Adobe Sign-instantie voordat u verdergaat.

Als de verbinding tot stand is gebracht, is het selectievakje Adobe-configuratie ingeschakeld geselecteerd en kunt u Adobe Sign gebruiken met [!DNL Workday].

### De stap Review Document Step configureren {#configure-review}

Het document voor de stap Review Document Step kan een van de volgende zijn:

* Een statisch document
* Een document dat is gegenereerd door een stap Document genereren binnen hetzelfde bedrijfsproces
* Een opgemaakt rapport dat is gemaakt met de rapportontwerpfunctie [!DNL Workday]

U kunt al deze documenten toevoegen met [Adobe-tekstcodes](https://adobe.com/go/adobesign_text_tag_guide_nl) om de vormgeving en positie van de specifieke onderdelen voor Adobe-ondertekening te bepalen. De documentbron moet zijn opgegeven in de definitie van het bedrijfsproces. Het is niet mogelijk om een ad-hocdocument te uploaden terwijl het bedrijfsproces wordt uitgevoerd.

Uniek aan het gebruik van Adobe Sign met een stap Document bekijken is de mogelijkheid om ondertekenaarsgroepen met serienummering te hebben. Op deze manier kunt u functiegebonden groepen opgeven die documenten op volgorde ondertekenen. Adobe Sign ondersteunt geen parallelle ondertekeningsgroepen.

Voor hulp die de Stap van het Document van het Overzicht vormt, verwijs naar [Snelle gids van het Begin](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}.

## Ondersteuning {#support}

### [!DNL Workday] ondersteuning {#workday-support}

[!DNL Workday] is de eigenaar van de integratie en fungeert als uw eerste contactpunt voor vragen over het bereik van de integratie, voor verzoeken om functies of in geval van problemen met het dagelijks functioneren van de integratie.

U kunt de volgende [!DNL Workday]-communityartikelen raadplegen over het oplossen van problemen met de integratie en het genereren van documenten:

* [Problemen met e-handtekeningintegraties oplossen](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [stap Documenten bekijken](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamisch genereren van documenten](https://community.workday.com/saml/login?destination=/articles/176443)
* [Tips voor het genereren van documenten](https://community.workday.com/node/183242)

### Adobe Sign-ondersteuning {#adobe-sign-support}

Adobe Sign is de integratiepartner en u dient contact op te nemen met Adobe Sign als de integratie geen handtekeningen kan verkrijgen of als de kennisgeving voor handtekeningen in de wachtrij mislukt.

Klanten van Adobe Sign dienen contact op te nemen met hun CSM (Customer Success Manager) voor ondersteuning. U kunt ook de technische ondersteuning van Adobe bellen: 1-866-318-4100, wachten tot de lijst met producten wordt opgesomd en bij de aanwijzingen eerst op 4 en dan op 2 drukken.

* [Adobe-tekstcodes toevoegen aan documenten](https://adobe.com/go/adobesign_text_tag_guide)
* [Documentconfiguratie en voorbeelden](https://experienceleague.adobe.com/docs/dc-sign-integrations/using/workday/quick-start.html?lang=en) bekijken{target=&quot;_blank&quot;}

## Algemene vragen {#faq}

### Waarom wordt de status niet bijgewerkt binnen [!DNL Workday], zelfs niet wanneer het document volledig is ondertekend? {#why-is-the-status-not-being-updated-within-workday-even-the-document-is-fully-signed}

De documentstatus in [!DNL Workday] wordt mogelijk niet weergegeven als de kandidaat niet op de knop &#39;[!UICONTROL Verzenden]&#39; klikt na het aanmelden in Adobe Sign.

Volgens de taak van [!DNL Workday] Status van elektronische ondertekening controleren: Om het proces te starten, kan de gebruiker de bijbehorende Inbox-taak verzenden.

Conform ontwikkeling [!DNL Workday]: De oorspronkelijke ondertekening wordt alleen voltooid als de gebruiker de inbox-taak verzendt na ondertekening van het document. Na ondertekening wordt het iframe gesloten en wordt de gebruiker omgeleid naar dezelfde taak, waar hij of zij op de knop [!UICONTROL Verzenden] kan klikken om het proces te voltooien.
