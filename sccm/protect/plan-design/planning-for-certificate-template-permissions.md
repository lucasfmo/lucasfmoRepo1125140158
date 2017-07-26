---
title: "Tanúsítványsablonok engedélyeinek tervezése |} Microsoft Docs"
description: "További tudnivalók az, hogy konfigurálnia kell a System Center Configuration Manager által használt tanúsítványsablonok engedélyeinek tervezése."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: eab0e09d-b09e-4c14-ab14-c5f87472522e
caps.latest.revision: 5
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 832be8c9fda727804f57e83768cd8799db722c67
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-certificate-template-permissions-for-certificate-profiles-in-system-center-configuration-manager"></a>A System Center Configuration Managerben tanúsítványprofilok tanúsítványsablonok engedélyeinek tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A következő információk segítségével tervezheti meg a System Center Configuration Manager használó tanúsítványprofilok központi telepítésekor a tanúsítványsablonok engedélyeinek tervezésében.  

## <a name="default-security-permissions-and-considerations"></a>Alapértelmezett biztonsági engedélyek és megfontolások  
 A System Center Configuration Manager segítségével a felhasználók és eszközök tanúsítványt igényelni a tanúsítványsablonok szükséges alapértelmezett biztonsági engedélyek a következők:  

-   Olvasás és Beléptetés ahhoz a fiókhoz, amelyiket a Hálózati eszközök tanúsítványigénylési szolgáltatásának alkalmazáskészlete használ  

-   Olvassa el a fiókhoz, amelyen fut a System Center Configuration Manager konzol  

 Ezek a biztonsági engedélyek kapcsolatos további információkért lásd: [tanúsítványinfrastruktúra konfigurálása](../deploy-use/certificate-infrastructure.md).  

 Ha ezt az alapértelmezett konfigurálást használja, a felhasználók és az eszközök nem tudnak közvetlenül lekérni tanúsítványokat a tanúsítványsablonokból, hanem minden lekérést a Hálózati eszközök tanúsítványigénylési szolgáltatásával kell kezdeményezni. Ez fontos korlátozás, mivel ezeket a tanúsítványsablonokat a tanúsítvány Tárgy tulajdonságában **A kérelem fogja tartalmazni** használatával kell konfigurálni, ami azt jelenti, hogy fennáll a megszemélyesítés kockázata, ha egy csaló felhasználó vagy sérült integritású eszköz kér le tanúsítványt. A alapértelmezett konfigurálásban az ilyen lekérést a Hálózati eszközök tanúsítványigénylési szolgáltatásának kell kezdeményezni. A megszemélyesítés kockázata azonban továbbra is fennáll, ha a Hálózati eszközök tanúsítványigénylési szolgáltatását futtató szolgáltatás sérült integritású. A kockázat elkerülését elősegítendő járjon el a Hálózati eszközök tanúsítványigénylési szolgáltatása, valamint a szerepkör futtatását végző számítógép biztonságának megfelelő bevált gyakorlat szerint.  

 Ha az alapértelmezett biztonsági engedélyek nem felelnek meg az üzleti követelményeinek, akkor lehetősége, hogy konfigurálja a tanúsítványsablonok biztonsági engedélyeit: Hozzáadhat olvasási és beléptetési engedélyek egyes felhasználókhoz és számítógépekhez.  

## <a name="adding-read-and-enroll-permissions-for-users-and-computers"></a>Olvasási és beléptetési engedélyek hozzárendelése egyes felhasználókhoz és számítógépekhez  
 Hozzáadás olvasási és beléptetési engedélyek egyes felhasználókhoz és számítógépekhez való hozzárendelése megfelelő lehet, ha egy külön csapat felügyeli a hitelesítésszolgáltató (CA) infrastruktúra csapatát, és külön csapat azt akarja, hogy felhasználók van érvényes Active Directory tartományi szolgáltatások fiókja, mielőtt elküldené a tanúsítványprofilt a felhasználó tanúsítványának lekérésére ellenőrzése a System Center Configuration Manager. Az ilyen konfiguráláshoz egy vagy több biztonsági csoportot kell az érintett felhasználókból összeállítani, és az olvasási és beléptetési engedélyeket a tanúsítványsablonokon ezeknek a csoportoknak kell megadni. Ebben a forgatókönyvben a hitelesítésszolgáltató rendszergazda felügyeli a biztonság ellenőrzését.  

 Az érintett számítógépi fiókokból hasonlóképpen összeállíthat egy vagy több olyan biztonsági csoportot, amelyeknek az olvasási és beléptetési engedélyeit a tanúsítványsablonokon adja meg. Ha olyan számítógépre telepít tanúsítványprofilt, amelyik egy tartomány tagja, az olvasási és beléptetési engedélyt a számítógép számítógépi fiókjának kell megadni. Ezek az engedélyek nem is szükséges, ha a számítógép nem egy tartományi memberâ "", ha például munkacsoportban működő számítógép vagy személyi mobilkészülék.  

 Bár ez a konfigurálás további biztonsági ellenőrzést jelent, bevált gyakorlatként nem ajánljuk. A hiba oka, hogy a megadott felhasználók, illetve eszköztulajdonosok a kérhetnek tanúsítványokat egymástól függetlenül a System Center Configuration Manager, és adjon meg értékeket a tanúsítvány tárgy, amelyik alkalmas lehet egy másik felhasználó vagy eszköz megszemélyesítésére.  

 Ezen kívül, ha olyan fiókokat ad meg, amelyek a tanúsítvány lekérésekor nem hitelesíthetők, a tanúsítványlekérés az alapértelmezés szerint sikertelen lesz. Például sikertelen lesz a tanúsítványlekérés, ha a Hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgáló olyan Active Directory erdőben van, amelyik nem megbízható azon erdő részére, amelyik a tanúsítványregisztrációs pont helyrendszer-kiszolgálóját tartalmazza. A tanúsítványregisztrációs pont konfigurálható, hogy a folytatást ne akadályozza, ha valamelyik fiók nem hitelesíthető, mivel nincs válasz a tartományvezérlőtől. Ez azonban biztonsági szempontból nem lehet bevált gyakorlat.  

 Tudjon róla, hogy ha a tanúsítványregisztrációs pont úgy lett konfigurálva, hogy ellenőrizze a fiók engedélyeit, és közben a tartományvezérlő is elérhető, és az elutasítja a hitelesítési kérelmet (például a fiók ki lett zárva vagy törölve lett), a tanúsítvány beléptetési kérelme sikertelen lesz.  

#### <a name="to-check-for-read-and-enroll-permissions-for-users-and-domain-member-computers"></a>Felhasználók és tartománytag számítógépek olvasási és beléptetési kérelmeinek ellenőrzése  

1.  A tanúsítványregisztrációs pontot üzemeltető helyrendszer-kiszolgáló hozza létre a következő DWORD-beállításkulcsot a 0 értékkel: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheck  

2.  Ha valamelyik fiók nem hitelesíthető, mivel nincs válasz a tartományvezérlőtől, és szeretné megkerülni az engedélyek ellenőrzését:  

    -   A tanúsítványregisztrációs pontot üzemeltető helyrendszer-kiszolgáló hozza létre a következő DWORD-beállításkulcsot 1 értékre: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheckOnlyIfAccountAccessDenied  

3.  A tanúsítványsablon tulajdonságainál a **Biztonság** lapon a kibocsátó hitelesítésszolgáltatóhoz adjon hozzá egy vagy több biztonsági csoportot, hogy olvasási és beléptetési engedélyt adhasson a felhasználók vagy eszközök fiókja részére.  

