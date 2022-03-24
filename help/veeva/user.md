---
title: Handboek voor Veva Vault
description: Gebruikershandleiding voor Veeva Vault-klanten over hoe Adobe Sign-integratie met Veeva kan worden gebruikt
products: Adobe Sign
content-type: reference
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Acrobat Sign, Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 39a43637-af3f-432e-a784-8f472aa86df5
source-git-commit: b326a9afa2c16333d390cac3b30a2c7c741a4360
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---

# Adobe Sign for [!DNL Veeva Vault]: Handboek {#veeva-vault-user-guide}

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://adobe.com/go/adobesign-support-center_nl)

Dit document is ontworpen om [!DNL Veeva Vault] klanten leren Adobe Sign gebruiken voor [!DNL Veeva Vault] integratie voor het verzenden van een overeenkomst.

## Overzicht {#overview}

Adobe Sign-integratie met [!DNL Veeva Vault] vergemakkelijkt het proces voor het verkrijgen van een handtekening of goedkeuring voor documentatie waarvoor geldige handtekeningen of controleerbare documentverwerking vereist zijn.

Het verzenden van documenten ter ondertekening lijkt op het verzenden van een e-mail, dus is het voor de meeste gebruikers gemakkelijk om deze te gebruiken.

Adobe Sign-integratie met [!DNL Veeva Vault] stroomlijnt en versnelt je document- en ondertekeningsworkflows. Door de integratieworkflow te gebruiken, kunt u:

* Bespaar tijd en resources die worden besteed aan slakkenmails, spoedberichten of faxen.
* Verzend contracten ter elektronische ondertekening of goedkeuring van [!DNL Veeva Vault]hebt toegang tot real-time contractgeschiedenis en bekijkt opgeslagen contracten.
* Volg de deals in real-time binnen uw organisatie en krijg updates wanneer overeenkomsten worden bekeken, ondertekend, geannuleerd of geweigerd.
* eSign-ondertekening in meer dan 20 talen en ondersteuning voor terugfaxen op meer dan 50 locaties wereldwijd.
* Maak herbruikbare overeenkomstsjablonen voor verzendopties.

## Een overeenkomst verzenden met Adobe Sign voor [!DNL Veeva Vault] {#send-sign-vault-agreement}

Een overeenkomst verzenden met Adobe Sign for Veeva:

1. Ga naar de [[!DNL Veeva Vault] aanmeldingspagina](https://login.veevavault.com/) en voer uw gebruikersnaam en wachtwoord in. De startpagina van uw Vault wordt geopend, zoals hieronder wordt weergegeven.

   ![](images/vault-home.png)

1. Selecteren **[!UICONTROL Bibliotheek]** en selecteer vervolgens **[!UICONTROL Maken]** in de rechterbovenhoek.

   ![](images/create-library.png)

1. Selecteren **[!UICONTROL Uploaden en doorgaan]**.

1. Upload elk document vanaf uw lokale station.

1. Selecteer in het dialoogvenster dat verschijnt **[!UICONTROL Type]** als *[!UICONTROL Klinisch]* en selecteer vervolgens een **[!UICONTROL Subtype]** en **[!UICONTROL Classificatie]**, indien nodig.

   ![](images/choose-document-type.png)

1. Selecteren **[!UICONTROL OK]** om het dialoogvenster te sluiten.

1. Selecteren **[!UICONTROL Volgende]**.

1. Vul in het weergegeven venster alle vereiste velden in de sectie Metagegevens in en selecteer **[!UICONTROL Opslaan]**.

   ![](images/metadata-details.png)

1. Er wordt een testdocument gemaakt in **[!UICONTROL Concept]** zoals hieronder weergegeven.

   ![](images/document-draft.png)

1. Selecteer in de rechterbovenhoek de optie ![tandwielpictogram](images/icon-gear.png) vervolgkeuzemenu en selecteer **[!UICONTROL Revisie starten]**.

   ![](images/start-review.png)

1. Selecteer de **[!UICONTROL Revisor]** en **[!UICONTROL Vervaldatum bekijken]**.

1. Selecteren **[!UICONTROL Starten]**. De documentstatus wordt gewijzigd in [!UICONTROL IN REVISIE].

   ![](images/in-review.png)

1. Voltooi de toegewezen taak namens de revisoren. Als u klaar bent, verandert de documentstatus in [!UICONTROL GECONTROLEERD].

   ![](images/reviewed-status.png)

1. Selecteren ![tandwielpictogram](images/icon-gear.png) vervolgkeuzemenu en selecteer **[!UICONTROL Adobe Sign]**.

   ![](images/select-adobe-sign.png)

1. Voer in het iFrame-venster dat wordt geopend in Vault het e-mailadres van de ontvanger in en selecteer **[!UICONTROL Volgende]**.

   ![](images/iframe.png)

   **Opmerking:** Als er geen Adobe Sign-gebruikersaccount voor de e-mail van de afzender bestaat, wordt in het iFrame-venster een bericht weergegeven, zoals hieronder wordt weergegeven. Het stuurt de gebruiker ook een e-mail met de instructies om het account te activeren.

   ![](images/iFrame-registration-message.png)

   ![](images/iFrame-confirm-email.png)

   Als *Gebruikers automatisch toewijzen* -functie is uitgeschakeld, het maken van Adobe Sign-gebruikers mislukt en het iFrame-venster toont een bericht waarin de gebruiker wordt gevraagd contact op te nemen met de Adobe Sign-accountbeheerder. De Adobe Sign-accountbeheerder kan een van de volgende handelingen uitvoeren:

   * Schakel het *Gebruikers automatisch toewijzen* voor het account.
   * Maak een gebruiker in Adobe Sign voordat u de Veva Vault Adobe Sign Integration gebruikt.

   ![](images/iFrame-contact-administrator.png)

1. Als het document is verwerkt, sleept u de handtekeningvelden uit het rechterdeelvenster en selecteert u **[!UICONTROL Verzenden]**.

   ![](images/add-signature-fields.png)

1. Het document wordt ter ondertekening naar de ontvangers gestuurd. Zodra de ontvanger de e-mail met het document ontvangt, verandert de documentstatus van [!UICONTROL Gereviseerd] aan [!UICONTROL In Adobe-ondertekening].

   ![](images/in-adobe-signing.png)

1. Zodra alle handtekeningen zijn vastgelegd en ingevuld in Adobe Sign, verandert de documentstatus in Vault in [!UICONTROL Goedgekeurd].

1. Selecteren **[!UICONTROL Documentbestanden]** en breid de **[!UICONTROL Uitvoeringen]** in Vault. Er wordt automatisch een nieuwe Vertoning met de naam &#39;Adobe Sign Rendition&#39; gemaakt als het document de status Goedgekeurd heeft.

   ![](images/document-files.png)

1. Download de Adobe Sign-vertoning voor het valideren van de ontvanger.

   ![](images/verify-signature.png)

## Een overeenkomst annuleren met Adobe Sign for [!DNL Veeva Vault] {#cancel-sign-vault-agreement}

1. Ga naar de [[!DNL Veeva Vault] aanmeldingspagina](https://login.veevavault.com/) en voer uw gebruikersnaam en wachtwoord in. De startpagina van uw Vault wordt geopend, zoals hieronder wordt weergegeven.

   ![](images/vault-home.png)

1. Selecteren **[!UICONTROL Bibliotheek]** en selecteert u het document. De documentstatus kan zijn: [!UICONTROL In Adobe Sign Draft], [!UICONTROL In Adobe Sign Authoring], of [!UICONTROL In Adobe-ondertekening].

   ![](images/document-adobe-sign-authoring.png)

1. Selecteren **[!UICONTROL Adobe Sign annuleren]**.

   ![](images/cancel-document.png)

1. Het activeert de webhandeling en laadt het iFrame-venster in [!UICONTROL Vault].

   ![](images/cancelled-document.png)

1. De documentstatus verandert automatisch in [!UICONTROL Revisie].

   ![](images/cancel-reviewed.png)

Nadat de documentstatus is gewijzigd in Revisie, kunt u deze opnieuw verzenden ter ondertekening.
