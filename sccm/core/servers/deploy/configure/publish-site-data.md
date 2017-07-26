---
title: "Helyadatok közzététele |} Microsoft Docs"
description: "Útmutató a Configuration Manager-helyek közzétételére az Active Directory tartományi szolgáltatásokban."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 17cf034f-eaff-43ce-bc8e-917213c1db74
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e7629fdf7fdf615fa27894158c3d101432c95a04
ms.openlocfilehash: bcfb002c503485f03ba27d7346acb61d0d3c6087
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="publish-site-data-for-system-center-configuration-manager"></a>A System Center Configuration Manager helyadatok közzététele

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután az Active Directory-séma kiterjesztése a System Center Configuration Manager, Configuration Manager-helyek közzéteheti az Active Directory tartományi szolgáltatásokban (AD DS). Ez lehetővé teszi, hogy az Active Directory számítógépek biztonságosan lekérhessék a helyinformációkat egy megbízható forrásból. Habár a helyinformációk közzététele az Active Directory tartományi szolgáltatások nem szükséges alapvető Configuration Manager funkcióihoz tartozó, csökkentheti ehhez adminisztratív terhelést.  

-   **Ha a egy webhely van-e konfigurálva az Active Directory tartományi Szolgáltatásokban való közzétételére**, Configuration Manager-ügyfelek automatikusan az Active Directory-közzétételen keresztül; felügyeleti pontokat keresnek. Globáliskatalógus-kiszolgáló LDAP-lekérdezést használják.  

-   **Ha a hely nem tesz közzé adatokat az AD DS-ben**, az ügyfeleknek más módszerrel kell megkeresniük az alapértelmezett felügyeleti pontot.  

Hogyan ügyfelek felügyeleti pont megtalálásához kapcsolatos információkért lásd: [ismertetése ügyfelek és a System Center Configuration Manager szolgáltatáskeresés](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

## <a name="configure-sites-to-publish-to-ad-ds"></a>Helyek konfigurálása az AD DS-be történő közzétételre  
 Az általános lépések a következők:  

-   Meg kell [az Active Directory-séma kiterjesztése a System Center Configuration Manager](../../../../core/plan-design/network/extend-the-active-directory-schema.md) minden olyan erdőben, ahol helyadatok lesznek közzétéve. Arról is győződjön meg a **rendszerkezelési** tároló megtalálható.  

-   Biztosítania kell az elsődleges helyeken, amelyek adatokat fog közzétenni számítógépfiókjának **teljes hozzáférés** számára a **rendszerkezelési** tárolóhoz és annak minden gyermekobjektumához.  

### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-active-directory-forest"></a>A helyadatok közzétételéhez az Active Directory-erdőhöz Configuration Manager-hely engedélyezése

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **Helykonfiguráció**, és kattintson a **helyek**. Válassza ki a helyet, amely rendelkezik közzéteszi a helyadatokat. Végül a a **Home** lap a **tulajdonságok** csoportjában kattintson a **tulajdonságok**.  

3.  Az a **közzétételi** lapon a hely tulajdonságai, válassza ki, amelyhez ez a hely közzéteszi az adatokat az erdők.  

4.  A konfiguráció mentéséhez kattintson az **OK** gombra.  

### <a name="to-set-up-active-directory-forests-for-publishing"></a>Az Active Directory-erdők közzétételhez beállítása  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen kattintson az **Active Directory-erdők**elemre. Ha korábban már futott az Active Directory-erdőfelderítés, az eredmények ablaktáblájában láthatók a felderített erdők. A helyi erdők és a megbízható erdők felderíthetők az Active Directory-erdőfelderítés futtatásával. Csak nem megbízható erdőket kell kézzel felvenni.  

    -   Korábban felderített erdő beállításához jelölje ki az erdőt az eredmények ablaktáblán. Végül a a **Home** lap a **tulajdonságok** csoportjában kattintson a **tulajdonságok** kattintva jelenítse meg az erdő tulajdonságait. Folytassa a 3. lépéssel.  

    -   Beállítása, amely nem szerepel, az új erdő a **Home** lap a **létrehozása** csoportjában kattintson **erdő hozzáadása** megnyitásához a **erdők hozzáadása** párbeszédpanel. Folytassa a 3. lépéssel.  

3.  Az a **általános** lapon adja meg a felderítése, és adja meg a kívánt erdő beállításait a **Active Directory-erdő fiókjának**.  

    > [!NOTE]  
    >  Az Active Directory-erdőfelderítés globális fiókot igényel a nem megbízható erdők felderítéséhez és az ezekben történő közzétételhez. Ha nem a helykiszolgáló számítógép-fiókját használja, csak globális fiókot választhat.  

4.  Ha azt tervezi, hogy a helyeknek engedélyezi az adatok közzétételét ebben az erdőben, a **Közzététel** lapon adja meg az erdőbeli közzététel beállításait.  

    > [!NOTE]  
    >  Ha engedélyezte a helyeket szeretne közzétenni az erdő, ki kell terjesztenie az Active Directory-sémáját a Configuration Manager számára. Az Active Directory-erdő fiókjának teljes hozzáférés engedéllyel a rendszer tárolóhoz kell rendelkeznie az adott erdőben.  

5.  Amikor befejezte az adott erdő Active Directory-erdőfelderítéssel való használatának konfigurálását, a konfiguráció mentéséhez kattintson az **OK** gombra.  

