---
title: "Hardverleltár bővítése |} Microsoft Docs"
description: "Ismerje meg, hogy bővíteni a hardverleltárt a System Center Configuration Managerben módjai."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5bfab4f-c55e-4545-877c-5c8db8bc1891
caps.latest.revision: 10
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 10c1d11a5cf06f3587fb6066801c0eab802dcf9a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-extend-hardware-inventory-in-system-center-configuration-manager"></a>A hardverleltár bővítése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Hardverleltár használatával eszközadatokat olvas be a Windows rendszerű számítógépeken a Windows Management Instrumentation (WMI). WMI a Microsoft általi implementációja a webalapú Enterprise Management (WBEM), iparági szabvány vállalati felügyeleti adataihoz való hozzáférést. A korábbi verziókban a Configuration Manager a Hardverleltár a a helykiszolgáló sms_def.mof fájljának módosításával lehetett bővíteni. Ez a fájl tartalmazta azt a WMI-osztályokat, a Hardverleltár által olvasható. A fájl szerkesztésével lehetőség nyílt a meglévő osztályok engedélyezésére és letiltására, valamint a leltár új osztályokkal való bővítésére.  

A Configuration.mof fájlt kell hardverleltárába az ügyfélen adatosztályok azonosítására szolgál, és nem tér el a Configuration Manager 2012. Adatosztályok létrehozásával leltár készíthető az ügyfélrendszerek meglévő vagy egyéni WMI-tárházainak adatosztályairól és beállításkulcsairól.  

 A Configuration.mof fájl ezenkívül azokat a WMI-szolgáltatókat is definiálja és regisztrálja, amelyek a hardverleltár során hozzáférnek az eszközadatokhoz. A szolgáltatók regisztrálása a használni kívánt szolgáltató típusa mellett az adott szolgáltató által támogatott osztályokat is definiálja.  

 Ha a Configuration Manager-ügyfelek házirendre vonatkozó kérelmet, például a normál ügyfélházirend lekérdezési időköze során a Configuration.MOF fájlt csatolva van a házirend törzséhez. Az ügyfelek ezt követően letöltik a fájlt, majd lefordítják azt. Ha adatosztályokat vesz fel a Configuration.mof fájlba, illetve adatosztályokat módosít vagy töröl a fájlban, az ügyfelek automatikusan lefordítják a leltárhoz kapcsolódó adatosztályokat érintő változtatásokat. Semmilyen további műveletet nem szükséges új vagy módosult adatosztályainak leltározásához a Configuration Manager-ügyfelek. Ez a fájl a **<CM telepítési helye\>\Inboxes\clifiles.src\hinv\\** mappában található az elsődleges hely kiszolgálóin.  

 A Configuration Managerben, akkor már nem az sms_def.mof fájl módosítása a Configuration Manager 2007. Ehelyett WMI-osztályokat lehet engedélyezni és letiltani, valamint a hardverleltárba összegyűjtendő új osztályokat lehet felvenni az ügyfélbeállítások használatával. A Configuration Manager bővíteni a hardverleltárt a következő metódusokat biztosít.  

> [!NOTE]  
>  Ha a Configuration.mof fájl egyéni leltárosztályok felvétele céljából manuálisan módosította, ezeket a módosításokat felülírja 1602-es verzióra való frissítéskor. Egyéni osztályok továbbra is használatára, akkor a frissítés után, hozzá kell adnia ezeket a Configuration.mof fájl "Added extensions" szakasza az 1602-es történő frissítése után.  
> Azonban ne módosítson semmit, ez a szakasz fenti, ezek a szakaszok módosításra vannak fenntartva a Configuration Manager által. A saját Configuration.mof fájl biztonsági másolata itt található:  
> **<CM telepítési könyvtára\>\data\hinvarchive\\\**.  

|Módszer|További információ|  
|------------|----------------------|  
|Meglévő leltárosztályok engedélyezése vagy letiltása|Engedélyezze vagy tiltsa le az alapértelmezett leltárosztályokat, vagy egyéni ügyfélbeállítások létrehozásával, amelyek lehetővé teszik a különböző hardverleltárosztályokat gyűjthet össze a megadott ügyfélgyűjteményekből. Tekintse meg a [engedélyezheti vagy tilthatja le a meglévő leltárosztályok](#BKMK_Enable) a jelen témakör eljárásában.|  
|Új leltárosztály felvétele|Egy új leltárosztályt felvenni egy másik eszköz WMI-névteréből. Tekintse meg a [egy új leltárosztály felvétele](#BKMK_Add) a jelen témakör eljárásában.|  
|Hardverleltárosztályok importálása és exportálása|Importálhat és exportálhat a Configuration Manager konzol leltárosztályokat tartalmazó Managed Object Format (MOF) fájlokat. Tekintse meg a [hardverleltárosztályok importálása](#BKMK_Import) és [hardverleltárosztályok exportálása](#BKMK_Export) ebben a témakörben szereplő eljárások.|  
|NOIDMIF-fájlok létrehozása|NOIDMIF-fájlok ügyféleszközök, amelyekről nem készíthető leltár a Configuration Manager által kapcsolatos információk összegyűjtéséhez használja. Ilyen adatok például az eszközszámokkal kapcsolatos azon információk, amelyek csak címkeként léteznek az adott eszközön. A NOIDMIF-fájlokra épülő leltárt automatikusan ahhoz az ügyféleszközhöz társítja a program, amelyről a leltáradatok származnak. Lásd: [NOIDMIF-fájlok létrehozása](#BKMK_NOIDMIF) ebben a témakörben.|  
|IDMIF-fájlok létrehozása|IDMIF-fájlok segítségével a szervezet, amely nem kapcsolódnak a Configuration Manager ügyfelek, például, kivetítőkről, fénymásolókról és hálózati nyomtatókról a adatokat gyűjteni. Lásd: [IDMIF-fájlok létrehozása](#BKMK_IDMIF) ebben a témakörben.|  

## <a name="procedures-to-extend-hardware-inventory"></a>Hardverleltár-bővítési eljárások  
Ezekkel az eljárásokkal konfigurálhatja a hardverleltár alapértelmezett ügyfélbeállításait, amelyek a hierarchia minden ügyfelére érvényesek lesznek. Ha azt szeretné, hogy ezeket a beállításokat csak néhány ügyfélen szeretné érvénybe léptetni, hozzon létre egy egyéni ügyféleszköz-beállítást, és rendelje hozzá egy gyűjteményhez, az adott ügyfelek. Lásd: [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../../core/clients/deploy/configure-client-settings.md).  

###  <a name="BKMK_Enable"></a> Meglévő leltárosztályok engedélyezése vagy letiltása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Az a **alapértelmezett ügyfélbeállítások** párbeszédpanelen válassza ki **Hardverleltár**.  

6.  Válassza az **Eszközbeállítások** lista **Osztályok beállítása**elemét.  

7.  A **Hardverleltárosztályok** párbeszédpanel jelölőnégyzeteivel válassza ki, hogy mely osztályokat és osztálytulajdonságokat szeretné felvenni a hardverleltárba. Az osztályok kibontásával a bennük lévő egyes tulajdonságokat is kiválaszthatja. A **Leltárosztályok keresése** mezővel rákereshet az egyes osztályokra.  

    > [!IMPORTANT]  
    >  A Configuration Manager hardverleltárának új osztályokkal ad hozzá, amikor a rendszer gyűjti, majd a helykiszolgálóra elküldött leltárfájl mérete növeli. Ez hátrányosan befolyásolhatja a hálózat és a Configuration Manager-hely teljesítményét. Csak azokat a leltárosztályokat engedélyezze, amelyeket össze kíván gyűjteni.  


###  <a name="BKMK_Add"></a> Új leltározási osztály hozzáadása  

Leltárosztályok csak a hierarchia legfelső szintű kiszolgálójáról és az alapértelmezett ügyfélbeállítások módosításával vehetők fel. Egyéni eszközbeállítások létrehozásakor ez a lehetőség nem választható.

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Az a **alapértelmezett ügyfélbeállítások** párbeszédpanelen válassza ki **Hardverleltár**.  

6.  Az a **eszközbeállítások** menüben válassza ki **osztályok beállítása**.  

7.  Az a **Hardverleltárosztályok** párbeszédpanelen válassza ki **Hozzáadás**.  

8.  A **Hardverleltárosztály hozzáadása** párbeszédpanelen kattintson a **Csatlakozás**gombra.  

9. A **Windows Management Instrumentation (WMI) csatlakozás** párbeszédpanelen adja meg annak a számítógépnek a nevét, amelyről szeretné beolvasni a WMI-osztályokat, valamint a beolvasáshoz használandó WMI-névteret. Ha a megadott WMI-névtér összes osztályát szeretné beolvasni, kattintson a **Rekurzív**elemre. Amennyiben nem helyi géphez csatlakozik, írja be egy olyan fiók hitelesítő adatait, amelynek van hozzáférése a távoli gép WMI-moduljához.  

10. Válasszon **csatlakozás**.  

11. Az a **Hardverleltárosztály hozzáadása** párbeszédpanel a **Leltárosztályok** listára, válassza ki, amelyet a Configuration Manager hardverleltárhoz adandó WMI-osztályokat.  

12. Ha módosítani szeretné a kiválasztott WMI-osztály adatait, válassza a **szerkesztése**, majd a a **Osztályminősítők** párbeszédpanelen adja meg a következő információkat:  

    -   **Megjelenített név** -ez fog megjelenni az erőforrás-kezelőben.  

    -   **Tulajdonságok** -adja meg az egységeket, mely minden tulajdonságban a WMI-osztály jelenik meg.  

     A tulajdonságok kulcstulajdonságként is megjelölhetők, így az osztály minden példánya egyedileg azonosítható. Ha nem definiál kulcsot az osztályhoz, és az ügyfél több osztálypéldányról küld jelentést, csak az a példány kerül be az adatbázisba, amelyet legutóbb észlelt a program.  

     Ha végzett a tulajdonságok konfigurálásával, kattintson a **OK** bezárásához a **Osztályminősítők** párbeszédpanelen, a másik párbeszédpanelt. 


###  <a name="BKMK_Import"></a> Hardverleltárosztályok importálása  

Leltárosztályok importálására csak az alapértelmezett ügyfélbeállítások módosításakor van lehetőség. Egyéni ügyfélbeállítások használatával ugyanakkor sémamódosítás nélküli információkat lehet importálni. Ilyen például egy meglévő osztály tulajdonságához tartozó **Igaz** érték **Hamis**értékre változtatása.  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >  **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Az a **alapértelmezett ügyfélbeállítások** párbeszédpanelen válassza ki **Hardverleltár**.  

6.  Az a **eszközbeállítások** menüben válassza ki **osztályok beállítása**.  

7.  Az a **Hardverleltárosztályok** párbeszédpanelen válassza ki **importálási**.  

8.  Az a **importálása** párbeszédpanelen jelölje ki a Managed Object Format (MOF) formátumú fájlt, amelyet szeretne importálni, és válassza a **OK**. Tekintse át az elemeket importálja, és kattintson a **importálási**.  

###  <a name="BKMK_Export"></a> Hardverleltárosztályok exportálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Az a **alapértelmezett ügyfélbeállítások** párbeszédpanelen válassza ki **Hardverleltár**.  

6.  Az a **eszközbeállítások** menüben válassza ki **osztályok beállítása**.  

7.  Az a **Hardverleltárosztályok** párbeszédpanelen válassza ki **exportálása**.  

    > [!NOTE]  
    >  Osztályok exportálásakor az összes kijelölt osztály exportálódik.  

8.  Az a **exportálása** párbeszédpanelen adja meg a Managed Object Format (MOF) fájlt, amelyet szeretne exportálni az osztályokat, és válassza **mentése**.  

## <a name="how-to-use-management-information-files-mif-files-to-extend-hardware-inventory"></a>Hardverleltár bővítése MIF-fájlokkal  
 Management Information Format (MIF) fájlok használatával bővíthetők a Configuration Manager által ügyfelekről gyűjtött Hardverleltár-információk. Hardverleltár közben a MIF-fájlokban tárolt információk bekerülnek az ügyfél leltárjelentésébe és a helyadatbázisba, ahol ugyanúgy használhatók, mint az ügyfél alapértelmezett leltáradatai. A MIF-fájlok kétfélék lehetnek: NOIDMIF és IDMIF típusúak.

> [!IMPORTANT]  
>  Mielőtt adatokat vehetne fel a MIF-fájlok a Configuration Manager adatbázisába, létre kell hoznia vagy importálása a hozzájuk tartozó osztályinformációkat. További információért lásd a jelen témakör [Új hardverleltárosztály hozzáadása](#BKMK_Add) és a [Hardverleltárosztályok importálása](#BKMK_Import) című szakaszait.  

###  <a name="BKMK_NOIDMIF"></a> NOIDMIF-fájlok létrehozása  
 NOIDMIF-fájlok, amelyek normál esetben nem kell összegyűjteni Configuration Manager ügyfél Hardverleltár-adatokat hozzáadni használható, és egy adott ügyféleszközhöz társítva. Sok cég például minden számítógépen, a szervezet eszközszámot tartalmazó címkével, és majd katalógus ezeket manuálisan. NOIDMIF-fájl létrehozásakor ezek az információk lehet hozzáadni a Configuration Manager-adatbázisba, és lekérdezések és jelentésére használható. NOIDMIF-fájlok létrehozásával kapcsolatos további információkért lásd: a Configuration Manager SDK dokumentációját.  

> [!IMPORTANT]  
>  NOIDMIF-fájl létrehozásakor az ANSI kódolással kell menteni. Az UTF-8 kódolású NOIDMIF-fájlokat a Configuration Manager nem tudja olvasni.  

 NOIDMIF-fájl létrehozása után mentenie azt a *% Windir %***\System32\CCM\Inventory\Noidmifs** mappájába. A Configuration Manager információkat gyűjt az ebben a mappában tárolt NODMIF-fájlokból a következő ütemezett hardverleltárciklus során.  

###  <a name="BKMK_IDMIF"></a> IDMIF-fájlok létrehozása  
 IDMIF-fájlok segítségével adja hozzá az adatokat, amelyek nem normál módon készíthető leltár a Configuration Manager által, és nincs társítva egy adott ügyféleszközhöz, a Configuration Manager adatbázisába. Ezzel segítségével például kivetítőkről, DVD-lejátszókról, fénymásolókról vagy egyéb eszközökről, a Configuration Manager-ügyfél nem tartalmazó adatokat gyűjteni. IDMIF-fájlok létrehozásával kapcsolatos további információkért lásd: a Configuration Manager SDK dokumentációját.  

 Miután létrehozott egy IDMIF-fájlokat tárolja a a *% Windir %***\System32\CCM\Inventory\Idmifs** mappa az ügyfélszámítógépeken. A Configuration Manager információkat gyűjt az ebben a fájlban a következő ütemezett hardverleltárciklus során. Új osztályok felvételével vagy importálásával osztályokat kell deklarálnia az IDMIF-fájlokban tárolt adatokhoz.  

> [!NOTE]
> A MIF-fájlok nagy mennyiségű adatot tartalmazhatnak, így az adatok gyűjtése negatív hatással lehet a hely teljesítményére. MIF-gyűjtését csak szükség esetén engedélyezze és konfigurálja a beállítást **maximális egyedi MIF-fájl mérete (KB)** a a Hardverleltár-beállításokat. További információkért lásd: [a System Center Configuration Manager hardverleltárának bemutatása](introduction-to-hardware-inventory.md).

