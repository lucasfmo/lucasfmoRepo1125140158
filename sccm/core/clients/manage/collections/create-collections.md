---
title: "Gyűjtemények létrehozása |} Microsoft Docs"
description: "Gyűjtemények létrehozása a System Center Configuration Manager könnyebben kezelhetik a felhasználók és eszközök csoportja."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1401a35e-4312-4d3b-8ceb-0abbb10d4f05
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: dee63826d8e6100f5b8402952175106076585030
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-collections-in-system-center-configuration-manager"></a>Gyűjtemények létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Gyűjtemények felhasználó vagy eszköz csoportosításain. Alkalmazáskezelés, a megfelelőségi beállítások központi, vagy szoftverfrissítéseket telepít, például gyűjtemények használata. Emellett gyűjtemények segítségével kezelheti az ügyfélbeállítások csoportjait, vagy szerepköralapú adminisztrációval használhatja azokat azon erőforrások megadására, amelyekhez a rendszergazda felhasználók hozzáférhetnek. A Configuration Manager számos beépített gyűjteményt tartalmaz. További információkért lásd: [a System Center Configuration Manager gyűjteményeinek bemutatása](../../../../core/clients/manage/collections/introduction-to-collections.md).  

> [!NOTE]  
>  Egy gyűjtemény tartalmazhat, felhasználók vagy eszközök, de soha sem egyszerre mindkettőre.  

 Az alábbi táblázat segítségével konfigurálja egy gyűjtemény tagjai a Configuration Manager szabályokat sorolja fel.  

|Tagsági szabály típusa|További információ|  
|--------------------------|----------------------|  
|Közvetlen szabály|Segítségével a felhasználók és a gyűjteményhez hozzáadni kívánt számítógépek kiválasztását. A tagság nem változik, kivéve, ha eltávolít egy erőforrást a Configuration Manager alkalmazásból. A Configuration Manager kell felderíteni az erőforrásokat, vagy Ön importálta az erőforrások közvetlen szabálygyűjteményekhez való is felvételük előtt. A közvetlen szabálygyűjteményekkel rendelkezik mint a lekérdezési szabálygyűjtemények nagyobb adminisztrációs terhelés, mert azok megkövetelik, hogy a manuális módosítások.|  
|Lekérdezési szabály|Dinamikus frissítése a Configuration Manager ütemezés szerint futtatott lekérdezés alapján gyűjtemény tagsága. Így például létrehozhat egy, az Active Directory tartományi szolgáltatásokban az Emberi erőforrások szervezeti egységben tag felhasználókat tartalmazó gyűjteményt. Ez a gyűjtemény automatikusan frissül, amikor új felhasználókat ad hozzá, vagy eltávolítja az emberi erőforrások szervezeti egységben.<br /><br /> Például a lekérdezéseket, amelyekkel létrehozása a gyűjtemények, lásd: [lekérdezések létrehozása a System Center Configuration Managerben](../../../../core/servers/manage/create-queries.md).|  
|Gyűjteménybefoglalási szabály|Egy másik gyűjtemény tagjainak szerepeljenek az aktuális gyűjtemény tagsága ütemezés szerint frissül, ha megváltozik a belefoglalt gyűjtemény Configuration Manager-gyűjteményhez.<br /><br /> Egy gyűjteményhez több gyűjteménybefoglalási szabályt is hozzáadhat.<br /> |  
|Gyűjteménykizárási szabály|A gyűjteménykizárási szabály lehetővé teszi egy másik gyűjtemény tagjainak kizárását a Configuration Manager-gyűjteményhez. Az aktuális gyűjtemény tagsága ütemezés szerint frissül, ha megváltozik a kizárt gyűjtemény.<br /><br /> Egy gyűjteményhez több gyűjteménykizárási szabályt is hozzáadhat. Ha egy gyűjteménybe is közé tartoznak a gyűjteményhez, és kizárási és ütközés lép, a gyűjteménykizárási szabály élvez elsőbbséget.<br />              **Példa:** Létrehozhat egy gyűjteményt, amely egy gyűjteménybefoglalási szabályt, és egy gyűjteménykizárási szabályt. A gyűjteménybefoglalási szabály a Dell asztali számítógépek gyűjteményét határozza meg. A gyűjteménykizárási szabály a 4 GB-nál kevesebb memóriával rendelkező számítógépek gyűjteményét határozza meg. Az új gyűjtemény azon Dell asztali számítógépeket fogja tartalmazni, amelyek legalább 4 GB memóriával rendelkeznek.|  

 Az alábbi eljárásokkal hozhat létre gyűjteményeket a Configuration Manager alkalmazásban. Ez vagy egy másik Configuration Manager-helyen létrehozott gyűjteményeket is importálhat. További információ a gyűjtemények importálása és exportálása: [a System Center Configuration Manager gyűjtemények kezelése](../../../../core/clients/manage/collections/manage-collections.md).  

 További információ a Linux és UNIX rendszerű számítógépek gyűjtemények létrehozásáról: [kezelése a Linux és UNIX rendszerű kiszolgálókon a System Center Configuration Manager-ügyfelek](../../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md).  

##  <a name="BKMK_1"></a> Eszközgyűjtemény létrehozása  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **Eszközgyűjtemények**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **eszközgyűjtemény létrehozása**.  

4.  Az a **általános** oldalon adja meg a **neve** és egy **Megjegyzés**. Ezt követően a **korlátozó gyűjtemény**, válassza a **Tallózás** jelölje be a korlátozó gyűjteményt. A gyűjtemény csak a korlátozó gyűjtemény tagjait fogja tartalmazni.  

5.  Az a **tagsági szabályok** oldalán a **eszközgyűjtemény létrehozása varázsló**, a a **szabály hozzáadása** listára, válassza ki a gyűjteményhez használni kívánt tagsági szabály típusa. Az egyes gyűjteményekhez több szabályt is konfigurálhat.  

        
        ##### To configure a direct rule  

        1.  Az **Eszközgyűjtemény létrehozása varázsló** **Erőforrás keresése**lapján adja meg a következő információkat:  

            -   **Erőforrásosztály**: Válassza ki a keresse meg és a gyűjteményhez hozzáadni kívánt erőforrás típusát. Válasszon a **Rendszererőforrás** értékek közül az ügyfélszámítógépek által visszaadott leltári adatok kereséséhez, vagy – ha az ismeretlen számítógépek által visszaadott értékek közül szeretne választani – válassza az **Ismeretlen számítógép** lehetőséget.  

            -   **Az attribútumnév**: Válassza ki a keresni kívánt kijelölt erőforrásosztályhoz társított attribútumot. Így például, ha a NetBIOS-név szerint szeretné kiválasztani a számítógépeket, válassza az **Erőforrásosztály** listából a **Rendszererőforrás** , az **Attribútum neve** listából pedig a **NetBIOS-név** elemet.  

            -   **Elavultként megjelölt erőforrások kizárása** – Ha egy ügyfélszámítógép elavultként, van megjelölve. Ez az érték nem tartalmaznak a keresési eredmények között.  

            -   **A Configuration Manager-ügyféllel nem rendelkező erőforrások kizárása** -ezek nem jelennek meg a keresési eredmények között.  

            -   **Érték:** Adjon meg egy értéket, amelynek a kijelölt attribútumnévben keresni szeretne. A százalékjel karaktert ( **%** ) helyettesítő karakterként használhatja. Olyan számítógépeket szeretne keresni, amelyek rendelkeznek egy NetBIOS neve "M" kezdetű, írja be például **M %** ebben a mezőben.  

        2.  Az a **erőforrások kiválasztása** lapon, válassza ki a gyűjteményhez hozzáadni kívánt erőforrások a **erőforrások** listában, és válassza a **következő**.  


        ##### To configure a query rule  

        1.  A **Lekérdezési szabály tulajdonságai** párbeszédpanelen adja meg a következő információkat:  

            -   **Név**: Adjon egyedi nevet.  

            -   **Lekérdezési utasítás importálása** – megnyitja a **tallózási lekérdezés** párbeszédpanelt, ahol kiválaszthatja a [Configuration Manager-lekérdezés](../../../../core/servers/manage/create-queries.md) a gyűjteményhez lekérdezési szabályként használandó.   

            -   **Erőforrásosztály:** Válassza ki a keresse meg és a gyűjteményhez hozzáadni kívánt erőforrás típusát. Válasszon egyet a **Rendszererőforrás** értékek közül az ügyfélszámítógépek által visszaadott leltári adatok kereséséhez, vagy – ha az ismeretlen számítógépek által visszaadott értékek közül szeretne választani – válassza az **Ismeretlen számítógép** lehetőséget.  

            -   **Lekérdezési utasítás szerkesztése** – megnyitja a **lekérdezési utasítás tulajdonságai** párbeszédpanel, amelyen elkészítheti egy lekérdezést a szabály használata a gyűjteményhez. A lekérdezésekkel kapcsolatban a [Technikai útmutató a System Center Configuration Manager lekérdezéseihez](../../../../core/servers/manage/queries-technical-reference.md) című cikk nyújt részletes tájékoztatást.  

    
        ##### To configure an include collection rule  

        In the **Select Collections** dialog box, select the collections you want to include in the new collection, then choose **OK**.  

        ##### To configure an exclude collection rule  

        In the **Select Collections** dialog box, select the collections you want to exclude from the new collection, then choose **OK**.  

    -   **Növekményes frissítések használata a gyűjteményhez** – válassza ezt a beállítást, rendszeres időközönként keressen, és frissíti az új vagy módosított erőforrásainak az előző gyűjteménykiértékeléshez képest, a teljes gyűjteményértékeléstől. A növekményes frissítések 10 perces időközönként történnek.  

        > [!IMPORTANT]  
        >  A következő osztályokat használó lekérdezési szabályok segítségével konfigurált gyűjtemények nem támogatják a növekményes frissítéseket:  
        >   
        >  -   SMS_G_System_CollectedFile  
        > -   SMS_G_System_LastSoftwareScan  
        > -   SMS_G_System_AppClientState  
        > -   SMS_G_System_DCMDeploymentState  
        > -   SMS_G_System_DCMDeploymentErrorAssetDetails  
        > -   SMS_G_System_DCMDeploymentCompliantAssetDetails  
        > -   SMS_G_System_DCMDeploymentNonCompliantAssetDetails  
        > -   SMS_G_User_DCMDeploymentCompliantAssetDetails (csak felhasználók gyűjteményei esetén)  
        > -   SMS_G_User_DCMDeploymentNonCompliantAssetDetails (csak felhasználók gyűjteményei esetén)  
        > -   SMS_G_System_SoftwareUsageData  
        > -   SMS_G_System_CI_ComplianceState  
        > -   SMS_G_System_EndpointProtectionStatus  
        > -   SMS_GH_System_ *  
        > -   SMS_GEH_System_ *  

    -   **A gyűjteményhez teljes frissítést ütemeznie** – a gyűjtemény tagsága rendszeres teljes értékelésének ütemezéséhez.  

6.  Az új gyűjtemény létrehozásához fejezze be a varázslót. Az új gyűjtemény az **Eszközök és megfelelőség** munkaterület **Eszközgyűjtemények** csomópontjában jelenik meg.  

> [!NOTE]  
>  Frissítse vagy töltse be újra a Configuration Manager konzolon a gyűjtemény tagjainak megjelenítéséhez. Azonban a tagok nem jelenik meg a gyűjtemény csak az első ütemezett frissítés után, vagy manuálisan válasszon **tagság frissítése** ahhoz a gyűjteményhez. A gyűjtemény frissítése néhány percig is eltarthat.  

##  <a name="BKMK_2"></a> Felhasználói gyűjtemény létrehozása  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **Felhasználógyűjtemények**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **Felhasználógyűjtemény létrehozása**.  

4.  Az a **általános** a wizardprovide oldalán egy **neve** és egy **Megjegyzés**. Ezt követően a **korlátozó gyűjtemény**, válassza a **Tallózás** jelölje be a korlátozó gyűjteményt. A gyűjtemény csak a korlátozó gyűjtemény tagjait fogja tartalmazni.  

5.  Az a **tagsági szabályok** lapján adja meg a következőket:  

    -   A **Szabály hozzáadása** listából válassza ki a gyűjteményhez használni kívánt tagsági szabálytípust. Az egyes gyűjteményekhez több szabályt is konfigurálhat.  

         ##### <a name="to-configure-a-direct-rule"></a>Közvetlen szabály konfigurálása  

        1.  Az a **erőforrás keresése** oldalán a **közvetlen tagsági szabály létrehozása varázsló**, adja meg:  

            -   **Erőforrásosztály**: Válassza ki a keresse meg és a gyűjteményhez hozzáadni kívánt erőforrás típusát. Válassza ki a **felhasználói erőforrás** értékeit a Configuration Manager által gyűjtött felhasználói adatok kereséséhez vagy **felhasználói csoporterőforrás** felhasználói csoportadatok Configuration Manager által összegyűjtött kereséséhez.  

            -   **Az attribútumnév**: Válassza ki a keresni kívánt erőforrásosztály társított attribútumot. Így például, ha a szervezeti egység (OU) neve szerint szeretné kiválasztani a felhasználókat, válassza az **Erőforrásosztály** listából a **Felhasználói erőforrás** , az **Attribútum neve** listából pedig a **Felhasználó OU-neve** elemet.  

            -   **Érték:** A keresendő értéket adjon meg. A százalékjel karaktert ( **%** ) helyettesítő karakterként használhatja. A Contoso szervezeti Egységben található felhasználók kereséséhez adja meg például **Contoso** ebben a mezőben.  

        2.  Az a **erőforrások kiválasztása** lapon, válassza ki a gyűjteményhez hozzáadni kívánt erőforrások a **erőforrások** listája.  

        ##### <a name="to-configure-a-query-rule"></a>Lekérdezési szabály konfigurálása  

        1.  Az a **lekérdezési szabály tulajdonságai** párbeszédpanelen adja meg:  

            -   **Név**: Egy egyedi nevet.  

            -   **Lekérdezési utasítás importálása** – megnyitja a **tallózási lekérdezés** párbeszédpanelt, ahol kiválaszthatja a [Configuration Manager-lekérdezés](../../../../core/servers/manage/queries-technical-reference.md) a gyűjteményhez lekérdezési szabályként használandó.  

            -   **Erőforrásosztály**: Válassza ki a keresse meg és a gyűjteményhez hozzáadni kívánt erőforrás típusát. Válassza ki a **felhasználói erőforrás** értékeit a Configuration Manager által gyűjtött felhasználói adatok kereséséhez vagy **felhasználói csoporterőforrás** felhasználói csoportadatok Configuration Manager által összegyűjtött kereséséhez.  

            -   **Lekérdezési utasítás szerkesztése** -megnyitja a **lekérdezési utasítás tulajdonságai** párbeszédpanelt, ahol [lekérdezés szerzői](../../../../core/servers/manage/queries-technical-reference.md) való használata a szabály a gyűjteményhez.  

        ##### <a name="to-configure-an-include-collection-rule"></a>Gyűjteménybefoglalási szabály konfigurálása  

        Az a **gyűjtemények kiválasztása** párbeszédpanelen jelölje ki az új gyűjteménybe felvenni, majd kattintson a kívánt gyűjteményeket **OK**.  

        ##### <a name="to-configure-an-exclude-collection-rule"></a>Gyűjteménykizárási szabály konfigurálása  

        Az a **gyűjtemények kiválasztása** párbeszédpanelen jelölje ki az új gyűjteményből kizárni, majd kattintson a kívánt gyűjteményeket **OK**.  


    -   **Növekményes frissítések használata a gyűjteményhez** – válassza ezt a beállítást, rendszeres időközönként keressen, és frissíti az új vagy módosított erőforrásainak az előző gyűjteménykiértékeléshez képest, a teljes gyűjteményértékeléstől. A növekményes frissítések 10 perces időközönként történnek.  

        > [!IMPORTANT]  
        >  A következő osztályokat használó lekérdezési szabályok segítségével konfigurált gyűjtemények nem támogatják a növekményes frissítéseket:  
        >   
        >  -   SMS_G_System_CollectedFile  
        > -   SMS_G_System_LastSoftwareScan  
        > -   SMS_G_System_AppClientState  
        > -   SMS_G_System_DCMDeploymentState  
        > -   SMS_G_System_DCMDeploymentErrorAssetDetails  
        > -   SMS_G_System_DCMDeploymentCompliantAssetDetails  
        > -   SMS_G_System_DCMDeploymentNonCompliantAssetDetails  
        > -   SMS_G_User_DCMDeploymentCompliantAssetDetails (csak felhasználók gyűjteményei esetén)  
        > -   SMS_G_User_DCMDeploymentNonCompliantAssetDetails (csak felhasználók gyűjteményei esetén)  
        > -   SMS_G_System_SoftwareUsageData  
        > -   SMS_G_System_CI_ComplianceState  
        > -   SMS_G_System_EndpointProtectionStatus  
        > -   SMS_GH_System_ *  
        > -   SMS_GEH_System_ *  

    -   **A gyűjteményhez teljes frissítést ütemeznie** – a gyűjtemény tagsága rendszeres teljes értékelésének ütemezéséhez.  

6.  Fejezze be a varázslót. Az új gyűjtemény az **Eszközök és megfelelőség** munkaterület **Felhasználógyűjtemények** csomópontjában jelenik meg.  

> [!NOTE]  
>  Frissítse vagy töltse be újra a Configuration Manager konzolon a gyűjtemény tagjainak megjelenítéséhez. A tagok mindazonáltal csak az első ütemezett frissítés után jelennek meg a gyűjteményben, illetve ha manuálisan végrehajtja a **Tagság frissítése** műveletet a gyűjteményhez. A gyűjtemény frissítése néhány percig is eltarthat.  

##  <a name="BKMK_3"></a> Gyűjtemény importálása  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **Felhasználógyűjtemények** vagy **Eszközgyűjtemények**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **gyűjtemények importálása**.  

4.  Az a **általános** oldalán a **gyűjtemények importálása varázsló**, válassza a **következő**.  

5.  Az a **MOF-fájl neve** lapon, válassza ki **Tallózás** majd keresse meg az importálni kívánt gyűjteményadatokat tartalmazó MOF-fájlt.  

    > [!NOTE]  
    >  A fájl, amelyeket szeretne importálni kell exportálták megegyezik a Configuration Manager azonos verzióját futtató helyről. További információ a gyűjtemények exportálásáról: [a System Center Configuration Manager gyűjtemények kezelése](../../../../core/clients/manage/collections/manage-collections.md).  

6.  Fejezze be a varázslót a gyűjtemény importálásához Az új gyűjtemény az **Eszközök és megfelelőség** munkaterület **Felhasználógyűjtemények** vagy **Eszközgyűjtemények** csomópontjában jelenik meg. Frissítse vagy töltse be újra a Configuration Manager konzolon az újonnan importált gyűjtemény tagjainak megjelenítéséhez.  

