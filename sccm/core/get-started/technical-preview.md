---
title: A System Center Configuration Manager Technical Preview |} Microsoft Docs
description: "További tudnivalók a technikai előzetes kiadásaiban, hogy adjuk meg test-drive új funkciók és képességek a System Center Configuration Managerben."
ms.custom: na
ms.date: 4/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: 157
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 3a7370fedee417588d219dc7bff46205faf42929
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="technical-preview-for-system-center-configuration-manager"></a>A System Center Configuration Manager Technical Preview kiadása

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

**Üdvözli a System Center Configuration Manager Technical Preview**. Ebben a témakörben részletekkel szolgálunk a kialakulóban lévő előzetesről, amelyben a jelenleg fejlesztés alatt álló új funkciókat és képességeket állítjuk előtérbe. A technical preview egyes verzióival új funkciókkal bővül, amelyek nem szerepelnek a System Center Configuration Manager aktuális ágának technikai előzetes verzióját szeretné elérhetővé tenni időpontjában. Ezek a funkciók bekerülhetnek a jelenlegi ág kiadásának egy jövőbeli frissítésébe, ám mielőtt véglegesítenénk és hozzáadnánk őket, lehetőséget biztosítunk arra, hogy kipróbálja ezeket a funkciókat és véleményt mondjon róluk.  

 Mivel technikai előzetes kiadásról van szó, a részletek és a funkciók változhatnak.  

 Ez a témakör mellett a Technical Preview verziót, amelyben az adott képesség először megjelenik, például a 2017. január 1701 verziója a Technical Preview összes verziója vonatkozik, és minden új képesség (vagy a szolgáltatás) is felsorolja adatokat tartalmaz. Ezekről a képességekről részletes információt talál az egyes előzetes verziókkal foglalkozó külön témakörökben.  

 What's new in Configuration Manager aktuális ágának kapcsolatos információkért lásd: [újdonságai a System Center Configuration Managerben](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012).



##  <a name="bkmk_reqs"></a> A Technical Preview követelményei és korlátozásai  

> [!IMPORTANT]     
>  A Technical Preview kizárólag tesztkörnyezetben történő használatra készült.  A Microsoft nem mindig biztosít támogatást, és egyes funkciók nem érhetők el a Preview kiadású szoftverben. A Preview-szoftver továbbá csökkentett vagy másfajta biztonsági, adatvédelmi lehetőségekkel, hozzáférhetőséggel, elérhetőséggel vagy megbízhatósági szabványokkal rendelkezhet, mint a kereskedelmi forgalomban kapható szoftverek.  

 A legtöbb termék előfeltételeinek, olvassa el a a [a System Center Configuration Manager által támogatott konfigurációk](../../core/plan-design/configs/supported-configurations.md). A Technical Preview kiadásokra az alábbi kivételek érvényesek:  

-   Az egyes telepítések 90 napig maradnak aktívak, mielőtt inaktívvá válnának.  

-   Az egyetlen támogatott nyelv az angol.


-   Csak a következő telepítésjelzők (kapcsolók) támogatottak:  

    -   **/silent**  
    -   **/testdbupgrade**    


-   Alapértelmezés szerint a technical preview használatakor a szolgáltatáskapcsolódási pont online üzemmódban Ha értéke telepíti, és nem támogatja egy offline módra való átállítást.

-   A Technical Preview minden konkrét verziójában megjelennek további részletes korlátozások vagy követelmények, ha azok alkalmazhatók  

-   Az áttelepítés ebbe az előzetes buildbe vagy abból nem támogatott.  

-   A frissítés erre az előzetes buildre nem támogatott.  

-   Az erről az előzetes buildről egy éles üzemű buildre (jelenlegi ág) történő frissítés nem támogatott. Azonban ha frissítések érhetők el egy előzetes verzióhoz, akkor találhatja meg és telepítheti azokat a **frissítés és karbantartás** csomópont a Configuration Manager konzol. A youtube.com webhelyen [Installing ConfigMgr Update Packages](https://www.youtube.com/embed/KBd_EGFbUT8) címmel találhat egy videót a konzolon végrehajtott frissítési folyamatról.  
-   Csak az önálló elsődleges helyek támogatottak. A központi felügyeleti hely, több elsődleges hely és a másodlagos helyek nem támogatottak.  

A következő termékeket és technológiákat a Configuration Manager fiókirodai támogatja. Azonban az ehhez a tartalomhoz a nem jelenti a termék vagy a verziójával, amely a termék egyes támogatási életciklusa támogatása kiterjesztését. Terméktámogatási ciklusukon túllépett termékek esetében nem támogatottak a Configuration Managerrel történő használathoz. A Microsoft terméktámogatási ciklusokkal kapcsolatos további információk megtekinthetők a [Microsoft terméktámogatási ciklus](http://go.microsoft.com/fwlink/p/?LinkId=208270) webhelyen.  

-   Csak az SQL Server alábbi verziói támogatottak:  

    -   SQL Server 2016 (szervizcsomag nélkül, és újabb verziók)
    -   Az SQL Server 2014 (Service Pack 1 és újabb verziók)
    -   SQL Server 2012 (Service Pack 3 vagy újabb)


-   A hely legfeljebb 10 ügyfelet támogat, amelyeknek az alábbi rendszerek egyikét kell futtatniuk:  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 8  
      -   Windows 7  

##  <a name="bkmk_install"></a> A Technical Preview telepítése és frissítése  
 A System Center Configuration Manager Technical Preview különbözik a jelenlegi kiadásban a System Center Configuration Manager.  

 A Technical Preview használatához először telepítenie kell a Technical Preview build **alapverzióját** . Az alapverzió telepítése után a **konzolon elvégezhető frissítésekkel** frissítheti a példányokat a legújabb előzetes verzióra.     A Technical Preview új verziói jellemzően havonta jelennek meg.

Mindegyik előzetes esetén támogatott, amíg három egymást követő kiadások érhetők el. Ezért, ha 1702 verziókban, 1610 verziója már nem támogatott, de 1611, 1612 és 1701 támogatására marad. Ha egy alapkonfiguráció csökken a nem támogatott (például 1610. verzió), továbbra is támogatott új Technical Preview-helyeken telepíthető, amíg új verziójú alapkonfigurációként érhető el, mindaddig, majd frissítse az telepítés valamelyik támogatott verzióra. Frissítésekor, ha a legfrissebb elérhető a konzolon nem lát, frissítse a legújabb verzióra érhető el, és ismételje meg a folyamat addig, amíg a technical preview legújabb verziójának telepítése.

> [!TIP]  
>  Amikor frissítést telepít a technikai előzeteshez, akkor a telepített előzetes verziót az új technikai előzetes verzióra frissíti.    A telepített technikai előzetest soha nem lehet a szoftver aktuális ágára frissíteni, és nem kaphat frissítéseket sem az aktuális ágból.  

**A Technical Preview aktív alapverziói:**  
Egy alapkonfigurációt a kiadása után legfeljebb 1 évig is telepítheti. Azonban amikor telepít egy új technical preview-helyeken, ajánlott az elérhető legújabb alapkonfigurációt.
-  **Technical Preview 1703** -a Configuration Manager Technical Preview 1703 áll rendelkezésre, mind a konzolon belüli frissítések a Configuration Manager Technical Preview, és új verziójú alapkonfigurációként, amely elérhető a TechNet Evaluation Center webhelyről.

-  **Technical Preview 1610** -a Configuration Manager Technical Preview 1610 volt elérhető, mind a konzolon belüli frissítések a Configuration Manager Technical Preview, és egy alapszintű verzióra. Ha adathordozó 1610 telepítéséhez, ajánlott 1703 verziót töltse le és telepítse a verziót.




##  <a name="BKMK_TPFeedback"></a> Visszajelzés küldése  
 Hálásak lennénk, ha visszajelzést adna a technikai előzetes kiadásainkról. Az egyes előzetes kiadások képességeivel kapcsolatos visszajelzések elküldéséhez kövesse a Microsoft Connect webhely [Configuration Manager visszajelzési programjának](https://connect.microsoft.com/ConfigurationManagervnext/Feedback) lapján elérhető visszajelzési űrlapra mutató hivatkozást.  

 Érdeklődve várjuk továbbá a további új szolgáltatásokkal kapcsolatos ötleteit is. Ha új ötleteket szeretne elküldeni, vagy szavazna mások ötleteire, [látogasson el a felhasználói véleményekkel foglalkozó weblapunkra](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> Technikai előzetes verziókban elérhető képességek  
 Az alábbi táblázat az egyes Configuration Manager technikai előzetes kiadásaiban elérhető képességeket.  A technikai előzetes kezdeti verziójában elérhető képességek a további verziókban is elérhetők maradnak. Hasonlóképpen képességeket kínál, amelyek a System Center Configuration Manager Release (aktuális ág) lettek hozzáadva a későbbi technikai előzetesekben elérhetők maradnak.  Kattintson az egyes előzetes verziókra, ha többet szeretne megtudni egy adott képességről.  

 |Képesség |Technikai előzetes verzióra |Aktuális ág verziója|  
|----------------|---------------------|--------------------|
 |Android-alkalmazások konfigurálása alkalmazás-konfigurációs házirendek  |[Technikai előzetes 1704](capabilities-in-technical-preview-1704.md#configure-android-apps-with-app-configuration-policies)|![Nincs hozzáadva](media/Red_X.gif)|
 |A biztonságos rendszerindítás adatokat gyűjt a Hardverleltár |[Technikai előzetes 1704](capabilities-in-technical-preview-1704.md#hardware-inventory-collects-secure-boot-information)|![Nincs hozzáadva](media/Red_X.gif)|
 |Feladatütemezések gyermek hozzáadása egy feladatütemezéshez|[Technikai előzetes 1704](capabilities-in-technical-preview-1704.md#add-child-task-sequences-to-a-task-sequence)|![Nincs hozzáadva](media/Red_X.gif)|
 |Töltse be újra a rendszerindító lemezképek Windows PE aktuális verziójával |[Technikai előzetes 1704](capabilities-in-technical-preview-1704.md#reload-boot-images-with-current-windows-pe-version)|![Nincs hozzáadva](media/Red_X.gif)|
 |Operációs rendszer központi telepítésének fejlesztései|[Technikai előzetes 1704](capabilities-in-technical-preview-1704.md#improvements-to-operating-system-deployment)|![Nincs hozzáadva](media/Red_X.gif)|
 |Eszközgyűjtemények mennyiségi programban vásárolt iOS-alkalmazások telepítése|[Technikai előzetes 1703](capabilities-in-technical-preview-1703.md#deploy-volume-purchased-ios-apps-to-device-collections)|[1702 verziója](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)|
 |A Szoftverközpont elérhető alkalmazásokra mutató közvetlen hivatkozásokat|[Technikai előzetes 1703](capabilities-in-technical-preview-1703.md#direct-links-to-applications-in-software-center)|![Nincs hozzáadva](media/Red_X.gif)
 |A Configuration Manager Windows-ügyfélszámítógépek számára a PFX-tanúsítványok|[Technikai előzetes 1703](capabilities-in-technical-preview-1703.md#pfx-certificates-for-configuration-manager-windows-client-computers)|![Nincs hozzáadva](media/Red_X.gif)|
 |Azure Services varázsló konfigurálása|[Technikai előzetes 1703](capabilities-in-technical-preview-1703.md#configure-azure-services-wizard)|![Nincs hozzáadva](media/Red_X.gif)|
 |A BIOS átalakítása UEFI egy operációs rendszer frissítési feladatütemezés| [Technikai előzetes 1703](capabilities-in-technical-preview-1703.md#convert-from-bios-to-uefi-during-an-in-place-upgrade) |[1702 verziója](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)|
 |Az összecsukható feladatütemezési csoportok| [Technikai előzetes 1703](capabilities-in-technical-preview-1703.md#collapsible-task-sequence-groups) |![Nincs hozzáadva](media/Red_X.gif)|
 |Ügyfélbeállítások konfigurálása Windows Analytics készültségi frissítése | [Technikai előzetes 1703](capabilities-in-technical-preview-1703.md#client-settings-to-configure-windows-analytics-for-upgrade-readiness) |![Nincs hozzáadva](media/Red_X.gif)|
 |Új megfelelőségi beállítások az iOS-eszközök|[Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#new-compliance-settings-for-ios-devices)|[1702 verziója](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client)|
 |S/MIME-támogatással rendelkező PFX-tanúsítványok létrehozása|[Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#create-pfx-certificates-with-s-mime-support)|[1702 verziója](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |Ellenőrizze a végrehajtható fájlok futtatásának egy alkalmazás telepítése előtt|[Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#check-for-running-executable-files-before-installing-an-application)|[1702 verziója](/sccm/apps/deploy-use/deploy-applications)|
 |Visszajelzés küldése a Configuration Manager konzolról | [Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#send-feedback-from-the-configuration-manager-console)    |[1702 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1702#send-feedback-from-the-configuration-managercconsole)  |
 |Módosítások történtek a frissítések és karbantartás  | [Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#changes-for-updates-and-servicing)  |[1702 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1702#changes-for-updates-and-servicing) |
 |Társközi gyorsítótár fejlesztései  | [Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#peer-cache-improvements) |[1702 verziója](/sccm/core/plan-design/hierarchy/client-peer-cache)|
 |Az Azure Active Directory használatával  | [Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |![Nincs hozzáadva](media/Red_X.gif)|
 |Feltételes hozzáférés eszköz megfelelőségi házirend fejlesztései | [Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#conditional-access-device-compliance-policy-improvements) |[1702 verziója](/sccm/mdm/deploy-use/create-compliance-policy)|
 |Kártevőirtó ügyfélaktivitási verziója | [Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert) |[1702 verziója](/sccm/protect/deploy-use/endpoint-configure-alerts?branch=live#alert-for-outdated-malware-client)|
 |Az üzleti frissítések a Windows Update megfelelőségi vizsgálata | [Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |![Nincs hozzáadva](media/Red_X.gif)|
 |A Szoftverközpont beállítások és az értesítési üzenetek nagy jelentőségű feladatütemezésekhez fejlesztései|[Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert)|[1702 verziója](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)|
 |Android munkahelyi támogatásához| [Technikai előzetes 1702](capabilities-in-technical-preview-1702.md#android-for-work-support) |[1702 verziója](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-for-work-enrollment)|
 |Határ csoportok fejleszthetjük tovább a szoftverfrissítési pontok frissítése | [Technikai előzetes 1701](capabilities-in-technical-preview-1701.md#boundary-groups-improvements-for-software-update-points)    |[1702 verziója](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)  |
 |Hardverleltár UEFI adatokat gyűjt. | [Technikai előzetes 1701](capabilities-in-technical-preview-1701.md#hardware-inventory-collects-uefi-information)|[1702 verziója](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#hardware-inventory-collects-uefi-information) |
 |Operációs rendszer központi telepítésének fejlesztései| [Technikai előzetes 1701](capabilities-in-technical-preview-1701.md#improvements-to-operating-system-deployment)|[1702 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment) |
 |Szoftverfrissítések gazdagépet a felhő alapú terjesztési pontokon| [Technikai előzetes 1701](capabilities-in-technical-preview-1701.md#host-software-updates-on-cloud-based-distribution-points)|![Nincs hozzáadva](media/Red_X.gif) |
 |Eszközállapot-igazolási adatok felügyeleti pontokon keresztül ellenőrzése| [Technikai előzetes 1701](capabilities-in-technical-preview-1701.md#validate-device-health-attestation-data-via-management-points)| [1702 verziója](/sccm/core/servers/manage/health-attestation) |
 |A Microsoft Azure Government felhő OMS-összekötő |[Technikai előzetes 1701](capabilities-in-technical-preview-1701.md#use-the-oms-connector-for-microsoft-azure-government-cloud) |[1702 verziója](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig) |
 |Android és iOS verziója már nem nem targetable a létrehozása varázsló |[Technikai előzetes 1701](capabilities-in-technical-preview-1701.md#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |![Nincs hozzáadva](media/Red_X.gif) |
 |Az OData-végpont adatelérési |[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|![Nincs hozzáadva](media/Red_X.gif)|
 |Data Warehouse szolgáltatási pont |[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#the-data-warehouse-service-point)|[1702 verziója](/sccm/core/servers/manage/data-warehouse)|
 |Tartalomtár Lemezkarbantartó eszköz |[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#content-library-cleanup-tool)|[1702 verziója](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) |
 |A konzolon belüli keresési fejlesztései |[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#improvements-for-in-console-search)|[1702 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-for-in-console-search)|
 |Egy alkalmazás telepítése tiltása, ha egy adott programot futtat|[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#prevent-installation-of-an-application-if-a-specified-program-is-running)|[1702 verziója](/sccm/apps/deploy-use/deploy-applications)|
 |Új Windows Hello-üzleti értesítés a végfelhasználók számára|[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#new-windows-hello-for-business-notification-for-end-users)|![Nincs hozzáadva](media/Red_X.gif)|
 |Windows áruház vállalati verziójának ügyfélszolgálatával a Configuration Managerben|[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#windows-store-for-business-support-in-configuration-manager)|![Nincs hozzáadva](media/Red_X.gif)|
 |A feladatütemezés sikertelen lesz, ha az előző laphoz való visszatéréshez|[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#return-to-previous-page-when-a-task-sequence-fails)|[1702 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment)|
 |Az expressz telepítési fájlok Windows 10-frissítés támogatása|[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#express-installation-files-support-for-windows-10-updates)|[1702 verziója](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)|
 |Az Azure Active Directory bevezetésének|[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#azure-active-directory-onboarding)|![Nincs hozzáadva](media/Red_X.gif)|
 |Az eszközök regisztrálásához konfigurálása multi-factor Authentication módosítása|[Technikai előzetes 1612](capabilities-in-technical-preview-1612.md#change-to-configuring-multi-factor-authentication-for-device-enrollment)|![Nincs hozzáadva](media/Red_X.gif)|
 |Előzetes tartalmát és a feladatütemezések központi telepítései |[Technikai előzetes 1611](capabilities-in-technical-preview-1611.md#pre-cache-content-for-available-deployments-and-task-sequences)|[1702 verziója](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
 |A Windows Defender konfigurációs beállításai|[Technikai előzetes 1610](capabilities-in-technical-preview-1610.md#windows-defender-configuration-settings)|[1610 verziója](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |Kérelem házirend Szinkronizáló felügyeleti konzoljáról|[Technikai előzetes 1610](capabilities-in-technical-preview-1610.md#request-policy-sync-from-administrator-console)|[1610 verziója](/sccm/mdm/deploy-use/sync-intune-device)|
 |Minden céges eszköz csomópont alatt további biztonsági szerepkör támogatása|[Technikai előzetes 1610](capabilities-in-technical-preview-1610.md#additional-security-role-support)|[1610 verziója](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management#new-hybrid-features-in-november-2016)|
 |Feltételes hozzáférés a Windows 10 VPN-profilok|[Technikai előzetes 1610](capabilities-in-technical-preview-1610.md#conditional-access-for-windows-10-vpn-profiles)|[1610 verziója](/sccm/protect/deploy-use/create-vpn-profiles#configure-the-authentication-method-for-the-vpn-profile)|
 |A szűrőt az automatikus központi telepítési szabályokat a tartalom mérete alapján|[Technikai előzetes 1610](capabilities-in-technical-preview-1610.md#filter-by-content-size-in-automatic-deployment-rules)|[1610 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1610#filter-by-content-size-in-automatic-deployment-rules) |
 |Szükséges szoftverek párbeszédpanelek továbbfejlesztett funkciók|[Technikai előzetes 1610](capabilities-in-technical-preview-1610.md#improved-functionality-for-required-software-dialogs)|[1610 verziója](/sccm/apps/deploy-use/deploy-applications)|
 |Korábban már jóváhagyott alkalmazáskérelmeinek megtagadása|[Technikai előzetes 1610](capabilities-in-technical-preview-1610.md#deny-previously-approved-application-requests)|[1610 verziója](/sccm/apps/deploy-use/deploy-applications)|
 |Ügyfelek kizárása az automatikus frissítés|[Technikai előzetes 1610](capabilities-in-technical-preview-1610.md#exclude-clients-from-automatic-upgrade)|[1610 verziója](/sccm/core/clients/manage/upgrade/exclude-clients-windows)|
 |Az Endpoint Protection fejlesztései|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#improvements-to-endpoint-protection)|[1610 verziója](/sccm/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)|
 |A regisztrált eszközök megnövekedett számát|[Technikai előzetes 1609](/sccm/mdm/deploy-use/enable-platform-enrollment)|[1610 verziója](/sccm/mdm/deploy-use/enable-platform-enrollment)|
 |További Apple DEP-beállítások|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#additional-apple-dep-settings)|[1610 verziója](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)|
 |Windows áruház Továbbfejlesztett integráció a vállalati és a Configuration Managerben|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md)|[1610 verziója](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |Új megfelelőségi beállítások a konfigurációs elemek|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#new-compliance-settings-for-configuration-items)|[1610 verziója](/sccm/compliance/deploy-use/create-configuration-items)|
 |Integráció a frissítési elemzés|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#integration-with-upgrade-analytics)|[1610 verziója](/sccm/core/clients/manage/upgrade/upgrade-analytics)|
 |A Windows 10 VPN hibrid profilok natív kapcsolat típusai|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#native-connection-types-for-windows-10-vpn-hybrid-profiles)|![Nincs hozzáadva](media/Red_X.gif)|
 |A határcsoportok fejlesztései|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#improvements-for-boundary-groups)|[1610 verziója](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#BKMK_BoundaryGroups)|
 |Az Office 365-ügyfél kezelési irányítópult|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#office-365-client-management-dashboard)|[1610 verziója](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard)|
 |Office 365-alkalmazásokat telepíteni az ügyfelek számára|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#deploy-office-365-apps-to-clients)|[1702 verziója](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)|
 |UEFI-átalakítás BIOS fejlesztései|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#BKMK_UEFIConversion)|[1610 verziója](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion)|
 |Intune megfelelőségi diagramok|[Technikai előzetes 1609](capabilities-in-technical-preview-1609.md#intune-compliance-charts)|[1610 verziója](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)|
 |A „ConfigMgr-ügyfél előkészítése a rögzítéshez” feladatütemezési lépés fejlesztései|[Technikai előzetes 1608](capabilities-in-technical-preview-1608.md#improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step)|[1610 verziója](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture)|
 |A szoftverközpont fejlesztései|[Technikai előzetes 1608](capabilities-in-technical-preview-1608.md#improvements-to-software-center)|[1610 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1610#general-improvements-to-software-center)|
 |Az Eszközintelligencia fejlesztései|[Technikai előzetes 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|![Nincs hozzáadva](media/Red_X.gif)|
 |A távvezérlés billentyűzet fordítás|[Technikai előzetes 1608](capabilities-in-technical-preview-1608.md#remote-control-keyboard-translation)|![Nincs hozzáadva](media/Red_X.gif)|
 |A Windows 10-kiadás frissítési szabályzatának változásai|[Technikai előzetes 1607](capabilities-in-technical-preview-1607.md#dmp_edition)|[1610 verziója](/sccm/compliance/deploy-use/upgrade-windows-version)|
 |Testreszabható védjegyezés a Software Center-párbeszédpanelekhez|[Technikai előzetes 1607](capabilities-in-technical-preview-1607.md#customizable-branding-for-software-center-dialogs)|![Nincs hozzáadva](media/Red_X.gif)|  
 |Többszörös eszközfelügyeleti pontok a helyszíni mobileszköz-felügyelethez|[Technikai előzetes 1606](capabilities-in-technical-preview-1606.md#dmp_onprem)|[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606#on-premises-mobile-device-management)|
 |Eszközök gyűjteménybe rendezése automatikusan|[Technikai előzetes 1606](capabilities-in-technical-preview-1606.md#dmp_category)|[1606 verziója](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections) |
 |Végrehajtási türelmi időszak a szükséges alkalmazások és szoftverfrissítések központi telepítésére|[Technikai előzetes 1606](capabilities-in-technical-preview-1606.md#dmp_grace)|[1610 verziója](/sccm/apps/deploy-use/deploy-applications)|
 |A Configuration Manager használata felügyelt telepítőként a Device Guarddal|[Technikai előzetes 1606](capabilities-in-technical-preview-1606.md#dmp_devg)|![Nincs hozzáadva](media/Red_X.gif)|
 |Felügyeleti átjáró (korábbi nevén Felhőbeli proxyszolgáltatás)|[Technikai előzetes 1606](capabilities-in-technical-preview-1606.md#cloud_proxy) | [1610 verziója](/sccm/core/clients/manage/plan-cloud-management-gateway)|  
 |Office 365-ügyfélügynök felügyelete a Configuration Managerben|[Technikai előzetes 1606](capabilities-in-technical-preview-1606.md#manage_o365) |[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606#software-updates)|  
 |A OSDPreserveDriveLetter feladatütemezési változó elavult|[Technikai előzetes 1606](capabilities-in-technical-preview-1606.md#osdpreservedriveletter) |[1606 verziója](/sccm/osd/understand/task-sequence-built-in-variables) |
 |A Frissítés és karbantartás csomópont változásai|[Technikai előzetes 1606](capabilities-in-technical-preview-1606.md#updatesandservicing)|[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606#updates-and-servicing) |
 |Alkalmazásonkénti VPN Windows 10-es eszközökhöz|[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_PerAppVPN)|[1606 verziója](/sccm/protect/deploy-use/create-vpn-profiles)|  
 |A „Szoftverfrissítések telepítése” feladatütemezési művelet fejlesztései|[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_InstallSU)|[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
 |A „ConfigMgr-ügyfél előkészítése a rögzítéshez” feladatütemezési lépés fejlesztései |[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_PrepareConfigMgrClient)|[1610 verziója](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) |
 |Türelmi időszak a szükséges alkalmazástelepítésekhez |[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_Grace)|![Nincs hozzáadva](media/Red_X.gif)|  
 |A távoli eszközök műveleteinek új felülete |[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_Remote)|[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Vállalati Windows Áruházbeli alkalmazások |[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_WSFB)|[1606 verziója](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |A mennyiségi licencszerződés keretében vásárolt alkalmazások általános fejlesztései|[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP2)|[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Nagyvállalati adatvédelem|[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP)|[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |A végfelhasználók alkalmazásokat telepíthetnek a vállalati portálról |[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|![Nincs hozzáadva](media/Red_X.gif)|  
 |Új lapok a frissítések és operációs rendszerek számára a Szoftverközpontban|[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_SW1)|[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Kiszolgálócsoport karbantartása |[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|[1606 verziója](/sccm/sum/deploy-use/service-a-server-group)|   
 |A Windows Defender Komplex veszélyforrások elleni védelem támogatása |[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_ATP)|[1606 verziója](/sccm/protect/deploy-use/windows-defender-advanced-threat-protection)|  
 |Új újraindítási lehetőségek Windows 10-ügyfelek számára szoftverfrissítés telepítése után|[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_RestartOptions)|[1606 verziója](/sccm/sum/plan-design/plan-for-software-updates#restart-options-for-Windows-10-clients-after-software-update-installation)|  
 |Helyszíni készülékállapot-igazolás |[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_DHA)|[1606 verziója](/sccm/core/servers/manage/health-attestation)|  
 |IMEI- vagy iOS-sorozatszámú céges eszközök előzetes bejelentése|[Technikai előzetes 1605](capabilities-in-technical-preview-1605.md#BKMK_IMEI)|[1606 verziója](/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id)|  
 |A Vállalati Windows Áruházból mennyiségi licencszerződés keretében vásárolt alkalmazások felügyelete| [Műszaki Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_WindowsVPP)|[1606 verziója](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |A Microsoft Passport for Work felügyeletének fejlesztései|[Műszaki Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_PFW)|[1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Lehetőség új szoftverfrissítési pontra való váltásra az ügyfeleken|[Műszaki Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_switchsup)|[1606 verziója](/sccm/sum/plan-design/plan-for-software-updates#BKMK_ManuallySwitchSUPs)|  
 |Az ügyfélgyorsítótár beállításainak és az ügyfél társgyorsítótárának kezelésére szolgáló beállítások |[Műszaki Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_peercache)|Ügyfélbeállítások: [1606 verziója](/sccm/core/plan-design/changes/whats-new-in-version-1606#administration)<br/>Társ-gyorsítótárazás: [1610 verziója](/sccm/core/plan-design/hierarchy/client-peer-cache)|  
 |A Passport for Work támogatása kulcstároló-szolgáltatóként |[Műszaki Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_passport)|[1606 verziója](/sccm/protect/deploy-use/create-certificate-profiles)|  
 |Helyszíni készülékállapot-igazolás|[Műszaki Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_onpremdha)|[1606 verziója](/sccm/core/servers/manage/health-attestation)|  
 |SmartLock-beállítás Android-eszközökhöz|[Műszaki Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_Smart)|[1606 verziója](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-and-samsung-knox-configuration-item-settings-reference)|  
 <!--  TP 1603 Aged out of support and all features in Current Branch Builds:
 |Improvements to Software Center|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_SC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Improvements to remote control|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#remote-control)|  
 |Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RamDiskTFTP)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
-->
 Technical preview kiadások összes szolgáltatása az aktuális ág minimális támogatott verziója rendelkezésre áll, amikor el lesznek távolítva, az előzetes verzióhoz tartozó részletek ezt a táblázatot.


## <a name="see-also"></a>Lásd még:  
[Újdonságok a System Center Configuration Managerben](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [A System Center Configuration Manager bemutatása](../../core/understand/introduction.md)

