---
title: "Összetevők helyet a Configuration Manager |} Microsoft Docs"
description: "Megtudhatja, hogyan módosíthatja a helyrendszerszerepkörök és a hely állapotjelentéseinek viselkedését helyösszetevők konfigurálásával."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5fccbbeb-0faa-4943-83c2-e67db62d392d
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 83550fbf0ef1f9adb0bb2c51a4f3c26a7500d352
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="site-components-for-system-center-configuration-manager"></a>A helyösszetevők a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Minden System Center Configuration Manager hely állíthat be a helyösszetevők módosítani a helyrendszer-szerepkörök és a hely állapotjelentéseinek viselkedését. Helyösszetevők konfigurálása egy helyhez, és egy alkalmazható helyrendszerszerepkört a helyen minden példányára vonatkoznak.  

## <a name="about-site-components"></a>Tudnivalók a helyösszetevőkről  
 A helyösszetevők beállításainak többsége magától értetődő, amikor a Configuration Manager konzolon. Azonban a következő adatok segítséget ismertetnek néhányat az összetettebb beállítás, vagy azokat magyarázó további tartalomhoz irányítja.  

### <a name="software-distribution"></a>Szoftverterjesztés  

-   **Tartalomterjesztési beállítások:**  Megadhatja a beállításokat, amelyek azt befolyásolják, hogyan továbbítsa a helykiszolgáló tartalmat a terjesztési pontokra. Az egyidejű terjesztési beállításokhoz használt értékek növelése estén a tartalomterjesztés nagyobb hálózati sávszélességet használhat.  

-   **Hálózatelérési fiók:**  A hálózatelérési fiók használatával kapcsolatos információkért lásd: [hálózatelérési fiók](../../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA).  

### <a name="software-update-point"></a>Szoftverfrissítési pont  

-   A szoftverfrissítési pont összetevő beállítási lehetőségeiről kapcsolatos információkért lásd: [egy szoftverfrissítési pont telepítése](../../../../sum/get-started/install-a-software-update-point.md).  

### <a name="management-point"></a>Felügyeleti pont  

-   **Felügyeleti pontok:** A hely állíthat be a felügyeleti pontok adatait közzététele az Active Directory tartományi szolgáltatásokban.  

     A Configuration Manager-ügyfelek felügyeleti pontokat használnak, keresse meg a szolgáltatások, és webhelyadatok megkereséséhez, például a határcsoporttagság és a PKI-tanúsítvány kijelölésére. Az ügyfelek a felügyeleti pontokat más felügyeleti pontok megkereséséhez a webhelyen, valamint a terjesztési pontokon, ahonnan letölthető a szoftver is használhatja. Felügyeleti pontok is segítenek az ügyfeleknek végzik a helyhozzárendelést, és hogy letöltsék az ügyfélházirendet, és töltse fel az ügyféladatokat.  

     Mivel a legbiztonságosabb mód arra, hogy az ügyfelek megtalálják a felügyeleti pontokat, az, ha közzétesszük őket az Active Directory Domain Servicesben, ezért általában az összes működő felügyeleti pontot ki szokták jelölni az Active Directory Domain Servicesben való közzétételre. Ezt a szolgáltatáskeresési módszert azonban igaz értékű a következő szükséges:

     - A séma ki van bővítve a Configuration Manager számára.
     - Van egy **rendszerkezelési** tároló, ebben a tárolóban való közzétételéhez a helykiszolgáló megfelelő biztonsági engedélyeket.
     - A Configuration Manager-hely közzététele az Active Directory tartományi szolgáltatásokban be van állítva.
     - Az ügyfelek a helykiszolgáló erdőjével ugyanabban az Active Directory erdőben tartozik.  

     Ha az intraneten lévő felügyeleti pontok megkereséséhez nem használható Active Directory tartományi szolgáltatásokban, [DNS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_dns) közzétételi helyette.  

 Szolgáltatás helyével kapcsolatos általános információkért lásd: [ismertetése ügyfelek és a System Center Configuration Manager szolgáltatáskeresés](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

-   **A kiválasztott intranet felügyeleti pontok közzététele a DNS-ben:** Adja meg ezt a beállítást, ha az intraneten lévő felügyeleti pontok nem található az Active Directory tartományi szolgáltatásokból. Ehelyett használhatnak a DNS szolgáltatási erőforrásrekord (SRV RR) a felügyeleti pont megtalálásához a hozzájuk rendelt helyen.  

    A Configuration Manager intranetes felügyeleti pontok közzététele a DNS-ben, a következő feltételeknek kell teljesülniük:  

    -   A DNS-kiszolgálóknak 8.1.2-es BIND verziójával rendelkezik, vagy később.  

    -   A DNS-kiszolgálók be vannak állítva az automatikus frissítések, és támogatja a szolgáltatási erőforrásrekordok kezelését.  

    -   A felügyeleti pontok a Configuration Manager a megadott teljesen minősített tartománynevek (FQDN) kell rendelkezniük (A vagy AAA rekordokkal) a DNS-ben.  

    > [!WARNING]  
    >  Hogy az ügyfelek megtalálják a DNS-ben közzétett felügyeleti pontokat meg kell rendelni az ügyfeleket egy bizonyos helyhez (használata helyett automatikus helyhozzárendelés). Ezek az ügyfelek beállítása a Helykód használatára a felügyeleti pontjuk tartományutótagjával. További információkért lásd: [keresése felügyeleti pontok](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points) a [ügyfelek hozzárendelése a System Center Configuration Manager hely](/sccm/core/clients/deploy/assign-clients-to-a-site).  

     Ha a Configuration Manager ügyfelek nem használhatják az Active Directory tartományi szolgáltatások vagy DNS-az intraneten lévő felügyeleti pontok megkereséséhez, használnak [WINS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_wins). Az első felügyeleti pontot, hogy telepítve van a hely automatikusan bekerül a WINS SZOLGÁLTATÁSBA, amikor az intranetes HTTP-ügyfélkapcsolatok fogadására van beállítva.  

### <a name="status-reporting"></a>Állapotjelentés  

-   Ezeket a beállításokat közvetlenül beállítása, amely tartalmazza a helyek és ügyfelek állapotjelentéseinek részletességi szintje.  

### <a name="email-notification"></a>E-mail értesítések  

-   Adja meg a fiók és a levelezési kiszolgáló adatait ahhoz, hogy a riasztások értesítő e-mailek küldése a Configuration Manager.  

### <a name="collection-membership-evaluation"></a>Gyűjteménytagság értékelése  

-   Ezzel a feladattal beállíthatja, hogy milyen gyakran végezze el a rendszer a gyűjteménytagság növekményes értékelését. A növekményes kiértékelés a gyűjtemény tagságát csak az új vagy megváltozott erőforrásokkal frissíti.  

### <a name="edit-the-site-components-at-a-site"></a>Egy hely összetevőinek szerkesztése  

Az alábbi lépések segítségével a hely összetevőinek szerkesztése:

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Helykonfiguráció** > **helyek**, majd válassza ki a konfigurálandó helyösszetevőket tartalmazó helyet.  

2.  Az a **Home** lap a **beállítások** csoportjában kattintson a **Helyösszetevők**. Válassza ki a konfigurálni kívánt.  

##  <a name="BKMK_ServiceMgr"></a> A helyösszetevők kezelése a Configuration Manager Service Manager segítségével  
A Configuration Manager Service Manager segítségével szabályozhatja a Configuration Manager szolgáltatások és a Configuration Manager szolgáltatásának vagy működő szálának állapotának megtekintése (néven Configuration Manager-összetevők). A következő Configuration Manager-összetevőivel kapcsolatos megismerése:  

-   Összetevők bármely helyrendszeren is futtathatók.  

-   Összetevők kezelése ugyanúgy kezelheti az, hogy a Windows rendszerbeli szolgáltatásoké. Meg is indítása, leállítása, szüneteltetése, folytatásához, vagy lekérdezi a Configuration Manager összetevőjét.  

A Configuration Manager szolgáltatás fut, amikor szükség van rá (általában amikor egy konfigurációs fájl beíródik egy összetevő beérkező fájljai közé). Egy műveletben érintett összetevőt azonosítania kell, ha a Configuration Manager Service Manager segítségével különböző szolgáltatások és szálak kezelése céljából. Majd megtekintheti az ennek eredményeképp létrejövő változást a Configuration Manager működésében. Például egy Configuration Manager szolgáltatások leállíthatja, amíg egy bizonyos válasz meg nem szűnik. Így meghatározhatja, hogy melyik szolgáltatás okozza az adott viselkedést.  

> [!TIP]  
>  Az alábbi eljárás segítségével kezelheti a Configuration Manager összetevőinek működését.  

### <a name="use-the-configuration-manager-service-manager"></a>A Configuration Manager Service Manager használatára  

1.  Kattintson a Configuration Manager konzolon **figyelés** >  **rendszerállapot**, és kattintson a **összetevő-állapot**.  

2.  A a **Home** lap a **összetevő** csoportjában kattintson a **Start**. Válassza ki **Configuration Manager Service Manager**.  

3.  Amikor a Configuration Manager Service Manager megnyílik, kapcsolódjon a felügyelni kívánt helyhez.  

     Ha nem látható a felügyelni kívánt hely, kattintson a **Hely**, majd a **Kapcsolódás**lehetőségre, és írja be a megfelelő hely helykiszolgálójának nevét.  

4.  Bontsa ki a helyet, és lépjen az **Összetevők** vagy a **Kiszolgálók** részre attól függően, hogy hol találhatók a felügyelni kívánt összetevők.  

5.  A jobb oldali ablaktáblában jelöljön ki egy vagy több összetevőt. Végül a a **összetevő** menüben kattintson a **lekérdezés** a kijelölt elemek állapotának frissítéséhez.  

6.  Miután az összetevő állapota frissült, használja a négy műveletalapú lehetőségének egyikét az **összetevő** menü az összetevők működésének módosításához. Miután egy műveletet kér, le kell kérdezni az összetevőt az új állapot megjelenítéséhez.  

7.  Zárja be a Configuration Manager Service Manager alkalmazást, amikor befejezte az összetevők működési állapotának módosítását.  

