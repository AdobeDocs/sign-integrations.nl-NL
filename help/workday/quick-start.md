---
title: Aan de slag met Workday
description: Een snelstartgids voor klanten die Adobe Sign in hun Workday-omgevingen willen gebruiken.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Acrobat Sign, Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: b326a9afa2c16333d390cac3b30a2c7c741a4360
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 30%

---

# [!DNL Workday] Gids Aan de slag{#workday-quick-start-guide}

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://www.adobe.com/go/adobesign-support-center)

## Overzicht {#overview}

Dit document is ontworpen om [!DNL Workday] beheerders begrijpen hoe ze de [!DNL Workday] Bedrijfsprocessen om Adobe Sign op te nemen voor het verkrijgen van elektronische handtekeningen. To use Adobe Sign within [!DNL Workday], you must know how to create and modify [!DNL Workday] items such as:

* [!UICONTROL Business Process Framework]
* Instelling en configuratie van de tenant
* Rapportage en [!DNL Workday] Studio-integratie

## Toegang tot Adobe Sign vanuit [!DNL Workday] {#access-adobe-sign}

[!UICONTROL Adobe Sign electronic signature capability] is surfaced as [!UICONTROL Review Document Step] action within the [!UICONTROL Business Process Framework (BPF)] and as a Distribute Documents task.

## [!UICONTROL De stap Review Document (Document bekijken)] {#review-document-step}

Adobe Sign for [!DNL Workday] wordt blootgesteld via de [!UICONTROL Documentstap controleren] die u kunt toevoegen aan elk van de meer dan 400 bedrijfsprocessen binnen [!DNL Workday], inclusief [!UICONTROL Aanbieding], [!UICONTROL Documenten en taken distribueren], [!UICONTROL Compenseren voorstellen]en meer.

You may refer to the [[!DNL Workday] community articles on [!UICONTROL Review Document Step]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Er is een 1:1-relatie tussen [!UICONTROL [!UICONTROL Documentstap controleren]s] en factureerbare transacties met Adobe Sign. You can combine multiple documents within a single [!UICONTROL Review Document Step] and they are presented as a single package for signature.

**Note**: Only a single *Dynamic* document can be referenced within a specific [!UICONTROL Review Document Step].

Een functie definiëren [!UICONTROL Documentstap controleren]:

1. Insert a [!UICONTROL Review Document Step].
1. Geef de groepen (rollen) op die kunnen reageren op de [!UICONTROL Documentstap controleren].

![De stappen voor bedrijfsprocessen](images/insert-review-doc-steptornm-575.png)

Om het [!UICONTROL Documentstap controleren]:

1. Specify the *[!UICONTROL eSignature Integration type]* as *[!UICONTROL eSign by Adobe]*.

1. Voeg rijen toe aan het handtekeningenraster.

   * Het handtekeningenraster bepaalt de volgorde waarin het document ter ondertekening wordt doorgestuurd. Elke rij kan een of meer functies bevatten en iedere rij vertegenwoordigt een stap in het ondertekeningsproces.
   * Elk lid van de functie binnen een bepaalde stap ontvangt een melding dat een ondertekeningsgebeurtenis in behandeling is.
   * Als één persoon met de desbetreffende functie zijn handtekening zet, is de die stap van de rij voltooid en wordt het document verplaatst naar de volgende stap in de rij.
   * Wanneer alle rijen zijn ondertekend, wordt de [!UICONTROL Documentstap controleren] is voltooid.

1. Geef het document op dat moet worden ondertekend. Als het document een [!UICONTROL BP van aanbieding], kunt u deze vanuit de stap Document genereren gebruiken. Als dat niet het geval is, kiest u een bestaand document of rapport.

1. Herhaal stap 3 voor zoveel documenten als nodig is.

   ![De stap Review Document (Document bekijken) configureren](images/configure-rd-stepsmaller-575.png)

1. Optionally, add a ‘redirect user’ for capturing ‘decline to sign’ actions. When users decline, [!DNL Workday] reroutes the documents to a configured security group for review.

Via het menu Gerelateerde handelingen van een [!UICONTROL Documentstap controleren]selecteert u **[!UICONTROL Bedrijfsproces]** > **[!UICONTROL Omleiden behouden]**. Next, select one of the following:

* **[!UICONTROL Naar achtergrond]**: Om de leden van de veiligheidsgroep toe te laten om een stap terug naar een vroegere stap in het bedrijfsproces te verzenden. Het bedrijfsproces wordt vanaf deze stap opnieuw gestart.
* **[!UICONTROL Ga naar volgende stap]**: Om de leden van de veiligheidsgroep toe te laten om een stap naar de volgende stap in het bedrijfsproces vooruit te gaan.
* **[!UICONTROL Security Groups]**: To redirect steps in the business process flow. De groepen van de veiligheid die bij deze herinnering tonen worden geselecteerd in het bedrijfsprocesveiligheidsbeleid in de Redirect sectie.

## Opmerkingen bij de stappen in het bedrijfsproces {#business-process-step-notes}

[!UICONTROL The Business Process Framework] is powerful; however, you must ensure that:

* Elk bedrijfsproces moet een voltooiingsstap hebben, die idealiter aan het eind van het bedrijfsproces is.

* Er wordt een voltooiingsstap ingesteld in het menu met verwante handelingen van het zoekpictogram. This is possible only while “viewing” the BP and not while “editing” it.

* Elke stap van het bedrijfsproces wordt achtereenvolgens uitgevoerd.

   U kunt de volgorde van een stap wijzigen door de waarde voor de volgorde te wijzigen. Als u bijvoorbeeld een stap wilt invoegen tussen de items &quot;c&quot; en &quot;d&quot;, geeft u een nieuw item op als &quot;ca&quot;.

### Voorbeeld: aanbieden {#example-offer}

The Offer BP is a sub process of the [!UICONTROL Job Application Dynamic BP] that must be configured to execute the Offer BP. Deze wordt geactiveerd wanneer de status Taaktoepassing wordt verplaatst naar &quot;[!UICONTROL Aanbieding]&quot; of &quot;[!UICONTROL Aanbieding maken]&quot;.

In the below example, a [!UICONTROL Review Document Step] is using a Dynamic Document step for both North America and Japan.

![Example of a [!DNL Workday] Business Process](images/bp-for-offersmaller-575.png)

Dit bedrijfsproces doet het volgende:

* Asks the initiator of the BP to propose compensation for the candidate (step b).
* Uses a step condition to test whether the current country is NOT Japan.

   Indien waar (true), wordt stap &#39;ba&#39; uitgevoerd, waarbij een Engelstalig document wordt gebruikt.

   Indien onwaar, voert het stap &quot;bb&quot;uit die een Japans taaldocument gebruikt.

* Defines the signature process in the [!UICONTROL Review Document Step] “bc”.
* Definieert het beslissingspunt om een aanbieding te doen in de vereiste voltooiingsstap &quot;d&quot;.

Het dynamische document dat in stap &quot;ba&quot; wordt gegenereerd, krijgt de naam [!UICONTROL Offer Letter] (Werkaanbod) en bevat één tekstblok met de naam [!UICONTROL Rapid Offer] (Snel aanbod). You can add multiple text blocks such as header, salutation, compensation, stock, closing, terms, and more as required.

![[!DNL Workday] view document page](images/offer-letter-575.png)

De onderstaande dynamische aanbiedingsbrief wordt gemaakt in de [!DNL Workday] rijke teksteditor. De items gemarkeerd in *grijs* zijn [!DNL Workday] verschafte objecten die verwijzen naar contextuele gegevens.

Items in {{brackets}} zijn [Adobe-tekstlabels](https://adobe.com/go/adobesign_text_tag_guide_nl).

![Voorbeeld van dynamisch formulier](images/script.png)

Within the [!UICONTROL Review Document Step], the dynamic document is referenced from the previous step and defines the sequential signature process via two signing groups.

The behavior illustrated below routes the dynamically generated document first to the Hiring Manager, and then to the Candidate.

![[!DNL Workday] signing groups being defined](images/configure-rd-stepsmaller-575.png)

### Voorbeeld: Documenten distribueren {#example-distribute-documents}

Geïntroduceerd in [!DNL Workday] 30. Met de taak Mass Distribute Documents or Tasks kunt u één document naar een grote groep (&lt;20K) afzonderlijke ondertekenaars verzenden. Dit is beperkt tot één handtekening per document. Creation of a distribution is performed by accessing the ‘[!UICONTROL Create Distribute Documents or Tasks]’ action from the search bar.

Voorbeeld: Verzend een formulier voor de keuze van een werknemer naar alle managers met [!UICONTROL Wereldwijde moderne services]. Desgewenst kunt u het filter verder filteren op individuele managers.

You can also access the **View Distribute Documents or Tasks** report to track the progress of the distribution.

![](images/create-distributedocumentsortasks.png)

### Voorbeeld: Rapporten {#example-reporting}

[!DNL Workday] heeft een veelzijdige infrastructuur voor rapporten. Als u de details van het Adobe Sign-proces wilt bekijken, controleert u de elementen van de *Review Document Event* (Gebeurtenis Document bekijken).

Hieronder ziet u een eenvoudig aangepast rapport dat kan worden uitgevoerd voor alle bedrijfsprocessen die Adobe Sign-transacties en hun status zoeken.

![[!DNL Workday]Voorbeeld van een aangepast rapport in ](images/review-document-eventsmaller-575.png)

Het volgende rapport is gegenereerd door te kijken naar de bedrijfsprocessen Offer (Aanbod), Onboarding (Inductie) en Propose Compensation (Salaris voorstellen) in een implementatie-tenant.

U ziet het volgende:

* De documenten die ter ondertekening zijn verzonden
* De gekoppelde stap in het bedrijfsproces
* De volgende persoon die wacht op ondertekening

![Voorbeeld van een [!DNL Workday] Rapport met drie objecten](images/workday-reportsmaller-575.png)

## Signed documents {#signed-documents}

The [!DNL Workday] signature cycle suppresses all email notifications by Adobe Sign. Users are informed of pending actions within their [!DNL Workday] inbox.

Once a document is signed by all Signature Groups, a copy of the signed document is distributed to all the members of the Signature Group via email.

Als u dit gedrag wilt onderdrukken, kunt u contact opnemen met uw [!UICONTROL Adobe Sign Success Manager] of de [Adobe Sign-ondersteuningsteam](https://adobe.com/go/adobesign-support-center).

Within [!DNL Workday], you can access the signed documents on the full process record. U kunt vinden:

* De documenten van de arbeider op het Profiel van de Arbeider, en
* Kandidaatdocumenten (aanbiedingsbrieven) op het kandidaatprofiel.

Op de onderstaande afbeelding ziet u een brief met een ondertekend aanbod voor de kandidaat Chris Foxx.

![Voorbeeld [!DNL Workday] aanbiedingsbrief](images/offer.png)

## Ondersteuning {#support}

### [!DNL Workday] ondersteuning {#workday-support}

[!DNL Workday] is de eigenaar van de integratie en fungeert als uw eerste contactpunt voor vragen over het bereik van de integratie, voor verzoeken om functies of in geval van problemen met het dagelijks functioneren van de integratie.

De [!DNL Workday] community heeft verschillende goede artikelen over het oplossen van problemen met de integratie en het genereren van documenten:

* [Problemen met de integratie van e-handtekeningen oplossen](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [De stap Document bekijken](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamisch documenten genereren](https://community.workday.com/node/176443)
* [Configuratietips voor het genereren van documenten met een werkaanbod](https://community.workday.com/node/183242)

### Adobe Sign support {#adobe-sign-support}

Adobe Sign is de integratiepartner en u dient contact op te nemen met Adobe Sign als de integratie geen handtekeningen kan verkrijgen of als de kennisgeving voor handtekeningen in de wachtrij mislukt.

Adobe Sign-klanten moeten contact opnemen met hun Customer Success-manager voor ondersteuning. Alternatief, [!UICONTROL Adobe Technische ondersteuning] telefonisch bereikbaar: 1-866-318-4100, wacht op productlijst dan ga binnen: 4 en vervolgens 2 (naar wens).

* [Adobe-tekstlabels toevoegen aan documenten](https://www.adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
