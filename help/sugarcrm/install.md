---
title: Adobe EchoSign for SugarCRM
description: Installatiehandleiding voor het inschakelen van de Adobe Sign-integratie met SugarCRM
product: Adobe Sign
content-type: reference
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 0512f616-568a-4b96-9bd1-48e67bc3536b
source-git-commit: 54216c4fc9442b6291e6b253fa619a1b62a0f40b
workflow-type: tm+mt
source-wordcount: '2354'
ht-degree: 1%

---


# [!DNL SugarCRM] Installatiegids {#sugarcrm-install-guide}

[Contact opnemen met de klantenservice](https://adobe.com/go/adobesign-support-center_nl)

Adobe [!DNL EchoSign] voor [!DNL SugarCRM] is een toonaangevende oplossing voor e-handtekeningen en webcontracten die elektronische handtekeningautomatisering biedt in [!DNL SugarCRM] voor e-handtekeningen en handtekeningen faxen. Gebruikers kunnen rechtstreeks contracten verzenden vanuit SugarCRM, de contractgeschiedenis bekijken en elektronisch ondertekende contracten opslaan met gekoppelde accounts, contactpersonen, offertes en meer.
Adobe [!DNL EchoSign] voor [!DNL SugarCRM] is beschikbaar voor alle ondersteunde versies van SugarCRM, inclusief 6.3 - 6.7 voor on-demand of on-premise oplossingen.

Dit document is een richtlijn voor [!DNL SugarCRM] beheerders om te leren hoe u Adobe [!DNL EchoSign] voor [!DNL SugarCRM] plug-in installeert en configureert.

## Deze insteekmodule installeren {#install-plugin}

1. Haal de Adobe [!DNL EchoSign] voor [!DNL SugarCRM]-archiefbestand op uit de [SugarExchange-lijst](http://www.sugarexchange.com/product_details.php?product=1123).
1. Meld u met uw beheerdersaccount aan bij [!DNL SugarCRM].
1. Ga naar **[!UICONTROL Beheer]** > **[!UICONTROL Module Loader]**.

   ![Afbeelding](images/module-loader.png)

1. Als u het archiefbestand van de Adobe [!DNL EchoSign] voor [!DNL SugarCRM]-plug-in wilt uploaden, selecteert u **[!UICONTROL Bladeren]**, selecteert u het archiefbestand en selecteert u **[!UICONTROL Uploaden]**.
1. Nadat het archiefbestand is geüpload, selecteert u **[!UICONTROL Installeren]** om de installatie te starten.
1. Bekijk de voorwaarden en bepalingen en selecteer **[!UICONTROL Accepteren]** > **[!UICONTROL Vastleggen]**.
1. Als de insteekmodule is geïnstalleerd, geeft de voortgangsbalk aan dat de installatie 100% is gelukt.  Als de voortgangsbalk niet 100% bereikt, selecteert u **[!UICONTROL Display Log]** om de fout te zien die door SugarCRM wordt aangetroffen.

   ![Afbeelding](images/display-log.png)

1. Ga na de installatie naar **[!UICONTROL Beheer > Repareren]** en selecteer **[!UICONTROL Snel repareren en opnieuw samenstellen]**.

>[!NOTE]
>
>Als u de plug-in op [!DNL SugarCRM] Op verzoek installeert, dient u een ondersteuningsticket in bij [!DNL SugarCRM] om de beperkingen van de pakketcontrole voor OnDemand tijdelijk te verwijderen, zodat het pakket kan worden geïnstalleerd. Dit maakt deel uit van het standaardproces.

## De insteekmodule upgraden {#upgrade-plugin}

Als u de Adobe [!DNL EchoSign] voor [!DNL SugarCRM]-plug-in bijwerkt naar een nieuwere versie, moet u de plug-in installeren zonder de vorige versie te verwijderen.
Nadat u de insteekmodule hebt bijgewerkt, gaat u naar **[!UICONTROL Beheer]** > **[!UICONTROL Repareren]** en selecteert u **[!UICONTROL Snelle reparatie en opnieuw samenstellen]**.

**Opmerking:** Als u een vorige plug-in verwijdert, dient u de tabellen niet te verwijderen tijdens het verwijderen. Anders kunt u de [!DNL EchoSign] overeenkomstgegevens verliezen.

## De insteekmodule configureren {#configure-plugin}

1. Als u al een Adobe-klant bent, gaat u door met stap 2.[!DNL EchoSign]

   Als u geen [!DNL EchoSign]-account hebt, [meld u aan voor een GRATIS proefversie van 14 dagen](https://sugarcrmintegration.echosign.com/public/login) en volg de stappen voor online registratie om uw Adobe [!DNL EchoSign]-account in te schakelen.
1. Meld u aan bij [Echo Sign-account](http://www.echosign.com) en voer de volgende stappen uit:
   1. Selecteer het tabblad **[!UICONTROL Account]**.
   1. Selecteer **[!UICONTROL EchoSign API]** linksonder.
   1. Selecteer **[!UICONTROL API-toegang inschakelen]** en ontvang uw API-sleutel van de pagina.

   ![Afbeelding](images/enable-api-access.png)

1. Ga in SugarCRM naar **[!UICONTROL Beheer]** > **[!UICONTROL Adobe EchoSign-instellingen]** en voer de API-sleutel in het veld **[!UICONTROL EchoSign API-sleutel]** in.
1. Configureer desgewenst de plug-in met de volgende instellingen:

   1. Automatisch PDF koppelen bij het maken van een overeenkomst vanuit een offerte: Selecteer of u automatisch een PDF van de offerte wilt bijvoegen als een [!DNL SugarCRM]-gebruiker een EchoSign-overeenkomst maakt in de module Aanhalingstekens.
   1. Lijst met ontvangers beheren: Selecteer welke modules worden weergegeven in het subdeelvenster Ontvanger in de module [!DNL EchoSign] Overeenkomsten. Hiermee wordt ook het subdeelvenster Overeenkomsten [!DNL EchoSign] aan deze modules toegevoegd.
   1. Voeg de verzendknoppen toe aan deze modules: Selecteer deze optie als u de knop of handeling Overeenkomst maken [!DNL EchoSign] wilt opnemen in de primaire handelingen van de Offertemodule.
   1. Selecteer **[!UICONTROL Opslaan]** om uw instellingen op te slaan.

**Opmerking:** De Adobe  [!DNL EchoSign] voor  [!DNL SugarCRM] insteekmodule vereist de  [PHP SOAP-extensie](http://www.php.net/manual/en/book.soap.php). Om SOAP-ondersteuning mogelijk te maken, configureert u PHP met enable-soap.

## Overeenkomstupdates ophalen (voor [!DNL SugarCRM] versies 6.3 of hoger) {#get-agreement-updates}

Voor versie 6.3 en hoger kunt u de volgende twee opties gebruiken om overeenkomsten te laten bijwerken. In eerdere versies van SugarCRM biedt de plug-in standaard alleen de callback-methode (optie 1).

### Optie 1: Stel de callback-methode in voor het pushen van updates naar EchoSign

Als uw website een openbare website is, kunt u ervoor zorgen dat Adobe EchoSign uw [!DNL SugarCRM]-instantie pingelt wanneer er een nieuwe gebeurtenis plaatsvindt. [!DNL SugarCRM] werkt vervolgens de overeenkomststatus, de gebeurtenissen bij en downloadt het ondertekende document (indien ondertekend) automatisch en in real-time. (Als u zich achter een firewall bevindt, moet u de IP-adressen van de [!DNL EchoSign]-server op een whitelist plaatsen of de geplande taakmethode voor het bijwerken van EchoSign-overeenkomsten gebruiken, zoals beschreven in de volgende sectie van deze handleiding).

1. Ga naar **[!UICONTROL Beheer]** > **[!UICONTROL Adobe EchoSign-instellingen]**.
1. Schakel het selectievakje **[!UICONTROL EchoSign-callbackmethode gebruiken]** in om gebeurtenissen en statussen van overeenkomsten bij te werken.
1. Selecteer **[!UICONTROL Opslaan]**.

### Optie 2: Stel een geplande taak in voor [!DNL SugarCRM] instanties achter een firewall

De [!DNL EchoSign] voor [!DNL SugarCRM] plug-in kan ook een Geplande taak gebruiken om [!DNL EchoSign] te vragen naar updates voor overeenkomsten die zijn verzonden ter ondertekening. De geplande methode van de baanvraag kan worden gebruikt als u een on-premise [!DNL SugarCRM] installatie achter een firewall hebt.

Instellen:

1. Ga naar **[!UICONTROL Beheer]** > **[!UICONTROL Planner]**.
1. Selecteer **[!UICONTROL Planning maken]** in het vervolgkeuzemenu voor tabbladen.
1. Voer een taaknaam in.
1. Selecteer **[!UICONTROL Adobe EchoSign Status Updater]** voor het veld Taak.
1. Stel de taak zo vaak als nodig in. Wij stellen voor om de overeenkomst elke 10 minuten te laten uitvoeren. Dit betekent dat het, nadat een overeenkomst is geopend, gelezen of ondertekend, tot 10 minuten kan duren voordat [!DNL SugarCRM] met die informatie wordt bijgewerkt.

   **Opmerking:** Als u veel overeenkomsten ter ondertekening hebt verzonden, kan dit te vaak leiden tot een vertraging van uw systeem.

   ![Afbeelding](images/echosign-status-updater.png)

1. Ga naar **[!UICONTROL Beheer]** > **[!UICONTROL Adobe EchoSign-instellingen]**.
1. Schakel het selectievakje **[!UICONTROL EchoSign-callbackmethode]** gebruiken uit om gebeurtenissen en statussen van overeenkomsten bij te werken.
1. Selecteer **[!UICONTROL Opslaan]**.
Opmerking: Schakel Planners in [!DNL SugarCRM] in om dit te laten werken.

EchoSign-overeenkomsten toevoegen aan andere [!DNL SugarCRM]-modules:

1. Ga naar **[!UICONTROL Beheer]** > **[!UICONTROL Studio]**.
1. Selecteer in de linkerkolommapstructuur de module voor het toevoegen van [!DNL EchoSign] overeenkomsten.
1. Selecteer **[!UICONTROL Relaties]** **[!UICONTROL Relaties toevoegen]**.
1. Selecteer in het vervolgkeuzemenu Tekst als **[!UICONTROL Een tot Veel]** en Module als **[!UICONTROL EchoSign-overeenkomsten]**.
1. Selecteer **[!UICONTROL Opslaan en implementeren]**.

   ![Afbeelding](images/save-and-deploy.png)

   [!DNL EchoSign] Overeenkomsten worden nu in de module weergegeven en overeenkomsten kunnen daar worden gemaakt en bijgehouden.

   ![Afbeelding](images/echosign-agreements.png)

**Andere configuratiestappen**

* **Verborgen  [!DNL EchoSign] modules**: U kunt de modules  [!DNL EchoSign] Ontvangers en  [!DNL EchoSign] Gebeurtenissen verbergen door naar de Tabs en Subpanels van de Module van het Beleid te gaan en hen naar de verborgen kolom te verplaatsen.
* **Pakketscan** uitschakelen: Als u packageScan op uw eigen systeem hebt ingeschakeld, moet u het tijdens de installatie uitschakelen. Als u [!DNL SugarCRM] On-Demand gebruikt, neemt u contact op met de [!DNL SugarCRM]-ondersteuning om packageScan voor u uit te schakelen.

## De insteekmodule verwijderen {#uninstall-plugin}

1. Meld u met uw beheerdersaccount aan bij [!DNL SugarCRM].
1. Ga naar **[!UICONTROL Beheer]** > **[!UICONTROL Module Loader]**.
1. Selecteer **[!UICONTROL Verwijderen]** naast de [!UICONTROL EchoSign for SugarCRM-plug-in].
1. Selecteer **[!UICONTROL Vastleggen]** om te beginnen met verwijderen. U kunt ook selecteren om de databasetabellen te verwijderen die voor de plug-in zijn gemaakt.

   ![Afbeelding](images/uninstall-plugin.png)

   Als de insteekmodule is verwijderd, geeft de voortgangsbalk aan dat de installatie 100% is gelukt. Als de voortgangsbalk niet 100% bereikt, selecteert u [!UICONTROL Display Log] om de fout te zien die door SugarCRM wordt aangetroffen.

   ![Afbeelding](images/uninstall-display-log.png)

## Adobe [!DNL EchoSign] gebruiken voor [!DNL SugarCRM] {#use-echosign-for-sugarcrm}

U kunt een Adobe-overeenkomst maken die is gekoppeld aan een account-, contact-, offerte- of andere [!DNL SugarCRM]-modules. [!DNL EchoSign] U kunt bestanden bijvoegen, ontvangers opgeven en ter ondertekening verzenden. Adobe [!DNL EchoSign] werkt [!DNL SugarCRM] bij met de huidige status van de overeenkomst en slaat het ondertekende contract op in [!DNL SugarCRM] zodra het volledig is uitgevoerd.

### Een Adobe-overeenkomst maken en bewerken[!DNL EchoSign] {#create-edit-agreements}

U kunt overeenkomsten maken via de module [!DNL EchoSign] Overeenkomsten of via modules die zijn geconfigureerd door een [!DNL SugarCRM]-beheerder.

1. Selecteer [!UICONTROL Handelingen] in de lijst op het tabblad [!UICONTROL EchoSign-overeenkomsten] **[!UICONTROL EchoSign-overeenkomst maken]**.
1. Voer in het hoofdgedeelte van de overeenkomst de volgende informatie in of maak een keuze uit verschillende opties voor overeenkomsten:[!DNL EchoSign]

   1. **[!UICONTROL Naam:]** voer een naam in voor de overeenkomst.
   1. **[!UICONTROL Handtekeningtype:]** Selecteer het type handtekening dat is geaccepteerd voor het document. De opties zijn e-handtekening en Handtekening faxen.
   1. **[!UICONTROL Ik moet deze overeenkomst ook ondertekenen:]** geef aan of de afzender de overeenkomst ook moet ondertekenen.
   1. **[!UICONTROL Handtekeningvolgorde:]** Als de vorige optie die ik ook moet ondertekenen is ingeschakeld, selecteert u ook de volgorde waarin de afzender en ontvangers moeten ondertekenen.
   1. **[!UICONTROL Ontvangers eraan herinneren te tekenen:]** Selecteer hoe vaak een ontvanger moet worden herinnerd om een document te ondertekenen. De opties zijn Dagelijks of Wekelijks.
   1. **[!UICONTROL Dagen tot ondertekeningsdeadline:]** geef het aantal dagen op tot de overeenkomst moet worden ondertekend.
   1. **[!UICONTROL Voorbeeld, positie handtekening of voeg formuliervelden toe:]**  selecteer deze optie om een voorbeeld van de overeenkomst te bekijken voordat deze wordt verzonden of sleep handtekeningvelden, beginvelden of andere formuliervelden naar de overeenkomst voordat deze naar ontvangers wordt verzonden. Nadat u een voorvertoning van het document hebt weergegeven of de gewenste velden naar het document hebt gesleept, moet u de knop Verzenden selecteren om de overeenkomst naar de ontvanger te verzenden.
   1. **[!UICONTROL Host tekent voor de eerste ondertekenaar:]** geef aan of de afzender de overeenkomst persoonlijk wil ondertekenen.
      * **[!UICONTROL Bericht:]** voeg een bericht voor de ontvanger toe.
      * **[!UICONTROL Account, Opportunity, Offerte:]** Selecteer of wijzig de account, opportunity of offerte die aan deze overeenkomst is gekoppeld.
      * **[!UICONTROL Taal:]** Geef de taal op waarin de ondertekeningspagina en e-mailmeldingen aan de ontvangers worden weergegeven.

      ![Afbeelding](images/create-agreements.png)


1. Voer in de sectie [!UICONTROL Beveiligingsopties] van de [!UICONTROL EchoSign-overeenkomst] de volgende informatie in:

   a) **[!UICONTROL Wachtwoord vereist om te ondertekenen:]** Geef aan of een wachtwoord moet worden ingevoerd voordat een ontvanger een document kan ondertekenen.
b) **[!UICONTROL Wachtwoord vereist voor openen:]** Geef aan of een wachtwoord moet worden ingevoerd voordat een ontvanger een PDF van de overeenkomst of ondertekende overeenkomst kan openen
c) **[!UICONTROL Wachtwoord:]** Geef het wachtwoord op dat moet worden gebruikt om een document te ondertekenen of te openen.
d) **[!UICONTROL Wachtwoord bevestigen:]** Bevestig het wachtwoord om een document te ondertekenen of te openen.

1. Voer in het gedeelte Overige van de overeenkomst de volgende informatie in:[!DNL EchoSign]

   a) **[!UICONTROL Gebruiker:]** Geef een [!DNL SugarCRM]-gebruiker op. De standaardinstelling is de gebruiker die momenteel is aangemeld bij het systeem.
b) **[!UICONTROL Teams:]** Als u de primaire teamtoewijzing wilt wijzigen, voert u de naam van het nieuwe primaire team in. Als u extra teams aan de record wilt toewijzen, klikt u op **[!UICONTROL Selecteren]** en selecteert u een team in de Teamlijst of selecteert u **[!UICONTROL Toevoegen aan]** om teamvelden toe te voegen en de teamnamen in te voeren. Zie &#39;Records toewijzen aan gebruikers en teams&#39; in de [!DNL SugarCRM] handleiding voor toepassingen voor meer informatie.

1. Selecteer **[!UICONTROL Opslaan]**.

### [!DNL EchoSign] weergave van overeenkomstdetails {#agreement-detail-view}

Nadat een [!DNL EchoSign] overeenkomst is opgeslagen, bevat de detailweergave van de overeenkomst de volgende subdeelvensters:

* **[!UICONTROL Ontvangers:]** Alle contactpersonen in dit subdeelvenster ontvangen de documenten die zijn opgegeven in het subdeelvenster Documenten. U moet een of meer ontvangers toevoegen voordat u de overeenkomst verzendt.
* **[!UICONTROL Documenten:]** Upload een nieuw document of selecteer een document dat al is geüpload  [!DNL SugarCRM] om ter ondertekening te verzenden.
* **[!UICONTROL Gebeurtenissen:]** Elke handeling met betrekking tot de overeenkomst, zoals wanneer de overeenkomst ter ondertekening is verzonden, bekeken of ondertekend, wordt in dit subdeelvenster weergegeven.
Als u een [!DNL EchoSign]-overeenkomst wilt bewerken, selecteert u de knop [!UICONTROL Bewerken] in de [!UICONTROL Gedetailleerde weergave] van de overeenkomst.

![Afbeelding](images/agreement-detail-view.png)

**Opmerking:** Nadat een overeenkomst ter ondertekening is verzonden, wordt de knop   Bewerken verwijderd uit de detailweergave om de record van gebeurtenissen te behouden. U kunt echter wel de knop Bewerken inschakelen. Ga hiertoe naar [!UICONTROL Beheer] > [!UICONTROL Adobe EchoSign-instellingen] en schakel de optie *[!UICONTROL uit Wanneer een overeenkomst ter ondertekening is verzonden, kunt u de bewerking of verwijdering van]* uitschakelen.

### Een document toevoegen aan een [!DNL EchoSign]-overeenkomst {#add-document}

[!DNL SugarCRM] gebruikers kunnen een nieuw document uploaden of een document selecteren dat al is geüpload  [!DNL SugarCRM] met behulp van het subdeelvenster Documenten van een EchoSign-overeenkomstrecord.
Als u een document wilt uploaden, selecteert u **[!UICONTROL Document uploaden]** in het subdeelvenster [!UICONTROL Documenten].

Zie de sectie ‘Documentmodule’ van de [!DNL SugarCRM] toepassingshandleiding voor meer informatie over de afzonderlijke velden van dat formulier.

Als u een document wilt selecteren, klikt u op **[!UICONTROL Selecteren]** in het subdeelvenster Documenten. Zie &#39;Record-informatie weergeven en beheren&#39; in de [!DNL SugarCRM] toepassingshandleiding voor meer informatie over het beheren van gerelateerde informatie in subdeelvensters.

![Afbeelding](images/add-document-to-agreement.png)

### Een ontvanger opgeven voor een overeenkomst [!DNL EchoSign] {#specify-recipient}

1. Selecteer in het subdeelvenster [!UICONTROL Ontvanger] van een [!DNL EchoSign]-overeenkomst **[!UICONTROL Ontvanger toevoegen]**.
1. Voer de volgende gegevens in:
a) [!UICONTROL Ontvanger:] Selecteer het type ontvanger in de vervolgkeuzelijst. Typ de naam of het e-mailadres van de ontvanger in het tekstveld. [!DNL SugarCRM] zoekt de naam op terwijl u typt en biedt een lijst met selecties aan. Selecteer een naam als er een overeenkomst is gevonden. U kunt ook het pijlpictogram selecteren om een naam te selecteren in een pop-upvenster. Als u de naam uit het veld wilt wissen, selecteert u het pictogram **[!UICONTROL X]**.
b) [!UICONTROL Rol:] Selecteer een rol in het vervolgkeuzemenu. De opties zijn Ondertekenaar en CC en Fiatteur. Een fiatteur hoeft het document niet te ondertekenen.
1. Selecteer Opslaan.

![Afbeelding](images/add-recipient-to-agreement.png)

### Overeenkomsten verzenden ter ondertekening {#send-for-signature}

Als overeenkomsten klaar zijn om ter ondertekening te worden verzonden, selecteert u **[!UICONTROL Send for Signature]** in het vervolgkeuzemenu linksboven op de pagina. De ontvangers ontvangen vervolgens een e-mail waarin ze op de hoogte worden gesteld van de documenten die op hun handtekening wachten. Nadat de ontvangers het document hebben ondertekend, ontvangt de afzender een e-mailmelding.
Als de optie [!UICONTROL Host tekent voor eerste ondertekenaar] is ingeschakeld, kunt u **[!UICONTROL Send for Signature]** selecteren om de ondertekenaar in staat te stellen het document te ondertekenen met de aanwezige afzender.

![Afbeelding](images/send-for-signature.png)

Er verschijnt een koppeling **[!UICONTROL Host Signing for Current Signer]** ook naast het veld [!UICONTROL Host Signing for First Signer], dat kan worden geopend totdat het document is ondertekend. U kunt deze koppeling gebruiken om de ondertekening van overeenkomsten voor meerdere ondertekenaars te hosten of om het pop-upvenster opnieuw te openen als het per ongeluk is gesloten.
Als [!UICONTROL Voorvertoning, positie handtekening of formuliervelden toevoegen] is ingeschakeld, selecteert u **[!UICONTROL Send for Signature]** om de afzender toe te staan een voorvertoning van het document weer te geven of velden naar het document te slepen voordat het document wordt verzonden. U moet **[!UICONTROL Verzenden]** in dat venster selecteren om de overeenkomst naar de ontvanger te verzenden.

Figuur 5: Selecteer Send for Signature om een document ter ondertekening naar een ontvanger te verzenden.

### Verzenden vanuit een offerterecord {#send-from-quote-record}

Adobe [!DNL EchoSign] is rechtstreeks geïntegreerd met offertes in [!DNL SugarCRM], zodat de PDF van de offerte automatisch wordt gegenereerd en als bijlage aan de overeenkomstrecord wordt toegevoegd.
Als u een offerte weergeeft, selecteert u **[!UICONTROL EchoSign-overeenkomst maken]** om de offerte te genereren en deze automatisch aan de overeenkomst te koppelen. In de nieuwe overeenkomst worden ook automatisch verwante opportunity&#39;s, accounts of offertes gekoppeld.

![Afbeelding](images/create-echosign-agreement.png)

Als u de automatische bijlage van de offerte-PDF bij de overeenkomst wilt uitschakelen, gaat u naar **[!UICONTROL Beheer]** > **[!UICONTROL Adobe EchoSign-instellingen]** en schakelt u het selectievakje *[!UICONTROL PDF automatisch koppelen uit bij het maken van een overeenkomst op basis van een offerte]*.

### Een overeenkomst annuleren {#cancel-agreement}

U kunt een [!DNL EchoSign]-overeenkomst annuleren nadat deze ter ondertekening is verzonden als alle ontvangers het document nog niet hebben ondertekend. Een [!UICONTROL Overeenkomst annuleren]-knop verschijnt in de detailweergave van een overeenkomst nadat een document ter ondertekening is verzonden. Selecteer **[!UICONTROL Overeenkomst annuleren]** om de overeenkomst te annuleren.

![Afbeelding](images/cancel-agreement.png)

Opmerking: Als een [!DNL EchoSign]-overeenkomst ter ondertekening wordt verzonden en de record wordt verwijderd, moet u de overeenkomst annuleren voordat u deze verwijdert.

### Handtekeningen bijhouden {#track-signatures}

In het subdeelvenster [!UICONTROL Gebeurtenissen] van een [!DNL EchoSign]-overeenkomst wordt de status bijgehouden van overeenkomsten die ter ondertekening worden verzonden. Selecteer **[!UICONTROL Status bijwerken]** om de laatste updates van een [!DNL EchoSign]-overeenkomst te bekijken. De knop [!UICONTROL Status bijwerken] is alleen beschikbaar nadat een overeenkomst ter ondertekening is verzonden.

![Afbeelding](images/update-cancel-status.png)

Nadat een overeenkomst ter ondertekening is verzonden, selecteert u **[!UICONTROL Status bijwerken]** om de laatste status op te halen.

![Afbeelding](images/events-subpanel.png)

### Herinneringen verzenden {#send-reminders}

Selecteer **[!UICONTROL Herinnering verzenden]** om een herinnering naar de huidige ondertekenaar te verzenden na het verzenden van de overeenkomst. Het verzendt onmiddellijk een e-mailherinnering naar de huidige ondertekenaar over de overeenkomst die op ondertekening wacht.

![Afbeelding](images/send-reminder.png)
