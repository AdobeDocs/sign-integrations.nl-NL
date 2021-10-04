---
title: Aan de slag met Workday
description: Een snelstartgids voor klanten die Adobe Sign in hun Workday-omgevingen willen gebruiken.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: 5ac9dc27dcdb6cab19281e6aafd4ea0524cc01d6
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 30%

---

# [!DNL Workday] Gids Aan de slag{#workday-quick-start-guide}

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://www.adobe.com/go/adobesign-support-center)

## Overzicht {#overview}

Dit document is ontworpen om beheerders van [!DNL Workday] te helpen begrijpen hoe ze de [!DNL Workday] bedrijfsprocessen kunnen aanpassen en Adobe Sign kunnen opnemen voor het verkrijgen van elektronische handtekeningen. Als u Adobe Sign wilt gebruiken binnen [!DNL Workday], moet u weten hoe u [!DNL Workday]-items kunt maken en wijzigen, zoals:

* [!UICONTROL Business Process Framework]
* Instelling en configuratie van de tenant
* Rapportage en integratie van [!DNL Workday] Studio

## Toegang tot Adobe Sign vanuit [!DNL Workday] {#access-adobe-sign}

[!UICONTROL De elektronische ondertekeningsmogelijkheden van Adobe Sign ] worden weergegeven als  [!UICONTROL Review Document ] Stepaction binnen het BPF ( [!UICONTROL Business Process Framework) ] en als Distribute Documents-taak.

## [!UICONTROL De stap Review Document (Document bekijken)] {#review-document-step}

Adobe Sign for [!DNL Workday] wordt weergegeven via de [!UICONTROL stap Document reviewen] die u kunt toevoegen aan elk van de meer dan 400 bedrijfsprocessen binnen [!DNL Workday], inclusief [!UICONTROL Offer], [!UICONTROL Documenten en taken distribueren], [!UICONTROL Compenseren] en meer.

U kunt verwijzen naar de [[!DNL Workday] communityartikelen op [!UICONTROL Documentstap reviseren]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Er is een 1:1-relatie tussen [!UICONTROL [!UICONTROL Document stap reviseren]s] en factureerbare transacties met Adobe Sign. U kunt meerdere documenten combineren in één [!UICONTROL stap Document controleren] en deze worden gepresenteerd als één pakket ter ondertekening.

**Opmerking**: Er kan slechts naar één  ** dynamisch document worden verwezen binnen een specifieke stap [!UICONTROL  Document ]revisie.

Een functionele [!UICONTROL Documentstap controleren] definiëren:

1. Voeg een [!UICONTROL stap Document controleren] in.
1. Geef de groepen (rollen) op die kunnen reageren op de [!UICONTROL stap Document controleren].

![De stappen voor bedrijfsprocessen](images/insert-review-doc-steptornm-575.png)

De [!UICONTROL stap Document controleren] configureren:

1. Geef het *[!UICONTROL eSignature Integration-type]* op als *[!UICONTROL eSign door Adobe]*.

1. Voeg rijen toe aan het handtekeningenraster.

   * Het handtekeningenraster bepaalt de volgorde waarin het document ter ondertekening wordt doorgestuurd. Elke rij kan een of meer functies bevatten en iedere rij vertegenwoordigt een stap in het ondertekeningsproces.
   * Elk lid van de functie binnen een bepaalde stap ontvangt een melding dat een ondertekeningsgebeurtenis in behandeling is.
   * Als één persoon met de desbetreffende functie zijn handtekening zet, is de die stap van de rij voltooid en wordt het document verplaatst naar de volgende stap in de rij.
   * Wanneer alle rijen zijn ondertekend, is de [!UICONTROL stap Document controleren] voltooid.

1. Geef het document op dat moet worden ondertekend. Als het document een [!UICONTROL Aanbieding BP] is, kunt u het van een Generate stap van het Document gebruiken. Als dat niet het geval is, kiest u een bestaand document of rapport.

1. Herhaal stap 3 voor zoveel documenten als nodig is.

   ![De stap Review Document (Document bekijken) configureren](images/configure-rd-stepsmaller-575.png)

1. Voeg desgewenst een ‘omleidingsgebruiker’ toe voor het vastleggen van ‘weigeren om te ondertekenen’-handelingen. Wanneer gebruikers weigeren, stuurt [!DNL Workday] de documenten door naar een geconfigureerde beveiligingsgroep voor revisie.

Selecteer **[!UICONTROL Bedrijfsproces]** > **[!UICONTROL Omleiding behouden]** in het menu met verwante handelingen van een [!UICONTROL Document stap reviseren]. Selecteer vervolgens een van de volgende opties:

* **[!UICONTROL Naar achtergrond]**: Om de leden van de veiligheidsgroep toe te laten om een stap terug naar een vroegere stap in het bedrijfsproces te verzenden. Het bedrijfsproces wordt vanaf deze stap opnieuw gestart.
* **[!UICONTROL Ga naar volgende stap]**: Om de leden van de veiligheidsgroep toe te laten om een stap naar de volgende stap in het bedrijfsproces vooruit te gaan.
* **[!UICONTROL Beveiligingsgroepen]**: Om stappen in de bedrijfsprocesstroom om te leiden. De groepen van de veiligheid die bij deze herinnering tonen worden geselecteerd in het bedrijfsprocesveiligheidsbeleid in de Redirect sectie.

## Opmerkingen bij de stappen in het bedrijfsproces {#business-process-step-notes}

[!UICONTROL Het ] framework voor bedrijfsprocessen is krachtig; u moet er echter voor zorgen dat :

* Elk bedrijfsproces moet een voltooiingsstap hebben, die idealiter aan het eind van het bedrijfsproces is.

* Er wordt een voltooiingsstap ingesteld in het menu met verwante handelingen van het zoekpictogram. Dit is alleen mogelijk tijdens het &quot;weergeven&quot; van het BP en niet tijdens het &quot;bewerken&quot; ervan.

* Elke stap van het bedrijfsproces wordt achtereenvolgens uitgevoerd.

   U kunt de volgorde van een stap wijzigen door de waarde voor de volgorde te wijzigen. Als u bijvoorbeeld een stap wilt invoegen tussen de items &quot;c&quot; en &quot;d&quot;, geeft u een nieuw item op als &quot;ca&quot;.

### Voorbeeld: aanbieden {#example-offer}

BP van de Aanbieding is een subproces van [!UICONTROL Dynamische BP van de Toepassing van de Taak] dat moet worden gevormd om BP van de Aanbieding uit te voeren. Deze wordt geactiveerd wanneer de status Taaktoepassing wordt verplaatst naar &quot;[!UICONTROL Aanbieding]&quot; of &quot;[!UICONTROL Aanbieding maken]&quot;.

In het onderstaande voorbeeld gebruikt een [!UICONTROL Review Document Step] een stap Dynamic Document voor zowel Noord-Amerika als Japan.

![Voorbeeld van een  [!DNL Workday] bedrijfsproces](images/bp-for-offersmaller-575.png)

Dit bedrijfsproces doet het volgende:

* Verzoekt de initiatiefnemer van de BP om een compensatie voor de kandidaat voor te stellen (stap b).
* Gebruikt een stapvoorwaarde om te testen of het huidige land GEEN Japan is.

   Indien waar (true), wordt stap &#39;ba&#39; uitgevoerd, waarbij een Engelstalig document wordt gebruikt.

   Indien onwaar, voert het stap &quot;bb&quot;uit die een Japans taaldocument gebruikt.

* Definieert het ondertekeningsproces in de [!UICONTROL stap Document controleren] &quot;bc&quot;.
* Definieert het beslissingspunt om een aanbieding te doen in de vereiste voltooiingsstap &quot;d&quot;.

Het dynamische document dat in stap &quot;ba&quot; wordt gegenereerd, krijgt de naam [!UICONTROL Offer Letter] (Werkaanbod) en bevat één tekstblok met de naam [!UICONTROL Rapid Offer] (Snel aanbod). U kunt desgewenst meerdere tekstblokken toevoegen, zoals koptekst, aanhef, compensatie, voorraad, sluiten, voorwaarden en meer.

![[!DNL Workday] documentpagina weergeven](images/offer-letter-575.png)

De onderstaande dynamische aanbiedingsbrief wordt gemaakt in de rijke teksteditor van [!DNL Workday]. De in *grijs* gemarkeerde items zijn [!DNL Workday] opgegeven objecten die verwijzen naar contextuele gegevens.

Items in {{brackets}} zijn [Adobe-tekstlabels](https://adobe.com/go/adobesign_text_tag_guide_nl).

![Voorbeeld van dynamisch formulier](images/script.png)

In de [!UICONTROL Documentstap controleren] wordt vanuit de vorige stap naar het dynamische document verwezen en wordt het opeenvolgende ondertekeningsproces via twee ondertekeningsgroepen gedefinieerd.

Het gedrag dat hieronder wordt geïllustreerd leidt het dynamisch geproduceerde document eerst aan de Manager van de Helling, en dan aan de Kandidaat.

![[!DNL Workday] ondertekeningsgroepen die worden gedefinieerd](images/configure-rd-stepsmaller-575.png)

### Voorbeeld: Documenten distribueren {#example-distribute-documents}

De taak Mass Distribute Documents or Tasks is geïntroduceerd in [!DNL Workday] 30 en kan worden gebruikt om één document te verzenden naar een grote groep (&lt;20K) afzonderlijke ondertekenaars. Dit is beperkt tot één handtekening per document. U kunt een distributie maken door de handeling &#39;[!UICONTROL Distribute documenten of taken maken]&#39; in de zoekbalk te openen.

Voorbeeld: Verzend een formulier voor de aandelenkeuze voor werknemers naar alle managers met [!UICONTROL Global Modern Services]. Desgewenst kunt u het filter verder filteren op individuele managers.

U kunt ook het rapport **View Distribute Documents or Tasks** openen om de voortgang van de distributie te volgen.

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

![Voorbeeld van een  [!DNL Workday] rapport met drie objecten](images/workday-reportsmaller-575.png)

## Ondertekende documenten {#signed-documents}

De handtekeningencyclus [!DNL Workday] onderdrukt alle e-mailmeldingen van Adobe Sign. Gebruikers worden in hun inbox [!DNL Workday] op de hoogte gesteld van openstaande handelingen.

Zodra een document is ondertekend door alle handtekeninggroepen, wordt een kopie van het ondertekende document via e-mail verspreid onder alle leden van de handtekeninggroep.

Als u dit gedrag wilt onderdrukken, kunt u contact opnemen met uw [!UICONTROL Adobe Sign Success Manager] of het [Adobe Sign Support team](https://adobe.com/go/adobesign-support-center).

Binnen [!DNL Workday] hebt u toegang tot de ondertekende documenten in de volledige procesrecord. U kunt vinden:

* De documenten van de arbeider op het Profiel van de Arbeider, en
* Kandidaatdocumenten (aanbiedingsbrieven) op het kandidaatprofiel.

Op de onderstaande afbeelding ziet u een brief met een ondertekend aanbod voor de kandidaat Chris Foxx.

![Voorbeeld  [!DNL Workday] aanbiedingsbrief](images/offer.png)

## Ondersteuning {#support}

### [!DNL Workday] ondersteuning {#workday-support}

[!DNL Workday] is de eigenaar van de integratie en fungeert als uw eerste contactpunt voor vragen over het bereik van de integratie, voor verzoeken om functies of in geval van problemen met het dagelijks functioneren van de integratie.

De [!DNL Workday]-community heeft verschillende goede artikelen over het oplossen van problemen met de integratie en het genereren van documenten:

* [Problemen met de integratie van e-handtekeningen oplossen](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [De stap Document bekijken](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamisch documenten genereren](https://community.workday.com/node/176443)
* [Configuratietips voor het genereren van documenten met een werkaanbod](https://community.workday.com/node/183242)

### Adobe Sign-ondersteuning {#adobe-sign-support}

Adobe Sign is de integratiepartner en u dient contact op te nemen met Adobe Sign als de integratie geen handtekeningen kan verkrijgen of als de kennisgeving voor handtekeningen in de wachtrij mislukt.

Adobe Sign-klanten moeten contact opnemen met hun Customer Success-manager voor ondersteuning. U kunt ook [!UICONTROL Technische ondersteuning voor Adobe] telefonisch bereiken: 1-866-318-4100, wacht op productlijst dan ga binnen: 4 en vervolgens 2 (naar wens).

* [Adobe-tekstlabels toevoegen aan documenten](https://www.adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
