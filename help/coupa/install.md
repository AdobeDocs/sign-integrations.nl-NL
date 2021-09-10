---
title: Installatiegids voor koppeling
description: Installatiehandleiding voor het inschakelen van Adobe Sign-integratie met Coupa BSM Suite
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 12c91be5-afec-4918-a8fc-ceb33bedf98b
source-git-commit: 623307e86f1b32edfbfa59dbd636ff74a6d09b62
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 7%

---

# [!DNL Coupa] Installatiegids{#coupa-installation-guide}

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://adobe.com/go/adobesign-support-center_nl)

## Overzicht {#overview}

In dit document wordt uitgelegd hoe u uw Adobe Sign-account configureert voor het integreren van een [!DNL Coupa BSM Suite]-exemplaar voor het verkrijgen van handtekeningen.

Vereisten:

* Abonnement op Adobe Sign Enterprise, [Adobe Sign Developer Edition](https://www.adobe.com/sign/developer-form.html) of [Adobe Sign Enterprise-proefversie](https://www.adobe.com/sign/business.html)
* Toegang tot Adobe Sign-beheerder
* [!DNL Coupa BSM Suite] Standaard- of geavanceerde instantie

De stappen op hoog niveau om de integratie te voltooien zijn:

* Een Adobe Sign-groep configureren voor gebruik met [!DNL Coupa BSM Suite]
* [!DNL Coupa BSM Suite] verbinden met Adobe Sign
* Een Adobe Sign-webhook maken voor het melden van uw [!DNL Coupa BSM Suite]-instantie

## Adobe Sign-groep configureren voor [!DNL Coupa BSM Suite] {#configure-adobe-sign-for-coupa}

Als u een specifieke toepassing van Adobe Sign voor [!DNL Coupa] binnen een organisatie wilt gebruiken, moeten de beheerders een Adobe Sign-groep maken die specifiek bedoeld is voor [!DNL Coupa BSM Suite]-gebruik. Deze Adobe Sign-groep moet één gebruikersaccount voor groepsbeheerders hebben die fungeert als serviceaccount. Aangezien dit serviceaccount wordt gebruikt voor alle handtekeningverzoeken, moet het anoniem blijven, bijvoorbeeld `Legal@xyz.com`, `Purchasing@xyz.com` of `CoupaCLM@xyz.com`, in plaats van persoonlijk, zoals `Bob.Smith@xyz.com`.

### Een groep en een gebruiker maken in Adobe Sign {#create-sign-user-group}

Een gebruiker maken in Adobe Sign:

1. Meld u als accountbeheerder aan bij Adobe Sign.
1. Navigeer naar **[!UICONTROL Account]** > **[!UICONTROL Gebruikers]**.
1. Als u een nieuwe gebruiker wilt maken, klikt u op het pictogram ![plus afbeelding](images/icon_plus.png).
1. Geef in het dialoogvenster dat wordt geopend de nieuwe gebruikersgegevens op:

   1. Geef een functionele e-mail die u kunt openen.

      * Deze gebruiker onderhoudt de OAuth-relatie.
      * Het e-mailadres moet een feitelijk adres zijn voor de verificatie.
   1. Voer de juiste waarden in voor [!UICONTROL Voornaam] en [!UICONTROL Achternaam].
   1. Selecteer **[!UICONTROL Een nieuwe groep maken voor deze gebruiker in het veld [!UICONTROL Primaire groep].]**
   1. Geef in het veld [!UICONTROL Nieuwe groepsnaam] een intuïtieve groepsnaam op, bijvoorbeeld *[!DNL Coupa BSM Suite]*.

   ![Het deelvenster Gebruiker maken](images/create-user.png)

1. Selecteer **[!UICONTROL Opslaan]**.

   Nadat u de gegevens hebt opgeslagen, wordt op de pagina [!UICONTROL Users] de nieuwe gebruiker met de status [!UICONTROL CREATED] weergegeven.

   ![Een weergave van de nieuwe gebruiker](images/post-user-creation.png)

   De status [!UICONTROL CREATED] geeft aan dat de gebruiker zijn e-mailadres nog niet heeft geverifieerd.

1. Het e-mailadres verifiëren:
   1. Meld u aan bij de e-mail van de nieuwe gebruiker.
   2. Zoek de e-mail &quot;Welkom bij Adobe Sign&quot;. Controleer indien nodig de spam- en junkmappen.
   3. Klik op **[!UICONTROL Klik hier om uw wachtwoord in te stellen]**
   4. Het wachtwoord instellen.

   Nadat u het e-mailadres hebt geverifieerd, verandert de status van de gebruiker van [!UICONTROL CREATED] in [!UICONTROL ACTIVE].

   ![Afbeelding van de nieuwe geactiveerde gebruiker](images/active-user.png)

### De verificatiegebruiker definiëren {#define-authenticating-user}

Als u een groep en een gebruiker in die groep hebt gemaakt, moet u van de gebruiker een &#39;groepsbeheerder&#39; maken.

De nieuwe gebruiker promoveren in de groep [!DNL Coupa BSM Suite]:

1. Navigeer naar de pagina [!UICONTROL Gebruikers] (als deze nog niet wordt afgebeeld).
2. Dubbelklik op de gebruiker.

   Er wordt een [!UICONTROL pagina Bewerken] geopend voor de gebruikersmachtigingen.

3. Selecteer onder de sectie Groepslidmaatschap de opties **[!UICONTROL Groepsbeheerder]** en **[!UICONTROL Kan verzenden]**.
4. Schakel de optie **[!UICONTROL Gebruiker is een accountbeheerder]** uit en **[!UICONTROL Gebruiker kan documenten ondertekenen]**.
5. Klik op **[!UICONTROL Opslaan]**.

   ![Afbeelding van gebruikersinstellingen](images/user-settings.png)

## Configureer de [!DNL Coupa BSM Suite]-instantie {#configure-coupa}

Als u de verbinding tussen de [!DNL Coupa BSM Suite ]-instantie en Adobe Sign wilt voltooien, moet er een vertrouwde relatie tot stand worden gebracht tussen de services.

De [!DNL Coupa BSM Suite] configureren:

1. Sluit uw [!DNL Coupa BSM Suite]-exemplaar aan op uw Adobe Sign-serviceaccount die u hierboven hebt gemaakt.
1. Maak een Adobe Sign-webhook-instantie om uw Coupa BSM Suite-instantie op de hoogte te stellen van updates van overeenkomsten.

Raadpleeg [Adobe Sign Coupa BSM Suite Instance support documentation](https://success.coupa.com/Support/Docs/Power_Apps/CLM_Standard/Signing_and_Approvals/Enable_E-Signatures_Through_Adobe_Sign_and_DocuSign){target=&quot;_blank&quot;} voor meer informatie over het maken van een verbinding met de [!DNL Coupa BSM Suite] en over het maken en registreren van een webhook.

## [!DNL Webhook] maken in Adobe Sign {#create-webhook}

De Coupa CLM-integratie gebruikt webhookmeldingen van Adobe Sign om updates over de status van de overeenkomst te verzenden. Het is essentieel om de webhook-installatie te voltooien, anders blijven de overeenkomsten die ter ondertekening zijn verzonden onvolledig of worden de ondertekende overeenkomsten niet teruggestuurd naar Coupa CLM.

Webhook maken in Adobe Sign:

1. Meld u aan bij Adobe Sign met de hierboven gemaakte groepsbeheerder, bijvoorbeeld `coupaclm@MyDomain.com`.

1. Navigeer naar **Groepen** > **Webhooks**.

   ![Afbeelding van gebruikersinstellingen](images/webhook-login.png)

1. Als u een nieuwe verbinding wilt maken, selecteert u het pictogram ![plus afbeelding](images/icon_plus.png).

1. Vul de vereiste velden in in het dialoogvenster Maken dat wordt geopend.

   **Opmerking:** U moet de URL voor de webhookhandler opvragen bij Coupa.

   ![Afbeelding van gebruikersinstellingen](images/webhook-create.png)

1. Selecteer de vereiste berichtparameters.

1. Selecteer **Opslaan**.

## Ondersteuning {#support}

### [!DNL Coupa BSM Suite] ondersteuning {#coupa-support}

[!DNL Coupa BSM Suite ] is de eigenaar van de integratie en moet uw eerste contactpunt zijn voor vragen over de reikwijdte van de integratie, functieverzoeken of problemen in het dagelijks functioneren van de integratie.

Voor om het even welke vragen, contacteer [Steun ](https://success.coupa.com/Support/Welcome_to_Coupa_Support){target=&quot;_blank&quot;}.

### Adobe Sign-ondersteuning {#adobe-sign-support}

Adobe Sign is de integratiepartner en moet worden benaderd als de integratie geen handtekeningen krijgt of als het melden van handtekeningen in behandeling mislukt.

Neem voor hulp bij het gebruik of configureren van Adobe Sign contact op met uw Customer Success Manager (CSM) of neem contact op met de [Adobe Sign-ondersteuning](https://adobe.com/go/adobesign-support-center).

Adobe Sign-beheerders kunnen ook tickets openen en ondersteuning verkrijgen via de Help (?) rechtsboven in de Adobe Sign-portal.

![Help op de Adobe Sign portal](images/sign-portal-help.png)
