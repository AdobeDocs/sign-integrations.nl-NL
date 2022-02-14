---
title: '[!DNL Veeva Vault] Installatiegids'
description: Installatiehandleiding voor de integratie van Adobe Sign met Veeva
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 5d61a428-06e4-413b-868a-da296532c964
source-git-commit: db0d9022e520e9db39254e78b66aab8b913f353a
workflow-type: tm+mt
source-wordcount: '3169'
ht-degree: 3%

---

# [!DNL Veeva Vault] Installatiegids{#veeva-installation-guide}

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://adobe.com/go/adobesign-support-center_nl)

## Overzicht {#overview}

In dit document wordt uitgelegd hoe u Adobe Sign kunt integreren met [!DNL Veeva Vault] platform. [!DNL Veeva Vault] is een ECM-platform (Enterprise Content Management) dat is ontwikkeld voor biowetenschappen. Een &quot;Vault&quot; is een content- en dataopslagplaats met een typisch gebruik voor archivering van regelgeving, rapportering over onderzoek, subsidieaanvragen, algemene contracten en meer. Een enkele onderneming kan meerdere &#39;waarden&#39; hebben die afzonderlijk moeten worden onderhouden.

De stappen op hoog niveau om de integratie te voltooien zijn:

* Activeer uw beheeraccount in Adobe Sign (alleen voor nieuwe klanten).
* Maak objecten om de geschiedenis van een levenscyclus van een overeenkomst in de Vault bij te houden.
* Maak een nieuw beveiligingsprofiel.
* Configureer een groep in Adobe Sign die de [!DNL Veeva Vault] integratiegebruiker.
* Maak documentvelden en uitvoeringen.
* Webacties configureren en de levenscyclus van het document bijwerken.
* Documenttype instellen voor gebruiker en gebruikersrol.
* Gebruik middleware om Veeva Vault aan Adobe Sign te koppelen.

>[!NOTE]
>
>Adobe Sign-beheerder moet de Adobe Sign-installatiestappen uitvoeren in Adobe Sign.

## Configureer [!DNL Veeva Vault] {#configure-veeva}

Om te configureren [!DNL Veeva Vault] voor integratie met Adobe Sign moet u de onderstaande stappen implementeren.

### Stap 1. Groep maken {#create-group}

Adobe Sign configureren voor [!DNL Vault], een nieuwe groep genaamd *Adobe Sign Admin Group* wordt gemaakt. Deze groep wordt gebruikt om de beveiliging op documentveldniveau in te stellen voor Adobe Sign-gerelateerde velden en moet *Adobe Sign-integratieprofiel* standaard.

![Afbeelding van details van handtekeninggebeurtenissen](images/create-admin-group.png)

### Stap 2. Het pakket implementeren {#deploy-package}

[Het pakket implementeren](https://helpx.adobe.com/content/dam/help/en/PKG-AdobeSign-Integration.zip) en doorloop de stappen. Na implementatie maakt het pakket:

* Aangepaste objecten: Handtekeningobject, Handtekeningobject, Handtekeninggebeurtenisobject, Verwerkingskluis-object
* Handtekeningobjectpagina-indeling
* Handtekeninggebeurtenisobjectpagina-indeling
* Paginalay-out van handtekeningobjecten
* Lay-out objectpagina van Locker-proces
* Adobe Sign Rendition-type
* Gedeeld veld signature__c, allow_adobe_sign_user_actions__c
* Adobe Sign Web Action
* Adobe Sign-webhandeling annuleren
* Machtigingenset voor Adobe Sign-beheeracties
* Adobe Sign Integration Profile-beveiligingsprofiel
* Toepassingsrol Adobe Sign-beheerdersrol
* Documenttype groep &#39;Adobe Sign Document&#39;

#### Handtekeningobject {#signature-object}

Handtekeningobject wordt gemaakt voor het opslaan van informatie over overeenkomsten. Een handtekeningobject is een database die informatie bevat in de volgende specifieke velden:

**Handtekeningobjectvelden**

| Veld | Label | Type | Beschrijving |
| --- | --- | ---| --- | 
| external_id_c | Overeenkomst-id | Tekenreeks (100) | Houdt de unieke overeenkomst-id van de Adobe Sign vast |
| file_hash__c | Bestandshash | Tekenreeks (50) | Bevat de md5-controlesom van het bestand dat naar Adobe Sign is verzonden |
| name_v | Naam | String (128) | Bevat de overeenkomstnaam |
| sender_c | Afzender | Object (gebruiker) | Bevat de verwijzing naar de Vault-gebruiker die de overeenkomst heeft gemaakt |
| signature_status__c | Handtekeningstatus | Tekenreeks (75) | Houdt de status van de overeenkomst vast in Adobe Sign |
| signature_type__c | Handtekeningtype | Tekenreeks (20) | Houdt het handtekeningtype van de overeenkomst vast in Adobe Sign (SCHRIFTELIJK of ESIGN) |
| start_date__c | Startdatum | DateTime | Datum waarop de overeenkomst ter ondertekening is verzonden |
| cancelation_date__c | Annuleringsdatum | DateTime | Houdt de datum vast waarop de overeenkomst is geannuleerd. |
| completion_date__c | Voltooiingsdatum | DateTime | Houdt de datum vast waarop de overeenkomst is voltooid. |
| viewable_rendition_used__c | Gebruikte zichtbare vertoning | Booleaanse waarde | Markering die aangeeft of de zichtbare vertoning ter ondertekening is verzonden. (standaard is dit waar) |

![Afbeelding van handtekeningobjectdetails](images/signature-object-details.png)

#### Handtekeningobject {#signatory-object}

Handtekeningobject wordt gemaakt om informatie op te slaan die betrekking heeft op de deelnemers aan een overeenkomst. Het bevat informatie onder de volgende specifieke gebieden:

**Handtekeningobjectvelden**

| Veld | Label | Type | Beschrijving |
| --- | --- | ---| --- | 
| email_c | E-mail | Tekenreeks (120) | Houdt de unieke overeenkomst-id van de Adobe Sign vast |
| external_id_c | Deelnemer-id | Tekenreeks (80) | Houdt de unieke id van de Adobe Sign-deelnemer |
| name_v | Naam | String (128) | Houdt de naam van een Adobe Sign-deelnemer vast |
| order__c | Volgorde | Nummer | Houdt het ordernummer van de Adobe Sign-overeenkomstdeelnemer |
| role_c | Rol | Tekenreeks (30) | Houdt de rol van de deelnemer aan de Adobe Sign-overeenkomst vast |
| signature__c | Handtekening | Object (handtekening) | Bevat de verwijzing naar de bovenliggende handtekeningrecord |
| signature_status__c | Handtekeningstatus | Tekenreeks (100) | Houdt de status van de deelnemer aan de Adobe Sign-overeenkomst |
| user_c | Gebruiker | Object (gebruiker) | Bevat de verwijzing naar de gebruikersrecord van de ondertekenaar als deelnemer een Vault-gebruiker is |

![Afbeelding van handtekeninggegevens](images/signatory-object-details.png)

#### Signature Event-object {#signature-event}

Handtekeninggebeurtenisobject wordt gemaakt om gebeurtenisgerelateerde informatie van een overeenkomst op te slaan. Het bevat informatie onder de volgende specifieke gebieden:

| Veld | Label | Type | Beschrijving |
| --- | --- | ---| --- | 
| acting_user_email_c | E-mail waarnemend gebruiker | Tekenreeks | Bevat het e-mailadres van de Adobe Sign-gebruiker die de handeling heeft uitgevoerd die ertoe heeft geleid dat de gebeurtenis is gegenereerd |
| acting_user_name__c | Handelsnaam | Tekenreeks | Houdt de naam vast van de Adobe Sign-gebruiker die de handeling heeft uitgevoerd die ertoe heeft geleid dat de gebeurtenis is gegenereerd |
| description_c | Beschrijving | Tekenreeks | Bevat de beschrijving van de Adobe Sign-gebeurtenis |
| event_date__c | Gebeurtenisdatum | DateTime | Houdt de datum en tijd van de Adobe Sign-gebeurtenis vast |
| event_type__c | Het type Event | Tekenreeks | Houdt het type Adobe Sign-gebeurtenis vast |
| name_v | Naam | Tekenreeks | Automatisch gegenereerde gebeurtenisnaam |
| participant_comment_c | Opmerking deelnemer | Tekenreeks | Bevat de eventuele opmerking van de Adobe Sign-deelnemer |
| participant_email_c | E-mail deelnemer | Tekenreeks | Bevat het e-mailadres van de Adobe Sign-deelnemer |
| participant_role__c | Rol van deelnemer | Tekenreeks | Houdt de rol van de Adobe Sign-deelnemer vast |
| signature__c | Handtekening | Object (handtekening) | Bevat de verwijzing naar de bovenliggende handtekeningrecord |

![Afbeelding van details van handtekeninggebeurtenissen](images/signature-event-object-details.png)

#### Object Process Locker {#process-locker}

Er wordt een Process Locker-object gemaakt om het Adobe Sign-integratieproces te vergrendelen. Er zijn geen aangepaste velden voor nodig.

![Afbeelding van details van handtekeninggebeurtenissen](images/process-locker-details.png)

### Stap 3. Beveiligingsprofielen instellen {#security-profiles}

Succesvolle pakketimplementatie in Stap 2 maakt een Adobe Sign Integration-profiel. Het Adobe Sign Integration Profile wordt toegewezen aan het systeemaccount en wordt door de integratie gebruikt bij het aanroepen van Vault API&#39;s. Dit profiel staat machtigingen toe voor:

* Vault-API&#39;s
* Lezen, maken, bewerken en verwijderen: Handtekening, handtekening, handtekeninggebeurtenissen en procesklubjecten

U moet de Adobe Sign Admin Group (gemaakt in Stap 1) bijwerken door het meegeleverde beveiligingsprofiel in te stellen op Adobe Sign Integration Profile, zoals weergegeven in de onderstaande afbeelding.

![Afbeelding van details van handtekeninggebeurtenissen](images/security-profiles.png)

### Stap 4. Gebruiker aanmaken {#create-user}

De gebruiker van de Vault-systeemaccount voor Adobe Sign-integratie moet:

* Een Adobe Sign-integratieprofiel hebben
* Een beveiligingsprofiel hebben
* Heb Specifiek veiligheidsbeleid dat wachtwoordafloop onbruikbaar maakt
* Word lid van de Adobe Sign Admin Group.

Volg de onderstaande stappen om dit te doen:

1. Maak een Vault-systeemaccount voor gebruikers van de Adobe Sign-integratie.

   ![Afbeelding van details van handtekeninggebeurtenissen](images/create-user.png)

2. Voeg de gebruiker toe aan de Adobe Sign Admin Group.

   ![Afbeelding van details van handtekeninggebeurtenissen](images/add-user.png)

### Stap 5. Documenttypegroep configureren {#create-document-type-group}

Wanneer u het Adobe Sign-pakket implementeert, wordt er een Document Type Group-record gemaakt met de naam &#39;Adobe Sign Document&#39;.

![Afbeelding van documenttypegroepen](images/document-type-groups.png)

U moet deze documenttypegroep toevoegen voor alle documentclassificaties die in aanmerking komen voor het Adobe Sign-proces. Aangezien de documenttype groepseigenschap niet van het type naar het subtype of van het subtype naar het classificatieniveau wordt overgeërfd, moet deze worden ingesteld voor de indeling van elk document die in aanmerking komt voor Adobe Sign.

![Afbeelding van documentbewerkingsgegevens](images/document-edit-details.png)

**Opmerking:** Als het instellingsobject van de gebruikersrol niet het veld bevat dat verwijst naar het object Groep documenttype, moet u het veld toevoegen. Ga hiervoor naar **[!UICONTROL Object]** > **[!UICONTROL Gebruikersrolinstelling]** > **[!UICONTROL Velden]** en voltooi de vereiste stappen, zoals weergegeven in de onderstaande afbeelding.

![Afbeelding van gebruikersrolinstellingen](images/create-setup-field.png)

![Afbeelding van documenttype](images/document-type.png)

### Stap 6. Gebruikersrolinstelling maken {#create-user-role-setup}

Als de levenscyclus correct is (zijn) geconfigureerd, moet het systeem ervoor zorgen dat de Adobe Sign Admin-gebruiker door DAC wordt toegevoegd voor alle documenten die in aanmerking komen voor Adobe Sign-proces. Dit wordt gedaan door het aangewezen verslag van de Opstelling van de Rol van de Gebruiker te creëren dat specificeert:

* Documenttypegroep als Adobe Sign-document
* Toepassingsrol als Adobe Sign-beheerdersrol
* Integratiegebruiker

![Afbeelding van gebruikersrolinstellingen](images/user-role-setup.png)

### Stap 7. Documentvelden instellen {#create-fields}

De pakketimplementatie maakt de volgende twee nieuwe gedeelde documentvelden die nodig zijn om de integratie tot stand te brengen:

* Handtekening (handtekening__c)
* Adobe Sign-gebruikersacties toestaan (allow_adobe_sign_user_actions__c)

![Afbeelding](images/2-document-fields.png)

Documentvelden instellen:

1. Ga naar het tabblad Configuratie en selecteer **[!UICONTROL Documentvelden]** > **[!UICONTROL Gedeelde velden]**.
1. Selecteer in het veld Sectie weergeven de optie **[!UICONTROL Weergave-sectie maken]** en toewijzen **[!UICONTROL Adobe Handtekening]** als sectielabel.

   ![Afbeelding](images/create-display-section.png)

1. Voor de twee gedeelde documentvelden (signature__c en allow_adobe_sign_user_actions__c) werkt u de UI-sectie bij met **[!UICONTROL Adobe Handtekening]** als sectielabel.
1. Voeg de drie gedeelde velden toe aan alle documenttypen die in aanmerking komen voor Adobe-ondertekening. Selecteer hiervoor op de pagina Basisdocument de optie **[!UICONTROL Toevoegen]** > **[!UICONTROL Bestaand gedeeld veld]** in de rechterbovenhoek.

   ![Afbeelding](images/create-document-fields.png)

   ![Afbeelding](images/add-existing-fields.png)

   ![Afbeelding](images/use-shared-fields.png)

1. Houd er rekening mee dat beide velden een specifieke beveiliging moeten hebben waarmee alleen leden van de Adobe Sign Admin Group hun waarden kunnen bijwerken.

   ![Afbeelding](images/security-overrides.png)

Vault-overlays uitschakelen (disable_vault_overlays__v) is een bestaand gedeeld veld. Optioneel kan het veld een specifieke beveiliging hebben waarmee alleen leden van de Adobe Sign-beheerdersgroep hun waarde kunnen bijwerken.

### Stap 8. Documentuitvoeringen declareren {#declare-renditions}

Het nieuwe weergavetype *Adobe Sign Rendition (adobe_sign_rendition__c)* wordt gebruikt door Vault-integratie voor het uploaden van ondertekende PDF-documenten naar Adobe Sign. U moet de Adobe Sign-uitvoering declareren voor elk documenttype dat in aanmerking komt voor Adobe-ondertekening.

![Afbeelding van weergavetypen](images/rendition-type.png)

![Afbeelding van weergavetypen](images/edit-details-clinical-type.png)

### Stap 9. Webhandelingen bijwerken {#web-actions}

Voor Adobe Sign- en Vault-integratie hebt u de volgende twee webhandelingen nodig:

* **Adobe Sign maken**: Er wordt een Adobe Sign-overeenkomst gemaakt of weergegeven.

   Type: Documentdoel: Weergeven binnen Vault-referenties: Enable Post Session credentials via Post Message URL: <https://api.na1.adobesign.com/api/gateway/veevavaultintsvc/partner/agreement?docId=${Document.id}&majVer=${Document.major_version_number__v}&minVer=${Document.minor_version_number__v}&vaultid=${Vault.id}&useWaitPage=true>

   ![Afbeelding van Adobe Sign maken](images/create-adobe-sign.png)

* **Adobe Sign annuleren**: Hiermee wordt een bestaande overeenkomst in Adobe Sign geannuleerd en wordt de oorspronkelijke documentstatus hersteld.

   Type: Documentdoel: Weergeven binnen Vault-referenties: Enable Post Session credentials via Post Message URL: : <https://api.na1.adobesign.com/api/gateway/veevavaultintsvc/partner/agreement/cancel?docId=${Document.id}&majVer=${Document.major_version_number__v}&minVer=${Document.minor_version_number__v}&vaultid=${Vault.id}&useWaitPage=true>

   ![Afbeelding van cancel Adobe Sign](images/cancel-adobe-sign.png)

### Stap 10. Documentlevenscyclus bijwerken {#document-lifecycle}

Voor elk documenttype dat in aanmerking komt voor Adobe-handtekening, moet u de bijbehorende levenscyclus van het document bijwerken door nieuwe levenscyclusrol en -statussen toe te voegen.

De levenscyclus van Adobe Sign-overeenkomsten heeft de volgende statussen:

* CONCEPT
* AUTHORING OF DOCUMENTS_NOT_YET_PROCESSED
* OUT_FOR_SIGNATURE of OUT_FOR_APPROVAL
* ONDERTEKEND OF GOEDGEKEURD
* GEANNULEERD
* VERLOPEN

Volg onderstaande stappen om de levenscyclus van documenten bij te werken:

1. Voeg de rol Levenscyclus toe. Adobe Sign-beheerdersrol moet worden toegevoegd aan alle levenscycli die worden gebruikt door documenten die in aanmerking komen voor Adobe-ondertekening, zoals hieronder wordt weergegeven.

   ![Afbeelding van levenscyclusbeheerrollen](images/document-lifecycle-admin-role.png)

   De beheerdersrol moet met de volgende opties worden gemaakt:

   * Dynamisch toegangsbeheer ingeschakeld.
   * Regels voor het delen van documenten die alleen Document Type Group bevatten, zoals weergegeven in de onderstaande afbeelding.

   ![Afbeelding van adobe-regel voor delen van handtekeningen](images/adobe-sign-sharing-rule.png)

2. Maak levenscyclusstaten. Ga hiervoor naar **[!UICONTROL Instellingen]** > **[!UICONTROL Configuratie]** > **[!UICONTROL Documentlevenscycli]** > **[!UICONTROL Algemene levenscycli]** > **[!UICONTROL Staten]** > **[!UICONTROL Maken]**. Maak vervolgens de volgende statussen:

   * In Adobe Sign Draft

   ![Afbeelding van adobe-regel voor delen van handtekeningen](images/create-draft-state.png)

   * In Adobe Sign Authoring

   ![Afbeelding van adobe-regel voor delen van handtekeningen](images/create-authoring-state.png)

   * In Adobe-ondertekening

   ![Afbeelding van adobe-regel voor delen van handtekeningen](images/create-signing-state.png)

3. Voeg gebruikershandelingen toe aan de onderstaande statussen.

   Wanneer een Vault-document naar Adobe Sign wordt verzonden, moet de status overeenkomen met de status van de overeenkomst. Hiervoor voegt u de volgende statussen toe in elke levenscyclus die wordt gebruikt door documenten die in aanmerking komen voor Adobe-ondertekening:

   * **Voor Adobe-handtekening** (Gereviseerd): Dit is een plaatsaanduidingsnaam voor het frame van waaruit het document naar Adobe Sign kan worden verzonden. Afhankelijk van het documenttype kan de status Concept of Gecontroleerd zijn. Het label van de documentstatus kan worden aangepast aan de vereisten van de klant. Voordat de handtekeningstatus Adobe wordt ingesteld, moeten de volgende twee gebruikersacties worden gedefinieerd:

      * Actie waarmee de status van het document wordt gewijzigd in *In Adobe Sign Draft* status. De naam van deze gebruikersactie moet voor alle documenttypes voor om het even welke levenscyclus gelijk zijn. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Actie die de webactie &quot;Adobe Sign&quot; noemt. Deze status moet zijn beveiligd zodat Adobe Sign Admin Role: document weergeven, inhoud weergeven, velden bewerken, relaties bewerken, bron downloaden, zichtbare uitvoering beheren en status wijzigen.

      ![Afbeelding van levenscyclusstatus 1](images/lifecycle-state1.png)

   * **In Adobe Sign Draft**: Dit is een plaatsaanduidingsnaam voor de status die aangeeft dat het document al is geüpload naar Adobe Sign en dat de overeenkomst de status DRAFT. Het is een vereiste staat. Deze status moet de volgende vijf gebruikersacties definiëren:

      * Actie waarmee de status van het document wordt gewijzigd in *In Adobe Sign Authoring* status. De naam van deze gebruikersactie moet voor alle documenttypes voor om het even welke levenscyclus gelijk zijn. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Actie waarmee de status van het document wordt gewijzigd in *In ondertekeningsstatus Adobe*. De naam van deze gebruikersactie moet voor alle documenttypes voor om het even welke levenscyclus gelijk zijn. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Actie waarmee de status van het document wordt gewijzigd in *Adobe Sign geannuleerd* status. De naam van deze gebruikersactie moet voor alle documenttypes voor om het even welke levenscyclus gelijk zijn. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Handeling die de webactie &quot;Adobe Sign&quot; noemt.
      * Handeling die de webhandeling ‘Adobe Sign annuleren’ aanroept. Deze status moet zijn beveiligd zodat de Adobe Sign-beheerdersrol het volgende kan doen: document weergeven, inhoud weergeven, velden bewerken, relaties bewerken, bron downloaden, zichtbare uitvoering beheren en status wijzigen.

      ![Afbeelding van levenscyclusstatus 2](images/lifecycle-state2.png)

   * **In Adobe Sign Authoring**: Dit is een tijdelijke aanduiding voor de status die aangeeft dat het document al is geüpload naar Adobe Sign en dat de overeenkomst de status AUTHORING of DOCUMENTS_NOT_YET_PROCESSED heeft. Het is een vereiste staat. Voor deze status moeten vier gebruikersacties worden gedefinieerd:

      * Handeling die de status van het document wijzigt in Adobe Sign Canceled state. De naam van deze gebruikersactie moet voor alle documenttypen gelijk zijn, ongeacht de levenscyclus. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Handeling waarmee de status van het document wordt gewijzigd in In Adobe Signing-status. De naam van deze gebruikersactie moet voor alle documenttypen gelijk zijn, ongeacht de levenscyclus. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Handeling die de webactie &quot;Adobe Sign&quot; noemt
      * Handeling die de webhandeling ‘Adobe Sign annuleren’ aanroept. Deze status moet zijn beveiligd zodat de Adobe Sign-beheerdersrol het volgende kan doen: document weergeven, inhoud weergeven, velden bewerken, relaties bewerken, bron downloaden, zichtbare uitvoering beheren en status wijzigen.

      ![Afbeelding van levenscyclusstatus 3](images/lifecycle-state3.png)

   * **In Adobe-ondertekening**: Dit is een plaatsaanduidingsnaam voor de status die aangeeft dat het document is geüpload naar Adobe Sign en dat de overeenkomst al is verzonden naar deelnemers (status OUT_FOR_SIGNATURE of OUT_FOR_APPROVAL). Het is een vereiste staat. Voor deze status moeten vijf gebruikersacties worden gedefinieerd:

      * Handeling die de status van het document wijzigt in Adobe Sign Canceled state. De doelstatus van deze actie kan elke klantbehoefte zijn en kan voor verschillende typen verschillen. De naam van deze gebruikersactie moet voor alle documenttypen gelijk zijn, ongeacht de levenscyclus. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Handeling die de status van het document wijzigt in Adobe Sign Afgewezen status. De doelstatus van deze actie kan elke klantbehoefte zijn en kan voor verschillende typen verschillen. De naam van deze gebruikersactie moet voor alle documenttypen gelijk zijn, ongeacht de levenscyclus. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Handeling waarmee de status van het document wordt gewijzigd in Adobe Signed state. De doelstatus van deze actie kan elke klantbehoefte zijn en kan voor verschillende typen verschillen. De naam van deze gebruikersactie moet echter gelijk zijn voor alle documenttypen, ongeacht de levenscyclus. Indien nodig kunnen de criteria voor deze actie worden ingesteld op &quot;Adobe Sign-gebruikersacties toestaan is gelijk aan Ja&quot;.
      * Handeling die de webhandeling aanroept *Adobe Sign*.
      * Handeling die een webhandeling aanroept *Adobe Sign annuleren*. Deze status moet zijn beveiligd zodat de Adobe Sign-beheerdersrol het volgende kan doen: document weergeven, inhoud weergeven, velden bewerken, relaties bewerken, bron downloaden, zichtbare uitvoering beheren en status wijzigen.

      ![Afbeelding van levenscyclusstatus 4](images/lifecycle-state4.png)

      * **Adobe ondertekend (goedgekeurd)**: Dit is een tijdelijke aanduiding voor de status die aangeeft dat het document is geüpload naar Adobe Sign en dat de overeenkomst is voltooid (ONDERTEKEND of GOEDGEKEURD). Het is een vereiste status en het kan een bestaande levenscyclusstatus zijn, zoals Goedgekeurd.
Voor deze status zijn geen handelingen van de gebruiker vereist. De beheerfunctie van Adobe Sign moet zijn beveiligd tegen: bekijk documenten, bekijk inhoud en bewerk velden.

   In het volgende diagram worden de toewijzingen weergegeven tussen Adobe Sign-overeenkomsten en vault-documentstatussen, waarbij de status ‘Voor Adobe-ondertekening’ Concept is.

   ![Afbeelding](images/sign-vault-mappings.png)

### Stap 11. Adobe Sign-stage toevoegen aan algemene levenscyclus in levenscyclusgroepen

![Afbeelding](images/add-adobe-sign-stage.png)

### Stap 12. Machtigingen instellen voor gebruikersrol in levenscyclusstatus

U moet de juiste machtigingen instellen voor elke gebruikersrol in de levenscyclusstatus, zoals weergegeven in de onderstaande afbeelding.

![Afbeelding](images/set-user-role-permissions.png)

### Stap 13. Automatische beveiliging instellen op basis van documentstatus en gebruikersrol

![Afbeelding](images/set-atomic-security.png)

### Stap 14. Documentberichten maken voor Adobe Sign Annuleren

![Afbeelding](images/create-cancel-message.png)

## Verbinden [!DNL Veeva Vault] naar Adobe Sign met behulp van middleware {#connect-middleware}

Nadat u de installatie voor [!DNL Veeva Vault] en de Adobe Sign-beheerdersaccount moet de beheerder een verbinding tussen de twee accounts maken met behulp van de middleware. De [!DNL Veeva Vault] en Adobe Sign-accountverbinding wordt gestart door Adobe Sign Identity en wordt vervolgens gebruikt om het[!DNL Veeva Vault]identiteit.
Voor systeembeveiliging en -stabiliteit moet de beheerder een toegewijde [!DNL Veeva Vault] systeem-/service-/utiliteitsaccount, zoals `adobe.for.veeva@xyz.com`in plaats van een persoonlijke gebruikersaccount, zoals `bob.smith@xyz.com`.

Een Adobe Sign-accountbeheerder moet de onderstaande stappen volgen om verbinding te maken [!DNL Veeva Vault] naar Adobe Sign met middleware:

1. Ga naar de [Adobe Sign for [!DNL Veeva Vault] Startpagina](https://static.adobesigncdn.com/veevavaultintsvc/index.html).
1. Selecteren **[!UICONTROL Aanmelden]** in de rechterbovenhoek.

   ![Afbeelding van aanmeldingsgegevens voor middleware](images/middleware_login.png)

1. Geef op de Adobe Sign-aanmeldingspagina die wordt geopend de e-mail en het wachtwoord van de accountbeheerder op en selecteer **[!UICONTROL Aanmelden]**.

   ![Afbeelding](images/middleware-signin.png)

   Nadat u zich hebt aangemeld, wordt op de pagina de bijbehorende e-mail-ID en het tabblad Instellingen weergegeven, zoals hieronder wordt weergegeven.

   ![Afbeelding](images/middleware_settings.png)

1. Selecteer de **[!UICONTROL Instellingen]** tabblad.

   Op de pagina Instellingen worden de beschikbare verbindingen weergegeven en *Geen verbindingen beschikbaar* in het geval van eerste verbindingsopstelling, zoals hieronder getoond.

   ![Afbeelding](images/middleware_newconnection.png)

1. Selecteren **[!UICONTROL Verbinding toevoegen]** om een nieuwe verbinding toe te voegen.

1. Geef in het dialoogvenster Verbinding toevoegen dat nu wordt geopend, de vereiste gegevens op, zoals [!DNL Veeva Vault] referenties.

   De Adobe Sign-referenties worden automatisch ingevuld vanaf de eerste Adobe Sign-aanmelding.

   ![Afbeelding](images/middleware_addconnection.png)

1. Selecteren **[!UICONTROL Valideren]** om de accountgegevens te valideren.

   Bij succesvolle validatie ziet u een melding &#39;Met succes gevalideerd door gebruiker&#39;, zoals hieronder weergegeven.

   ![Afbeelding](images/middleware_validated.png)

1. Als u het gebruik wilt beperken tot een bepaalde Adobe Sign-groep, vouwt u de **[!UICONTROL Groep]** en selecteer een van de beschikbare groepen.

   ![Afbeelding](images/middleware_group.png)

1. Als u een controlerapport wilt toevoegen aan de ondertekende uitvoering, schakelt u het selectievakje in **[!UICONTROL Controlerapport toevoegen aan ondertekende vertoning]**.

   ![Afbeelding](images/add-audit-report.png)

1. Schakel het selectievakje in als u automatische provisioning van gebruikers in Adobe Sign wilt toestaan **[!UICONTROL Gebruikers automatisch toewijzen]**.

   **Opmerking:** Automatische provisioning van nieuwe Adobe Sign-gebruikers werkt alleen als deze optie is ingeschakeld op Adobe Sign-accountniveau in Adobe Sign en als deze optie **[!UICONTROL Gebruikers automatisch toewijzen]** voor de[!DNL Veeva Vault]Adobe Sign-integratie zoals hieronder weergegeven door de Adobe Sign-accountbeheerder.

   ![Afbeelding](images/allow-auto-provisioning.png)

1. Selecteren **[!UICONTROL Opslaan]** om uw nieuwe verbinding op te slaan.

   De nieuwe verbinding wordt weergegeven op het tabblad Instellingen, waarin de integratie tussen [!DNL Veeva Vault] en Adobe Sign.

   ![Afbeelding](images/middleware_setup.png)

