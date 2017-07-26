---
title: "PKI-tanúsítványok központi telepítési |} Microsoft Docs"
description: "Kövesse a részletes példa áttekintésével megismerheti, hogyan hozhat létre és telepíthet, amelyek a System Center Configuration Manager használ a PKI-tanúsítványokat."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3417ff88-7177-4a0d-8967-ab21fe7eba17
caps.latest.revision: 11
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: b15f85b4483bbae2444d4e73d2e2aa0b3979d9ab
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="step-by-step-example-deployment-of-the-pki-certificates-for-system-center-configuration-manager-windows-server-2008-certification-authority"></a>Részletes példa tanúsítványok központi telepítését a nyilvános kulcsokra épülő infrastruktúra a System Center Configuration Manager: Windows Server 2008 hitelesítésszolgáltató

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez részletes példa a központi telepítési, egy Windows Server 2008 hitelesítésszolgáltatót (CA) használ, eljárások, amelyek bemutatják a létrehozása és telepítése a System Center Configuration Manager használ a nyilvános kulcsokra épülő infrastruktúra (PKI) tanúsítványokat tartalmaz. Ezek a műveletek vállalati hitelesítésszolgáltatót és tanúsítványsablonokat tartalmaznak. A lépéseket csak tesztelési célú hálózatban ajánlott végrehajtani megvalósíthatósági példaként.  

 Mivel nincs egységes módszer a szükséges tanúsítványok, tekintse meg az adott PKI központi telepítési dokumentációjában szükséges eljárások és ajánlott eljárások az éles környezetben a szükséges tanúsítványok telepítéséhez. További információ a tanúsítványkövetelményekről [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

> [!TIP]  
>  Ez a témakör az operációs rendszerek, amelyek nem szerepelnek a tesztelési célú hálózat követelményei szakaszban található utasítások módosíthatja. Ha azonban a kiállító hitelesítésszolgáltatót a Windows Server 2012 rendszerben futtatja, a rendszer nem kéri a tanúsítványsablon verziójának megadását. Ehelyett adja meg a **kompatibilitási** a sablon tulajdonságok lapon:  
>   
>  -   **Hitelesítésszolgáltató**: **Windows Server 2003**  
> -   **Tanúsítvány kedvezményezettje**: **Windows XP / Server 2003**  

## <a name="in-this-section"></a>A szakasz tartalma  
 A következő részek lépésről létrehozása és telepítése a System Center Configuration Managerrel használható következő tanúsítványok:  

 [Tesztelési célú hálózat követelményei](#BKMK_testnetworkenvironment)  

 [A tanúsítványok áttekintése](#BKMK_overview2008)  

 [A webkiszolgáló-tanúsítvány az IIS-t futtató helyrendszerek telepítése](#BKMK_webserver2008_cm2012)  

 [A szolgáltatástanúsítvány a felhő alapú terjesztési pontok telepítése](#BKMK_clouddp2008_cm2012)  

 [A Windows rendszerű számítógépeken az ügyféltanúsítvány központi telepítése](#BKMK_client2008_cm2012)  

 [Az ügyféltanúsítványt a terjesztési pontok telepítése](#BKMK_clientdistributionpoint2008_cm2012)  

 [Mobileszközök beléptetési tanúsítványának központi telepítése](#BKMK_mobiledevices2008_cm2012)  

 [A tanúsítványok telepítése AMT-hez](#BKMK_AMT2008_cm2012)  

 [A Mac számítógépeken futó ügyfele tanúsítvány telepítése](#BKMK_MacClient_SP1)  

##  <a name="BKMK_testnetworkenvironment"></a>Tesztelési célú hálózat követelményei  
 A lépésenkénti útmutatás követelményei a következők:  

-   A tesztelési célú hálózat az Active Directory tartományi szolgáltatásokat és a Windows Server 2008 rendszert futtatja, és egyetlen tartományként és egyetlen erdőként van telepítve.  

-   A tagkiszolgálón fut a Windows Server 2008 Enterprise Edition telepítve van rá az Active Directory tanúsítványszolgáltatások szerepkör, és egy vállalati legfelső szintű hitelesítésszolgáltatóként (CA) van beállítva, hogy.  

-   Több számítógépen, amelyen Windows Server 2008 (Standard Edition vagy Enterprise Edition R2 vagy újabb verzió) telepítve van-e, tagkiszolgálóként kapja meg, hogy a számítógép, és az Internet Information Services (IIS) telepítve van rajta. A számítógép lesz a System Center Configuration Manager helyrendszer-kiszolgáló, amely egy intranetes teljes tartománynevét (FQDN) ügyfélkapcsolatok támogatásához az intranetes és internetes teljes tartománynév, ha a System Center Configuration Manager és az ügyfelek által beléptetett mobileszközök támogatnia kell adnia az interneten.  

-   Egy Windows Vista ügyfél, amely rendelkezik a legújabb szervizcsomaggal, és a számítógép be van állítva az a számítógép neve, amely ASCII-karakterekből, és csatlakozik a tartományhoz. A számítógép lesz a System Center Configuration Manager-ügyfélszámítógépen.  

-   Jelentkezzen be egy legfelső szintű tartományi rendszergazdai fiókot vagy egy vállalati tartományi rendszergazdai fiókot, és ezt a fiókot használják a telepítési példában szereplő összes művelethez.  

##  <a name="BKMK_overview2008"></a>A tanúsítványok áttekintése  
 A következő táblázat a PKI-tanúsítványokat, melyek lehet szükség a System Center Configuration Manager, és megismerkedhet használatukkal típusú.  

|Szükséges tanúsítvány|Tanúsítvány leírása|  
|-----------------------------|-----------------------------|  
|Webkiszolgáló-tanúsítvány az IIS-t futtató helyrendszerekhez|Ez a tanúsítvány használható az adatok titkosítására és a kiszolgáló hitelesítésére az ügyfeleken. Az kívülről kell telepíteni a System Center Configuration Manager helyrendszer-kiszolgálókra, amelyek be vannak állítva a System Center Configuration Managerben a HTTPS vagy futó Internet Information Services (IIS).<br /><br /> Állítsa be, és a tanúsítvány telepítése lépéseit, lásd: [a webkiszolgáló-tanúsítvány az IIS-t futtató helyrendszerek telepítése](#BKMK_webserver2008_cm2012) ebben a témakörben.|  
|Az ügyfelek szolgáltatástanúsítványai a felhőalapú terjesztési pontokhoz való csatlakozáshoz|Ez a tanúsítvány konfigurálásáról és telepítéséről lépéseiért lásd: [a szolgáltatástanúsítvány a felhő alapú terjesztési pontok telepítése](#BKMK_clouddp2008_cm2012) ebben a témakörben.<br /><br /> **Fontos:** Ez a tanúsítvány a Windows Azure felügyeleti tanúsítvánnyal együtt használható. A felügyeleti tanúsítvány kapcsolatban bővebben lásd: [felügyeleti tanúsítvány létrehozása](http://go.microsoft.com/fwlink/p/?LinkId=220281) és [felügyeleti tanúsítvány hozzáadása Windows Azure-előfizetéshez](http://go.microsoft.com/fwlink/?LinkId=241722) az MSDN Library Windows Azure Platform szakaszában.|  
|Ügyféltanúsítvány a Windows rendszerű számítógépekhez|Ezzel a tanúsítvánnyal hitelesíti a System Center Configuration Manager-ügyfélszámítógépek számára, hogy be vannak állítva a HTTPS-t. Azt is segítségével a felügyeleti pontok és állapotáttelepítési pontok a működésük állapotának figyelésére, ha azok be vannak állítva a HTTPS protokoll használatát. Az kívülről kell telepíteni a System Center Configuration Manager a számítógépeken.<br /><br /> Állítsa be, és a tanúsítvány telepítése lépéseit, lásd: [központi telepítése Windows rendszerű számítógépeken az ügyféltanúsítvány](#BKMK_client2008_cm2012) ebben a témakörben.|  
|Ügyféltanúsítvány a terjesztési pontokhoz|Ennek a tanúsítványnak két célja van:<br /><br /> Ezzel a tanúsítvánnyal hitelesíthető a terjesztési pont egy HTTPS használatára konfigurált felügyeleti ponton, mielőtt a terjesztési pont elküldi az állapotüzeneteket.<br /><br /> Amikor a terjesztési pontra vonatkozó **PXE-támogatás engedélyezése ügyfeleknek** beállítás meg van adva, a rendszer elküldi a tanúsítványt a PXE által elindított számítógépeknek, hogy csatlakozhassanak a HTTPS használatára konfigurált felügyeleti ponthoz az operációs rendszer telepítése közben.<br /><br /> Állítsa be, és a tanúsítvány telepítése lépéseit, lásd: [telepítheti az ügyféltanúsítványt a terjesztési pontok](#BKMK_clientdistributionpoint2008_cm2012) ebben a témakörben.|  
|Beléptetési tanúsítvány a mobileszközökhöz|Ezzel a tanúsítvánnyal be vannak állítva a HTTPS-t System Center Configuration Manager mobileszközös ügyfeleinek hitelesítésére. A System Center Configuration Manager mobileszköz beléptetésének részeként kell telepíteni, és a konfigurált tanúsítványsablont választja, a mobileszközök ügyfélbeállításaként.<br /><br /> Ez a tanúsítvány beállítása lépéseiért lásd: [mobileszközök beléptetési tanúsítványának központi telepítése](#BKMK_mobiledevices2008_cm2012) ebben a témakörben.|  
|Az Intel AMT tanúsítványai|Három tanúsítvány kapcsolódik az Intel AMT-alapú számítógépek sávon kívüli felügyeleti:<ul><li>Az Active Management Technology AMT kiépítési tanúsítvány</li><li>Egy AMT webkiszolgáló-tanúsítvány</li><li>Szükség esetén egy ügyfél-hitelesítési tanúsítvány a 802. 1 X-hitelesítésű vezetékes vagy vezeték nélküli hálózatokhoz</li></ul>Az AMT kiépítési tanúsítványt kívülről kell telepíteni a System Center Configuration Manager a sávon kívüli szolgáltatási pont számítógépén, és majd a telepített tanúsítvány kiválasztása a sávon kívüli szolgáltatási pont tulajdonságainál. Az AMT webkiszolgáló-tanúsítvány és az ügyfél-hitelesítési tanúsítvány AMT kiépítése és felügyelete közben telepíthető, és a sávon kívüli felügyeleti összetevő tulajdonságai párbeszédpanelen válassza ki a konfigurált tanúsítványsablonok.<br /><br /> Állítsa be ezeket a tanúsítványokat lépéseiért lásd: [a tanúsítványok telepítése Amt](#BKMK_AMT2008_cm2012) ebben a témakörben.|  
|Ügyféltanúsítvány a Mac rendszerű számítógépekhez|Igényli, és telepítse a tanúsítványt Mac rendszerű számítógépről, használja a System Center Configuration Manager-regisztrációt, és válassza ki a konfigurált tanúsítványsablont, a mobileszközök ügyfélbeállításaként.<br /><br /> Ez a tanúsítvány beállítása lépéseiért lásd: [telepítheti az ügyféltanúsítványt a Mac számítógépek](#BKMK_MacClient_SP1) ebben a témakörben.|  

##  <a name="BKMK_webserver2008_cm2012"></a>A webkiszolgáló-tanúsítvány az IIS-t futtató helyrendszerek telepítése  
 Ehhez a központi tanúsítványtelepítéshez a következő eljárások tartoznak:  

-   Létrehozása és kiállítása a webkiszolgáló tanúsítványsablon a hitelesítésszolgáltatón  

-   A webkiszolgáló-tanúsítvány kérése  

-   Konfigurálja az IIS-t a webkiszolgáló-tanúsítvány használatára  

###  <a name="BKMK_webserver22008"></a>Létrehozása és kiállítása a webkiszolgáló tanúsítványsablon a hitelesítésszolgáltatón  
 Ez az eljárás tanúsítványsablont hoz létre a System Center Configuration Manager helyrendszerekhez, és hozzáadja azt a hitelesítésszolgáltatóhoz.  

##### <a name="to-create-and-issue-the-web-server-certificate-template-on-the-certification-authority"></a>Webkiszolgáló-tanúsítvány sablonjának létrehozása és kiállítása a hitelesítésszolgáltatónál  

1.  Hozzon létre egy biztonsági csoportot nevű **ConfigMgr IIS-kiszolgálók** , amely rendelkezik a tagkiszolgálókat IIS-t futtató helyrendszerek System Center Configuration Manager telepítéséhez.  

2.  Azon a tagkiszolgálón, amelyen a tanúsítványszolgáltatások telepítve, a hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok** majd **kezelése** betöltése a **tanúsítványsablonok** konzol.  

3.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely rendelkezik **webkiszolgáló** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

4.  Az a **Sablon duplikálása** párbeszédpanelen ellenőrizze, hogy **a Windows 2003 Server, Enterprise Edition** van kiválasztva, és válassza a **OK**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition**beállítást.  

5.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr webkiszolgáló-tanúsítvány**, a Configuration Manager helyrendszerein használni kívánt ügyféltanúsítványok előállításához.  

6.  Válassza ki a **tulajdonosnévvel** lapot, és győződjön meg arról, hogy **a kérelem fogja tartalmazni** van kiválasztva.  

7.  Válassza ki a **biztonsági** lapot, és távolítsa el a **beléptetés** engedélyt a **Tartománygazdák** és **vállalati rendszergazdák** biztonsági csoportokat.  

8.  Válasszon **Hozzáadás**, adja meg **ConfigMgr IIS-kiszolgálók** a szöveg mezőbe, majd válassza a **OK**.  

9. Válassza ki a **beléptetés** engedélyt ehhez a csoporthoz, és ne törölje a **olvasási** engedéllyel.  

10. Válasszon **OK**, majd zárja be a **Tanúsítványsablonok konzolt**.  

11. A hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

12. Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr webkiszolgáló-tanúsítvány**, és válassza a **OK**.  

13. Ha nem kell további tanúsítványokat, zárja be létrehoznia és kiállítania **hitelesítésszolgáltató**.  

###  <a name="BKMK_webserver32008"></a>A webkiszolgáló-tanúsítvány kérése  
 Ez az eljárás lehetővé teszi, hogy adja meg az intranetes és internetes teljes tartománynevet, hogy a helyrendszer-kiszolgáló tulajdonságainak a beállítása, és telepíti az IIS-t futtató tagkiszolgálóra a webkiszolgáló-tanúsítvány.  

##### <a name="to-request-the-web-server-certificate"></a>A webkiszolgáló-tanúsítvány igénylésének lépései  

1.  Győződjön meg arról, hogy a számítógép biztosan hozzáférhessen a használatával létrehozott tanúsítványsablon IIS-t futtató tagkiszolgálót indítsa újra a **olvasási** és **beléptetés** engedéllyel.  

2.  Válasszon **Start**, válassza a **futtassa**, és írja be **mmc.exe.** Az üres konzolban kattintson **fájl**, és válassza a **beépülő modul hozzáadása/eltávolítása**.  

3.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **tanúsítványok** közül **elérhető beépülő modulok**, és válassza a **Hozzáadás**.  

4.  Az a **beépülő modul** párbeszédpanelen válassza ki **számítógépfiók**, és válassza a **következő**.  

5.  Az a **számítógép kijelölése** párbeszédpanelen ellenőrizze, hogy **helyi számítógép: (a számítógép a konzol fut)** van kiválasztva, és válassza a **Befejezés**.  

6.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **OK**.  

7.  A konzolon bontsa ki **tanúsítványok (helyi számítógép)**, és válassza a **személyes**.  

8.  Kattintson a jobb gombbal **tanúsítványok**, válassza a **feladataival**, és válassza a **új tanúsítvány kérése**.  

9. Az a **előkészületek** lapon, válassza ki **következő**.  

10. Ha megjelenik a **tanúsítványigénylési házirend kiválasztása** lapon, válassza ki **következő**.  

11. A a **tanúsítványkérés** lapon, és keresse meg a **ConfigMgr webkiszolgáló-tanúsítvány** a rendelkezésre álló tanúsítványok listájáról, és válassza a **a tanúsítvány igényléséhez több információ szükséges. Kattintson ide a beállítások konfigurálásához** beállításra.  

12. Az a **tanúsítvány tulajdonságai** párbeszédpanel a **tulajdonos** lapján ne módosításait **tulajdonos neve**. Ez azt jelenti, hogy a **Tulajdonos neve** szakasz **Érték** mezőjének üresen kell maradnia. Ehelyett a **alternatív nevének** területen válassza ki a **típus** legördülő listában, és válassza a **DNS**.  

13. Az a **érték** adja meg a teljes tartományneveket, a rendszer a System Center Configuration Manager hely tulajdonságainál adja meg, és válassza **OK** bezárásához a **tanúsítvány tulajdonságai** párbeszédpanel megnyitásához.  

     Példák:  

    -   Ha a helyrendszer csak az intranetről érkező ügyfélkapcsolatokat fogja fogadni, és az intranetes teljes Tartománynevet a helyrendszer-kiszolgáló **server1.internal.contoso.com**, adja meg **server1.internal.contoso.com**, és válassza a **Hozzáadás**.  

    -   Ha a helyrendszer az intranetről és az internetről is fog ügyfélkapcsolatokat fogadni, az intranetes helyrendszer-kiszolgáló teljes tartományneve **server1.internal.contoso.com** , az internetes helyrendszer-kiszolgáló teljes tartományneve pedig **server.contoso.com**:  

        1.  Adja meg **server1.internal.contoso.com**, és válassza a **Hozzáadás**.  

        2.  Adja meg **server.contoso.com**, és válassza a **Hozzáadás**.  

        > [!NOTE]  
        >  Megadhatja a teljes tartományneveket a System Center Configuration Manager bármilyen sorrendben. Azonban ellenőrizze, hogy minden olyan eszköznek, fogja használni a tanúsítványt, például a mobileszközök és a proxy-webkiszolgálók, használhatja a tanúsítvány Tulajdonos alternatív neve (SAN) és a több értékkel a tulajdonos alternatív nevének. Ha az eszközök csak korlátozottan támogatják a tanúsítványok tulajdonosának alternatív nevét megadó értékeket, lehetséges, hogy meg kell változtatnia a teljes tartománynevek sorrendjét, vagy a Tulajdonos neve beállítás értékét kell használnia.  

14. A a **tanúsítványok kérése** lapon, válassza ki **ConfigMgr webkiszolgáló-tanúsítvány** a listából a rendelkezésre álló tanúsítványok, és válassza a **beléptetés**.  

15. Az a **Tanúsítványtelepítés – eredmények** lapon Várjon, amíg a tanúsítvány van telepítve, és válassza a **Befejezés**.  

16. Zárja be a **Tanúsítványok (Helyi számítógép)**párbeszédpanelt.  

###  <a name="BKMK_webserver42008"></a>Konfigurálja az IIS-t a webkiszolgáló-tanúsítvány használatára  
 Ez az eljárás összeköti a telepített tanúsítványt az IIS **Alapértelmezett webhely**beállításával.  

##### <a name="to-set-up-iis-to-use-the-web-server-certificate"></a>Hozzon létre az IIS a webkiszolgáló-tanúsítvány használatára  

1.  A telepített IIS-t tartalmazó tagkiszolgálón kattintson **Start**, válassza a **programok**, válassza ki **felügyeleti eszközök**, és válassza a **Internet Information Services (IIS) Manager**.  

2.  Bontsa ki a **helyek**, kattintson a jobb gombbal **alapértelmezett webhely**, és válassza a **kötések szerkesztése**.  

3.  Válassza ki a **https** bejegyzést, és válassza a **szerkesztése**.  

4.  Az a **hely kötésének szerkesztése** párbeszédpanelen válassza ki a ConfigMgr webkiszolgáló-tanúsítványok használatával igényelt tanúsítványt, és válassza a **OK**.  

    > [!NOTE]  
    >  Ha nem biztos abban, hogy ez az a megfelelő tanúsítvány, válasszon egyet, és válassza a **nézet**. Ez lehetővé teszi, hogy a tanúsítványok a tanúsítványok beépülő modulban a kiválasztott tanúsítvány adatainak összehasonlítását. Például a tanúsítványok beépülő modulban jeleníti meg a a tanúsítvány igényléséhez használt tanúsítványsablont. Ezután összehasonlíthatja az aktuálisan kiválasztott tanúsítvány tanúsítvány-ujjlenyomata a ConfigMgr webkiszolgáló-tanúsítványok sablonnal igényelt tanúsítvány tanúsítvány-ujjlenyomata a **hely kötésének szerkesztése** párbeszédpanel megnyitásához.  

5.  Válasszon **OK** a a **hely kötésének szerkesztése** párbeszédpanel mezőbe, majd válassza a **Bezárás**.  

6.  Zárja be az **Internet Information Services (IIS) kezelője**eszközt.  

 A tagkiszolgálót most már be van állítva a System Center Configuration Manager webkiszolgáló-tanúsítvány.  

> [!IMPORTANT]  
>  Ha a System Center Configuration Manager helyrendszer-kiszolgáló ezen a számítógépen telepíti, győződjön meg arról, hogy adjon meg ugyanazokat a teljes tartományneveket a helyrendszer tulajdonságai, amikor a kért tanúsítvány megadott.  

##  <a name="BKMK_clouddp2008_cm2012"></a>A szolgáltatástanúsítvány a felhő alapú terjesztési pontok telepítése  

Ehhez a központi tanúsítványtelepítéshez a következő eljárások tartoznak:  

-   [Létrehozása és kiállítása az egyéni webkiszolgáló tanúsítványsablon a hitelesítésszolgáltatón](#BKMK_clouddpcreating2008)  

-   [Az egyéni webkiszolgáló-tanúsítvány kérése](#BKMK_clouddprequesting2008)  

-   [A felhő alapú terjesztési pontok az egyéni webkiszolgáló-tanúsítvány exportálása](#BKMK_clouddpexporting2008)  

###  <a name="BKMK_clouddpcreating2008"></a>Létrehozása és kiállítása az egyéni webkiszolgáló tanúsítványsablon a hitelesítésszolgáltatón  
 Ez az eljárás tanúsítványsablont hoz létre egyéni a webkiszolgáló-tanúsítvány sablonja alapján. A tanúsítvány a System Center Configuration Manager felhő alapú terjesztési pontok és a titkos kulcsnak exportálhatónak kell lennie. Létrehozása után a tanúsítványsablon a hitelesítésszolgáltató részévé válik.  

> [!NOTE]  
>  Ez az eljárás egy a webkiszolgáló-tanúsítvány sablonjának létrehozott tanúsítványsablont használja, az IIS-t futtató helyrendszerek. Bár mindkét tanúsítványnak kiszolgálóhitelesítési funkcióval igényelnek, a felhő alapú terjesztési pontok a tanúsítványt meg kell adnia egy egyénileg definiált értéket a tulajdonos nevének és a titkos kulcsot exportálni kell. A biztonság érdekében célszerű, így nem tanúsítványsablonok beállítása, hogy a titkos kulcs exportálható legyen, ha ez a konfiguráció nem szükséges. A felhőalapú terjesztési ponthoz, ez a beállítás szükséges, mivel kell importálja a tanúsítványt fájlként, nem pedig válassza ki azt a tanúsítványtárolóból.  
>   
>  Amikor ezt a tanúsítványt egy új tanúsítványsablont hoz létre, korlátozhatja a számítógépeket, amelyek igényelhet olyan tanúsítványt, amelynek titkos kulcs exportálható legyen. Éles hálózati környezetben akkor előfordulhat, hogy emellett szóba jöhet a tanúsítvány a következő módosításokat:  
>   
>  -   Telepítse a tanúsítványt, a biztonság további erősítése jóváhagyást igényel.  
> -   A tanúsítvány érvényességi időtartamának növelése. Mivel a kell exportálni, és importálja a tanúsítványt az Érvényesség lejárata előtt minden alkalommal, megnövelheti az érvényességi időtartam csökkenti, milyen gyakran kell ismételnie ezt az eljárást. Azonban megnövelheti az érvényességi időtartam is csökkenti a biztonsági tanúsítvány, mert a támadók titkos kulcs visszafejtésére és a tanúsítvány ellopására több időt biztosít.  
> -   Egyéni érték használata a tanúsítványnál a Tulajdonos alternatív neve (SAN) mezőben, hogy jobban megkülönböztethető legyen ez a tanúsítvány az IIS rendszerrel használt szokásos webkiszolgáló-tanúsítványoktól.  

##### <a name="to-create-and-issue-the-custom-web-server-certificate-template-on-the-certification-authority"></a>Létrehozása és kiállítása az egyéni webkiszolgáló tanúsítványsablon a hitelesítésszolgáltatón  

1.  Hozzon létre egy biztonsági csoportot nevű **ConfigMgr Helykiszolgálók** , amely rendelkezik a tagkiszolgálókat telepítéséhez a System Center Configuration Manager elsődleges hely kiszolgálóin, amelyek felhőalapú terjesztési pontokat fogják kezelni.  

2.  A hitelesítésszolgáltató konzolt futtató tagkiszolgálón kattintson a jobb gombbal **tanúsítványsablonok**, és válassza a **kezelése** a Tanúsítványsablonok kezelése konzol betöltéséhez.  

3.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely rendelkezik **webkiszolgáló** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

4.  Az a **Sablon duplikálása** párbeszédpanelen ellenőrizze, hogy **a Windows 2003 Server, Enterprise Edition** van kiválasztva, és válassza a **OK**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition**beállítást.  

5.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr felhőalapú terjesztési pont tanúsítványa**, a felhő alapú terjesztési pontok a webkiszolgáló-tanúsítvány létrehozásához.  

6.  Válassza ki a **kérelmek kezelése** lapra, és válassza a **a titkos kulcs exportálható**.  

7.  Válassza ki a **biztonsági** lapot, és távolítsa el a **beléptetés** engedélyt a **vállalati rendszergazdák** biztonsági csoport.  

8.  Válasszon **Hozzáadás**, adja meg **ConfigMgr Helykiszolgálók** a szöveg mezőbe, majd válassza a **OK**.  

9. Ehhez a csoporthoz adja meg a **Beléptetés** engedélyt, és ne törölje az **Olvasás** engedélyt.  

10. Válasszon **OK**, majd zárja be a **Tanúsítványsablonok konzolt**.  

11. A hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

12. Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr felhőalapú terjesztési pont tanúsítványa**, és válassza a **OK**.  

13. Ha nem kell további tanúsítványokat, zárja be létrehoznia és kiállítania **hitelesítésszolgáltató**.  

###  <a name="BKMK_clouddprequesting2008"></a>Az egyéni webkiszolgáló-tanúsítvány kérése  
 Ez az eljárás kér, és telepíti az egyéni webkiszolgáló-tanúsítvány azon a tagkiszolgálón, amely a helykiszolgáló.  

##### <a name="to-request-the-custom-web-server-certificate"></a>Az egyéni webkiszolgáló-tanúsítvány igénylésének lépései  

1.  Indítsa újra a tagkiszolgálót, létrehozása és konfigurálása után a **ConfigMgr Helykiszolgálók** biztonsági csoportra, és győződjön meg arról, hogy a számítógép biztosan hozzáférhessen a használatával létrehozott tanúsítványsablon a **olvasási** és **beléptetés** engedéllyel.  

2.  Válasszon **Start**, válassza a **futtatása**, és írja be **mmc.exe.** Az üres konzolban kattintson **fájl**, és válassza a **beépülő modul hozzáadása/eltávolítása**.  

3.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **tanúsítványok** közül **elérhető beépülő modulok**, és válassza a **Hozzáadás**.  

4.  Az a **beépülő modul** párbeszédpanelen válassza ki **számítógépfiók**, és válassza a **következő**.  

5.  Az a **számítógép kijelölése** párbeszédpanelen ellenőrizze, hogy **helyi számítógép: (a számítógép a konzol fut)** van kiválasztva, és válassza a **Befejezés**.  

6.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **OK**.  

7.  A konzolon bontsa ki **tanúsítványok (helyi számítógép)**, és válassza a **személyes**.  

8.  Kattintson a jobb gombbal **tanúsítványok**, válassza a **feladataival**, és válassza a **új tanúsítvány kérése**.  

9. Az a **előkészületek** lapon, válassza ki **következő**.  

10. Ha megjelenik a **tanúsítványigénylési házirend kiválasztása** lapon, válassza ki **következő**.  

11. A a **tanúsítványok kérése** lapon, és keresse meg a **ConfigMgr felhőalapú terjesztési pont tanúsítványa** a rendelkezésre álló tanúsítványok listájáról, és válassza a **további információt az regisztrálnia kell a tanúsítványt. dönthet úgy, itt a beállítások**.  

12. A a **tanúsítvány tulajdonságai** párbeszédpanel a **tulajdonos** lapon, az a **tulajdonos neve**, válassza a **köznapi név** , a **típus**.  

13. Az **Érték** mezőben adja meg a szolgáltatás és a tartomány választott nevét teljes tartománynév (FQDN) formátumban. Példa: **clouddp1.contoso.com**.  

    > [!NOTE]  
    >  Egyedivé teszi a szolgáltatás nevét a névtérben. A DNS szolgáltatást fogja használni alias (CNAME rekord) létrehozásánál ennek a szolgáltatásnévnek a leképezéséhez automatikusan előállított azonosítóra (GUID) és egy IP-címre a Windows Azure rendszerből.  

14. Válasszon **Hozzáadás**, és válassza a **OK** bezárásához a **tanúsítvány tulajdonságai** párbeszédpanel megnyitásához.  

15. A a **tanúsítványok kérése** lapon, válassza ki **ConfigMgr felhőalapú terjesztési pont tanúsítványa** a listából a rendelkezésre álló tanúsítványok, és válassza a **beléptetés**.  

16. Az a **Tanúsítványtelepítés – eredmények** lapon Várjon, amíg a tanúsítvány van telepítve, és válassza a **Befejezés**.  

17. Zárja be a **Tanúsítványok (Helyi számítógép)**párbeszédpanelt.  

###  <a name="BKMK_clouddpexporting2008"></a>A felhő alapú terjesztési pontok az egyéni webkiszolgáló-tanúsítvány exportálása  
 Ez az eljárás fájlba exportálja az egyéni webkiszolgáló-tanúsítványt, így az importálható lesz, amikor létrehozza a felhőalapú terjesztési pontot.  

##### <a name="to-export-the-custom-web-server-certificate-for-cloud-based-distribution-points"></a>Az egyéni webkiszolgáló-tanúsítvány exportálásának lépései felhőalapú terjesztési pontokhoz  

1.  A a **tanúsítványok (helyi számítógép)** konzol, kattintson a jobb gombbal az imént telepített tanúsítványra, majd a **feladataival**, és válassza a **exportálása**.  

2.  A Tanúsítványexportáló varázslóban kattintson **következő**.  

3.  Az a **titkos kulcs exportálása** lapon, válassza ki **Igen, a titkos kulcs exportálását választom**, és válassza a **következő**.  

    > [!NOTE]  
    >  Ha ez a beállítás nem érhető el, a tanúsítványt a titkos kulcs exportálásának engedélyezése nélkül hozták létre. Ebben az esetben nem exportálhatja a tanúsítványt a megkívánt formátumban. Be kell állítania a tanúsítványsablont, hogy a titkos kulcs exportálható, majd indítsa újra a tanúsítványt.  

4.  Az a **Exportfájlformátum** lapon, ügyeljen arra, hogy a **személyes információcsere - PKCS #12 (. PFX)** beállítást.  

5.  Az a **jelszó** csoportjában adja meg egy erős jelszót a titkos kulcsot tartalmazó exportált tanúsítvány védelméhez, és válassza a **következő**.  

6.  Az a **exportálandó fájl** adja meg azokat a exportálni, és válassza a kívánt fájl nevét **következő**.  

7.  A varázsló bezárásához kattintson a **Befejezés** a a **Tanúsítványexportáló varázsló** lapon, és válassza a **OK** a művelet megerősítését kérő párbeszédpanelen.  

8.  Zárja be a **Tanúsítványok (Helyi számítógép)**párbeszédpanelt.  

9. A fájlt biztonságos helyen tárolja, és győződjön meg arról, hogy hozzá tud férni a System Center Configuration Manager konzolról.  

 A tanúsítvány ezzel készen áll az importálásra, amikor felhőalapú terjesztési pontot hoz létre.  

##  <a name="BKMK_client2008_cm2012"></a>A Windows rendszerű számítógépeken az ügyféltanúsítvány központi telepítése  
 Ehhez a központi tanúsítványtelepítéshez a következő eljárások tartoznak:  

-   A hitelesítésszolgáltatón a munkaállomás-hitelesítési tanúsítvány sablonjának létrehozása és kiállítása  

-   A munkaállomás-hitelesítési sablon automatikus igénylésének konfigurálása csoportházirend használatával  

-   Automatikusan léptetni a munkaállomás-hitelesítési tanúsítványt, és a számítógépek telepítésének ellenőrzése  

###  <a name="BKMK_client02008"></a>A hitelesítésszolgáltatón a munkaállomás-hitelesítési tanúsítvány sablonjának létrehozása és kiállítása  
 Ez az eljárás tanúsítványsablont hoz létre a System Center Configuration Manager-ügyfelet a számítógépeken, és hozzáadja azt a hitelesítésszolgáltatóhoz.  

##### <a name="to-create-and-issue-the-workstation-authentication-certificate-template-on-the-certification-authority"></a>A munkaállomás-hitelesítési tanúsítvány sablonjának létrehozása és kiállítása a hitelesítésszolgáltatónál  

1.  A hitelesítésszolgáltató konzolt futtató tagkiszolgálón kattintson a jobb gombbal **tanúsítványsablonok**, és válassza a **kezelése** a Tanúsítványsablonok kezelése konzol betöltéséhez.  

2.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely rendelkezik **munkaállomás-hitelesítési** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

3.  Az a **Sablon duplikálása** párbeszédpanelen ellenőrizze, hogy **a Windows 2003 Server, Enterprise Edition** van kiválasztva, és válassza a **OK**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition**beállítást.  

4.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr ügyféltanúsítvány**, a Configuration Manager ügyfélszámítógépein használni kívánt ügyféltanúsítványok előállításához.  

5.  Válassza ki a **biztonsági** lapon jelölje be a **tartományi számítógépek** csoportot, és válassza ki a engedéllyel **olvasási** és **automatikus igénylés**. Ne törölje a **Beléptetés**engedélyt.  

6.  Válasszon **OK**, majd zárja be a **Tanúsítványsablonok konzolt**.  

7.  A hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

8.  Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr ügyféltanúsítvány**, és válassza a **OK**.  

9. Ha nem kell további tanúsítványokat, zárja be létrehoznia és kiállítania **hitelesítésszolgáltató**.  

###  <a name="BKMK_client12008"></a>A munkaállomás-hitelesítési sablon automatikus igénylésének konfigurálása csoportházirend használatával  
 Ez az eljárás állít be a csoportházirend automatikus igénylése az ügyféltanúsítványt a számítógépeken.  

##### <a name="to-set-up-autoenrollment-of-the-workstation-authentication-template-by-using-group-policy"></a>A munkaállomás-hitelesítési sablon automatikus igénylésének beállítása a csoportházirenddel  

1.  A tartományvezérlőn, válassza a **Start**, válassza a **felügyeleti eszközök**, és válassza a **a Csoportházirend kezelése**.  

2.  Nyissa meg a tartományhoz, kattintson jobb gombbal a tartományra, és válassza a **egy csoportházirend-objektum létrehozása ebben a tartományban, és hivatkozás létrehozása itt**.  

    > [!NOTE]  
    >  Ez a lépés ajánlott eljárásként használja új csoportházirend létrehozását az egyéni beállításokhoz, és nem az Active Directory tartományi szolgáltatásaival telepített alapértelmezett tartományi házirendet szerkeszti. Ennek a csoportházirendnek tartományi szinten rendel, akkor alkalmazza azt a tartomány összes számítógépéhez. Éles környezetben korlátozhatja az automatikus igénylést, hogy csak a kiválasztott számítógépeken beléptetett. A csoportházirend egy szervezeti egység szintjén rendelhet, vagy a tartomány csoportházirendjét, egy biztonsági csoporttal szűrheti, hogy csak a csoport számítógépeinek vonatkozik. Ha korlátozza az automatikus igénylést, akkor ne felejtse el bevenni a kiszolgáló be van állítva a felügyeleti pontnak.  

3.  Az a **új csoportházirend-objektum** párbeszédpanelen adja meg egy nevet, például **automatikus igénylés tanúsítványai**, az új Csoportházirendnek, és válassza a **OK**.  

4.  Az eredménypanelen a a **csatolt csoportházirend-objektumok** lapon kattintson a jobb gombbal az új Csoportházirendre, és válassza a **szerkesztése**.  

5.  Az a **Csoportházirendkezelés-szerkesztő**, bontsa ki a **házirendek** alatt **számítógép konfigurációja**, majd lépjen **Windows-beállítások** / **biztonsági beállítások** / **nyilvános kulcs házirendjei**.  

6.  Kattintson a jobb gombbal nevű **Tanúsítványszolgáltatások ügyfele - automatikus igénylés**, és válassza a **tulajdonságok**.  

7.  Az a **konfigurációs modell** legördülő menüben válassza ki **engedélyezve**, válassza a **lejárt tanúsítványok megújítása, folyamatban lévő tanúsítványok frissítése, eltávolítása a visszavont tanúsítványok**, válassza a **tanúsítványsablonokat használó tanúsítványok frissítése**, és válassza a **OK**.  

8.  Zárja be a **Csoportházirend kezelése**ablakot.  

###  <a name="BKMK_client22008"></a>Automatikusan léptetni a munkaállomás-hitelesítési tanúsítványt, és a számítógépek telepítésének ellenőrzése  
 Ez az eljárás az ügyféltanúsítványt telepíti a számítógépeken, és ellenőrzi a telepítést.  

##### <a name="to-automatically-enroll-the-workstation-authentication-certificate-and-verify-its-installation-on-the-client-computer"></a>Automatikus léptetni a munkaállomás-hitelesítési tanúsítványt, és az ügyfélszámítógép telepítésének ellenőrzése  

1.  Indítsa újra munkaállomás számítógépét, és várjon néhány percet, mielőtt bejelentkezik.  

    > [!NOTE]  
    >  A számítógép újraindítása a legbiztonságosabb módszer annak biztosítására, hogy sikeres legyen a tanúsítvány automatikus igénylése.  

2.  Jelentkezzen be rendszergazdai jogosultságokkal rendelkező fiókkal.  

3.  A keresési mezőbe, írja be a **mmc.exe.**, majd nyomja le az **Enter**.  

4.  Az üres kezelőkonzolon kattintson **fájl**, és válassza a **beépülő modul hozzáadása/eltávolítása**.  

5.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **tanúsítványok** közül **elérhető beépülő modulok**, és válassza a **Hozzáadás**.  

6.  Az a **beépülő modul** párbeszédpanelen válassza ki **számítógépfiók**, és válassza a **következő**.  

7.  Az a **számítógép kijelölése** párbeszédpanelen ellenőrizze, hogy **helyi számítógép: (a számítógép a konzol fut)** van kiválasztva, és válassza a **Befejezés**.  

8.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **OK**.  

9. A konzolon bontsa ki **tanúsítványok (helyi számítógép)**, bontsa ki a **személyes**, és válassza a **tanúsítványok**.  

10. Az eredmények ablaktáblájában győződjön meg arról, hogy rendelkezik-e a tanúsítvány **ügyfél-hitelesítés** a a **kívánt felhasználási cél** oszlopban, és hogy **ConfigMgr ügyféltanúsítvány** szerepel a **tanúsítványsablon** oszlop.  

11. Zárja be a **Tanúsítványok (Helyi számítógép)**párbeszédpanelt.  

12. Ismételje meg az 1 – 11. lépéseket a tagkiszolgálóra, ellenőrizze, hogy a kiszolgálót, amely hoznak létre a felügyeleti pontként is rendelkezik-e az ügyféltanúsítványt a.  

 A számítógép most már be van állítva a System Center Configuration Manager ügyfél tanúsítvánnyal.  

##  <a name="BKMK_clientdistributionpoint2008_cm2012"></a>Az ügyféltanúsítványt a terjesztési pontok telepítése  

> [!NOTE]  
>  Ez a tanúsítvány olyan adathordozó programkódjára is használható, amely nem PXE-rendszerindítást használ, mivel a tanúsítvánnyal szembeni követelmények azonosak.  

 Ehhez a központi tanúsítványtelepítéshez a következő eljárások tartoznak:  

-   A hitelesítésszolgáltatón egyéni munkaállomás-hitelesítési tanúsítvány sablonjának létrehozása és kiállítása  

-   Az egyéni munkaállomás-hitelesítési tanúsítvány igénylésének lépései  

-   A terjesztési pontok ügyféltanúsítványának exportálása  

###  <a name="BKMK_clientdistributionpoint02008"></a>A hitelesítésszolgáltatón egyéni munkaállomás-hitelesítési tanúsítvány sablonjának létrehozása és kiállítása  
 Ez az eljárás tanúsítványsablont hoz létre egyéni System Center Configuration Manager terjesztési pontok számára, hogy a titkos kulcs exportálható, és a tanúsítványsablont hozzáadja a hitelesítésszolgáltatóhoz.  

> [!NOTE]  
>  Ez az eljárás egy másik tanúsítványsablont a létrehozott tanúsítványsablont használja, az ügyfélszámítógépek számára. Bár mindkét tanúsítványnak ügyfél-hitelesítésre alkalmas igényelnek, a tanúsítványt a terjesztési pont van szükség, hogy a titkos kulcs exportálása. A biztonság érdekében célszerű, így nem tanúsítványsablonok beállítása, a titkos kulcs exportálható legyen, ha ez a konfiguráció nem szükséges. A terjesztési ponton, ez a beállítás szükséges, mivel kell importálnia a tanúsítványt fájlként helyett válassza ki azt a tanúsítványtárolóból.  
>   
>  Amikor ezt a tanúsítványt egy új tanúsítványsablont hoz létre, korlátozhatja a számítógépeket, amelyek igényelhet olyan tanúsítványt, amelynek titkos kulcs exportálható legyen. Központi telepítési példánkban ez a System Center Configuration Manager helyrendszer-kiszolgálók IIS-t futtató korábban létrehozott biztonsági csoport lesz. Olyan éles hálózati környezetben, amely az IIS helyrendszerszerepköreit terjeszti, érdemes megfontolnia a terjesztési pontokat futtató kiszolgálókhoz új biztonsági csoport létrehozását, így a tanúsítványt kizárólag ezekre a helyrendszeri kiszolgálókra korlátozhatja. Emellett szóba jöhet a következő módosítások végrehajtása is ennél a tanúsítványnál:  
>   
>  -   Telepítse a tanúsítványt, a biztonság további erősítése jóváhagyást igényel.  
> -   A tanúsítvány érvényességi időtartamának növelése. Mivel a kell exportálni, és importálja a tanúsítványt az Érvényesség lejárata előtt minden alkalommal, megnövelheti az érvényességi időtartam csökkenti, milyen gyakran kell ismételnie ezt az eljárást. Azonban megnövelheti az érvényességi időtartam is csökkenti a biztonsági tanúsítvány, mert a támadók titkos kulcs visszafejtésére és a tanúsítvány ellopására több időt biztosít.  
> -   Egyéni érték használata a tanúsítványnál a Tulajdonos vagy a Tulajdonos alternatív neve (SAN) mezőben, hogy jobban megkülönböztethető legyen ez a tanúsítvány a szokásos ügyféltanúsítványoktól. Ez különösen hasznos lehet, ha ugyanazt a tanúsítványt használja több terjesztési ponthoz.  

##### <a name="to-create-and-issue-the-custom-workstation-authentication-certificate-template-on-the-certification-authority"></a>Az egyéni munkaállomás-hitelesítési tanúsítvány sablonjának létrehozása és kiállítása a hitelesítésszolgáltatónál  

1.  A hitelesítésszolgáltató konzolt futtató tagkiszolgálón kattintson a jobb gombbal **tanúsítványsablonok**, és válassza a **kezelése** a Tanúsítványsablonok kezelése konzol betöltéséhez.  

2.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely rendelkezik **munkaállomás-hitelesítési** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

3.  Az a **Sablon duplikálása** párbeszédpanelen ellenőrizze, hogy **a Windows 2003 Server, Enterprise Edition** van kiválasztva, és válassza a **OK**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition**beállítást.  

4.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr-ügyfél terjesztési pontjának tanúsítványa**, az ügyfél-hitelesítési tanúsítványt, a terjesztési pontok létrehozásához.  

5.  Válassza ki a **kérelmek kezelése** lapra, és válassza a **a titkos kulcs exportálható**.  

6.  Válassza ki a **biztonsági** lapot, és távolítsa el a **beléptetés** engedélyt a **vállalati rendszergazdák** biztonsági csoport.  

7.  Válasszon **Hozzáadás**, adja meg **ConfigMgr IIS-kiszolgálók** a szöveg mezőbe, majd válassza a **OK**.  

8.  Ehhez a csoporthoz adja meg a **Beléptetés** engedélyt, és ne törölje az **Olvasás** engedélyt.  

9. Válasszon **OK**, majd zárja be a **Tanúsítványsablonok konzolt**.  

10. A hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

11. Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr-ügyfél terjesztési pontjának tanúsítványa**, és válassza a **OK**.  

12. Ha nem kell további tanúsítványokat, zárja be létrehoznia és kiállítania **hitelesítésszolgáltató**.  

###  <a name="BKMK_clientdistributionpoint12008"></a>Az egyéni munkaállomás-hitelesítési tanúsítvány igénylésének lépései  
 Ez az eljárás kér, és arra a tagkiszolgálóra, amelyen fut az IIS, és hogy hoznak létre a terjesztési pontok az egyéni ügyféltanúsítványt, majd telepíti.  

##### <a name="to-request-the-custom-workstation-authentication-certificate"></a>Az egyéni munkaállomás-hitelesítési tanúsítvány igénylésének lépései  

1.  Válasszon **Start**, válassza a **futtatása**, és írja be **mmc.exe.** Az üres konzolban kattintson **fájl**, és válassza a **beépülő modul hozzáadása/eltávolítása**.  

2.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **tanúsítványok** közül **elérhető beépülő modulok**, és válassza a **Hozzáadás**.  

3.  Az a **beépülő modul** párbeszédpanelen válassza ki **számítógépfiók**, és válassza a **következő**.  

4.  Az a **számítógép kijelölése** párbeszédpanelen ellenőrizze, hogy **helyi számítógép: (a számítógép a konzol fut)** van kiválasztva, és válassza a **Befejezés**.  

5.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **OK**.  

6.  A konzolon bontsa ki **tanúsítványok (helyi számítógép)**, és válassza a **személyes**.  

7.  Kattintson a jobb gombbal **tanúsítványok**, válassza a **feladataival**, és válassza a **új tanúsítvány kérése**.  

8.  Az a **előkészületek** lapon, válassza ki **következő**.  

9. Ha megjelenik a **tanúsítványigénylési házirend kiválasztása** lapon, válassza ki **következő**.  

10. A a **tanúsítványkérés** lapon, válassza ki **ConfigMgr-ügyfél terjesztési pontjának tanúsítványa** a rendelkezésre álló tanúsítványok listájáról, és válassza a **beléptetés**.  

11. Az a **Tanúsítványtelepítés – eredmények** lapon Várjon, amíg a tanúsítvány van telepítve, és válassza a **Befejezés**.  

12. Az eredmények ablaktáblájában győződjön meg arról, hogy rendelkezik-e a tanúsítvány **ügyfél-hitelesítés** a a **kívánt felhasználási cél** oszlop, és hogy **ConfigMgr-ügyfél terjesztési pontjának tanúsítványa** szerepel a **tanúsítványsablon** oszlop.  

13. Ne zárja be a **Tanúsítványok (Helyi számítógép)**párbeszédpanelt.  

###  <a name="BKMK_exportclientdistributionpoint22008"></a>A terjesztési pontok ügyféltanúsítványának exportálása  
 Ezzel az eljárással exportálja fájlba az egyéni munkaállomás-hitelesítési tanúsítványt, így az, hogy importálni lehessen a terjesztési pont tulajdonságainál.  

##### <a name="to-export-the-client-certificate-for-distribution-points"></a>A terjesztési pontok ügyféltanúsítványának exportálása  

1.  A a **tanúsítványok (helyi számítógép)** konzol, kattintson a jobb gombbal az imént telepített tanúsítványra, majd a **feladataival**, és válassza a **exportálása**.  

2.  A Tanúsítványexportáló varázslóban kattintson **következő**.  

3.  Az a **titkos kulcs exportálása** lapon, válassza ki **Igen, a titkos kulcs exportálását választom**, és válassza a **következő**.  

    > [!NOTE]  
    >  Ha ez a beállítás nem érhető el, a tanúsítványt a titkos kulcs exportálásának engedélyezése nélkül hozták létre. Ebben az esetben nem exportálhatja a tanúsítványt a megkívánt formátumban. Be kell állítania a tanúsítványsablont, hogy a titkos kulcs exportálható, és majd indítsa újra a tanúsítványt.  

4.  Az a **Exportfájlformátum** lapon, ügyeljen arra, hogy a **személyes információcsere - PKCS #12 (. PFX)** beállítást.  

5.  Az a **jelszó** csoportjában adja meg egy erős jelszót a titkos kulcsot tartalmazó exportált tanúsítvány védelméhez, és válassza a **következő**.  

6.  Az a **exportálandó fájl** adja meg azokat a exportálni, és válassza a kívánt fájl nevét **következő**.  

7.  A varázsló bezárásához kattintson a **Befejezés** a a **Tanúsítványexportáló varázsló** lapon, és válassza a **OK** a művelet megerősítését kérő párbeszédpanelen.  

8.  Zárja be a **Tanúsítványok (Helyi számítógép)**párbeszédpanelt.  

9. A fájlt biztonságos helyen tárolja, és győződjön meg arról, hogy hozzá tud férni a System Center Configuration Manager konzolról.  

 A tanúsítvány importálásra, amikor állít be a terjesztési pont készen áll.  

> [!TIP]  
>  Is használhatja ugyanazt a tanúsítványfájlt, ha beállít egy operációs rendszer központi telepítése nem használja a PXE rendszerindító adathordozó programkódját, és a feladatütemezés, a lemezkép telepítéséhez kapcsolatba kell lépnie a felügyeleti pont HTTPS-ügyfélkapcsolatokat igényel.  

##  <a name="BKMK_mobiledevices2008_cm2012"></a>Mobileszközök beléptetési tanúsítványának központi telepítése  
 Ennél a tanúsítványtelepítésnél egy eljárással hozható létre és állítható ki a beléptetési tanúsítványsablon a hitelesítésszolgáltatón.  

### <a name="create-and-issue-the-enrollment-certificate-template-on-the-certification-authority"></a>Létrehozása és kiállítása a beléptetési tanúsítványsablon a hitelesítésszolgáltatón  
 Ez az eljárás a System Center Configuration Manager mobileszközök beléptetési tanúsítványsablont hoz létre, és hozzáadja azt a hitelesítésszolgáltatóhoz.  

##### <a name="to-create-and-issue-the-enrollment-certificate-template-on-the-certification-authority"></a>A beléptetési tanúsítványsablon létrehozása és kiállítása a hitelesítésszolgáltatónál  

1.  Hozzon létre egy biztonsági csoportot, amely a felhasználókat, akik regisztrálni fogják a mobileszközeiket a System Center Configuration Managerben.  

2.  Azon a tagkiszolgálón, amelyen a tanúsítványszolgáltatások telepítve, a hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, és válassza a **kezelése** a Tanúsítványsablonok kezelése konzol betöltéséhez.  

3.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely rendelkezik **hitelesített munkamenet** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

4.  Az a **Sablon duplikálása** párbeszédpanelen ellenőrizze, hogy **a Windows 2003 Server, Enterprise Edition** van kiválasztva, és válassza a **OK**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition**beállítást.  

5.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr mobileszköz-beléptetési tanúsítvány**, a System Center Configuration Manager által felügyelendő mobileszközök beléptetési tanúsítványainak előállításához.  

6.  Válassza ki a **tulajdonosnévvel** lapra, győződjön meg arról, hogy **az Active Directoryból** jelölve, jelölje be **köznapi név** a a **tulajdonos nevének formátuma:**, és törölje a jelet **egyszerű felhasználónév (UPN)** a **következő információk belefoglalása az alternatív tulajdonosnévbe**.  

7.  Válassza ki a **biztonsági** lapra, válassza ki a biztonsági csoport, amely rendelkezik a mobileszközökkel rendelkező felhasználók, és válassza a engedéllyel **beléptetés**. Ne törölje az **Olvasás**engedélyt.  

8.  Válasszon **OK**, majd zárja be a **Tanúsítványsablonok konzolt**.  

9. A hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

10. Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr mobileszköz-beléptetési tanúsítvány**, és válassza a **OK**.  

11. Ha nem kell további tanúsítványokat létrehoznia és kiállítania, zárja be a hitelesítésszolgáltató konzolt.  

 A mobileszköz-beléptetési tanúsítványsablon készen áll a kiválasztásra, amikor az ügyfél beállításai mobileszköz beléptetési profiljának beállítása.  

##  <a name="BKMK_AMT2008_cm2012"></a>A tanúsítványok telepítése AMT-hez  
 Ehhez a központi tanúsítványtelepítéshez a következő eljárások tartoznak:  

-   Hozzon létre, ki és az AMT kiépítési tanúsítvány telepítése  

-   Létrehozása és kiállítása a webkiszolgáló-tanúsítványt az AMT-alapú számítógépek  

-   Ügyfél létrehozása és kiállítása a 802.1 X AMT-alapú számítógépek ügyféltanúsítványokat  

###  <a name="BKMK_AMTprovisioning2008"></a>Hozzon létre, ki és az AMT kiépítési tanúsítvány telepítése  
 A belső hitelesítésszolgáltató a kiépítési tanúsítvány hozzon létre, amikor az AMT-alapú számítógépek be vannak állítva a belső legfelső szintű hitelesítésszolgáltató tanúsítvány-ujjlenyomatával. Ha ez nem áll fenn, és egy külső hitelesítésszolgáltatónak kell használnia, használja az AMT kiépítési tanúsítványt, amelyek többnyire azt írják elő a vállalat nyilvános webhelyén igényelheti a tanúsítványt kiállító vállalat utasításait. Előfordulhat, hogy is találhat részletes tájékoztatást a választott külső Hitelesítésszolgáltatóról az a [Intel vPro szakértői központban: Microsoft vPro kezelhetőségi webhely](http://go.microsoft.com/fwlink/?LinkId=132001).  

> [!IMPORTANT]  
>  Előfordulhat, hogy a külső hitelesítésszolgáltatók nem támogatják az Intel AMT kiépítési objektumazonosítót. Ha ez a helyzet, adja meg a **Intel(R) Client Setup Certificate** OU attribútumot.  

 Amikor AMT kiépítési tanúsítványt igényel egy külső Hitelesítésszolgáltatótól kér le, telepítse a tanúsítványt azon a tagkiszolgálón, amely a sávon kívüli szolgáltatási pont tárolni fogja a számítógép személyes tanúsítványtárolójába.  

##### <a name="to-request-and-issue-the-amt-provisioning-certificate"></a>Az AMT kiépítési tanúsítvány igénylése és kiállítása  

1.  Hozzon létre egy biztonsági csoportot, amely rendelkezik, amely a sávon kívüli szolgáltatási pont helyrendszer-kiszolgálók számítógépfiókja.  

2.  Azon a tagkiszolgálón, amelyen a tanúsítványszolgáltatások telepítve, a hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, és válassza a **kezelése** betöltése a **tanúsítványsablonok** konzol.  

3.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely rendelkezik **webkiszolgáló** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

4.  Az a **Sablon duplikálása** párbeszédpanelen ellenőrizze, hogy **a Windows 2003 Server, Enterprise Edition** van kiválasztva, és válassza a **OK**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition**beállítást.  

5.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr AMT kiépítés**, az AMT kiépítési tanúsítványsablon előállításához.  

6.  Válassza ki a **tulajdonosnévvel** lapra, majd **az Active Directoryból**, és válassza a **köznapi név**.  

7.  Válassza ki a **bővítmények** lapra, győződjön meg arról, hogy **alkalmazás-házirendek** van kiválasztva, és válassza a **szerkesztése**.  

8.  Az a **használati szabályzatok bővítmény szerkesztése** párbeszédpanelen válassza ki **Hozzáadás**.  

9. Az a **alkalmazás-házirend hozzáadása** párbeszédpanelen válassza ki **új**.  

10. A a **az új házirend** párbeszédpanelen adja meg a **AMT kiépítés** a a **neve** mezőben, és írja be a következő számot a **objektumazonosító**: **2.16.840.1.113741.1.2.3**.  

11. Válasszon **OK**, és válassza a **OK** a a **alkalmazás-házirend hozzáadása** párbeszédpanel megnyitásához.  

12. Válasszon **OK** a a **használati szabályzatok bővítmény szerkesztése** párbeszédpanel megnyitásához.  

13. Az a **új sablon tulajdonságai** párbeszédpanelen a következő van megadva, a **Tanúsítványhasználati házirend** leírása: **Kiszolgálóhitelesítés** és **AMT kiépítés**.  

14. Válassza ki a **biztonsági** lapot, és távolítsa el a **beléptetés** engedélyt a **Tartománygazdák** és **vállalati rendszergazdák** biztonsági csoportokat.  

15. Válasszon **Hozzáadás**, adja meg a sávon kívüli szolgáltatási pont helyrendszerszerepkörének számítógépfiókját tartalmazó biztonsági csoport nevét, és válassza a **OK**.  

16. Válassza ki a **beléptetés** engedélyt ehhez a csoporthoz, és ne törölje a **olvasási** engedély...  

17. Válasszon **OK**, majd zárja be a **tanúsítványsablonok** konzol.  

18. A **hitelesítésszolgáltató**, kattintson a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

19. Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr AMT kiépítés**, és válassza a **OK**.  

    > [!NOTE]  
    >  Ha nem tudja végrehajtani a 18. vagy 19. lépést, ellenőrizze, hogy a Windows Server 2008 Enterprise Edition kiadását használja-e. Bár a Windows Server Standard Edition és a tanúsítványszolgáltatások sablonok állíthat be, nem telepíthet tanúsítványokat a módosított tanúsítványsablonokkal, ha nem használja a kiadás a Windows Server 2008 Enterprise által.  

20. Ne zárja be a **Hitelesítésszolgáltató**párbeszédpanelt.  

 A belső hitelesítésszolgáltató AMT kiépítési tanúsítvány már készen áll a sávon kívüli szolgáltatási pont számítógépén kell telepíteni.  

##### <a name="to-install-the-amt-provisioning-certificate"></a>Az AMT kiépítési tanúsítvány telepítése  

1.  Indítsa újra a tagkiszolgálót, amelyen az IIS-t, győződjön meg arról, hogy hozzáférhessen a tanúsítványsablonhoz a konfigurált engedéllyel.  

2.  Válasszon **Start**, válassza a **futtatása**, és írja be **mmc.exe.** Az üres konzolban kattintson **fájl**, és válassza a **beépülő modul hozzáadása/eltávolítása**.  

3.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **tanúsítványok** közül **elérhető beépülő modulok**, és válassza a **Hozzáadás**.  

4.  Az a **beépülő modul** párbeszédpanelen válassza ki **számítógépfiók**, és válassza a **következő**.  

5.  Az a **számítógép kijelölése** párbeszédpanelen ellenőrizze, hogy **helyi számítógép: (a számítógép a konzol fut)** van kiválasztva, és válassza a **Befejezés**.  

6.  Az a **hozzáadása vagy eltávolítása a beépülő modulok** párbeszédpanelen válassza ki **OK**.  

7.  A konzolon bontsa ki **tanúsítványok (helyi számítógép)**, és válassza a **személyes**.  

8.  Kattintson a jobb gombbal **tanúsítványok**, válassza a **feladataival**, és válassza a **új tanúsítvány kérése**.  

9. Az a **előkészületek** lapon, válassza ki **következő**.  

10. Ha megjelenik a **tanúsítványigénylési házirend kiválasztása** lapon, válassza ki **következő**.  

11. A a **tanúsítványkérés** lapon jelölje be **AMT kiépítés** a rendelkezésre álló tanúsítványok listájáról, és válassza a **beléptetés**.  

12. Az a **Tanúsítványtelepítés – eredmények** lapon Várjon, amíg a tanúsítvány van telepítve, és válassza a **Befejezés**.  

13. Zárja be a **Tanúsítványok (Helyi számítógép)**párbeszédpanelt.  

 A belső hitelesítésszolgáltató AMT kiépítési tanúsítvány telepítve van, és ki kell választani a sávon kívüli szolgáltatási pont tulajdonságainál készen áll.  

### <a name="create-and-issue-the-web-server-certificate-for-amt-based-computers"></a>Létrehozása és kiállítása a webkiszolgáló-tanúsítványt az AMT-alapú számítógépek  
 A következő művelettel készítheti elő a webkiszolgáló-tanúsítványokat az AMT-alapú számítógépekhez.  

##### <a name="to-create-and-issue-the-web-server-certificate-template"></a>Létrehozása és kiállítása a webkiszolgáló tanúsítványsablon  

1.  Hozzon létre egy üres biztonsági csoportot, amely rendelkezik az AMT számítógépfiókokat, amely a System Center Configuration Manager hoz létre az AMT kiépítés során.  

2.  Azon a tagkiszolgálón, amelyen a tanúsítványszolgáltatások telepítve, a hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, és válassza a **kezelése** betöltése a **tanúsítványsablonok** konzol.  

3.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely rendelkezik **webkiszolgáló** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

4.  Az a **Sablon duplikálása** párbeszédpanelen ellenőrizze, hogy **a Windows 2003 Server, Enterprise Edition** van kiválasztva, és válassza a **OK**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition.**  

5.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr AMT webkiszolgáló-tanúsítvány**, hogy az AMT számítógépeken a sávon kívüli felügyeleti használandó webtanúsítványok előállításához.  

6.  Válassza ki a **tulajdonos neve** lapra, majd **az Active Directoryból**, válassza a **köznapi név** a a **tulajdonos nevének formátuma**, és törölje a jelet **egyszerű felhasználónév (UPN)** értéket az alternatív tulajdonosnév beállításánál.  

7.  Válassza ki a **biztonsági** lapot, és távolítsa el a **beléptetés** engedélyt a **Tartománygazdák** és **vállalati rendszergazdák** biztonsági csoportokat.  

8.  Válasszon **Hozzáadás**, és adja meg az AMT kiépítéshez létrehozott biztonsági csoport nevét, és válassza a **OK**.  

9. Válassza ki a következő **engedélyezése** a biztonsági csoport engedélyeit: **Olvasási** és **regisztrálása**.  

10. Válasszon **OK**, majd zárja be a **tanúsítványsablonok** konzol.  

11. Az a **hitelesítésszolgáltató** konzoljában a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

12. Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr AMT webkiszolgáló-tanúsítvány**, és válassza a **OK**.  

13. Ha nem kell további tanúsítványokat, zárja be létrehoznia és kiállítania **hitelesítésszolgáltató**.  

 Az AMT webkiszolgáló-tanúsítvány készen áll a webkiszolgáló-tanúsítványok AMT-alapú számítógépek beállítása. Válassza ki a tanúsítványsablont a sávon kívüli felügyeleti összetevő tulajdonságai párbeszédpanelen.  

### <a name="create-and-issue-the-client-authentication-certificates-for-8021x-amt-based-computers"></a>Ügyfél létrehozása és kiállítása a 802.1 X AMT-alapú számítógépek ügyféltanúsítványokat  
 A következő eljárást akkor használja, ha az AMT-alapú számítógépek ügyféltanúsítványokat fognak használni a 802.1X-hitelesítésű vezetékes vagy vezeték nélküli hálózatokhoz.  

##### <a name="to-create-and-issue-the-client-authentication-certificate-template-on-the-ca"></a>Az ügyfél-hitelesítési tanúsítvány sablonjának létrehozása és kiállítása a hitelesítésszolgáltatónál  

1.  Azon a tagkiszolgálón, amelyen a tanúsítványszolgáltatások telepítve, a hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, és válassza a **kezelése** betöltése a **tanúsítványsablonok** konzol.  

2.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely rendelkezik **munkaállomás-hitelesítési** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition.**  

3.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr AMT 802.1 X ügyfél-hitelesítési tanúsítvány**, hogy az AMT számítógépeken a sávon kívüli felügyeleti használandó ügyféltanúsítványok előállításához.  

4.  Válassza ki a **tulajdonosnévvel** lapra, majd **az Active Directoryból**, és válassza a **köznapi név** a a **tulajdonos nevének formátuma**. Törölje a jelet **DNS-név** a alternatív tulajdonos neve, és válassza a **egyszerű felhasználónév (UPN)**.  

5.  Válassza ki a **biztonsági** lapot, és távolítsa el a **beléptetés** engedélyt a **Tartománygazdák** és **vállalati rendszergazdák** biztonsági csoportokat.  

6.  Válasszon **Hozzáadás**, adja meg a nevét, a biztonsági csoport, amely a rendszer adja meg a sávon kívüli felügyeleti összetevő tulajdonságai párbeszédpanelen az AMT-alapú számítógépek számítógépfiókjainak tárolásához, és válassza a **OK**.  

7.  Válassza az alábbi **engedélyezés** a biztonsági csoport engedélyeit: **Olvasási** és **regisztrálása**.  

8.  Válasszon **OK**, majd zárja be a **tanúsítványsablonok** felügyeleti konzol **certtmpl – [tanúsítványsablonok]**.  

9. Az a **hitelesítésszolgáltató** felügyeleti konzolt, kattintson a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

10. Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr AMT 802.1 X ügyfél-hitelesítési tanúsítvány**, és válassza a **OK**.  

11. Ha nem kell további tanúsítványokat, zárja be létrehoznia és kiállítania **hitelesítésszolgáltató**.  

 Az ügyfél-hitelesítési tanúsítványsablon ezzel készen áll arra, hogy tanúsítványokat állítson ki a 802.1X ügyfél-hitelesítéshez használható AMT-alapú számítógépeknek. Válassza ki a tanúsítványsablont a sávon kívüli felügyeleti összetevő tulajdonságai párbeszédpanelen.  

##  <a name="BKMK_MacClient_SP1"></a>Telepítheti az ügyféltanúsítványt a Mac számítógépekhez  

Ennél a tanúsítványtelepítésnél egy eljárással hozható létre és állítható ki a beléptetési tanúsítványsablon a hitelesítésszolgáltatón.  

###  <a name="BKMK_MacClient_CreatingIssuing"></a>Létrehozása és kiállítása a Mac-ügyfél tanúsítványsablon a hitelesítésszolgáltatón  
 Ez az eljárás tanúsítványsablont hoz létre egy egyéni a System Center Configuration Manager Mac számítógépekre, és a tanúsítványsablont hozzáadja a hitelesítésszolgáltatóhoz.  

> [!NOTE]  
>  Ez az eljárás a Windows rendszerű ügyfélszámítógépekhez vagy a terjesztési pontokhoz létrehozott tanúsítványsablontól különböző tanúsítványsablont használ.  
>   
>  Amikor ezt a tanúsítványt egy új tanúsítványsablont hoz létre, korlátozhatja a tanúsítványkérelmet engedéllyel rendelkező felhasználók számára.  

##### <a name="to-create-and-issue-the-mac-client-certificate-template-on-the-certification-authority"></a>A MAC ügyfél-tanúsítvány sablonjának létrehozása és kiállítása a hitelesítésszolgáltatónál  

1.  Hozzon létre egy biztonsági csoportot, amely rendelkezik a felhasználói fiókokat a rendszergazdákat, akik regisztrálni fogják a tanúsítványt a Mac számítógépen a System Center Configuration Manager használatával.  

2.  A hitelesítésszolgáltató konzolt futtató tagkiszolgálón kattintson a jobb gombbal **tanúsítványsablonok**, és válassza a **kezelése** a Tanúsítványsablonok kezelése konzol betöltéséhez.  

3.  Az eredménypanelen kattintson a jobb gombbal az bejegyzést, amely megjeleníti **hitelesített munkamenet** a a **sablon megjelenítendő neve** oszlop, és válassza a **Sablon duplikálása**.  

4.  Az a **Sablon duplikálása** párbeszédpanelen ellenőrizze, hogy **a Windows 2003 Server, Enterprise Edition** van kiválasztva, és válassza a **OK**.  

    > [!IMPORTANT]  
    >  Ne válassza a **Windows 2008 Server, Enterprise Edition**beállítást.  

5.  Az a **új sablon tulajdonságai** párbeszédpanel a **általános** lapra, adja meg a sablon nevét, például **ConfigMgr Mac-ügyféltanúsítványa**, a Mac ügyfél-tanúsítvány előállításához.  

6.  Válassza ki a **tulajdonos neve** lapra, győződjön meg arról, hogy **az Active Directoryból** van kiválasztva, válassza a **köznapi név** a a **tulajdonos nevének formátuma:**, és törölje a jelet **egyszerű felhasználónév (UPN)** a **következő információk belefoglalása az alternatív tulajdonosnévbe**.  

7.  Válassza ki a **biztonsági** lapot, és távolítsa el a **beléptetés** engedélyt a **Tartománygazdák** és **vállalati rendszergazdák** biztonsági csoportokat.  

8.  Válasszon **Hozzáadás**, adja meg a biztonsági csoportot, amelyiket az első lépésben létrehozott, és válassza a **OK**.  

9. Válassza ki a **beléptetés** engedélyt ehhez a csoporthoz, és ne törölje a **olvasási** engedéllyel.  

10. Válasszon **OK**, majd zárja be a **Tanúsítványsablonok konzolt**.  

11. A hitelesítésszolgáltató konzolon kattintson a jobb gombbal **tanúsítványsablonok**, válassza a **új**, és válassza a **Kiállítandó tanúsítványsablon**.  

12. Az a **tanúsítványsablonok engedélyezése** párbeszédpanelen válassza ki az imént létrehozott, az új sablon **ConfigMgr Mac-ügyféltanúsítványa**, és válassza a **OK**.  

13. Ha nem kell további tanúsítványokat, zárja be létrehoznia és kiállítania **hitelesítésszolgáltató**.  

 A Mac ügyféltanúsítvány-sablonjához készen áll a kiválasztásra, amikor a beléptetéshez szükséges ügyfélbeállítások beállítása.

