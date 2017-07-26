---
title: "Helyrendszerszerepkörök előkészítése operációs rendszerek központi telepítése |} Microsoft Docs"
description: "A helyrendszer-szerepkörök konfigurálása, operációs rendszerek a System Center Configuration Manager telepítése előtt."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0ef5f3ce-b0e4-4775-b5c2-b245e45b4194
caps.latest.revision: 11
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 761c3f58f7c57d8f87ee802da37821895062546d
ms.openlocfilehash: 11c0f169afebdb071fefb5ce300fd1ae3481a94f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-site-system-roles-for-operating-system-deployments-with-system-center-configuration-manager"></a>Helyrendszerszerepkörök előkészítése az operációs rendszerek központi telepítéséhez a System Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager operációs rendszerek központi telepítéséhez, elő kell készítenie a következő hely helyrendszerszerepkörök, amelyekhez szükséges, specifikus konfigurációk és szempontokat.

##  <a name="BKMK_DistributionPoints"></a> Terjesztési pontok  
 A terjesztési pont helyrendszerszerepkör az ügyfelek által letölthető forrásfájlokat tartalmazza, például alkalmazástartalmat, szoftverfrissítéseket, operációs rendszerek lemezképeit és rendszerindító lemezképeket. A sávszélességhez tartozó, az ütemezési és egyéb beállításokkal szabályozhatja a tartalom terjesztését.  

 Fontos, hogy elegendő terjesztési ponttal rendelkezzen az operációs rendszerek számítógépekre történő központi telepítésének ellátásához. Emellett az is fontos, hogy körültekintően megtervezze ezeknek a terjesztési pontoknak az elhelyezkedését a hierarchiában. Látni fogja a legtöbb tervezéshez szükséges információk [tartalom és tartalomkezelési infrastruktúra kezelése](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md). Van azonban néhány további tervezési szempont is, amelyet az operációs rendszerek központi telepítésekor a terjesztési pontok kapcsán figyelembe kell venni.  

###  <a name="BKMK_AdditionalPlanning"></a> További szempontok terjesztési pontok tervezéséhez  
 A terjesztési pontok tervezése kapcsán a következő szempontokat kell még figyelembe venni:  

-   **Hogyan akadályozható meg az operációs rendszerek nem kívánt központi telepítése?**  

     A Configuration Manager nem tesz különbséget a Helykiszolgálók további célszámítógépei egy gyűjtemény. Ha olyan gyűjteményre telepít kötelező feladatütemezést, amelyikben helykiszolgáló is van, a helykiszolgáló ugyanúgy futtatja a feladatütemezést, mint a gyűjteményben lévő többi számítógép. Ügyeljen arra, hogy az operációs rendszerhez kapcsolódó központi telepítés olyan gyűjteményt használjon, amely a központi telepítéshez kijelölt ügyfeleket tartalmazza.  

     A magas kockázatú, feladatütemezéssel végzett központi telepítések működése felügyelhető. A magas kockázatú központi telepítés az, amelyik automatikusan megy végbe az ügyfélen, és adott esetben nem kívánt eredményeket okozhat. Ilyenek például a Kötelező célú, operációs rendszert központilag telepítő feladatütemezések. A nem kívánt magas kockázatú központi telepítés lehetőségének csökkentése érdekében különböző ellenőrzési beállításokat konfigurálhat a telepítésre. További információkért lásd: [magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

-   **Egyszerre hány számítógép kaphat operációsrendszer-képet egyetlen terjesztési pontról?**  

     A szükséges terjesztési pontok számának meghatározásakor figyelembe kell venni a terjesztési pont feldolgozási és lemez I/O-sebességét, a hálózaton rendelkezésre álló sávszélességet, valamint azt a hatást, amelyet a telepítőcsomag lemezképének nagysága jelent az erőforrásokra nézve. Például egy 100 megabájtos (MB) Ethernet hálózaton a 4 gigabájtos (GB) lemezkép csomagját egy óra alatt legfeljebb 11 számítógépen lehet feldolgozni, nem számítva a kiszolgáló egyéb erőforrási tényezőit.  

     `100 Megabits/sec = 12.5 Megabytes/sec = 750 Megabytes/min = 45 Gigabytes/hour = 11 images @ 4GB per image.`  

     Tehát ha egy operációs rendszert egy bizonyos számú számítógépre egy megadott időkereten belül kell telepíteni, a lemezkép csomagját megfelelő számú terjesztési pontra kell eljuttatni.  

-   **Az operációs rendszerek telepíthetők-e központilag terjesztési pontra?**  

     Az operációs rendszerek terjesztési pontra is telepíthetők központilag, de az operációsrendszer-képnek egy másik terjesztési pontról kell érkeznie.  

###  <a name="BKMK_PXEDistributionPoint"></a> Terjesztési pontok konfigurálása PXE kérelmek fogadásához  
 Operációs rendszerek központi telepítéséhez a Configuration Manager-ügyfelek, amelyek PXE rendszerindítási kérelmeket, konfigurálnia kell egy vagy több terjesztési pontot a PXE kérelmek fogadásához. Ha megfelelően konfigurált a terjesztési pontot, akkor az válaszol a PXE rendszerindítási kérelemre, és meghatározza a megfelelő elvégzendő központi telepítési műveletet.

> [!IMPORTANT]  
> A  [Központi Windows-telepítési szolgáltatásokat](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_WDS) minden PXE használatára beállított terjesztési ponton telepíteni kell.  

 A következő eljárás használható létező terjesztési pont úgy módosításához, hogy fogadja a PXE rendszerindítási kérelmeket. További információ új terjesztési pont telepítéséről: [Terjesztési pont telepítése vagy módosítása](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).  

#### <a name="to-modify-an-existing-distribution-point-to-accept-pxe-requests"></a>Létező terjesztési pont módosítása a PXE kérelmek fogadásához  

1.  Kattintson a Configuration Manager konzolon **felügyeleti**, bontsa ki a **áttekintése** kattintson **terjesztési pontok**.  

2.  Jelölje ki a konfigurálni kívánt terjesztési pontot, majd a **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**gombra.  

3.  A terjesztési pont tulajdonságok oldalán kattintson a **PXE** fülre. Válassza a **PXE-támogatás engedélyezése ügyfeleknek** lehetőséget a PXE adott terjesztési ponton való engedélyezéséhez.  

4.  A PXE engedélyezésének megerősítéséhez kattintson az **Igen** gombra a **Szükséges portok felülvizsgálata PXE-hez** párbeszédpanelen. A Configuration Manager automatikusan beállítja az alapértelmezett portokat a Windows tűzfalon. Ha más tűzfalat használ, manuálisan kell beállítania a portokat.  

    > [!NOTE]  
    >  Ha a Központi Windows-telepítési szolgáltatások (WDS) és a DHCP ugyanazon a kiszolgálón van telepítve, a WDS-t egy másik port figyelésére kell beállítania (ugyanis a DHCP ugyanazt a portot figyeli). További információk: [Figyelembe veendő szempontok, ha egyazon kiszolgálón WDS-t és DHCP-t is telepített](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_WDSandDHCP).  

5.  Ha szeretné aktiválni, hogy a Központi Windows-telepítési szolgáltatások (WDS) válaszoljon a PXE-kérelmekre, jelölje be **A bejövő PXE-kérésekre való válaszolás engedélyezése ennek a terjesztési pontnak** jelölőnégyzetet. Ezzel a beállítással engedélyezheti vagy letilthatja a szolgáltatást anélkül, hogy eltávolítaná a PXE funkciót a terjesztési pontról.  

6.  Válassza ki **Ismeretlen számítógépek támogatásának engedélyezése** operációs rendszerek központi telepítéséhez a Configuration Manager által nem kezelt számítógépekre.  

7.  A PXE típusú központi telepítések további biztonsága érdekében jelölje be a **Jelszó kérése, ha a számítógépek a PXE szolgáltatást használják**jelölőnégyzetet, és erős jelszót határozzon meg.  

8.  A **Felhasználó-eszköz kapcsolat** listában határozza meg, hogy a terjesztési pont a PXE típusú központi telepítéseknél hogyan társítson felhasználókat a célszámítógéphez.  

    -   Ha nem szeretne felhasználót társítani a célszámítógéphez, válassza a **Felhasználó-eszköz kapcsolat használatának tiltása** lehetőséget.  

    -   Válassza a **Felhasználó-eszköz kapcsolat engedélyezése manuális jóváhagyással** lehetőséget, hogy a felhasználók célszámítógéphez társításához várni kelljen egy rendszergazda jóváhagyására.  

    -   Válassza a **Felhasználó-eszköz kapcsolat engedélyezése automatikus jóváhagyással** lehetőséget, hogy a felhasználók célszámítógéphez társítását a rendszer automatikusan jóváhagyja.  

     További információkért lásd: [rendelje hozzá a felhasználókat a célszámítógéppel](../get-started/associate-users-with-a-destination-computer.md).  

9. Adja meg, hogy a terjesztési pont bármely hálózati interfész vagy csak bizonyos hálózati interfészek esetén válaszolhat a PXE-kérésekre. Ha azt választja, hogy a terjesztési pont csak bizonyos hálózati interfészeknek válaszoljon, akkor adja meg mindegyik hálózati interfész MAC-címét.  

10. Adja meg másodpercben, hogy a több PXE képességű terjesztési pont használatakor mennyi késleltetési idő legyen a számítógép kérelmére reagálás előtt.  

11. Kattintson az **OK** gombra a terjesztési pont tulajdonságainak frissítéséhez.  

###  <a name="BKMK_RamDiskTFTP"></a> A RamDisk TFTP blokkméretének és ablakméretének testreszabása PXE-képes terjesztési pontokon  
Testreszabhatja a RamDisk TFTP-blokkméret és a Configuration Manager verziója 1606, az ablak mérete, a PXE-képes terjesztési pontok verziótól kezdve. Ha testreszabta a hálózatot, akkor a rendszerindító lemezkép letöltése időtúllépési hiba miatt sikertelen lehet, ha a blokk vagy az ablak mérete túl nagy. A RamDisk TFTP blokkméretének és ablakméretének testreszabásával lehetővé válik a TFTP-forgalom optimalizálása, amikor PXE-t használ a konkrét hálózati követelmények teljesítésére.   
A leghatékonyabb konfiguráció meghatározásához tesztelje a testreszabott beállításokat a környezetében.  

-   **TFTP-blokkméret**: A blokkméret a kiszolgáló által (a tárgyalt RFC 2347 szabványnak megfelelően) a fájlt letöltő ügyfélre küldött adatcsomagok mérete. A nagyobb blokkméret lehetővé teszi a kiszolgáló számára, hogy kevesebb csomagot küldjön, így kevesebbet kell várakozni a kiszolgáló és az ügyfél közötti üzenetváltás miatti késésekre. A nagyobb blokkméret ugyanakkor töredezett csomagokat eredményezhet, amit a PXE-ügyfelek implementációjának többsége nem támogat.  

-   **TFTP-ablakméret**: TFTP egy visszaigazolási (ACK) csomagot igényel minden adatblokk küldött. A kiszolgáló egészen addig nem küldi el a következő blokkot a sorozatból, amíg meg nem kapja az előző blokk ACK-csomagját. A TFTP-ablak a Központi Windows-telepítési szolgáltatások egyik funkciója, amellyel meghatározható, hogy hány adatblokk tölt ki egy ablakot. A kiszolgáló közvetlenül egymás után küldi az adatblokkokat egészen addig, amíg az ablak megtelik, majd az ügyfél ACK-csomagot küld. Az ablak méretének növelésével csökkenthető az ügyfél és a kiszolgáló közötti üzenetváltás miatti várakozások száma, ezzel együtt pedig a rendszerindító lemezkép letöltésének teljes időtartama is.  


#### <a name="to-modify-the-ramdisk-tftp-window-size"></a>A RamDisk TFTP-ablakméret módosítása  

-   Egyéni RamDisk TFTP-blokkméret beállításához vegye fel a következő beállításkulcsot a PXE-képes terjesztési pontokon:  

     **Hely**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Név: RamDiskTFTPWindowSize  

     **Típus**: REG_DWORD  

     **Érték**: &lt;egyéni ablakméret >  

 Az alapértelmezett érték 1 (azaz 1 adatblokk tölti ki az ablakot).  

#### <a name="to-modify-the-ramdisk-tftp-block-size"></a>A RamDisk TFTP-blokkméret módosítása  

-   Egyéni RamDisk TFTP-blokkméret beállításához vegye fel a következő beállításkulcsot a PXE-képes terjesztési pontokon:  

     **Hely**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Név: RamDiskTFTPBlockSize  

     **Típus**: REG_DWORD  

     **Érték**: &lt;egyéni blokkméret >  

 Az alapértelmezett érték 4096 (4k).  


###  <a name="BKMK_DPMulticast"></a> Terjesztési pontok konfigurálása a csoportos küldés támogatásához  
 A Multicast (csoportos küldés) olyan hálózatoptimalizálási módszer, amelyet akkor használhat terjesztési pontokon, ha valószínűleg egyszerre több ügyfélgép is letölti ugyanazt az operációsrendszer-képet. A csoportos küldés használatakor egyidejűleg több számítógép is letöltheti ugyanazon operációs rendszer lemezképét, mivel azt a terjesztési pont küldi csoportosan ahelyett, hogy az adatok másolatát mindegyik ügyfélgéphez külön kapcsolaton kellene küldenie. A csoportos küldés támogatásához legalább egy terjesztési pontot kell konfigurálnia. További információkért lásd: [Windows központi telepítése a hálózaton keresztül használjon csoportos](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 Az operációs rendszer központi telepítése előtt konfigurálnia kell egy terjesztési pontot a csoportos küldés támogatására. A következő eljárással meglévő terjesztési pontot tud módosítani a csoportos küldés támogatására. Új terjesztési pont telepítésével kapcsolatos információkért lásd: [telepítse és konfigurálja a terjesztési pontok](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).

#### <a name="to-enable-multicast-for-a-distribution-point"></a>Csoportos küldés engedélyezése a terjesztési ponton  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  A **Felügyelet** munkaterületen bontsa ki az **Áttekintés**csomópontot, majd válassza a **Terjesztési pontok** csomópontot.  

3.  Válassza ki azt a terjesztési pontot, amelyet az operációs rendszer lemezképének csoportos küldéséhez használni kíván.  

4.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

5.  Válassza a **Csoportos küldés** lapot, és konfigurálja a következő beállításokat:  

    -   **A csoportos küldés**: Akkor válassza ezt a beállítást, a terjesztési pont csoportos küldéshez.  

    -   **Csoportos kapcsolat fiókja**: Adjon meg egy fiókot a helyadatbázishoz való kapcsolódáshoz.  

    -   **Csoportos Címbeállítások**: Adja meg az IP-címek a célszámítógépekre történő adatküldéshez. Alapértelmezés szerint az IP-cím olyan DHCP-kiszolgálótól kérhető le, amelyen engedélyezve van a csoportos címek terjesztése. A hálózati környezettől függően 239.0.0.0 és 239.255.255.255 közötti IP-címeket adhat meg.  

        > [!IMPORTANT]  
        >  Ezeknek az IP-címeknek elérhetőnek kell lenniük azokról a célszámítógépekről, amelyek az operációsrendszer-lemezképet kérik. Ez azt jelenti, hogy a célszámítógép és a helykiszolgáló közötti útválasztókat és tűzfalakat a csoportos küldési forgalom engedélyezésére kell konfigurálni.  

    -   **UDP-porttartomány**: Adja meg a célszámítógépekre történő adatküldéshez használt tartomány UDP-portok.  

        > [!IMPORTANT]  
        >  Ezeknek a portoknak elérhetőnek kell lenniük azokról a célszámítógépekről, amelyek az operációsrendszer-lemezképet kérik. Ez azt jelenti, hogy a célszámítógép és a helykiszolgáló közötti útválasztókat és tűzfalakat a csoportos küldési forgalom engedélyezésére kell konfigurálni.  

    -   **Ütemezett csoportos küldés engedélyezése**: Adja meg, hogy a Configuration Manager szabályozza, mikor kell elkezdeni az operációs rendszerek telepítését a célszámítógépekre. Kattintson az **Ütemezett csoportos küldés engedélyezése**elemre, majd adja meg a következő beállításokat.  

         Az a **munkamenet indításának késleltetése** adja meg, hány perc, a Configuration Manager vár, mielőtt reagálni az első telepítési kérésre.  

         Az a **munkamenet minimális mérete** adja meg, hány kérésnek kell érkeznie, mielőtt Configuration Manager az operációs rendszer központi telepítését megkezdené.  

    -   **Átviteli sebesség**: Történő a célszámítógépekre történő adatletöltéshez használt átviteli sebesség kiválasztására.  

    -   **Ügyfelek maximális**: Adja meg a célszámítógépeken, amelyek a terjesztési pontról töltheti le az operációs rendszer maximális számát.  

6.  Kattintson az **OK** gombra.  

##  <a name="BKMK_StateMigrationPoints"></a> Állapotáttelepítési pont  
 Az állapotáttelepítési pont tárolja azokat a felhasználói állapotadatokat, amelyeket az egyik számítógépről megszerzett, másik számítógépen helyreállított. Az olyan esetekben azonban, amikor ugyanarról a számítógépről rögzíti a felhasználó az operációs rendszer központi telepítésével kapcsolatos beállításait, például olyan környezetben, ahol frissíti az operációs rendszert a célszámítógépen, választhat, hogy az adatokat ugyanezen a számítógépen tárolja-e rögzített hivatkozások használatával, vagy pedig állapotáttelepítési pontot használ. Az egyes számítógépekre való központi telepítésre az állapottároló létrehozásakor a Configuration Manager automatikusan társítást hoz létre az állapottároló és a célszámítógép között. Az állapotáttelepítési pont tervezésekor vegye figyelembe a következő tényezőket.  

### <a name="user-state-size"></a>A felhasználói állapot mérete  
 A felhasználói állapot mérete közvetlen hatással van az állapotáttelepítési ponton a lemez tárolási igénybevételére és az áttelepítés során a hálózat teljesítményére. Vegye számításba a felhasználói állapot méretét és az áttelepíteni kívánt számítógépek számát. Foglalkozzon azzal is, hogy a számítógépről mely beállításokat kell áttelepíteni. Ha a **Dokumentumok** mappa például már rendelkezik biztonsági másolattal a kiszolgálón, lehet, hogy azt nem kell áttelepíteni a lemezkép telepítésének részeként. A felesleges áttelepítések érdekében a felhasználói állapotadatok összesített mérete lehet kisebb, és ez csökkenti azt a hatást, ami egyéként az állapotáttelepítési ponton a hálózati teljesítményt és a lemezhasználatot érintené.  

### <a name="user-state-migration-tool"></a>A Felhasználói állapot áttelepítését szolgáló eszköz  
 Az operációs rendszerek központi telepítése során szükséges felhasználói állapotadatok beolvasásához, valamint azok helyreállításhoz a Felhasználói állapot áttelepítését szolgáló eszköznek (USMT) az USMT forrásfájljaira mutató csomagját kell használni. A Configuration Manager automatikusan létrehozza ezt a csomagot a Configuration Manager konzolján a **szoftverkönyvtár** > **Alkalmazáskezelés** > **csomagok**. A Configuration Manager használ az operációs rendszer felhasználói állapotának rögzítésére, és majd annak visszaállítására egy másik operációs rendszer terjesztése a Windows Assessment and Deployment Kit (Windows ADK), az USMT 10.0.  

 Az USMT 10.0 különböző áttelepítési forgatókönyveinek leírását lásd: [Common Migration Scenarios](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)(Gyakori áttelepítési helyzetek).  

### <a name="retention-policy"></a>Adatmegőrzési házirend  
 Az állapotáttelepítési pont konfigurálásakor megadható, hogy mennyi ideig kell megőrizni a rajta tárolt felhasználói állapotadatokat. Az adatok megőrzési ideje az állapotáttelepítési ponton két szemponttól függ:  

-   Az a hatás, amelyik a lemez tárolási kapacitását befolyásolja.  

-   Az egyik követelmény lehet az, hogy az adatok megmaradjanak addig, amíg azokat újra át kell telepíteni.  

 A állapotáttelepítés két fázisban történik: Az adatok rögzítésével és az adatok helyreállítása. Az adatok rögzítésekor a rendszer az állapotáttelepítési ponton gyűjti össze és menti a felhasználói állapotadatokat. Az adatok helyreállításakor a felhasználói állapotadatok az állapotáttelepítési pontról lesznek lekérve, a célszámítógépre lesznek írva, majd a tárolt adatok zárolását a feladatütemezés **Állapot tárolásának felszabadítása** lépése fogja feloldani. A megőrzési idő az adatok zárolásának felszabadításakor kezdődik. Ha azt a lehetőséget választja, hogy rögtön törli az áttelepített adatokat, a felhasználói állapotadatok a felszabadításuk után rögtön törlődnek. Ha azt a lehetőséget választja, hogy bizonyos ideig megtartja az adatokat, az adatok akkor törlődnek, ha a felszabadításuk után a megadott idő lejár. Minél hosszabb megőrzési időt állít be, annál nagyobb lemezterületre lesz valószínűleg szüksége.  

### <a name="select-drive-to-store-user-state-migration-data"></a>Válassza ki a felhasználóáttelepítési adatok tárolására szolgáló meghajtót.  
 Az állapotáttelepítési pont konfigurálásakor meg kell adni a kiszolgálón az áttelepítéshez használt felhasználói állapotadatok tárolására szolgáló meghajtót. A meghajtó a meghajtók rögzített listájából választható ki. Előfordulhat azonban, hogy ezek közül néhány meghajtó nem írható meghajtót jelöl, például CD meghajtót vagy hálózati megosztás nélküli meghajtót. Az is lehet, hogy egyes meghajtói betűjelek nincsenek leképezve a számítógépen valamilyen meghajtóra. Az állapotáttelepítési pont konfigurálásakor csak írható, megosztott meghajtót szabad megadni.  

### <a name="configure-a-state-migration-point"></a>Állapotáttelepítési pont konfigurálása  
 Az alábbi módszerekkel konfigurálhat állapotáttelepítési pontot a felhasználói állapotadatok tárolására:  

-   A **Helyrendszer-kiszolgáló létrehozása varázslóval** hozzon létre egy új helyrendszer-kiszolgálót az állapotáttelepítési pont számára.  

-   A **Helyrendszer-szerepkörök hozzáadása varázslóval** vegyen fel egy állapotáttelepítési pontot egy meglévő kiszolgálóra.  

 A varázslók az alábbi adatok megadását kérik az állapotáttelepítési ponthoz:  

-   A felhasználói állapotadatok tárolására szolgáló mappákat.  

-   Az ügyfelek maximális számát, amelyek adatokat tárolhatnak az állapotáttelepítési ponton.  

-   A minimális szabad lemezterületet az állapotáttelepítési ponton a felhasználói állapotadatok tárolására.  

-   A szerepkörre vonatkozó törlési házirendet. Beállíthatja, hogy a rendszer azonnal, vagy adott nap elteltével törölje-e a felhasználói állapotadatokat, miután visszaállítja azt egy számítógépen.  

-   Azt, hogy az állapotáttelepítési pont csak a felhasználói állapotadatok visszaállítására irányuló kérelmekre válaszoljon-e. Ha ezt engedélyezi, az állapotáttelepítési pontot nem használhatja felhasználói állapotadatok tárolására.  

 A helyrendszerszerepkörök telepítésének lépéseit, lásd: [helyrendszer-szerepkörök hozzáadásához](../../core/servers/deploy/configure/add-site-system-roles.md).  

