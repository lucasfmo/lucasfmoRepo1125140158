---
title: "Windows-szolgáltatások támogatása |} Microsoft Docs"
description: "Ismerje meg, hogy mely Windows- és hálózati szolgáltatások a System Center Configuration Manager támogatja."
ms.custom: na
ms.date: 3/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: e040552dab21ba9a71e06a78f6acc2ffe1b0eb61
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="support-for-windows-features-and-networks-in-system-center-configuration-manager"></a>Támogatja a Windows-szolgáltatások és a hálózatok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör ismerteti a System Center Configuration Manager támogatja a közös Windows és a hálózati funkciók.  


##  <a name="bkmk_branchcache"></a> BranchCache  
Használhatja a Windows BranchCache a Configuration Manager BranchCache engedélyezéséhez a terjesztési pontokon, és az ügyfelek számára a BranchCache elosztott gyorsítótáras üzemmódban konfigurálásakor.

A BranchCache beállításai az alkalmazások, a különböző csomagok és a feladatütemezések központi telepítéséhez használhatók.  

A BranchCache követelményeinek teljesülése, esetén ez a funkció lehetővé teszi a távoli ügyfelek a tartalom beszerzését azokról a helyi ügyfelekről, amelyek gyorsítótárában elérhető a tartalom.  

Amikor például az első, BranchCache kezelésére képes ügyfélszámítógép tartalmat kér egy BranchCache-kiszolgálóként konfigurált terjesztési pontról, akkor az ügyfélszámítógép ezt a tartalmat letölti és gyorsítótárazza. Ez a tartalom elérhetővé válik, ehhez a tartalomhoz kért azonos alhálózaton található ügyfelek számára.

Ezek az ügyfelek szintén gyorsítótárba helyezik a tartalmat. Így az azonos alhálózatban lévő további ügyfeleknek nem kell letölteniük a tartalmat a terjesztési pontról, és a tartalom több ügyfélre is terjeszthető a későbbi átvitelek lehetővé tételéhez.  

**A BranchCache a Configuration Manager támogatására vonatkozó követelményeinek:**  
-   **Terjesztési pontok konfigurálása:**  
    Adja hozzá a **Windows BranchCache** funkciót a terjesztési pontként konfigurált helyrendszer-kiszolgálóhoz.    

    -   A BranchCache támogatására konfigurált kiszolgálón található terjesztési pontok esetében nincs szükség további konfigurációra.   
    -   Nem adható hozzá a Windows BranchCache felhőalapú terjesztési pontra, de a felhő alapú terjesztési pontok támogatják a le a tartalmat vannak konfigurálva a Windows BranchCache-ügyfelek által.  

-   **Ügyfelek konfigurálása:**    
    -   Az ügyfelek, amelyek támogatják a BranchCache szolgáltatást elosztott gyorsítótáras BranchCache-üzemmód kell állítani.  
    -   Az operációsrendszer-beállítása, a BITS-ügyfélbeállításokat a BranchCache támogatásához engedélyezni kell.   <br /> <br />
        
    Az ügyfelek támogatják a BranchCache szolgáltatást konfigurálásának információkért lásd: a [konfigurálja az ügyfeleket](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache#configure-clients-for-branchcache) szakasz [konfigurálása a BranchCache a Windows 10 frissítései](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache).


**A Configuration Manager támogatja a következő ügyféloldali operációs rendszerek a Windows BranchCache segítségével:**  

|Operációs rendszer|Támogatás részletei|  
|----------------------|---------------------|  
|Windows 7 SP1|Alapértelmezés szerint támogatott|  
|Windows 8|Alapértelmezés szerint támogatott|  
|Windows 8.1|Alapértelmezés szerint támogatott|  
|Windows 10|Alapértelmezés szerint támogatott|  
|Windows Server 2008 SP2|**Használatához BITS 4.0 szükséges**: A Configuration Manager-ügyfelek szoftverfrissítéseket és a szoftverterjesztés használatával telepítheti a BITS 4.0 kiadást. További információk a BITS 4.0-s kiadásról: [Windows Management Framework](http://go.microsoft.com/fwlink/p/?LinkId=181979).<br /><br /> Ezen az operációs rendszeren a BranchCache ügyfélfunkciói nem támogatottak a hálózatról futtatott szoftverterjesztés, illetve az SMB-fájlátvitel esetén. Ez az operációs rendszer nem képes továbbá használni a BranchCache funkcióit felhőalapú terjesztési pontokkal.|  
|Windows Server 2008 R2|Alapértelmezés szerint támogatott|  
|Windows Server 2012|Alapértelmezés szerint támogatott|  
|Windows Server 2012 R2|Alapértelmezés szerint támogatott|  

 További információkért a BranchCache szolgáltatásról tekintse meg a Windows Server dokumentáció [Windows rendszerhez készült BranchCache](http://go.microsoft.com/fwlink/p/?LinkId=177945) című részét.  

##  <a name="bkmk_Workgroups"></a>Munkacsoportban lévő számítógépek  
A Configuration Manager támogatja a munkacsoportokba tartozó ügyfeleket.  

-   A Configuration Manager támogatja az ügyfelek munkacsoportból egy munkacsoportból egy tartományba vagy egy tartományból egy munkacsoportba. További információkért lásd: [Configuration Manager-ügyfelek telepítése munkacsoporthoz tartozó számítógépeken](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup) a a [ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) témakör.  

> [!NOTE]  
>  A munkacsoportokba tartozó ügyfelek is támogatják, de minden helyrendszernek egy támogatott Active Directory-tartomány tagjai kell lennie.  


##  <a name="bkmmk_datadedup"></a> Adatdeduplikáció  
A Configuration Manager támogatja a terjesztésipontos adatdeduplikációt az alábbi operációs rendszereken:  

-   Windows Server 2012  

-   Windows Server 2012 R2  

> [!IMPORTANT]  
>  A csomagforrásfájlokat futtató kötet nem választható ki adatdeduplikálásra. Ennek az az oka az adatdeduplikáció újraelemzési pontokat használ, és a Configuration Manager nem támogatja a tartalom forráshelyeként használatát újraelemzési pontokon tárolt fájlokkal.  

További információkért lásd: [Configuration Manager terjesztési pontok és a Windows Server 2012 Data Deduplication](http://blogs.technet.com/b/configmgrteam/archive/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication.aspx) a Configuration Manager munkacsoportjának blogjából és [az Adatdeduplikáció áttekintése](http://technet.microsoft.com/library/hh831602.aspx) a Windows Server TechNet könyvtárban.  

##  <a name="bkmk_DA"></a> DirectAccess  
A Configuration Manager támogatja a DirectAccess szolgáltatást, a Windows Server 2008 R2 vagy újabb számára ügyfelei és helyrendszerei kiszolgáló közötti kommunikációt.  

-   Ha a DirectAccess összes követelményének mindegyike teljesül, a DirectAccess lehetővé teszi a Configuration Manager-ügyfelek az interneten keresztül kommunikálnak a hozzájuk rendelt helyen, mintha az intraneten.  

-   A kiszolgálók által kezdeményezett műveletek, például a távvezérlés vagy az ügyfelek leküldéses telepítése esetében a kezdeményező számítógépnek (például a helykiszolgálónak) IPv6-ot kell futtatnia, és az összes beavatkozó hálózati eszköznek is támogatnia kell ezt a protokollt.  

A Configuration Manager nem támogatja a következőket DirectAccess szolgáltatáson keresztül:  

-   Operációs rendszerek központi telepítése  

-   A Configuration Manager-helyek közötti kommunikáció  

-   Egy helyen belül a Configuration Manager helyrendszer-kiszolgálók közötti kommunikáció  

##  <a name="bkmk_dualboot"></a> Kétrendszeres számítógépek  
 A Configuration Manager nem tudja kezelni egy számítógépen egynél több operációs rendszert. Ha egynél több operációs rendszert egy olyan számítógépen, felügyelni, állítsa be úgy a felderítési és telepítési módszerek, amely segítségével győződjön meg arról, hogy a Configuration Manager ügyfél csak a felügyelni kívánt operációs rendszer telepítve van.  

##  <a name="bkmk_IPv6"></a>Az Internet Protocol version 6  
 Mellett az Internet Protocol version 4 (IPv4) a Configuration Manager támogatja az Internet Protocol version 6 (IPv6) a következő kivételekkel:  

|Funkció| Kivétel az IPv6-támogatás alól|  
|--------------|-------------------------------|  
|Felhőalapú terjesztési pontok|A Microsoft Azure és a felhőalapú terjesztési pontok támogatásához IPv4 szükséges.|  
|A Microsoft Intune és a Microsoft szolgáltatás-összekötője által regisztrált mobileszközök|A Microsoft Intune és a Microsoft szolgáltatás-összekötője által regisztrált mobileszközök támogatásához IPv4 szükséges.|  
|Hálózatfelderítés|A DHCP-kiszolgálók a Hálózatfelderítésben való keresésre konfigurálásakor IPv4 szükséges.|  
|Operációs rendszer központi telepítése|Az operációs rendszerek központi telepítésének támogatásához IPv4 szükséges.|  
|Ébresztési proxy kommunikációja|Az ügyfél ébresztési proxycsomagjainak támogatásához IPv4 szükséges.|  
|Windows CE|A Windows CE-eszközökön a Configuration Manager-ügyfél támogatásához IPv4 szükséges.|  

##  <a name="bkmk_NAT"></a> Hálózati címfordítás  
 Hálózati címfordítás (NAT) nem támogatott a Configuration Managerben, kivéve, ha a hely támogatja az interneten lévő ügyfeleket és az ügyfél nem észleli, hogy csatlakozik az internethez. Az internetalapú ügyfélfelügyelettel kapcsolatos további információkért lásd: [a System Center Configuration Manager internetalapú ügyfelei kezelésének tervezése](../../../core/clients/deploy/plan/plan-for-managing-internet-based-clients.md).  

##  <a name="bkmk_storage"></a> Speciális tárolótechnológiák  
 A Configuration Manager működéséről minden olyan hardverrel, amelyek rendelkeznek a Configuration Manager telepítve van az operációs rendszer verziója a Windows hardverkompatibilitási listája.

A helykiszolgálói szerepkörökhöz NTFS-fájlrendszer szükséges, hogy a könyvtár- és fájlengedélyek beállíthatóak legyenek. A Configuration Manager azt feltételezi, hogy teljes tulajdonjoggal rendelkezik a logikai meghajtó, mert a külön számítógépeken futó helyrendszerek nem osztható meg a logikai partícióval semmilyen tárolótechnológián. Azonban mindegyik számítógép használhat egy külön logikai partíciót egy megosztott tárolóeszköz ugyanazon fizikai partícióján.  

 **A támogatással kapcsolatos megfontolások:**  

-   **Tárolóhálózat**: Egy tárolóhálózat (SAN) akkor támogatott, ha egy támogatott Windows-alapú kiszolgáló közvetlenül csatlakozik a TÁROLÓHÁLÓZAT által futtatott kötetre.  

-   **Egypéldányos tárolás**: A Configuration Manager nem támogatja a terjesztési pont csomagok és aláírásmappák mappák konfigurációs Egypéldányos tárolás SIS-engedélyező köteteken.  

     A Configuration Manager-ügyfél gyorsítótárában ezenkívül nem támogatott SIS-engedélyező köteteken.  

-   **Cserélhető lemezmeghajtó**: A Configuration Manager nem támogatja a Configuration Manager helyrendszerei vagy az ügyfél telepítése egy cserélhető meghajtón.  

