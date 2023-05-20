---
title: Installatie van Workday-proefversie
description: Workday-installatiegids voor een proefaccount in Adobe Sign
uuid: 0c51f329-b7c1-44a2-88a3-670be7673747
products: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 63ed2d5b-9d82-4f87-97e1-2dde23501e89
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: beafe6c0-262f-4f5b-9315-a023a4eef4a2
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---

# [!DNL Workday] Proefinstallatie{#workday-trial-installation}

## Overzicht {#overview}

Dit document is ontworpen om [!DNL Workday] klanten leren hoe ze een proefaccount kunnen activeren bij Adobe Sign en deze vervolgens kunnen integreren in [!DNL Workday] tenant. Adobe Sign gebruiken in [!DNL Workday], moet u weten hoe u kunt maken en wijzigen [!DNL Workday] items zoals:

* Kader voor bedrijfsprocessen
* Instelling en configuratie van de tenant
* Rapportage en [!DNL Workday] Studio-integratie

**Opmerking**: Als u een bestaand Adobe Sign-account hebt, hoeft u niet een proefversie te starten. U kunt contact opnemen met uw Client Success Manager om een verzoek in te dienen [!DNL Workday] integratie.

De stappen op hoog niveau om integratie te voltooien zijn:

* Activeer je proefaccount met Adobe Sign
* Een integratiesleutel genereren in Adobe Sign
* Installeer de integratiesleutel in de [!DNL Workday] Tenant

## Je Adobe Sign-proefaccount activeren {#activate-sign-trial-account}

Als u een 30-daagse proefversie van Adobe Sign wilt aanvragen, moet u deze invullen [registratieformulier](https://land.echosign.com/esign-trial-workday-registration.html).

**Opmerking**: We raden u ten zeerste aan een geldig functioneel e-mailadres te gebruiken om de proefversie te maken en geen tijdelijke e-mail. U moet deze e-mail openen om het account te verifiëren, dus het adres moet geldig zijn.

![Het aanvraagformulier voor proefversies](images/trial-land.png)

Binnen één werkdag kan een Adobe Sign on-boarding specialist uw account (in Adobe Sign) voorzien voor [!DNL Workday]. Na voltooiing ontvangt u een bevestigingsbericht zoals hieronder getoond.

![Het welkomstbericht van Adobe Sign](images/welcome-email-2020.png)

Uw account initialiseren en toegang krijgen tot uw Adobe Sign [!UICONTROL Home] , volgt u de aanwijzingen in de e-mail.

![Het Adobe Sign-dashboard](images/classic-home.png)

## Een integratiesleutel genereren {#generate-an-integration-key}

Voor nieuwe installaties moet u een integratiesleutel genereren in Adobe Sign en deze vervolgens invoeren in [!DNL Workday]. Deze sleutel verifieert de Adobe Sign en [!DNL Workday] omgevingen om elkaar te vertrouwen en content te delen.

Een integratiesleutel genereren in Adobe Sign:

1. Meld u aan bij uw beheerder in Adobe Sign.
1. Navigeren naar **[!UICONTROL **Account]** > **[!UICONTROL Persoonlijke voorkeuren]** > **[!UICONTROL Toegangstokens**]**.
1. Klik op **omcirkeld plusteken** aan de rechterkant van het venster.

   Het opent de [!UICONTROL Integratiesleutel maken] interface.

   ![Afbeelding van de navigatie naar de pagina Toegangstokens](images/navigate-to-group-accesstokens.png)

1. Geef uw sleutel een intuïtieve naam, zoals [!DNL Workday].

   De integratiesleutel moet de volgende elementen hebben ingeschakeld:

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_read
   * library_read

   ![Het deelvenster Integratiesleutel maken](images/create-integration-key-575.png)

1. Klikken **[!UICONTROL Opslaan]**.

   De [!UICONTROL Toegangstokens] wordt weergegeven met de sleutels die in uw account zijn ontworpen.

1. Klik op de sleuteldefinitie die is gemaakt voor [!DNL Workday].

   De [!UICONTROL Integratiesleutel] wordt boven aan de definitie weergegeven.

1. Klik op **[!UICONTROL Integratiesleutel]** koppeling.

   De integratiesleutel wordt weergegeven.

   ![De koppeling integratiesleutel](images/integration-key.png)

1. Kopieer deze sleutel en sla deze op een veilige plaats op voor de volgende stap.
1. Klikken **[!UICONTROL OK]**.

   ![Het deelvenster Integratiesleutel](images/copy-the-key-575.png)

## Configureer de [!DNL Workday] huurder {#configuring-the-workday-tenant}

### De integratiesleutel installeren {#install-the-integration-key}

De integratiesleutel in het dialoogvenster [!DNL Workday] tenant brengt de vertrouwensrelatie met Adobe Sign tot stand. Als die relatie eenmaal tot stand is gebracht, kan elk bedrijfsproces een [!UICONTROL Documentstap controleren] toegevoegd om het ondertekeningsproces mogelijk te maken.

**Opmerking**: Adobe Sign is overal in de [!DNL Workday] milieu.

De integratiesleutel installeren:

1. Meld u aan bij [!DNL Workday] als accountbeheerder.
1. Zoek naar en open **[!UICONTROL Tenant instellen bewerken - Bedrijfsprocessen]** pagina.

1. Geef informatie op voor de volgende vier velden:

   * **[!UICONTROL Adobe Document Cloud-dankbetuiging]**: Een vaste tekstbevestiging van de integratie.

   * **[!UICONTROL Adobe Document Cloud API-sleutel]**: Waar de integratiesleutel is geïnstalleerd

   * **[!UICONTROL E-mailadres Adobe Document Cloud-afzender]**: Het e-mailadres van de beheerder op groepsniveau in Adobe Sign

   * **[!UICONTROL Documenten verwijderen die nog niet zijn ondertekend wanneer het document is geannuleerd]**: Een optionele configuratie waarmee documenten uit de handtekeningencyclus worden verwijderd als een document wordt geannuleerd in [!DNL Workday].

   ![De velden voor de Adobe Sign-integratiesleutel](images/bp-filled-torn2-575.png)

1. Voltooi vervolgens de installatie:

   1. Plak uw integratiesleutel in de [!UICONTROL Adobe Sign API Integration Key] veld.
   1. Typ het e-mailadres van de Adobe Sign-beheerder in het dialoogvenster [!UICONTROL E-mailadres Adobe Document Cloud-afzender] veld.
   1. Klikken **[!UICONTROL OK]**.

   ![De velden Integratiesleutel en het e-mailveld voor de belangrijkste houder](images/bp-filled-small.png)

Adobe Sign-functionaliteit kan nu aan elk willekeurig bedrijfsproces worden toegevoegd door een [!UICONTROL Documentstap controleren] en configureren voor gebruik **[!UICONTROL Elektronisch ondertekenen door Adobe]** als het type e-handtekening.

### De stap Review Document Step configureren {#configure-the-review-document-step}

Het document voor de stap Review Document Step kan een statisch document zijn; een document dat is gegenereerd door een stap Document genereren binnen hetzelfde bedrijfsproces; of een opgemaakt rapport dat is gemaakt met de [!DNL Workday] Rapportontwerper. Al deze gevallen kunnen worden aangevuld met [Adobe-tekstlabels](https://adobe.com/go/adobesign_text_tag_guide) om het uiterlijk en de positie van de specifieke componenten voor ondertekening door de Adobe te bepalen. De documentbron moet worden opgegeven binnen de definitie van het bedrijfsproces. Het is niet mogelijk om een ad-hocdocument te uploaden terwijl het bedrijfsproces wordt uitgevoerd.

Uniek aan het gebruik van Adobe Sign met een stap Document bekijken is de mogelijkheid om ondertekenaarsgroepen met serienummering te hebben. Met ondertekenaarsgroepen kunt u op rollen gebaseerde groepen opgeven die zich achter elkaar aanmelden. Adobe Sign ondersteunt geen parallelle ondertekeningsgroepen.

Voor hulp bij het configureren van de stap Review Document Step, kunt u verwijzen naar de [Aan de slag](https://adobe.com//go/adobesign_workday_quick_start){target="_blank"}.

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

Adobe Sign-klanten moeten contact opnemen met hun Customer Success Manager (CSM) voor ondersteuning. U kunt ook telefonisch bij Technische ondersteuning voor Adobe terecht komen: 1-866-318-4100; wacht op de productlijst en voer vervolgens in: 4 en vervolgens 2 (naar wens).

* [Adobe-tekstcodes toevoegen aan documenten](https://adobe.com/go/adobesign_text_tag_guide)

* [Documentconfiguratie en voorbeelden bekijken](https://www.adobe.com//go/adobesign_workday_quick_start){target="_blank"}

[**Contact opnemen met Adobe Sign-ondersteuning**](https://www.adobe.com/go/adobesign-support-center)
