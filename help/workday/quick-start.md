---
title: Workday-gids Aan de slag
description: Een snelstartgids voor klanten die Adobe Sign in hun Workday-omgevingen willen gebruiken.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: 2cc0ea55ee7dca3682896c61c85eec29a555339c
workflow-type: tm+mt
source-wordcount: '1347'
ht-degree: 0%

---

# [!DNL Workday] Aan de slag{#workday-quick-start-guide}

[**Contact opnemen met Adobe Sign-ondersteuning**](https://www.adobe.com/go/adobesign-support-center)

## Overzicht {#overview}

Dit document is ontworpen om [!DNL Workday] beheerders begrijpen hoe ze de [!DNL Workday] Bedrijfsprocessen om Adobe Sign op te nemen voor het verkrijgen van elektronische handtekeningen. Adobe Sign gebruiken in [!DNL Workday], moet u weten hoe u kunt maken en wijzigen [!DNL Workday] items zoals:

* [!UICONTROL Business Process Framework]
* Instelling en configuratie van de tenant
* Rapportage en [!DNL Workday] Studio-integratie

## Adobe Sign openen binnen [!DNL Workday] {#access-adobe-sign}

[!UICONTROL Adobe Sign-functie voor elektronische ondertekening] wordt weergegeven als [!UICONTROL Documentstap controleren] actie binnen de [!UICONTROL Business Process Framework (BPF)] en als taak Documenten distribueren.

## [!UICONTROL Documentstap controleren] {#review-document-step}

Adobe Sign for [!DNL Workday] wordt blootgesteld via de [!UICONTROL Documentstap controleren] die u kunt toevoegen aan elk van de meer dan 400 bedrijfsprocessen binnen [!DNL Workday], inclusief [!UICONTROL Aanbieding], [!UICONTROL Documenten en taken distribueren], [!UICONTROL Compenseren voorstellen]en meer.

U kunt verwijzen naar de [[!DNL Workday] communautaire artikelen over [!UICONTROL Documentstap controleren]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Er is een 1:1-relatie tussen [!UICONTROL [!UICONTROL Documentstap controleren]s] en factureerbare transacties met Adobe Sign. U kunt meerdere documenten combineren binnen één [!UICONTROL Documentstap controleren] en worden ter ondertekening aangeboden als één pakket.

**Opmerking**: Slechts één *Dynamisch* kan binnen een specifiek document naar dit document worden verwezen [!UICONTROL Documentstap controleren].

Een functie definiëren [!UICONTROL Documentstap controleren]:

1. Een [!UICONTROL Documentstap controleren].
1. Geef de groepen (rollen) op die kunnen reageren op de [!UICONTROL Documentstap controleren].

![De stappen in het bedrijfsproces](images/insert-review-doc-steptornm-575.png)

Om het [!UICONTROL Documentstap controleren]:

1. Geef de *[!UICONTROL Type eSignature Integration]* als *[!UICONTROL Elektronisch ondertekenen door Adobe]*.

1. Voeg rijen toe aan het handtekeningraster.

   * Het handtekeningraster geeft de seriële volgorde aan waarin het document wordt gerouteerd voor ondertekening. Elke rij kan een of meer rollen bevatten en elke rij vertegenwoordigt een stap in het ondertekeningsproces.
   * Elk lid van de rol binnen een bepaalde stap wordt op de hoogte gesteld dat een ondertekeningsgebeurtenis in behandeling is.
   * Zodra één persoon uit de rol ondertekent, wordt de rijstap voltooid en wordt het document verplaatst naar de volgende rijstap.
   * Wanneer alle rijen zijn ondertekend, wordt de [!UICONTROL Documentstap controleren] is voltooid.

1. Geef het document op dat moet worden ondertekend. Als het document een [!UICONTROL BP van aanbieding], kunt u deze vanuit de stap Document genereren gebruiken. Kies anders een bestaand document of rapport.

1. Herhaal stap 3 voor zoveel documenten als u nodig hebt.

   ![Stap revisiedocument configureren](images/configure-rd-stepsmaller-575.png)

1. Voeg desgewenst een ‘omleidingsgebruiker’ toe voor het vastleggen van ‘weigeren om te ondertekenen’-handelingen. Wanneer gebruikers weigeren [!DNL Workday] Hiermee worden de documenten ter controle doorgestuurd naar een geconfigureerde beveiligingsgroep.

Via het menu Gerelateerde handelingen van een [!UICONTROL Documentstap controleren]selecteert u **[!UICONTROL Bedrijfsproces]** > **[!UICONTROL Omleiden behouden]**. Selecteer vervolgens een van de volgende opties:

* **[!UICONTROL Naar achtergrond]**: Om de leden van de veiligheidsgroep toe te laten om een stap terug naar een vroegere stap in het bedrijfsproces te verzenden. Het bedrijfsproces begint opnieuw bij die stap.
* **[!UICONTROL Ga naar volgende stap]**: Om de leden van de veiligheidsgroep toe te laten om een stap naar de volgende stap in het bedrijfsproces vooruit te gaan.
* **[!UICONTROL Beveiligingsgroepen]**: Om stappen in de bedrijfsprocesstroom om te leiden. De groepen van de veiligheid die bij deze herinnering tonen worden geselecteerd in het bedrijfsprocesveiligheidsbeleid in de Redirect sectie.

## Opmerkingen bij de stappen in het bedrijfsproces {#business-process-step-notes}

De [!UICONTROL Business Process Framework] krachtig is; u moet er echter voor zorgen dat :

* Elk bedrijfsproces moet een voltooiingsstap hebben, die idealiter aan het eind van het bedrijfsproces is.

* Er wordt een voltooiingsstap ingesteld in het menu met verwante handelingen van het zoekpictogram. Dit is alleen mogelijk tijdens het &quot;weergeven&quot; van het BP en niet tijdens het &quot;bewerken&quot; ervan.

* Elke stap van het bedrijfsproces wordt opeenvolgend uitgevoerd.

   U kunt de volgorde van een stap wijzigen door de waarde van de volgorde te wijzigen. Als u bijvoorbeeld een stap wilt invoegen tussen de items &quot;c&quot; en &quot;d&quot;, geeft u een nieuw item op als &quot;ca&quot;.

### Voorbeeld: aanbieden {#example-offer}

De BP van de Aanbieding is een subproces van het [!UICONTROL Dynamische BP van taaktoepassing] dat moet worden geconfigureerd om de BP van de Aanbieding uit te voeren. Deze wordt geactiveerd wanneer de status Taaktoepassing wordt verplaatst naar &quot;[!UICONTROL Aanbieding]&quot; of &quot;[!UICONTROL Aanbieding maken]&quot;.

In het onderstaande voorbeeld wordt een [!UICONTROL Documentstap controleren] gebruikt een stap Dynamisch document voor zowel Noord-Amerika als Japan.

![Voorbeeld van een [!DNL Workday] Bedrijfsproces](images/bp-for-offersmaller-575.png)

Dit BP doet het volgende:

* Verzoekt de initiatiefnemer van de BP om een compensatie voor de kandidaat voor te stellen (stap b).
* Gebruikt een stapvoorwaarde om te testen of het huidige land GEEN Japan is.

   Indien waar (true), wordt stap &#39;ba&#39; uitgevoerd, waarbij een Engelstalig document wordt gebruikt.

   Indien onwaar, voert het stap &quot;bb&quot;uit die een Japans taaldocument gebruikt.

* Definieert het ondertekeningsproces in het dialoogvenster [!UICONTROL Documentstap controleren] &quot;bc&quot;.
* Definieert het beslissingspunt om een aanbieding te doen in de vereiste voltooiingsstap &quot;d&quot;.

Het dynamische document dat in stap &quot;ba&quot; wordt gegenereerd, wordt [!UICONTROL Aanbiedingsbrief] en bevat één tekstblok met de naam [!UICONTROL Snelle aanbieding]. U kunt desgewenst meerdere tekstblokken toevoegen, zoals koptekst, aanhef, compensatie, voorraad, sluiten, voorwaarden en meer.

![[!DNL Workday] documentpagina weergeven](images/offer-letter-575.png)

De onderstaande dynamische aanbiedingsbrief wordt gemaakt in de [!DNL Workday] rijke teksteditor. De items gemarkeerd in *grijs* zijn [!DNL Workday] verschafte objecten die verwijzen naar contextuele gegevens.

Items in {{brackets}} zijn [Adobe-tekstlabels](https://adobe.com/go/adobesign_text_tag_guide).

![Voorbeeld van dynamisch formulier](images/script.png)

Binnen de [!UICONTROL Documentstap controleren]wordt vanaf de vorige stap naar het dynamische document verwezen en wordt het opeenvolgende ondertekeningsproces via twee ondertekeningsgroepen gedefinieerd.

Het gedrag dat hieronder wordt geïllustreerd leidt het dynamisch geproduceerde document eerst aan de Manager van de Helling, en dan aan de Kandidaat.

![[!DNL Workday] ondertekeningsgroepen die worden gedefinieerd](images/configure-rd-stepsmaller-575.png)

### Voorbeeld: Documenten distribueren {#example-distribute-documents}

Geïntroduceerd in [!DNL Workday] 30. Met de taak Mass Distribute Documents or Tasks kunt u één document naar een grote groep (&lt;20K) afzonderlijke ondertekenaars verzenden. Het is beperkt tot één handtekening per document. Het maken van een distributie wordt uitgevoerd door de opdracht ‘[!UICONTROL Verspreide documenten of taken maken]van de zoekbalk.

Voorbeeld: Verzend een formulier voor de keuze van een werknemer naar alle managers met [!UICONTROL Wereldwijde moderne services]. Desgewenst kunt u het filter verder filteren op individuele managers.

U kunt ook de **Documenten of taken distribueren weergeven** verslag uit om de voortgang van de verspreiding te volgen.

![](images/create-distributedocumentsortasks.png)

### Voorbeeld: Rapportage {#example-reporting}

[!DNL Workday] beschikt over een uitgebreide rapportageinfrastructuur. Als u de details van het Adobe Sign-proces wilt bekijken, inspecteert u de elementen van het *Revisiedocumentgebeurtenis*.

Hieronder vindt u een eenvoudig aangepast rapport dat kan worden uitgevoerd voor alle BP&#39;s die op zoek zijn naar Adobe Sign-transacties en hun status.

![Voorbeeld van een [!DNL Workday] Aangepast rapport](images/review-document-eventsmaller-575.png)

Het volgende rapport is gegenereerd door te kijken naar BP&#39;s voor aanbiedingen, onboarding en Propose Compensation binnen een implementatietenant.

Je kunt zien:

* De ter ondertekening verzonden documenten
* De bijbehorende stap BP
* De volgende persoon die wacht op ondertekening

![Voorbeeld van een [!DNL Workday] Rapport met drie objecten](images/workday-reportsmaller-575.png)

## Ondertekende documenten {#signed-documents}

De [!DNL Workday] handtekeningencyclus onderdrukt alle e-mailmeldingen van Adobe Sign. Gebruikers worden op de hoogte gesteld van lopende handelingen binnen hun [!DNL Workday] inbox.

Zodra een document is ondertekend door alle handtekeninggroepen, wordt een kopie van het ondertekende document via e-mail verspreid onder alle leden van de handtekeninggroep.

Als u dit gedrag wilt onderdrukken, kunt u contact opnemen met uw [!UICONTROL Adobe Sign Success Manager] of de [Adobe Sign-ondersteuningsteam](https://adobe.com/go/adobesign-support-center).

Within [!DNL Workday], hebt u toegang tot de ondertekende documenten in de volledige procesrecord. U kunt vinden:

* De documenten van de arbeider op het Profiel van de Arbeider, en
* Kandidaatdocumenten (aanbiedingsbrieven) op het kandidaatprofiel.

Op de onderstaande afbeelding ziet u een brief met een ondertekend aanbod voor de kandidaat Chris Foxx.

![Voorbeeld [!DNL Workday] aanbiedingsbrief](images/offer.png)

## Ondersteuning {#support}

### [!DNL Workday] ondersteuning {#workday-support}

[!DNL Workday] is de eigenaar van de integratie en moet uw eerste contactpunt zijn voor vragen over de reikwijdte van de integratie, functieverzoeken of problemen in het dagelijks functioneren van de integratie.

De [!DNL Workday] community heeft verschillende goede artikelen over het oplossen van problemen met de integratie en het genereren van documenten:

* [Integraties van e-handtekeningen oplossen](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Stap Documenten controleren](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamische documentgeneratie](https://community.workday.com/node/176443)
* [Tips voor configuratie van documentgeneratie](https://community.workday.com/node/183242)

### Adobe Sign-ondersteuning {#adobe-sign-support}

Adobe Sign is de integratiepartner en moet worden benaderd als de integratie geen handtekeningen krijgt of als het melden van handtekeningen in behandeling mislukt.

Adobe Sign-klanten moeten contact opnemen met hun [!UICONTROL Customer Success Manager] voor ondersteuning. Alternatief, [!UICONTROL Adobe Technische ondersteuning] telefonisch bereikbaar: 1-866-318-4100, wacht op productlijst dan ga binnen: 4 en vervolgens 2 (naar wens).

* [Adobe-tekstcodes toevoegen aan documenten](https://www.adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
