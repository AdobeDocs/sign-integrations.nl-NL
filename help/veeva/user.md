---
title: Handboek voor Veva Vault
description: Gebruikershandleiding voor Veeva Vault-klanten over hoe Adobe Sign-integratie met Veeva kan worden gebruikt
products: Adobe Sign
content-type: reference
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 39a43637-af3f-432e-a784-8f472aa86df5
source-git-commit: 63a34c2d77ba7a262670da624c86a3730de0fdc5
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 3%

---

# Adobe Sign voor [!DNL Veeva Vault]: Handboek {#veeva-vault-user-guide}

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://adobe.com/go/adobesign-support-center_nl)

Dit document is ontworpen om [!DNL Veeva Vault] klanten te helpen bij het gebruik van Adobe Sign voor integratie [!DNL Veeva Vault] om een overeenkomst te verzenden.

## Overzicht {#overview}

Adobe Sign-integratie met [!DNL Veeva Vault] vergemakkelijkt het proces voor het verkrijgen van een handtekening of goedkeuring voor alle documentatie waarvoor geldige handtekeningen of controleerbare documentverwerking vereist zijn.

Het verzenden van documenten ter ondertekening lijkt op het verzenden van een e-mail, dus is het voor de meeste gebruikers gemakkelijk om deze te gebruiken.

Adobe Sign-integratie met [!DNL Veeva Vault] stroomlijnt en versnelt je document- en ondertekeningsworkflows. Door de integratieworkflow te gebruiken, kunt u:

* Bespaar tijd en resources die worden besteed aan slakkenpost, spoedberichten en faxen.
* Verzend contracten ter elektronische ondertekening of goedkeuring vanuit [!DNL Veeva Vault], open real-time contractgeschiedenis en bekijk opgeslagen contracten.
* Volg de deals in real-time binnen uw organisatie en krijg updates wanneer overeenkomsten worden bekeken, ondertekend, geannuleerd of geweigerd.
* eSign-ondertekening in meer dan 20 talen en ondersteuning voor terugfaxen op meer dan 50 locaties wereldwijd.
* Maak herbruikbare overeenkomstsjablonen voor verzendopties.

## Een overeenkomst verzenden met Adobe Sign voor [!DNL Veeva Vault] {#send-sign-vault-agreement}

Een overeenkomst verzenden met Adobe Sign for Veeva:

1. Ga naar de [[!DNL Veeva Vault] aanmeldingspagina](https://login.veevavault.com/) en voer uw gebruikersnaam en wachtwoord in. De startpagina van uw Vault wordt geopend, zoals hieronder wordt weergegeven.

   ![](images/vault-home.png)

1. Selecteer het tabblad **[!UICONTROL Bibliotheek]** en selecteer vervolgens **[!UICONTROL Maken]** in de rechterbovenhoek.

   ![](images/create-library.png)

1. Selecteer **[!UICONTROL Uploaden en doorgaan]**.

1. Upload elk document vanaf uw lokale station.

1. Selecteer **[!UICONTROL Type]** als *[!UICONTROL Klinisch]* in het dialoogvenster dat verschijnt en selecteer vervolgens een **[!UICONTROL Subtype]** en **[!UICONTROL Classificatie]**, indien nodig.

   ![](images/choose-document-type.png)

1. Selecteer **[!UICONTROL Ok]** om het dialoogvenster te sluiten.

1. Selecteer **[!UICONTROL Volgende]**.

1. Vul in het weergegeven venster alle vereiste velden in de sectie met metagegevens in en selecteer **[!UICONTROL Opslaan]**.

   ![](images/metadata-details.png)

1. Er wordt een testdocument gemaakt met de status **[!UICONTROL Draft]**, zoals hieronder weergegeven.

   ![](images/document-draft.png)

1. Selecteer in de rechterbovenhoek ![tandwielpictogram](images/icon-gear.png) in het vervolgkeuzemenu en selecteer **[!UICONTROL Revisie starten]**.

   ![](images/start-review.png)

1. Selecteer de **[!UICONTROL Reviewer]** en **[!UICONTROL Vervaldatum controleren]**.

1. Selecteer **[!UICONTROL Start]**. De documentstatus wordt gewijzigd in [!UICONTROL IN REVIEW].

   ![](images/in-review.png)

1. Voltooi de toegewezen taak namens de revisoren. Als u klaar bent, wordt de documentstatus gewijzigd in [!UICONTROL REVIEWED].

   ![](images/reviewed-status.png)

1. Selecteer ![tandwielpictogram](images/icon-gear.png) vervolgkeuzemenu en selecteer **[!UICONTROL Adobe Sign]**.

   ![](images/select-adobe-sign.png)

1. Voer in het iFrame-venster dat wordt geopend in Vault het e-mailadres van de ontvanger in en selecteer **[!UICONTROL Volgende]**.

   ![](images/iframe.png)

1. Als het document is verwerkt, sleept u de handtekeningvelden naar het rechterdeelvenster en selecteert u **[!UICONTROL Verzenden]**.

   ![](images/add-signature-fields.png)

1. Het document wordt ter ondertekening naar de ontvanger gestuurd. Zodra de ontvanger het document per e-mail ontvangt, verandert de documentstatus van [!UICONTROL Reviewed] in [!UICONTROL In Adobe Signing].

   ![](images/in-adobe-signing.png)

1. Zodra alle handtekeningen zijn vastgelegd en ingevuld in Adobe Sign, verandert de documentstatus in Vault in [!UICONTROL Goedgekeurd].

1. Selecteer de optie **[!UICONTROL Documentbestanden]** en vouw de sectie **[!UICONTROL Vertoningen]** in de vault uit. Er wordt automatisch een nieuwe Vertoning met de naam &#39;Adobe Sign Rendition&#39; gemaakt als het document de status Goedgekeurd heeft.

   ![](images/document-files.png)

1. Download de Adobe Sign-vertoning voor het valideren van de ontvanger.

   ![](images/verify-signature.png)

## Een overeenkomst annuleren met Adobe Sign voor [!DNL Veeva Vault] {#cancel-sign-vault-agreement}

1. Ga naar de [[!DNL Veeva Vault] aanmeldingspagina](https://login.veevavault.com/) en voer uw gebruikersnaam en wachtwoord in. De startpagina van uw Vault wordt geopend, zoals hieronder wordt weergegeven.

   ![](images/vault-home.png)

1. Selecteer het tabblad **[!UICONTROL Bibliotheek]** en selecteer vervolgens het document. De documentstatus kan zijn: [!UICONTROL In Adobe Sign Draft], [!UICONTROL In Adobe Sign Authoring] of [!UICONTROL In Adobe Signing].

   ![](images/document-adobe-sign-authoring.png)

1. Selecteer **[!UICONTROL Adobe Sign annuleren]**.

   ![](images/cancel-document.png)

1. De webhandeling wordt geactiveerd en het iFrame-venster wordt geladen in [!UICONTROL Vault].

   ![](images/cancelled-document.png)

1. De documentstatus verandert automatisch in [!UICONTROL Revisie].

   ![](images/cancel-reviewed.png)

Nadat de documentstatus is gewijzigd in Revisie, kunt u deze opnieuw verzenden ter ondertekening.
