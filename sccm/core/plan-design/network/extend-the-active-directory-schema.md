---
title: "A közzététel és az Active Directory-séma |} Microsoft Docs"
description: "A System Center Configuration Manager központi telepítését és konfigurálását ügyfelek folyamat egyszerűsítése Active Directory-séma kiterjesztése."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bc15ee7e-4d0a-4463-ae2c-f72d8d45d65d
caps.latest.revision: 17
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 88649111ea3a38c027efb4952211546afd0bf27e
ms.openlocfilehash: 58beef440db8e019a06ce7c4c8eaabc8e85ce954
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-active-directory-for-site-publishing"></a>Hely közzététele az Active Directory előkészítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ha a System Center Configuration Manager kiterjeszti az Active Directory-sémát, akkor új struktúrákat vezet közzétételére egy biztonságos helyre, ahol az ügyfelek által könnyen elérhető, a Configuration Manager-helyek által használt Active Directory.  

Célszerű a helyi ügyfelek kezelésekor kiterjesztett Active Directory-sémát az bővített Configuration Managerben. Kiterjesztett séma egyszerűsítheti a központi telepítését, és az ügyfelek beállításával. Kiterjesztett séma azt is lehetővé teszi, hogy az ügyfelek hatékonyan keressék meg az erőforrásokat, például a tartalomkiszolgálókat és a további szolgáltatások, a másik Configuration Manager helyrendszer-szerepkörök biztosító.  

-   Ha még nem ismeri a milyen kiterjesztett séma biztosít a Configuration Manager telepítési, áttekintheti az [sémakiterjesztések a System Center Configuration Manager](../../../core/plan-design/network/schema-extensions.md) annak érdekében, hogy ehhez a döntéshez.  

-   Ha nem használ kiterjesztett sémát, más módszerrel, például a DNS és WINS-szolgáltatások és a helyrendszer-kiszolgálók kereséséhez állíthat be. A szolgáltatások megkeresésének ezen módjaihoz további beállítások szükségesek, és nem ezek az előnyben részesített szolgáltatáskeresési módszerek az ügyfelek számára. További tudnivalókért olvassa el a [ismertetése ügyfelek és a System Center Configuration Manager szolgáltatáskeresés](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md),  

-   Ha az Active Directory-séma lett kiterjesztve, a Configuration Manager 2007 vagy System Center 2012 Configuration Manager, majd, nem kell további teendője. A sémakiterjesztések nem változnak, és már lesz érvényben.  

A séma kiterjesztése egyszeri művelet bármely erdőben. És használhatja a kiterjesztett Active Directory-séma meghosszabbításához kövesse az alábbi lépéseket:  

## <a name="step-1-extend-the-schema"></a>1. lépés Sémakiterjesztés  
A séma kibővítése a Configuration Manager:  

-   Egy fiókot használjon, amely a Sémagazdák biztonsági csoport tagja.  

-   Jelentkeznie a séma-főkiszolgáló tartományvezérlőbe.  

-   Futtassa a **Extadsch.exe** eszközt, vagy használja az LDIFDE parancssori segédprogramot a **ConfigMgr_ad_schema.ldf** fájlt. Az eszköz és a fájl is a **SMSSETUP\BIN\X64** a Configuration Manager telepítési adathordozójáról mappájába.  

#### <a name="option-a-use-extadschexe"></a>"A" lehetőség Extadsch.exe használatára  

1.  Futtassa az **extadsch.exe** fájlt az új osztályok és attribútumok az Active Directory-sémához való hozzáadásához.  

    > [!TIP]  
    >  Az eszközt parancssorból futtassa, hogy közben megtekinthesse a visszajelzéseket.  

2.  Győződjön meg arról, hogy a séma kiterjesztése a rendszermeghajtó gyökérmappájában található extadsch.log megtekintésével sikeres volt.  

#### <a name="option-b-use-the-ldif-file"></a>"B" lehetőség Az LDIF fájl használata  

1.  Szerkessze a **ConfigMgr_ad_schema.ldf** megadhatók a legfelső szintű Active Directory-tartomány, a kiterjeszteni kívánt fájlt:  

    -   Cserélje le a szöveget az összes példányát **DC = x**, a fájl a kiterjeszteni kívánt tartomány teljes neve.  

    -   Például a kiterjeszteni kívánt tartomány teljes neve widgets.microsoft.com neve, ha összes előfordulását módosítsa DC = x a fájlban **DC = widgets, DC = microsoft, DC = com**.  

2.  Használja az LDIFDE parancssori segédprogramot tartalmának importálása a **ConfigMgr_ad_schema.ldf** fájl az Active Directory tartományi szolgáltatásokban:  

    -   Például a következő parancssort Active Directory tartományi szolgáltatások importálja a sémakiterjesztéseket, bekapcsolja a részletes naplózást, és létrehoz egy naplófájlt az importálási folyamat során: **ldifde – i – f ConfigMgr_ad_schema.ldf – v – j &lt;naplófájl tárolási helye\>**.  

3.  Győződjön meg arról, hogy sikeres volt-e a séma kiterjesztése, tekintse át az előző lépésben használt parancssorral létrehozott naplófájlt.  

## <a name="step-2--create-the-system-management-container-and-grant-sites-permissions-to-the-container"></a>2. lépés  A rendszerkezelési tároló létrehozása és helyengedélyek megadása a tárolónak  
 A séma kiterjesztése után létre kell hoznia egy tárolót **rendszerkezelési** az Active Directory tartományi szolgáltatások (AD DS):  

-   Hoz létre a tárolót egyszer minden olyan elsődleges vagy másodlagos helyhez, amely adatokat fog közzétenni az Active Directory tartományban.  

-   Minden egyes tároló esetén engedélyt kell a számítógépfiók minden elsődleges és másodlagos helykiszolgáló, amely adatokat fog közzétenni az erre a tartományra. Minden felhasználói fiókhoz kell **teljes hozzáférés** a tárolóhoz, speciális engedéllyel rendelkező **alkalmazás**, annál **Ez az objektum és a gyermekobjektumok**.  

#### <a name="to-add-the-container"></a>A tároló felvétele  

1.  Olyan fiókot használjon, amely **Az összes gyermekobjektum létrehozása** engedéllyel rendelkezik a **rendszertárolón** az Active Directory tartományi szolgáltatásaiban.  

2.  Futtatás **ADSI-szerkesztő** (adsiedit.msc), és csatlakozzon a helykiszolgáló tartományához.  

3.  Hozza létre a tárolót:  

    -   Bontsa ki a **tartomány** &lt;számítógép teljesen minősített tartományneve\>, bontsa ki a &lt;megkülönböztető név\>, kattintson a jobb gombbal **CN = rendszer**, válassza ki **új**, és válassza a **objektum**.  

    -   Az a **objektum létrehozása** párbeszédpanelen válassza ki **tároló**, és válassza a **következő**.  

    -   Az a **érték** adja meg a **rendszerkezelési**, és válassza a **következő**.  

4.  Engedélyek kiosztása:  

    > [!NOTE]  
    >  Igény szerint az engedélyek tárolóba való felvételéhez más eszközt is használhat, például az Active Directory – felhasználók és számítógépek felügyeleti eszközt (dsa.msc)  

    -   Kattintson a jobb gombbal **CN = rendszerkezelés**, és válassza a **tulajdonságok**.  

    -   Válassza ki a **biztonsági** lapra, majd **Hozzáadás**, majd adja hozzá a helykiszolgáló számítógépfiókjának a a **teljes hozzáférés** engedéllyel.  

    -   Válasszon **speciális**, válassza ki a helykiszolgáló számítógépfiókját, és válassza a **szerkesztése**.  

    -   Az a **alkalmazás** menüben válassza ki **Ez az objektum és a gyermekobjektumok**.  

5.  Válasszon **OK** gombra a konzol bezárásához és a konfiguráció mentéséhez.  

## <a name="step-3-set-up-sites-to-publish-to-active-directory-domain-services"></a>3. lépés Active Directory tartományi szolgáltatásokban való közzétételére helyek beállítása  
 A tároló be van állítva, engedélyekkel és a Configuration Manager elsődleges hely telepítését, miután állíthat be, hogy a hely adatok közzétételére az Active Directory.  

 A közzététel kapcsolatban bővebben lásd: [helyadatok közzététele a System Center Configuration Manager](../../../core/servers/deploy/configure/publish-site-data.md).  

