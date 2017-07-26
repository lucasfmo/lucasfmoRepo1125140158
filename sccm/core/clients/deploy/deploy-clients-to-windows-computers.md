---
title: "Windows-ügyfelek központi telepítése |} Microsoft Docs"
description: "Ismerje meg az ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 341f0d0b-f907-44cf-9e10-e1b41fc15f82
caps.latest.revision: 13
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 83878b71b876c725920b228190000fc849a063db
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-clients-to-windows-computers-in-system-center-configuration-manager"></a>Ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Configuration Manager-ügyfelek telepítése előtt győződjön meg arról, hogy minden a [Előfeltételek](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md) érvényben vannak, és, hogy végrehajtotta az összes szükséges központi telepítés konfigurációja.   

##  <a name="BKMK_ClientPush"></a>Ügyfelek telepítése ügyfélleküldéssel  

Amikor ügyfélleküldéses telepítést konfigurál egy helyen, az ügyfél telepítése automatikusan zajlik a hely beállított határain belül felderített számítógépeken, ha a határok határcsoportként vannak konfigurálva. Emellett ugyanakkor az Ügyfélleküldéses telepítés varázslóval is kezdeményezhet ügyfélleküldéses telepítést egy adott gyűjteményre, vagy a gyűjtemény egy erőforrására vonatkozóan.  

Telepíti a Configuration Manager-ügyfelet is használhatja az Ügyfélleküldéses telepítés varázsló [lekérdezés](../../../core/servers/manage/queries-technical-reference.md) eredmények. A sikeres telepítés esetén a lekérdezés által visszaküldött elemek egyikének kell lennie az attribútum **ResourceID** osztályból **rendszererőforrás**.   

Ha a helykiszolgáló nem lépjen kapcsolatba az ügyfélszámítógépen vagy a telepítés megkezdéséhez automatikusan újra kísérletet tesz óránként legfeljebb 7 napig.  

Az ügyfél-telepítési folyamat könnyebb nyomon követéséhez a telepítés előtt állítson rendszerbe egy tartalék állapotkezelő pontot. Ügyfélleküldéses telepítéskor a rendszer automatikusan az ügyfelekhez társítja a környezetben telepített tartalék állapotkezelő pontot. Az ügyféltelepítés előrehaladásának nyomon követéséhez tekintse meg az ügyfelek központi telepítési és társítási jelentéseit. 

Ügyfelek naplófájljai részletesebb hibaelhárítási információt nyújtanak, és nincs szükség a tartalék állapotkezelő pont. A helykiszolgálón található CCM.log fájl például rögzít minden kapcsolódási problémát a helykiszolgáló és a számítógépek között, az ügyfélen található CCMSetup.log fájl pedig a telepítési folyamathoz kapcsolódó információkat rögzíti.  

> [!IMPORTANT]  
>  A sikeres ügyfélleküldéses telepítéshez először győződjön meg arról, hogy a telepítés valamennyi előfeltétele teljesül. Ezek a feltételek "A telepítési módszer függőségei" című [Windows rendszerű számítógépekre a System Center Configuration Manager-ügyfelek központi telepítéséhez szükséges előfeltételek](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md).  

### <a name="to-configure-the-site-to-automatically-use-client-push-for-discovered-computers"></a>A hely konfigurálása automatikus ügyfélleküldéses telepítésre a felderített számítógépeken

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **helyek**.  

3.  Válassza ki a helyet, amelyhez automatikus helyre kiterjedő ügyfélleküldés telepítését konfigurálni szeretné.  

4.  Az a **Home** lap a **beállítások** csoportjában válassza **ügyfél-telepítési beállítások** > **leküldéses ügyféltelepítés**.  

5.  Az a **általános** lapján a **Ügyfélleküldéses telepítés tulajdonságai** párbeszédablakban válassza **automatikus helyi szintű ügyfélleküldéses telepítés engedélyezése**. Jelölje ki azokat a rendszer, amelyhez a Configuration Manager rendszerekre küldje le az ügyfélszoftvert.  

6.  Válassza ki, hogy az ügyfél telepítéséhez a tartományvezérlőkön.  

7.  Az a **fiókok** lapján adjon meg egy vagy több fiókot, hogy a számítógép csatlakozáshoz használhat az ügyfélszoftver telepítéséhez a Configuration Manager. Kattintson a **létrehozása** ikonra, írja be a **felhasználónév** és **jelszó** (legfeljebb 38 karakteres), erősítse meg a jelszót, és kattintson **OK**. Meg kell adnia legalább egy leküldéses ügyféltelepítési fiókot, amelynek helyi rendszergazdai jogosultságokkal kell rendelkeznie minden olyan számítógépen, amelyre telepíteni kívánja az ügyfelet. Ha nem ad meg egy ügyfélleküldéses telepítési fiókot, a Configuration Manager próbálja használni a helyrendszer-számítógépfiókot, aminek következtében meghiúsul a tartományok közötti leküldéses.  

    
    > [!NOTE]  
    >  Ha másodlagos helyről szeretné igénybe venni az ügyfélleküldéses telepítési módszert, a fiókot az ügyfélleküldést kezdeményező másodlagos helyen kell megadni.  
    >   
    >  Az ügyfélleküldéses telepítési fiók kapcsolatos további információkért tekintse meg a következő eljárást: "az az Ügyfélleküldéses telepítés varázsló használata".  

8.  Fejezze be a **telepítési tulajdonságok** fülre.

     [Ügyfél-telepítési tulajdonságok](../../../core/clients/deploy/about-client-installation-properties.md) ezen a lapon megadott közzé az Active Directory tartományi szolgáltatásokban, ha a séma ki van bővítve a Configuration Manager számára, és olvassa el, ha a CCMSetup futását telepítési tulajdonságok nélkül Ügyféltelepítések.  

    > [!NOTE]  
    >  Ha engedélyezi az ügyfélleküldéses telepítés egy másodlagos helyen, győződjön meg arról, hogy az SMSSITECODE tulajdonság értéke a szülő elsődleges hely a Configuration Manager Helyadatbázis nevét. Ha az Active Directory-séma ki van bővítve a Configuration Manager számára, akkor is állíthatja ezt a megfelelő helyhozzárendelés automatikus azonosításához Auto.  

### <a name="to-use-the-client-push-installation-wizard"></a>Az Ügyfélleküldéses telepítés varázsló használata

1.  Kattintson a Configuration Manager konzol **felügyeleti** >  **Helykonfiguráció** > **helyek**.  

3.  Válassza ki a helyet, amelyhez automatikus helyre kiterjedő ügyfélleküldés telepítését konfigurálni szeretné.  

4.  Az a **Home** lapon > **beállítások** csoportjában válassza **ügyfél-telepítési beállítások** > **leküldéses ügyféltelepítés**.  

5.  Fejezze be a **telepítési tulajdonságok** fülre.  

     [Ügyfél-telepítési tulajdonságok](../../../core/clients/deploy/about-client-installation-properties.md) ezen a lapon megadott közzé az Active Directory tartományi szolgáltatásokban, ha a séma ki van bővítve a Configuration Manager számára, és olvassa el, ha a CCMSetup futását telepítési tulajdonságok nélkül Ügyféltelepítések.  

6.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség**.  

7.  Az **Eszközök és megfelelőség** munkaterületen válasszon egy vagy több számítógépet vagy egy számítógép-gyűjteményt.  

8.  A **Kezdőlapon** válasszon egyet az alábbi lehetőségek közül:  

    -   Ha azt szeretné, hogy az ügyfél egy vagy több számítógépre történő telepítéséhez a **eszköz** csoportjában válassza **ügyfél telepítése**.  

    -   Ha szeretné-e telepíteni az ügyfelet a gyűjtemény számítógépeinek, az a **gyűjtemény** csoportjában válassza **ügyfél telepítése**.  

9. Az a **előkészületek** oldalán a **ügyfél telepítése varázsló**, tekintse át az adatokat, és válassza a **következő**.  

10. Fejezze be a **telepítési beállítások** lap.  

11. Ellenőrizze a telepítési beállításokat, majd zárja be a varázslót.  

> [!NOTE]  
>  A varázslóval akkor is telepíthet ügyfeleket, ha a hely nincs konfigurálva ügyfélleküldéshez.  

##  <a name="BKMK_ClientSUP"></a>A Szoftvertelepítés-alapú ügyfelek telepítése  
 Szoftverfrissítés-alapú ügyféltelepítés tesz közzé, egy szoftverfrissítési az ügyfél a szoftverfrissítési ponton. Ez a módszer használata egy első telepítése vagy frissítése.  

 Ha a számítógép rendelkezik az ügyfél telepítve van, a Configuration Manager ellátja az ügyfelet az ügyfélházirendet, beleértve a szoftverfrissítések szoftverfrissítési pont kiszolgálójának nevével és portjával letölti a szoftverfrissítéseket a.   

> [!IMPORTANT]  
>  A szoftverfrissítés-alapú telepítéshez azonos WSUS-kiszolgálót kell használnia az ügyféltelepítéshez és a szoftverfrissítésekhez. A kiszolgálónak egy elsődleges hely aktív szoftverfrissítési pontjának kell lennie. További információkért lásd: [egy szoftverfrissítési pont telepítése](../../../sum/get-started/install-a-software-update-point.md).  

Ha a számítógép nem rendelkezik telepített Configuration Manager-ügyfél, kell konfigurálása és hozzárendelése egy házirend objektum (GPO) az Active Directory tartományi szolgáltatásokban adhatja meg a szoftverfrissítési pont kiszolgálónevének.  

Szoftverfrissítés-alapú ügyféltelepítés esetén nem használhat parancssori tulajdonságokat. Ha a Configuration Manager kibővítette az Active Directory-sémát, ügyfélszámítógépek a telepítéskor automatikusan lekérdezik a telepítési tulajdonságokat az Active Directory tartományi szolgáltatások telepítése.  

Ha nem bővítette ki az Active Directory-sémát, csoportházirenddel juttathatja el az ügyfél-telepítési tulajdonságokat a helyen lévő számítógépekre. Ezeket a beállításokat a rendszer automatikusan alkalmazza minden szoftverfrissítés-alapú ügyféltelepítésre. További információkért lásd: [Az ügyféltelepítés tulajdonságainak megadása (csoportházirenden és szoftverfrissítésen alapuló ügyféltelepítés)](#BKMK_Provision), illetve: [Ügyfélszoftverek helyhez rendelése a System Center Configuration Managerben](../../../core/clients/deploy/assign-clients-to-a-site.md).  

Használja a következő eljárásokat kell konfigurálni a szoftverfrissítés használata a Configuration Manager-ügyfél nélküli számítógépeket pont ügyféltelepítés és szoftverfrissítések frissíti, és az ügyfél közzététele a szoftverfrissítési szoftverfrissítési pont.  

> [!NOTE]  
>  Ha a számítógépek egy korábbi szoftvertelepítést követően újraindításra várnak, egy szoftverfrissítés-alapú ügyféltelepítés a számítógép újraindítását okozhatja.  

### <a name="configure-a-group-policy-object-in-active-directory-domain-services-to-specify-the-software-update-point-for-client-installation-and-software-updates"></a>Állítsa be a csoportházirend-objektum az Active Directory tartományi szolgáltatások adhatja meg a szoftverfrissítési pont az ügyfél telepítése és a szoftver frissítések:  

1.  A Csoportházirend-kezelő konzollal nyisson meg egy új vagy meglévő csoportházirend-objektumot.  

2.  A konzolon bontsa ki **számítógép konfigurációja**, bontsa ki a **felügyeleti sablonok**, bontsa ki a **Windows-összetevők**, és válassza a **Windows Update**.  

3.  Nyissa meg a beállítás tulajdonságait **adja meg az intraneten futó Microsoft frissítési szolgáltatás helye**, és válassza a **engedélyezve**.  

4.  A mezőbe **frissítések keresését végző intranetes frissítési szolgáltatás**, adja meg a nevét és a szoftverfrissítési pont kiszolgálójának portja:  

    -   Ha a Configuration Manager helyrendszer egy teljesen minősített tartománynevét (FQDN) használatára van konfigurálva, használja a teljes tartománynév formátumának.  

    -   Ha a Configuration Manager helyrendszer nem teljes tartománynév használatára van konfigurálva, rövid neve formátumának a használatára.  

    > [!NOTE]  
    >  A port számának megállapításához lásd: [WSUS a System Center Configuration Managerben használt portok beállításainak megállapítása](../../../sum/plan-design/plan-for-software-updates.md).  

     Például: **http://server1.contoso.com:8530**  

5.  A mezőbe **állítsa be a statisztikát tároló intranetkiszolgálót**, adja meg a statisztikát tároló intranetkiszolgálót nevét. Nincs a szoftverfrissítési pont kiszolgálójának azonos, és a formátum nem egyezik meg, hogy ugyanarra a kiszolgálóra kell.  

6.  Rendelje hozzá a csoportházirend-objektumot azokhoz a számítógépekhez, amelyen létre szeretné telepíteni az ügyfelet és szoftverfrissítéseket fogadni.  

### <a name="to-publish-the-configuration-manager-client-to-the-software-update-point"></a>A Configuration Manager-ügyfél közzététele a szoftverfrissítési ponton  

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **Helykonfiguráció** > **helyek**.  

3.  Válassza ki a helyet, amelyhez a szoftverfrissítés-alapú ügyféltelepítést konfigurálni szeretné.  

4.  Az a **Home** lap a **beállítások** csoportjában válassza **ügyfél-telepítési beállítások**, és válassza a **szoftverfrissítés-alapú ügyféltelepítés**.  

5.  Válassza ki **szoftverfrissítés-alapú ügyféltelepítés engedélyezése**.  

6.  Ha az ügyfélszoftver, a Configuration Manager helykiszolgálón újabb verziójú, mint, amely a szoftverfrissítési pont, frissítse a **újabb verziójú ügyfélcsomag észlelve** párbeszédpanel. Kattintson a **Igen** közzététele az alkalmazás legújabb verziójára.  

    > [!NOTE]  
    >  Ha az ügyfélszoftver nem volt korábban közzétett a szoftverfrissítési ponthoz, ez a mező üres lesz.  

A Configuration Manager-ügyfél a szoftverfrissítés nem frissül automatikusan, ha új verzió. Ha a hely frissítése során új ügyfélverziót telepít, meg kell ismételnie ezt az eljárást, és a 6. lépésben az **Igen** gombra kell kattintania.  

##  <a name="BKMK_ClientGP"></a>Ügyfelek telepítése a csoportházirenddel  
 Használhatja a csoportházirend az Active Directory tartományi szolgáltatásokban való közzétételére vagy hozzárendelésére a vállalati számítógépeken való telepítés Configuration Manager-ügyfél. Az ügyfél telepíti, a számítógép indításakor. A Csoportházirend használata esetén az ügyfél a Vezérlőpulton megjeleníti **programok telepítése és törlése** telepítése a felhasználó számára.  

 Csoportházirend-alapú telepítéshez használja az ügyfél Windows Installer-csomagját (CCMSetup.msi). Ez a fájl a mappában található  **&lt;ConfigMgr telepítési könyvtára\>\bin\i386** a Configuration Manager helykiszolgálón. A telepítés testreszabásához fájl tulajdonságait nem lehet hozzáadni.  

> [!IMPORTANT]  
>  Az ügyfél-telepítési fájlok eléréséhez rendszergazdai engedélyekkel kell rendelkeznie.  

-   Ha az Active Directory-séma ki van bővítve a Configuration Manager és **a hely közzététele az Active Directory tartományi szolgáltatások** kiválasztásakor a **speciális** lapján a **hely tulajdonságai** párbeszédpanelen ügyfélszámítógépek automatikusan keresni a telepítési tulajdonságokat az Active Directory tartományi szolgáltatások. További információk a közzétett telepítési tulajdonságokról: [Információ az Active Directory tartományi szolgáltatásokban közzétett ügyfélszoftver-telepítési tulajdonságokról a System Center Configuration Managerben](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

-   Ha az Active Directory-séma nem lett kibővítve, eljárással az ebben a témakörben a telepítési tulajdonságok tárolásához a számítógépek beállításjegyzékében: [Az ügyféltelepítés tulajdonságainak megadása (csoportházirenden és szoftverfrissítésen alapuló ügyféltelepítés) hogyan](#BKMK_Provision). Ezeket a telepítési tulajdonságokat fogja használni, amikor az ügyfél telepítve van.  

A Windows Server dokumentációjában olvashat arról, miként használhatja a házirendeket szoftvertelepítésre az Active Directory tartományi szolgáltatásokban.  

##  <a name="BKMK_Manual"></a>Ügyfelek manuális telepítése  
 Manuálisan telepíthető az ügyfélszoftvert a számítógépeken a vállalat által a CCMSetup.exe programmal. A program és a hozzá kapcsolódó fájlok megtalálhatók a **ügyfél** mappában található a Configuration Manager telepítési mappájában a helykiszolgálón és a hely felügyeleti pontjain. A mappát a rendszer a következőképpen osztja meg a hálózaton:  

 \\\\*&lt;Hely kiszolgáló neve\>*\SMS_*&lt;Helykód\>*\Client\  

 Ha  *&lt;Helykiszolgálónév\>*  a a felügyeleti pontot futtató kiszolgálók egyikének neve és  *&lt;Helykód\>*  pedig annak az elsődleges hely az ügyfél fog tartozni.  Ha a CCMSetup.exe parancsot a parancssorból szeretné futtatni az ügyfélen, hálózati meghajtót kell csatlakoztatnia ehhez a helyhez, és ezután futtathatja a parancsot.  

> [!IMPORTANT]  
>  Az ügyfél-telepítési fájlok eléréséhez rendszergazdai engedélyekkel kell rendelkeznie.  

 A CCMSetup.exe másolja át az összes szükséges előfeltételek az ügyfélszámítógépen, és meghívja a Windows Installer-csomag (Client.msi) az ügyfél telepítéséhez. A Client.msi nem futtatható közvetlenül.  

 A CCMSetup.exe és a Client.msi telepítőfájlhoz is megadhat parancssori tulajdonságokat az ügyféltelepítés működésének módosításához. Győződjön meg arról, hogy a CCMSetup tulajdonságait kell előbb megadni (karakterrel kezdődő tulajdonságokat  **/** ) Client.msi tulajdonságainak megadása előtt. Példa:  

```  
CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=AUTO FSP=SMSFP01  
```  
és az ügyfél telepítése a következő tulajdonságokkal megy végbe:  

|Tulajdonság|Leírás|  
|--------------|-----------------|  
|**smsmp01**|A CCMSetup e tulajdonsága az SMSMP01 felügyeleti pontot adja meg a szükséges ügyfél-telepítési fájlok letöltéséhez.|  
|**/logon**|A CCMSetup e tulajdonsága határozza meg, hogy a telepítés álljon le, ha egy meglévő Configuration Manager-ügyfelet a számítógépen megtalálható.|  
|**SMSSITECODE = AUTO**|A Client.msi e tulajdonsága határozza meg, hogy az ügyfél megpróbálja megkeresni a Configuration Manager helykódja szeretné használni, például Active Directory tartományi szolgáltatások használatával.|  
|**FSP = SMSFP01**|A Client.msi e tulajdonsága azt adja meg, hogy az SMSFP01 nevű tartalék állapotkezelő pontot kell használni az ügyfélszámítógép által küldött állapotüzenetek fogadásához.|  

 A CCMSetup.exe tulajdonságairól a [Tudnivalók a System Center Configuration Manager ügyféltelepítési tulajdonságairól](../../../core/clients/deploy/about-client-installation-properties.md) című cikk nyújt részletes tájékoztatást.  

### <a name="examples"></a>Példák
 Ezekben a példákban az Active Directory-ügyfelek az intraneten találhatók, és a hely különböző jellemzőinek megfelelő értékek szerepelnek:  

 **MPSERVER** = a felügyeleti pontot tartalmazó kiszolgáló   
**FSPSERVER** = a tartalék állapotkezelő pontot tartalmazó kiszolgáló  
**ABC** = helykód  
**contoso.com** = tartománynév  

 Minden helyrendszer-kiszolgálók intranetes teljes Tartománynévvel van konfigurálva, és a helyük közzé van téve az ügyfél Active Directory-erdőben.  

 Az ügyfélszámítógépen, jelentkezzen be helyi rendszergazdaként, meghajtót (z:) rendel\\\MPSERVER\SMS_ABC\Client, váltson a parancssorban a z meghajtóra, és futtassa a következő parancsok egyikét.  

 **1. példa:**  

```  
CCMSetup.exe  
```  
Ez a példa az ügyfél telepítése További tulajdonságok nélkül, hogy a rendszer automatikusan konfigurálja az Active Directory tartományi szolgáltatásokban közzétett ügyfél-telepítési tulajdonságokat. Például az ügyfél automatikusan konfigurálja a hely kódja (az ügyfél hálózati helye az ügyfél-hozzárendelésre beállított határcsoportban szereplő igényel), egy felügyeleti pontot, a tartalék állapotkezelő pontot, hogy az ügyfél csak a HTTPS protokoll használatával kell kommunikációt. Az Active Directory-ügyfeleken automatikusan konfigurálható ügyféltelepítési tulajdonságokról az [Információ az Active Directory tartományi szolgáltatásokban közzétett ügyfélszoftver-telepítési tulajdonságokról a System Center Configuration Managerben](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md) című cikk nyújt tájékoztatást.  

 **2. példa:**  

```  
CCMSetup.exe /MP:mpserver.contoso.com /UsePKICert SMSSITECODE=ABC CCMHOSTNAME=server05.contoso.com CCMFIRSTCERT=1 FSP=server06.constoso.com  
```  
Ez a példa felülírja az automatikus beállítás, amely Active Directory tartományi szolgáltatások biztosít, és nem igényli, hogy az ügyfél hálózati helye az ügyfél-hozzárendelésre beállított határcsoportban szerepel-e. Ehelyett a telepítés megadja a helyet, az intranetes felügyeleti pontot és az internetes felügyeleti pontot, az internetről érkező kapcsolatok fogadására beállított tartalék állapotkezelő pontot, valamint a leghosszabb érvényességi időtartammal rendelkező PKI-ügyféltanúsítvány (ha elérhető) használatát.  

##  <a name="BKMK_ClientLogonScript"></a>Ügyfelek telepítése bejelentkezési parancsfájlok  
 A Configuration Manager támogatja a Configuration Manager ügyfélszoftver telepítése bejelentkezési parancsfájlok. A **CCMSetup.exe** programfájlt használhatja a bejelentkezési parancsprogramokban az ügyféltelepítés elindításához.  

 A bejelentkezési parancsfájlos telepítés ugyanazokat a módszereket használja, mint a kézi ügyféltelepítés. Megadhatja a CCMSsetup.exe **/logon** telepítési tulajdonságát, amely megakadályozza az ügyfél telepítését, ha a számítógépen már megtalálható az ügyfél bármelyik verziója. Ez megakadályozza az ügyfél újbóli telepítését, amikor újból lefut a bejelentkezési parancsfájl.  

 Ha nincs telepítési megadva forrás, amely használ a **/Source** tulajdonság, és nincs olyan felügyeleti pont használatával megadott telepítés, amelynek be kell szereznie a **/MP** tulajdonság CCMSetup.exe keresheti meg a felügyeleti pont keresést az Active Directory tartományi szolgáltatások, ha a séma megtörtént-e a Configuration Manager és a helyet közzéteszi az Active Directory tartományi szolgáltatások. Másik megoldásként az ügyfél a DNS vagy a WINS használatával is megkeresheti a felügyeleti pontot.  

##  <a name="BKMK_ClientApp"></a>Ügyfelek telepítése csomag és program  
 A Configuration Manager hozhat létre és telepítsen egy csomagot és programot, amely frissíti az ügyfélszoftvert a hierarchia kiválasztott számítógépein. Egy csomagdefiníciós fájlt, amely megadja a csomagtulajdonságok általánosan használt értékeit a Configuration Manager van megadva. Az ügyféltelepítés működését további parancssori tulajdonságok megadásával testre szabhatja.  

> [!NOTE]  
>  Ezzel a módszerrel a Configuration Manager 2007-ügyfelek nem frissíthető. Ehelyett használjon automatikus ügyfélfrissítést, amely automatikusan létrehozza és telepíti az ügyfél legújabb verzióját. További információk: [Ügyfélszoftverek verziófrissítése a System Center Configuration Managerben](../../../core/clients/manage/upgrade/upgrade-clients.md).  
>   
>  A Configuration Manager-ügyfél régebbi verzióiról áttelepítésével kapcsolatos további információkért lásd: [a System Center Configuration Manager ügyfelek áttelepítési stratégiájának tervezése](../../../core/migration/planning-a-client-migration-strategy.md).  

 
###<a name="to-create-a-package-and-program-for-the-client-software"></a>Csomag és program létrehozása az ügyfélszoftverhez  

A következő eljárással hozhat létre a Configuration Manager-csomagot és programot, hogy központilag telepíthető a Configuration Manager-ügyfélszámítógépek számára, hogy frissítse az ügyfélszoftvert.  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **csomagok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **csomag létrehozása definícióból**.  

4.  A a **Csomagdefiníció** lapján jelöljön ki **Microsoft** a a **Publisher** legördülő listából válassza ki, és válassza ki **Configuration Manager ügyfélfrissítési** a a **Csomagdefiníció** listája.  

5.  Az a **forrásfájlok** lapon jelölje be **mindig a forrásmappából szerezze be a fájlok**.  

6.  Az a **Forrásmappához** lapon jelölje be **hálózati elérési út (UNC-név)** és adja meg a hálózati elérési útját a számítógép és az ügyfél telepítési fájljait tartalmazó mappát.  

    > [!NOTE]  
    >  A számítógép, amelyen a Configuration Manager központi telepítését futtató hozzáféréssel kell rendelkeznie a megadott hálózati mappához, ellenkező esetben a telepítés sikertelen lesz.  

    Ha módosítani szeretné az ügyfél-telepítési tulajdonságok valamelyikét, megváltoztathatja a CCMSetup.exe parancssori paramétereit a **Configuration Manager ügynök frissítése csendes üzemmódban – Tulajdonságok** párbeszédpanel **Általános** lapján. Az alapértelmezett telepítési tulajdonság a következő: **/noservice SMSSITECODE=AUTO**.  

9. Terjessze a csomagot minden olyan terjesztési pontra, amelyen el szeretné helyezni az ügyfélfrissítési csomagot. Ezután végrehajthatja a csomag-ügyfeleket, amelyek a frissíteni kívánt számítógép-gyűjteményekre.  

## <a name="how-to-install-clients-to-intune-mdm-managed-windows-devices"></a>Ügyfelek telepítése Intune MDM által felügyelt Windows rendszerű eszközök

A Microsoft Intune-nal beléptetett számítógépekre telepítheti az Ügyféltelepítő fájlokat. 

Gondoskodjon arról, hogy az eszköz felügyelt állapotban marad, az ügyfélszoftver telepítése után, az eszköz a vállalati hálózaton, és a Configuration Manager hely határán belül kell lennie. 

> [!NOTE]
> Az ügyfélszoftver telepítése után az eszköz regisztrációját Intune-ban.

### <a name="to-install-clients-with-intune"></a>Az Intune-ügyfelek telepítése:

1. Az Intune-ban [hozzon létre egy alkalmazást](/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) a Configuration Manager-ügyfél telepítő fájlját tartalmazó **ccmsetup.msi**.

2. Az Intune Software Publisher használatát használja a következő parancssori paraméterek:

  **CCMSETUPCMD = "/ MP:&lt;felügyeleti pont teljes Tartományneve > SMSMP =&lt;felügyeleti pont teljes Tartományneve > SMSSITECODE =&lt;a hely kódja > DNSSUFFIX =&lt;felügyeleti pont DNS-utótag >"**

3. [Az alkalmazás telepítése](/intune/deploy-use/deploy-apps-in-microsoft-intune) a regisztrált Windows rendszerű számítógépekre.

##  <a name="BKMK_ClientImage"></a>A számítógép lemezképét az ügyfelek telepítése  
A Configuration Manager ügyfélszoftvert a fő rendszerkép számítógépén, amely a használni kívánt kép más számítógépekre telepíthet.   

### <a name="to-prepare-the-client-computer-for-imaging"></a>Az ügyfélszámítógép előkészítése a lemezképpel végrehajtott telepítéshez  

1.  Manuálisan telepítse a Configuration Manager-ügyfélszoftvert a fő rendszerkép számítógépén. További információ: [A Configuration Manager-ügyfelek telepítése manuálisan](#BKMK_Manual).  

    > [!IMPORTANT]  
    >  A Configuration Manager-hely kódja nem ad meg az ügyfél számára a CCMSetup.exe parancssori tulajdonságainál.  

2.  A parancssorba írja be a **net stop ccmexec** tulajdonságot, hogy az **SMS ügynökállomás** szolgáltatás (Ccmexec.exe) ne fusson a fő rendszerkép számítógépén.  

3.  Távolítson el minden tanúsítványt a fő rendszerkép számítógépén lévő helyi számítógéptárból.  Ha például nyilvános kulcsokra épülő infrastruktúrájú (PKI) tanúsítványokat használ, el kell távolítania a tanúsítványokat a **Személyes** tárolóból a **Számítógép** és a **Felhasználó** objektum esetében egyaránt, mielőtt rendszerképet készítene a számítógépről.

4.  Ha az ügyfelek egy másik Configuration Manager hierarchiából, a fő rendszerkép számítógépétől lesznek telepítve, távolítsa el a megbízható legfelső szintű kulcsot a fő rendszerkép számítógépéről.  
    > [!NOTE]  
    >  Ha az ügyfelek nem tudják lekérdezni az Active Directory Domain Servicesben a felügyeleti pont helyét, a megbízható legfelső szintű kulcs használatával határozzák meg a megbízható felügyeleti pontokat. Ha a lemezképpel telepített összes ügyfél abban a hierarchiában lesz telepítve, amelyben a fő számítógép is található, hagyja a helyén a megbízható legfelső szintű kulcsot. Ha az ügyfelek más hierarchiákban lesznek telepítve, távolítsa el a megbízható legfelső szintű kulcsot, és legjobb megoldásként az új megbízható legfelső szintű kulcs használatával végezze el ezen ügyfelek előzetes kiépítését. További információk: [A megbízható legfelső szintű kulcs tervezése](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK). 

5.  Használjon megfelelő lemezképkészítő szoftvert a mesterszámítógép lemezképének rögzítéséhez.  

6.  Telepítse központilag a lemezképet a célszámítógépekre.  

##  <a name="BKMK_ClientWorkgroup"></a>Ügyfelek telepítése munkacsoporthoz tartozó számítógépeken  
 A Configuration Manager ügyfél telepítése a munkacsoportokban lévő számítógépeket támogatja. Munkacsoporthoz tartozó számítógépeken az ügyfél telepítési módszerét lásd: [A Configuration Manager-ügyfelek telepítése manuálisan](#BKMK_Manual).  

 Előfeltételek:  

-   Az ügyfelet manuálisan kell telepíteni a munkacsoport egyes számítógépein. A telepítés során a bejelentkezett felhasználónak helyi rendszergazdai jogosultságokkal kell rendelkeznie.  

-   A Configuration Manager helykiszolgáló tartományában lévő erőforrások eléréséhez a helyhez a hálózatelérési fiókot kell konfigurálni. Szoftver telepítési összetevő tulajdonságaként adja meg ezt a fiókot. További információkért lásd: [A System Center Configuration Manager helyösszetevői](../../../core/servers/deploy/configure/site-components.md).  

 Korlátozások vonatkoznak:  

-   A munkacsoportba tartozó ügyfelek nem kereshetnek felügyeleti pontokat az Active Directory Domain Servicesben, helyette DNS, WINS vagy más felügyeleti pontot kell használniuk.  

-   A globális barangolás nem támogatott, mivel az ügyfelek nem tudják lekérdezni a helyadatokat az Active Directory tartományi szolgáltatásokból.  

-   Az Active Directory felderítési módszerei nem képesek felderíteni munkacsoportokban lévő számítógépeket.  

-   Nem telepíthet központilag szoftvert munkacsoportbeli számítógépek felhasználói számára.  

-   Nem használhatja az ügyfélleküldéses telepítési módszert az ügyfél telepítéséhez munkacsoportbeli számítógépeken.  

-   Munkacsoporthoz tartozó ügyfelek nem használhatják a Kerberos hitelesítéshez, és manuális jóváhagyásra lehet szükség.  

-   A munkacsoportba tartozó ügyfelek nem konfigurálhatók terjesztési pontként. A Configuration Manager megköveteli, hogy terjesztési pontként működő számítógépek egy tartomány tagjai legyenek.  

### <a name="to-install-the-client-on-workgroup-computers"></a>Az ügyfél telepítése munkacsoportbeli számítógépeken  

Ellenőrizze az Előfeltételek teljesülését, majd kövesse a című szakasz utasításait [hogyan kell telepíteni a Configuration Manager ügyfelek manuális](#BKMK_Manual).  

   Ez a példa telepíti az ügyfelet intranetes ügyfélfelügyelethez, és megadja a helykódot és a felügyeleti pont keresésére DNS-utótag:`**CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=constoso.com**`  

     

   Ennél a példánál az szükséges, hogy a sikeres automatikus helyhozzárendelés érdekében az ügyfél egy határcsoportban konfigurált hálózati helyen legyen. A parancs tartalék állapotkezelő pont az ügyfél telepítésének nyomon követéséhez és annak minden ügyfél-kommunikációs problémák azonosításához FSPSERVER kiszolgálón tartalmazza:`**CCMSetup.exe FSP=fspserver.constoso.com**`  

      

##  <a name="BKMK_ClientInternet"></a>Az Internet alapú ügyfélfelügyelethez ügyfelek telepítése  
 Ha a Configuration Manager-hely támogatja az Internet alapú ügyfélfelügyelet az, amelyek időnként az intraneten, és egyes esetekben az interneten, két lehetősége van ügyfelek intraneten való telepítésekor:  

-   Megadhatja a Client.msi-tulajdonság a CCMHOSTNAME =*&lt;az Internet alapú felügyeleti pontjának internetes teljes Tartománynevét\>*  az ügyfél telepítésekor, például manuális telepítés vagy ügyfélleküldés használatával. Amikor ezt a módszert használja, az ügyfelet közvetlenül kell hozzárendelnie a helyhez, nem használhat automatikus helyhozzárendelést. Ebben a témakörben [A Configuration Manager-ügyfelek telepítése manuálisan](#BKMK_Manual) című szakasz példát tartalmaz ehhez a konfigurálási módszerhez.  

-   Telepítheti az ügyfelet intranetes ügyfélfelügyelethez, és egy internetes ügyfél-felügyeleti pontot az ügyfélhez a Configuration Manager ügyféltulajdonságainak használatával a Vezérlőpulton, illetve parancsfájl használatával, majd rendelje hozzá. Ennél a módszernél automatikus ügyfél-hozzárendelést használhat. Részletesebb tájékoztatás a témakör [Ügyfelek konfigurálása internetalapú ügyfélfelügyeletre az ügyfél telepítése után](#BKMK_ConfigureIBCM_MP) című szakaszában olvasható.  

 Ha interneten lévő ügyfeleket kell telepítenie, mert ezek csak internetes ügyfelek, vagy mert telepítenie kell ezeket, mielőtt visszakerülnének az intranetre, válasszon a következő támogatott módszerek közül:  

-   Az ügyfelek kapcsolódni ideiglenesen az intranethez, a virtuális magánhálózat (VPN) egy olyan mechanizmus biztosítása, és telepítse azokat a megfelelő ügyfél-telepítési módszer használatával.  

-   Amely független a Configuration Manager alkalmazásból, például az ügyfél telepítési forrásfájlok cserélhető adathordozón, a felhasználóknak küld utasításokkal telepítése csomagolására telepítési módszert használja. Az ügyféltelepítési forrásfájlok találhatók a  *&lt;Telepítésiútvonal\>*a Configuration Manager-hely és a felügyeleti pontok \Client mappájában. Az adathordozón legyen egy parancsfájl, amely végrehajtja a mappa manuális átmásolását, és ebből a mappából a CCMSetup.exe és a CCMSetup megfelelő parancssori tulajdonságainak használatával telepíti az ügyfelet.  

> [!NOTE]  
>  A Configuration Manager nem támogatja az ügyfél közvetlen telepítését az Internet alapú felügyeleti pont vagy az Internet alapú szoftverfrissítési pontról.  

 Mivel az interneten keresztült felügyelt ügyfeleknek kommunikálniuk kell az internetes helyrendszerekkel, ezért az ilyen ügyfelek telepítése előtt biztosítsa, hogy ezek nyilvános kulcsokra épülő infrastruktúrájú (PKI) tanúsítványokkal rendelkezzenek. Telepítenie kell ezeket a tanúsítványokat egymástól függetlenül a Configuration Manager alkalmazásból. További információ a tanúsítványkövetelményekről: [A System Center Configuration Manager PKI-tanúsítványának követelményei](../../../core/plan-design/network/pki-certificate-requirements.md).  

### <a name="to-install-clients-on-the-internet-by-specifying-ccmsetup-command-line-properties"></a>Ügyfelek telepítése az interneten a CCMSetup parancssori tulajdonságainak megadásával  

1.  Kövesse [A Configuration Manager-ügyfelek telepítése manuálisan](#BKMK_Manual) című szakasz utasításait, és mindig foglalja bele a következőket:  

    -   CCMSetup parancssori tulajdonság **/source:***&lt;a másolt Client mappa elérési útja\>*  

    -   CCMSetup parancssori tulajdonsága: **/UsePKICert**  

    -   Client.msi-tulajdonsággal **CCMHOSTNAME =***&lt;teljes Tartománynevet az internetes felügyeleti pont\>*  

    -   Client.msi-tulajdonsággal **SMSSIGNCERT =***&lt;exportált helykiszolgáló aláíró tanúsítványának helyi elérési útja\>*  

    -   Client.msi-tulajdonsággal **SMSSITECODE =***&lt;Helykód Internet alapú felügyeleti pont\>*  

    > [!NOTE]  
    >  Ha a hely egynél több internet alapú felügyeleti ponttal rendelkezik, bármelyik felügyeleti pontot megadhatja a CCMHOSTNAME tulajdonságnál. Amikor a Configuration Manager-ügyfél a megadott Internet alapú felügyeleti ponthoz csatlakozik, a felügyeleti pont elküldi az ügyfélnek a rendelkezésre álló Internet alapú felügyeleti pontok listáját a helyen, és az ügyfél véletlenszerűen választ egyet a listáról.  

2.  Ha nem kívánja, hogy az ügyfél ellenőrizze a visszavont tanúsítványok listáját (CRL), adja meg a CCMSetup **/NoCRLCheck** parancssori tulajdonságát.  

3.  Ha az Internet alapú tartalék állapotkezelő pontot használ, adja meg a Client.msi-tulajdonsággal **FSP =***&lt;az Internet alapú tartalék állapotkezelő pont internetes teljes Tartományneve\>*.  

4.  Ha kizárólag internetes ügyfélfelügyeletre telepíti az ügyfelet, adja meg a **CCMALWAYSINF=1** Client.msi-tulajdonságot.  

5.  Ellenőrizze, hogy rendelkezik-e további CCMSetup parancssori tulajdonságainak megadása. Például lehetséges, hogy egy tanúsítvány kiválasztási feltétel megadásához, ha az ügyfél egynél több érvényes PKI-tanúsítvánnyal rendelkezik. Az elérhető tulajdonságok listája a [Tudnivalók a System Center Configuration Manager ügyféltelepítési tulajdonságairól](../../../core/clients/deploy/about-client-installation-properties.md) című cikkben olvasható.  

   Például: `**CCMSetup.exe /source: D:\Clients /UsePKICert CCMHOSTNAME=server1.contoso.com SMSSIGNCERT=siteserver.cer SMSSITECODE=ABC FSP=server2.contoso.com CCMALWAYSINF=1 CCMFIRSTCERT=1**`  

   Ez a példa az ügyfél forrásfájljait a D meghajtó mappájából telepíti a következő beállításokkal: PKI-ügyféltanúsítvány használata és a leghosszabb ideig érvényes tanúsítvány választása kizárólag internetes ügyfélfelügyeletre, az ügyfél hozzárendelése a SERVER1 nevű internet alapú felügyeleti ponthoz és az internet alapú tartalék állapotkezelő ponthoz a contoso.com tartományban, valamint az ügyfél hozzárendelése az ABC helyhez.  

###  <a name="BKMK_ConfigureIBCM_MP"></a>Ügyfél telepítése után Internet alapú Ügyfélfelügyelethez ügyfelek konfigurálása  
 Az ügyfél telepítése után az internet alapú felügyeleti pont hozzárendeléséhez a következő eljárásokat használhatja. Az első manuális konfigurálást igényel, és kevés ügyfélnél megfelelő. A második pedig jobban megfelelő sok ügyfél konfigurálásához.  

#### <a name="to-configure-clients-for-internet-based-client-management-after-client-installation-by-assigning-the-internet-based-management-point-in-configuration-manager-properties"></a>Ügyfelek konfigurálása internet alapú ügyfélfelügyeletre az ügyfél telepítése után internet alapú felügyeleti pont hozzárendelésével a Configuration Manager tulajdonságainál  

1.  Az ügyfélszámítógép Vezérlőpultján lépjen **Configuration Manager** elemre, majd tulajdonságainak megnyitásához kattintson rá duplán.  

2.  Az **Internet** lapon, az Internetes teljes tartománynév mezőben adja meg az internetalapú felügyeleti pont teljes tartománynevét.  

    > [!NOTE]  
    >  Az **Internet** lap csak akkor érhető el, ha az ügyfél PKI-ügyféltanúsítvánnyal rendelkezik.  

3.  Adja meg a proxykiszolgáló beállításait, ha az ügyfél proxykiszolgálón keresztül éri el az internetet.  

#### <a name="to-configure-clients-for-internet-based-client-management-after-client-installation-by-using-a-script"></a>Ügyfelek konfigurálása internet alapú ügyfélfelügyeletre az ügyfél telepítése után parancsfájl használatával  

1.  Nyisson meg egy szövegszerkesztőt, például a Jegyzettömböt.  

2.  Másolja és illessze be a következő fájlba. Az *mp.contoso.com* helyére írja internetalapú felügyeleti pontjának internetes teljes tartománynevét.  

    ```  
    on error resume next  

    ' Create variables.  
    Dim newInternetBasedManagementPointFQDN  
    Dim client  

    newInternetBasedManagementPointFQDN = "mp.contoso.com"  

    ' Create the client COM object.  
    Set client = CreateObject ("Microsoft.SMS.Client")  

    ' Set the Internet-Based Management Point FQDN by calling the SetCurrentManagementPoint method.  
    client.SetInternetManagementPointFQDN newInternetBasedManagementPointFQDN  

    ' Clear variables.  
    Set client = Nothing  
    Set internetBasedManagementPointFQDN = Nothing  

    ```  

    > [!NOTE]  
    >  Ha törölnie kell egy megadott internetalapú felügyeleti pontot, hogy az ügyfél ne legyen konfigurálva internetalapú felügyeleti pont használatára, távolítsa el az idézőjelek közötti értéket. Ekkor a sor a következő lesz: **newInternetBasedManagementPointFQDN = ""**.  

4.  Mentse a fájlt .vbs kiterjesztéssel.  

5.  Használja a cscript programot a parancsfájl futtatásához az ügyfélszámítógépeken a következő módszerek valamelyikével:  

    -   Telepítse központilag a fájlt meglévő Configuration Manager-ügyfelekre csomag és program használatával.  

    -   Futtassa helyileg a fájlt meglévő Configuration Manager-ügyfeleken: ehhez az Intézőben kattintson duplán a parancsfájlra.  

 Előfordulhat, hogy az ügyfél a módosítások életbe léptetéséhez indítsa újra.  

##  <a name="BKMK_Provision"></a>Ügyfél-telepítési tulajdonságok (csoport házirend- és szoftver-alapú ügyféltelepítés) kiépítése  
 A Configuration Manager ügyféltelepítési tulajdonságokkal számítógépek Windows csoportházirend segítségével. Ezek a tulajdonságok a számítógép beállításjegyzékében tárolódnak, és az ügyfélszoftver telepítésekor olvassa el. Ez az eljárás általában nem szükséges, de szükség lehet az ügyféltelepítés bizonyos eseteinél, például:  

-   Csoportházirend beállításain vagy szoftverfrissítési ponton alapuló ügyfél-telepítési módszert használ, és nem lett kibővítve az Active Directory-sémát a Configuration Manager számára.  

-   Adott számítógépeken felül szeretné bírálni az ügyfél-telepítési tulajdonságokat.  

> [!NOTE]  
>  Ha bármelyik telepítési tulajdonságot megadja a CCMSetup.exe parancssorában, a számítógépeken előkészített telepítési tulajdonságokat nem fogja használni a rendszer.  

 A csoportházirend ConfigMgrInstallation.adm nevű felügyeleti sablonja van megadva, a Configuration Manager telepítési adathordozón, amely ügyfélszámítógépek telepítési tulajdonságok kiépítéséhez használható.   

### <a name="to-configure-and-assign-client-installation-properties-by-using-a-group-policy-object"></a>Ügyfél-telepítési tulajdonságok konfigurálása és hozzárendelése csoportházirend objektum használatával  

1.  Importálja a ConfigMgrInstallation.adm felügyeleti sablont egy új vagy meglévő csoportházirend objektumba szerkesztő használatával, például Windows Csoportházirendobjektum-szerkesztő. A fájl a mappában található **TOOLS\ConfigMgrADMTemplates** a Configuration Manager telepítési adathordozón.  

2.  Nyissa meg az importált **Ügyfél-telepítési beállítások konfigurálása** beállítás tulajdonságait.  

3.  Válasszon **engedélyezett**.  

4.  A **CCMSetup** mezőben adja meg a CCMSetup szükséges parancssori tulajdonságait. A CCMSetup összes tulajdonságának listája és a használatukat bemutató példák a [Tudnivalók a System Center Configuration Manager ügyféltelepítési tulajdonságairól](../../../core/clients/deploy/about-client-installation-properties.md) című cikkben olvashatók.  

5.  A csoportházirend-objektum hozzárendelése a Configuration Manager ügyfél-telepítési tulajdonságok kiépítéséhez kívánt számítógépeket.  

 A Windows csoportházirendjéről a tudnivalókat a Windows Server megfelelő dokumentációja tartalmazza.  

### <a name="see-also"></a>További információ
[Ügyféltelepítési módszerek a System Center Configuration Managerben](../../../core/clients/deploy/plan/client-installation-methods.md)
