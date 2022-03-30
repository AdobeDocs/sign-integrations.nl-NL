---
title: Installatiegids voor koppeling
description: Installatiehandleiding voor het inschakelen van Adobe Sign-integratie met Coupa BSM Suite
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 12c91be5-afec-4918-a8fc-ceb33bedf98b
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 7%

---

# [!DNL Coupa] Installatiegids{#coupa-installation-guide}

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://adobe.com/go/adobesign-support-center_nl)

## Overzicht {#overview}

In dit document wordt uitgelegd hoe u uw Adobe Sign-account kunt configureren voor integratie [!DNL Coupa BSM Suite] -instantie voor het ophalen van handtekeningen.

Vereisten:

* Abonnement op Adobe Sign Enterprise; [Adobe Sign Developer Edition](https://www.adobe.com/sign/developer-form.html), of [Proefversie Adobe Sign Enterprise](https://www.adobe.com/sign/business.html)
* Toegang tot Adobe Sign-beheerder
* [!DNL Coupa BSM Suite] Standaard- of geavanceerde instantie

De stappen op hoog niveau om de integratie te voltooien zijn:

* Een Adobe Sign-groep configureren voor gebruik met [!DNL Coupa BSM Suite]
* Verbinden [!DNL Coupa BSM Suite] naar Adobe Sign
* Een Adobe Sign-webhook maken om uw [!DNL Coupa BSM Suite] instantie

## Adobe Sign Group configureren voor [!DNL Coupa BSM Suite] {#configure-adobe-sign-for-coupa}

Een specifiek gebruik van Adobe Sign voor [!DNL Coupa] binnen een organisatie moeten de beheerders een Adobe Sign-groep maken die specifiek is voor [!DNL Coupa BSM Suite] gebruik. Deze Adobe Sign-groep moet één gebruikersaccount voor groepsbeheerders hebben die fungeert als serviceaccount. Aangezien deze serviceaccount wordt gebruikt voor alle handtekeningverzoeken, moet deze bijvoorbeeld anoniem worden gehouden, `Legal@xyz.com`, `Purchasing@xyz.com`, of `CoupaCLM@xyz.com`, in plaats van persoonlijke, zoals `Bob.Smith@xyz.com`.

### Een groep en een gebruiker maken in Adobe Sign {#create-sign-user-group}

Een gebruiker maken in Adobe Sign:

1. Meld u als accountbeheerder aan bij Adobe Sign.
1. Navigeren naar **[!UICONTROL Account]** > **[!UICONTROL Gebruikers]**.
1. Als u een nieuwe gebruiker wilt maken, klikt u op de knop ![afbeelding met plusteken](images/icon_plus.png) pictogram.
1. Geef in het dialoogvenster dat wordt geopend de nieuwe gebruikersgegevens op:

   1. Geef een functionele e-mail die u kunt openen.

      * Deze gebruiker onderhoudt de OAuth-relatie.
      * Het e-mailadres moet een feitelijk adres zijn voor de verificatie.
   1. Voer de juiste waarden in voor [!UICONTROL Voornaam] en [!UICONTROL Achternaam].
   1. In het dialoogvenster [!UICONTROL Primaire groep] veld, selecteren **[!UICONTROL Een nieuwe groep maken voor deze gebruiker]**.
   1. In het dialoogvenster [!UICONTROL Nieuwe groepsnaam] veld, geef een intuïtieve groepsnaam op zoals *[!DNL Coupa BSM Suite]*.

   ![Het deelvenster Gebruiker maken](images/create-user.png)

1. Selecteren **[!UICONTROL Opslaan]**.

   Nadat u de gegevens hebt opgeslagen, [!UICONTROL Gebruikers] wordt de nieuwe gebruiker getoond met een [!UICONTROL GEMAAKT] status.

   ![Een weergave van de nieuwe gebruiker](images/post-user-creation.png)

   De [!UICONTROL GEMAAKT] geeft aan dat de gebruiker zijn e-mailadres nog niet heeft geverifieerd.

1. Het e-mailadres verifiëren:
   1. Meld u aan bij de e-mail van de nieuwe gebruiker.
   2. Zoek de e-mail &quot;Welkom bij Adobe Sign&quot;. Controleer indien nodig de spam- en junkmappen.
   3. Klik op **[!UICONTROL Klik hier om uw wachtwoord in te stellen]**
   4. Het wachtwoord instellen.

   Nadat u het e-mailadres hebt geverifieerd, verandert de status van de gebruiker in [!UICONTROL GEMAAKT] aan [!UICONTROL ACTIEF].

   ![Afbeelding van de nieuwe geactiveerde gebruiker](images/active-user.png)

### De verificatiegebruiker definiëren {#define-authenticating-user}

Als u een groep en een gebruiker in die groep hebt gemaakt, moet u van de gebruiker een &#39;groepsbeheerder&#39; maken.

Om de nieuwe gebruiker te promoten in de [!DNL Coupa BSM Suite] groep:

1. Navigeer naar de pagina [!UICONTROL Gebruikers] (als deze nog niet wordt afgebeeld).
2. Dubbelklik op de gebruiker.

   Het opent een [!UICONTROL Bewerken] pagina voor de gebruikersmachtigingen.

3. Selecteer onder de sectie Groepslidmaatschap de optie **[!UICONTROL Groepsbeheerder]** en **[!UICONTROL Kan verzenden]** opties.
4. Deselecteer de **[!UICONTROL Gebruiker is een accountbeheerder]** en **[!UICONTROL Gebruiker kan documenten ondertekenen]** opties.
5. Klik op **[!UICONTROL Opslaan]**.

   ![Afbeelding van gebruikersinstellingen](images/user-settings.png)

## Configureer de [!DNL Coupa BSM Suite] instantie {#configure-coupa}

Als u de verbinding wilt voltooien tussen de [!DNL Coupa BSM Suite ] -instantie en Adobe Sign moet een vertrouwde relatie tot stand worden gebracht tussen de services.

Om het [!DNL Coupa BSM Suite]:

1. Verbind uw [!DNL Coupa BSM Suite] -exemplaar naar uw Adobe Sign-serviceaccount dat u hierboven hebt gemaakt.
1. Maak een Adobe Sign-webhook-instantie om uw Coupa BSM Suite-instantie op de hoogte te stellen van updates van overeenkomsten.

Voor meer informatie over hoe u de [!DNL Coupa BSM Suite] en hoe u webhook maakt en registreert, raadpleegt u [Ondersteuningsdocumentatie voor Adobe Sign Coupa BSM Suite-instantie](https://success.coupa.com/Support/Docs/Power_Apps/CLM_Standard/Signing_and_Approvals/Enable_E-Signatures_Through_Adobe_Sign_and_DocuSign){target=&quot;_blank&quot;}.

## Maken [!DNL Webhook] in Adobe Sign {#create-webhook}

De Coupa CLM-integratie gebruikt webhookmeldingen van Adobe Sign om updates over de status van de overeenkomst te verzenden. Het is essentieel om de webhook-installatie te voltooien, anders blijven de overeenkomsten die ter ondertekening zijn verzonden onvolledig of worden de ondertekende overeenkomsten niet teruggestuurd naar Coupa CLM.

Webhook maken in Adobe Sign:

1. Meld u aan bij Adobe Sign met de hierboven gemaakte groepsbeheerder, bijvoorbeeld `coupaclm@MyDomain.com`.

1. Navigeren naar **Groepen** > **Webhooks**.

   ![Afbeelding van gebruikersinstellingen](images/webhook-login.png)

1. Als u een nieuwe verbinding wilt maken, selecteert u de optie ![afbeelding met plusteken](images/icon_plus.png) pictogram.

1. Vul de vereiste velden in in het dialoogvenster Maken dat wordt geopend.

   **Opmerking:** U moet de URL voor de webhookhandler opvragen bij Coupa.

   ![Afbeelding van gebruikersinstellingen](images/webhook-create.png)

1. Selecteer de vereiste berichtparameters.

1. Selecteren **Opslaan**.

## Ondersteuning {#support}

### [!DNL Coupa BSM Suite] ondersteuning {#coupa-support}

[!DNL Coupa BSM Suite ] is de eigenaar van de integratie en moet uw eerste contactpunt zijn voor vragen over de reikwijdte van de integratie, functieverzoeken of problemen in het dagelijks functioneren van de integratie.

Neem voor alle query&#39;s contact op met [Coupa-ondersteuning](https://success.coupa.com/Support/Welcome_to_Coupa_Support){target=&quot;_blank&quot;}.

### Adobe Sign-ondersteuning {#adobe-sign-support}

Adobe Sign is de integratiepartner en moet worden benaderd als de integratie geen handtekeningen krijgt of als het melden van handtekeningen in behandeling mislukt.

Voor hulp bij het gebruik of configureren van Adobe Sign kunt u contact opnemen met uw Customer Success Manager (CSM) of contact opnemen met [Adobe Sign-ondersteuning](https://adobe.com/go/adobesign-support-center).

Adobe Sign-beheerders kunnen ook tickets openen en ondersteuning verkrijgen via de Help (?) rechtsboven in de Adobe Sign-portal.

![Help op de Adobe Sign portal](images/sign-portal-help.png)
