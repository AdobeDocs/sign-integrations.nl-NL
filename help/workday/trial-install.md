---
title: Workday-proefversie installeren
description: Workday-installatiegids voor een proefaccount in Adobe Sign
uuid: 0c51f329-b7c1-44a2-88a3-670be7673747
products: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 63ed2d5b-9d82-4f87-97e1-2dde23501e89
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: beafe6c0-262f-4f5b-9315-a023a4eef4a2
source-git-commit: ba5e0fccfdb7cd278cc0ae57dc03da1e17b51577
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 39%

---

# [!DNL Workday] Proefversie installeren{#workday-trial-installation}

## Overzicht {#overview}

Dit document is ontworpen om klanten van [!DNL Workday] te helpen bij het activeren van een proefaccount bij Adobe Sign en het vervolgens te integreren in [!DNL Workday] tenant. Als u Adobe Sign wilt gebruiken binnen [!DNL Workday], moet u weten hoe u [!DNL Workday]-items kunt maken en wijzigen, zoals:

* Kader voor bedrijfsprocessen
* Instelling en configuratie van de tenant
* Rapportage en integratie van [!DNL Workday] Studio

**Opmerking**: Als u een bestaand Adobe Sign-account hebt, hoeft u geen proefversie te starten. U kunt contact opnemen met uw Client Success Manager om [!DNL Workday]-integratie aan te vragen.

Dit zijn de geavanceerde stappen voor het voltooien van de integratie:

* Activeer uw proefaccount bij Adobe Sign
* Een integratiesleutel genereren in Adobe Sign
* Installeer de integratiesleutel in de [!DNL Workday] tenant

## Je Adobe Sign-proefaccount activeren {#activate-sign-trial-account}

Als u een proefversie van 30 dagen van Adobe Sign wilt aanvragen, moet u dit [registratieformulier](https://land.echosign.com/esign-trial-workday-registration.html) invullen.

**Opmerking**: We raden u ten zeerste aan een geldig functioneel e-mailadres te gebruiken om de proefversie te maken en geen tijdelijke e-mail. U moet deze e-mail openen om het account te verifiëren, dus het adres moet geldig zijn.

![Aanvraagformulier voor de proefversie](images/trial-land.png)

Binnen één werkdag kan een Adobe Sign on-boarding specialist uw account (in Adobe Sign) aanbieden voor [!DNL Workday]. Na voltooiing ontvangt u een bevestigingsbericht zoals hieronder getoond.

![De welkomste-mail van Adobe Sign](images/welcome-email-2020.png)

Volg de aanwijzingen in de e-mail om uw account te initialiseren en toegang te krijgen tot uw Adobe Sign-pagina [!UICONTROL Home].

![Het Adobe Sign-dashboard](images/classic-home.png)

## Een integratiesleutel genereren {#generate-an-integration-key}

Voor nieuwe installaties moet u een integratiesleutel genereren in Adobe Sign en deze vervolgens invoeren in [!DNL Workday]. Met deze sleutel worden de Adobe Sign- en [!DNL Workday]-omgevingen geverifieerd om elkaar te vertrouwen en inhoud te delen.

Een integratiesleutel genereren in Adobe Sign:

1. Meld u aan als beheerder in Adobe Sign.
1. Navigeer naar **[!UICONTROL **Account]** > **[!UICONTROL Persoonlijke voorkeuren]** > **[!UICONTROL Toegangstokens**]**.
1. Klik op het **omcirkelde pluspictogram** rechts in het venster.

   Het opent [!UICONTROL Create Integratiesleutel] interface.

   ![Afbeelding van de navigatie naar de pagina Toegangstoken](images/navigate-to-group-accesstokens.png)

1. Geef uw sleutel een intuïtieve naam, zoals [!DNL Workday].

   Voor de integratiesleutel moeten de volgende elementen zijn ingeschakeld:

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_read
   * library_read

   ![Het deelvenster Integratiesleutel maken](images/create-integration-key-575.png)

1. Klik op **[!UICONTROL Opslaan]**.

   De pagina [!UICONTROL Toegangstokens] verschijnt met de sleutels die zijn ontworpen in uw account.

1. Klik op de sleuteldefinitie die is gemaakt voor [!DNL Workday].

   De koppeling [!UICONTROL Integratiesleutel] verschijnt boven aan de definitie.

1. Klik op de koppeling **[!UICONTROL Integratiesleutel.]**

   De integratiesleutel wordt weergegeven.

   ![De koppeling Integratiesleutel](images/integration-key.png)

1. Kopieer deze sleutel en sla deze op een veilige plaats op voor de volgende stap.
1. Klik op **[!UICONTROL OK]**.

   ![Het deelvenster Integratiesleutel](images/copy-the-key-575.png)

## Configureer de [!DNL Workday] tenant {#configuring-the-workday-tenant}

### De integratiesleutel installeren {#install-the-integration-key}

Door de integratiesleutel in de [!DNL Workday] tenant te installeren, wordt de vertrouwensrelatie met Adobe Sign tot stand gebracht. Als die relatie eenmaal is ingesteld, kan aan elk bedrijfsproces een [!UICONTROL stap Document reviewen] worden toegevoegd die het ondertekeningsproces mogelijk maakt.

**Opmerking**: Adobe Sign is in de hele  [!DNL Workday] omgeving voorzien van het merkteken &quot;Adobe Document Cloud&quot;.

De integratiesleutel installeren:

1. Meld u bij [!DNL Workday] aan als accountbeheerder.
1. Zoek naar en open de pagina **[!UICONTROL Tenant instellen bewerken - Bedrijfsprocessen]**.

1. Geef informatie op voor de volgende vier velden:

   * **[!UICONTROL Adobe Document Cloud-erkenning]**: Een vaste tekstbevestiging van de integratie.

   * **[!UICONTROL Adobe Document Cloud API-sleutel]**: Waar de integratiesleutel is geïnstalleerd

   * **[!UICONTROL E-mailadres]** van Adobe Document Cloud-afzender: Het e-mailadres van de beheerder op groepsniveau in Adobe Sign

   * **[!UICONTROL Documenten verwijderen die wachten op e-handtekening wanneer het document wordt geannuleerd]**: Een optionele configuratie waarmee documenten uit de handtekeningencyclus worden verwijderd als een document wordt geannuleerd  [!DNL Workday].

   ![De velden voor de Adobe Sign-integratiesleutel](images/bp-filled-torn2-575.png)

1. Voltooi vervolgens de installatie:

   1. Plak uw integratiesleutel in het veld [!UICONTROL Integratiesleutel Adobe Sign-API.]
   1. Typ het e-mailadres van de beheerder van Adobe Sign in het veld [!UICONTROL E-mailadres afzender Adobe Document Cloud.]
   1. Klik op **[!UICONTROL OK]**.

   ![De velden Integratiesleutel en het e-mailveld voor sleutelhouders](images/bp-filled-small.png)

Adobe Sign-functionaliteit kan nu worden toegevoegd aan elk willekeurig bedrijfsproces door een [!UICONTROL stap Document controleren] toe te voegen en te configureren voor het gebruik van **[!UICONTROL eSign door Adobe]** als type e-handtekening.

### De stap Review Document Step configureren {#configure-the-review-document-step}

Het document voor de stap Review Document Step kan een statisch document zijn; een document dat is gegenereerd door een stap Document genereren binnen hetzelfde bedrijfsproces; of een opgemaakt rapport dat is gemaakt met de rapportontwerpfunctie [!DNL Workday]. U kunt al deze documenten verbeteren met [Adobe-tekstlabels](https://adobe.com/go/adobesign_text_tag_guide_nl) om de vormgeving en positie van specifieke componenten voor Adobe Sign te bepalen. De documentbron moet zijn opgegeven in de definitie van het bedrijfsproces. Het is niet mogelijk om een ad-hocdocument te uploaden terwijl het bedrijfsproces wordt uitgevoerd.

Uniek aan het gebruik van Adobe Sign met een stap Document bekijken is de mogelijkheid om ondertekenaarsgroepen met serienummering te hebben. Met ondertekenaarsgroepen kunt u op rollen gebaseerde groepen opgeven die zich achter elkaar aanmelden. Adobe Sign ondersteunt geen parallelle ondertekeningsgroepen.

Voor hulp die de Stap van het Document van het Overzicht vormt, kunt u naar [Snelle Gids van het Begin](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;} verwijzen.

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

Klanten van Adobe Sign dienen contact op te nemen met hun CSM (Customer Success Manager) voor ondersteuning. U kunt ook telefonisch bij Technische ondersteuning voor Adobe terecht komen: 1-866-318-4100; wacht op de productlijst en voer vervolgens in: 4 en vervolgens 2 (naar wens).

* [Adobe-tekstlabels toevoegen aan documenten](https://adobe.com/go/adobesign_text_tag_guide)

* [Documentconfiguratie en voorbeelden bekijken](https://www.adobe.com/go/adobesign_workday_quick_start)

[**Contact opnemen met de ondersteuning van Adobe Sign**](https://adobe.com/go/adobesign-support-center_nl)
