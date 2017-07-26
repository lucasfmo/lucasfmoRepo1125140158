---
title: "SCEP-tanúsítványprofilok létrehozása |} Microsoft Docs"
description: "Útmutató a tanúsítványprofilokkal központilag felügyelt azokat a tanúsítványokat, a System Center Configuration Managerben van szükségük."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 634d612c-92d7-4c03-873a-b2e730c9a72d
caps.latest.revision: 16
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: aa8924a013ebdbee888cab33001fddbe7ad2d67e
ms.openlocfilehash: 80a716f5a42a81e5550eb1b5c7f14534e14a4fb7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="create-certificate-profiles"></a>Tanúsítványprofilok létrehozása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Tanúsítványprofilok használatával a Configuration Manager (SCCM) ellátja az felügyelt eszközöket a vállalati erőforrások eléréséhez szükséges tanúsítványokat. Tanúsítványprofilok létrehozása, előtt állítsa be a tanúsítvány-infrastruktúra, a [tanúsítvány-infrastruktúra beállítása a System Center Configuration Manager](certificate-infrastructure.md).  

Ez a témakör ismerteti a megbízható legfelső szintű és az SCEP-tanúsítványprofilok létrehozása. Ha azt szeretné, hogy PFX-tanúsítványprofilok létrehozása, lásd: [létrehozása PFX-tanúsítványprofilok](../../protect/deploy-use/create-pfx-certificate-profiles.md).


## <a name="create-a-new-certificate-profile"></a>Új Tanúsítványprofil létrehozásához  

### <a name="start-the-create-certificate-profile-wizard"></a>A Tanúsítványprofil létrehozása varázsló elindítása  

1.  A System Center Configuration Manager konzolon kattintson **eszközök és megfelelőség**.  

2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a **Megfelelőségi beállítások**, majd a **Hozzáférés a vállalati erőforrásokhoz**pontot, és kattintson a **Tanúsítványprofilok**lehetőségre.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Tanúsítványprofil létrehozása**elemre.  

### <a name="provide-general-information-about-the-certificate-profile"></a>A tanúsítványprofillal kapcsolatos általános adatok megadása  

A Tanúsítványprofil létrehozása varázsló **Általános** lapján adja meg az alábbi adatokat:  

-   **Név**: Adjon meg egy egyedi nevet a tanúsítványprofilnak. Legfeljebb 256 karakter használható.  

-   **Leírás**: Adjon meg egy leírást, amely áttekintést ad a tanúsítványprofilról, valamint más olyan releváns információkat, ami segít azonosítani a System Center Configuration Manager-konzolon. Legfeljebb 256 karakter használható.  

-   **Adja meg a létrehozni kívánt tanúsítványprofil típusát**: Válasszon egyet a következő tanúsítvány a profil típusa:  

-   **Megbízható Hitelesítésszolgáltatói tanúsítvány**: Válassza ezt a tanúsítványprofil-típust, ha azt szeretné, a megbízható legfelső szintű hitelesítésszolgáltató (CA) telepítéséhez vagy köztes Hitelesítésszolgáltatói tanúsítvány megbízható tanúsítványlánc kialakításához, amikor a felhasználók vagy eszközök egy másik eszközt kell hitelesítenie. Az eszköz lehet például RADIUS-kiszolgáló (Remote Authentication Dial-In User Service) vagy virtuális magánhálózati (VPN-) kiszolgáló. Emellett Egyszerű tanúsítványigénylési protokollt (SCEP) használó tanúsítványprofil létrehozása előtt is megbízható hitelesítésszolgáltatói tanúsítványprofilt kell konfigurálnia. Ebben az esetben a megbízható hitelesítésszolgáltatói tanúsítványnak a felhasználó vagy eszköz számára tanúsítványt biztosító hitelesítésszolgáltató megbízható legfelső szintű tanúsítványának kell lennie.  

-   **Egyszerű tanúsítványigénylési protokoll (SCEP) beállításai**: Válassza ki ezt a tanúsítványprofil-típust, ha azt szeretné, hogy egy felhasználó vagy eszköz tanúsítványt igényelni az egyszerű tanúsítványigénylési protokoll és a hálózati eszközök tanúsítványigénylési szolgáltatása szerepkör-szolgáltatás használatával.

-   **Személyes információk Exchange PKCS #12 (PFX) beállítások – importálás**: Válassza ezt a PFX-tanúsítvány importálásához. PFX-tanúsítvány létrehozása kapcsolatos információkért tekintse meg további [létrehozása PFX-tanúsítványprofilok](../../protect/deploy-use/create-pfx-certificate-profiles.md).



### <a name="configure-a-trusted-ca-certificate"></a>Megbízható Hitelesítésszolgáltatói tanúsítvány konfigurálása  

> [!IMPORTANT]  
>  SCEP-tanúsítványprofil létrehozása előtt be kell állítania legalább egy megbízható hitelesítésszolgáltatói tanúsítványprofilt.    
>  
>  Ha módosítja a következő értékek után a tanúsítvány van telepítve egy új tanúsítvány kérelmezése:
>  -  Adja meg a kulcs tárolása
>  -  Tanúsítványsablon neve
>  -  Tanúsítvány típusa
>  -  Tulajdonos nevének formátuma
>  -  Tulajdonos alternatív neve
>  -  Tanúsítvány érvényességi időtartama
>  -  Kulcshasználat
>  -  Kulcs mérete
>  -  Kibővített kulcshasználat
>  -  Legfelső szintű hitelesítésszolgáltató tanúsítványa

1.  A Tanúsítványprofil létrehozása varázsló **Megbízható hitelesítésszolgáltatói tanúsítvány** lapján adja meg az alábbi adatokat:  

 -   **Tanúsítványfájl**: Kattintson a **importálási** , majd keresse ki a használni kívánt tanúsítványfájlt.  

 -   **Céltár**: Több tanúsítványtárral rendelkező eszközökön válassza ki a tanúsítványt. Egy tárral rendelkező eszközök esetén a rendszer figyelmen kívül hagyja a beállítást.  

2.  A **Tanúsítvány ujjlenyomata** értékével ellenőrizheti, hogy a megfelelő tanúsítványt importálta-e.  


### <a name="configure-scep-certificate-information-only-for-scep-certificates"></a>(Csak SCEP-tanúsítványok) a SCEP-Tanúsítványadatok konfigurálása  

1.  A Tanúsítványprofil létrehozása varázsló **SCEP-kiszolgálók** lapján adja meg a Hálózati eszközök tanúsítványigénylési szolgáltatása (NDES) azon kiszolgálóinak URL-címeit, amelyek a tanúsítványokat kiállítják majd SCEP-n keresztül. Dönthet úgy, hogy automatikusan rendel hozzá egy NDES URL-címet a tanúsítványregisztrációs pont helyrendszer-kiszolgáló konfigurációja alapján, vagy hozzáadhat URL-címeket manuálisan.  

2.  Fejezze be a **SCEP-igénylés** a Tanúsítványprofil létrehozása varázsló oldalán.

 -  **Újrapróbálkozások**: Adja meg az eszköz automatikusan újrapróbálkozik a tanúsítványigénylés a hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgáló teljes száma. Ezzel a beállítással azok a helyzetek támogathatók, amelyekben az elfogadás előtt egy hitelesítésszolgáltató-kezelőnek kell jóváhagynia a tanúsítványkérelmet. A beállításra jellemzően fokozott biztonságú környezetekben, illetve akkor van szükség, ha nem vállalati, hanem független kiállító hitelesítésszolgáltatót használ. A beállítás továbbá tesztelési célra is használható a tanúsítványigénylési lehetőségek vizsgálatára, mielőtt a kiállító hitelesítésszolgáltató feldolgozza a tanúsítványkérelmet. Az **Újrapróbálkozási késleltetés (perc)** beállítással együtt használandó.  

 -   **Újrapróbálkozási késleltetés (perc)**: Adja meg az időköz percben, ha hitelesítésszolgáltató-kezelői jóváhagyást használ, mielőtt a kiállító hitelesítésszolgáltató feldolgozná a tanúsítványkérelmet egyes beléptetési kísérletek közötti. Ha tesztelési célból használ kezelői jóváhagyást, valószínűleg érdemes alacsony értéket megadnia, hogy a kérelem jóváhagyása után ne kelljen sokat várnia arra, hogy az eszköz újra tanúsítványt próbáljon igényelni. Ha azonban kezelői jóváhagyást használ éles hálózati környezetben, magasabb értéket lehet célszerű megadni, hogy elég idő álljon rendelkezésre a hitelesítésszolgáltatói rendszergazda számára a függőben lévő jóváhagyások ellenőrzésére és jóváhagyására.  

 -   **Megújítási küszöb (%)**: Adja meg, hogy az eszköz a tanúsítvány megújítását igényelje a tanúsítvány élettartamának hány százalékánál.  

 -   **(KSP) szolgáltató**: Adja meg a tanúsítványt a kulcs tárolására. Az alábbi értékek közül választhat:  

   -   **Telepítés platformmegbízhatósági modul (TPM), ha van**: Telepíti a kulcsot a TPM-be. Ha nincs TPM modul, a rendszer a szoftverkulcs társzolgáltatójába telepíti a kulcsot.  

   -   **Telepítés csak platformmegbízhatósági modul (TPM)**: Telepíti a kulcsot a TPM-be. Ha nincs TPM modul, a telepítés meghiúsul.  

   -   **Telepítés csak a Windows Hello for Business szolgáltatásba, másként meghibásodás történik**: Ez a beállítás a Windows 10 asztali és mobil eszközökhöz érhető el. Regisztrálja a kulcsot a **vállalati Windows Hello**, a leírt [üzleti beállításait a System Center Configuration Managerben a Windows Hello-](../../protect/deploy-use/windows-hello-for-business-settings.md). A beállítás a **Többtényezős hitelesítés megkövetelését** is lehetővé teszi az eszközök regisztrálásakor az adott eszközökre való tanúsítványkibocsátás előtt. További információ: [Többtényezős hitelesítés használata a Microsoft Intune-ban](https://technet.microsoft.com/library/dn889751.aspx) .

   > [!NOTE]  
   > 
   > Amikor egy felhasználó létrehoz egy Windows Hello for Business PIN-kódja, a Windows a Configuration Manager által figyelt az értesítést küld. Ez lehetővé teszi a Configuration Manager gyorsan értesülhet arról hogy mely felhasználók hozott létre a Windows Hello PIN-kód. A Configuration Manager majd is kiadhatnak új tanúsítványok azoknak a felhasználóknak a Windows Hello használata, a kulcstároló-szolgáltató egy.  

   -   **Telepítés Szoftverkulcstároló-Szolgáltatóba**: A szoftverkulcs társzolgáltatójába telepíti a kulcsot.  

 -   **Tanúsítványigénylés eszközei**: Ha a tanúsítványprofil központi telepítése egy felhasználói gyűjteménybe, válassza ki, hogy a tanúsítványigénylés engedélyezése csak a felhasználó elsődleges eszközén, vagy minden eszközön, amelyre a felhasználó bejelentkezik. A tanúsítványprofil eszközgyűjteménybe való telepítése esetén válassza ki, hogy csak az eszköz elsődleges felhasználója számára engedélyezi-e a tanúsítványigénylést, vagy minden felhasználó számára, aki az adott eszközre bejelentkezik.  

3.  A Tanúsítványprofil létrehozása varázsló **Tanúsítványprofilok** lapján adja meg az alábbi adatokat:  

 -   **Tanúsítványsablon neve**: Kattintson a **Tallózás** és válassza ki, amely a hálózati eszközök tanúsítványigénylési szolgáltatása használatára van konfigurálva, és egy kiállító Hitelesítésszolgáltatót bővült, amely a tanúsítványsablon nevét. Tanúsítványsablonok sikeres megtalálásához, a System Center Configuration Manager konzol futtatásához használt felhasználói fióknak rendelkeznie kell olvasási engedéllyel a tanúsítványsablonhoz. Ha a **Tallózás**nem használható, be is írhatja a tanúsítványsablon nevét.  

 > [!IMPORTANT]
 >   
 >  Ha a tanúsítványsablon neve nem ASCII-karaktereket is tartalmaz (például a kínai ábécéből), a rendszer nem telepíti a tanúsítványt. Ebben az esetben a tanúsítvány telepítéséhez először létre kell hoznia a tanúsítványsablon másolatát a hitelesítésszolgáltatón, majd át kell neveznie azt kizárólag ASCII-karakterek használatával.  

   Attól függően, hogy tallózással keresi meg a tanúsítványsablont, vagy begépeli a tanúsítvány nevét, ügyeljen az alábbiakra:  

 -   Ha tallózással jelöli ki a tanúsítványsablont, a rendszer a lap egyes mezőit automatikusan kitölti a tanúsítványsablonból. Ezek az értékek egyes esetekben csak másik tanúsítványsablon választásával módosíthatók.  

 -   Ha beírja a tanúsítványsablon nevét, ügyeljen arra, hogy a név pontosan azonos legyen a Hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgáló beállításjegyzékében szereplő névvel. A tanúsítványsablon valódi nevét adja meg, ne pedig a tanúsítványsablon megjelenített nevét.  

   A tanúsítványsablonok nevei kereséséhez keresse meg a következő kulcsot: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. Az **EncryptionTemplate**, a **GeneralPurposeTemplate**és a **SignatureTemplate**beállítások értékei a tanúsítványsablonokat jelölik. Alapértelmezés szerint mindhárom tanúsítványsablon értéke **IPSECIntermediateOffline**, amely az **IPSec (kapcsolat nélküli kérelem)**megjelenített sablonnévhez tartozik.  

   > [!WARNING]  
   > 
   >  System Center Configuration Manager nem tudja ellenőrizni a tanúsítványsablon tartalmát, amikor Tallózás helyett a tanúsítványsablon nevét, mert valószínűleg beállítások is választhatók, amely nem támogatja a tanúsítványsablont, és sikertelen tanúsítványigényléshez vezethet. Ha ez történik, a CPR.log fájlban a w3wp.exe bejegyzésnél egy hibaüzenet fog szerepelni, amely azt jelzi, hogy a tanúsítvány-aláírási kérelemben szereplő tanúsítványnév nem egyezik meg a kérdésben szereplő névvel.  
   >   
   >  Amikor beírja a **GeneralPurposeTemplate** értékéhez megadott tanúsítványsablon-nevet, a tanúsítványprofilhoz be kell jelölnie a **Kulcstitkosítás** és a **Digitális aláírás** beállításokat. Ha azonban csak a **Kulcstitkosítás** beállítást szeretné engedélyezni a tanúsítványprofilhoz, az **EncryptionTemplate** beállításkulcshoz tartozó tanúsítványsablon-nevet adja meg. Ha azonban csak a **Kulcstitkosítás** beállítást szeretné engedélyezni a tanúsítványprofilhoz, az **EncryptionTemplate** beállításkulcshoz tartozó tanúsítványsablon-nevet adja meg.  

 -   **Tanúsítvány típusa**: Adja meg, hogy egy eszköz vagy felhasználó számára telepíti a tanúsítványt.  
 -   **Tulajdonos nevének formátuma**: A listáról válassza ki, hogyan System Center Configuration Manager automatikusan hozza létre a tulajdonos nevét a tanúsítványkérelemben. Ha a tanúsítvány felhasználóhoz tartozik, a felhasználó e-mail címét is feltüntetheti a tulajdonos nevében. 
    
   > [!NOTE]  
   > 
   > Kiválasztása **IMEI-számmal** vagy **sorozatszám** lehetővé teszi a különböző ugyanaz a felhasználó tulajdonában lévő eszközök közötti különbséget. Például az eszközök tudta megosztani a köznapi nevet, de nem egy IMEI-számmal vagy sorozatszámot. Ha az eszköz nem készít jelentést az imei-Azonosítót vagy sorozatszámot, a tanúsítványt a köznapi nevet tartalmazó kell kiállítani.

 -   **Tulajdonos alternatív neve**: Adja meg, hogyan System Center Configuration Manager automatikusan hozza létre a tulajdonos alternatív neve (SAN) értékeit a tanúsítványkérelemben. Ha felhasználói tanúsítványtípust választott ki, akkor például az egyszerű felhasználónevet (UPN) is használhatja a tulajdonos alternatív neveként.  Ha az ügyféltanúsítványt fogja hitelesítésre használni egy hálózati házirend-kiszolgáló felé, a tulajdonos alternatív neveként az egyszerű felhasználónevet kell beállítania.  

   > [!NOTE]  
   >  - Az iOS rendszerű eszközök támogatják a korlátozott tulajdonosnév-formátumok és a tulajdonos alternatív nevének használatát az SCEP-tanúsítványokban. Ha nem támogatott formátumot ad meg, a rendszer nem igényel tanúsítványt iOS-alapú eszközökhöz. Amikor SCEP-tanúsítványprofil telepítését állítja be iOS-alapú eszközökre, a **Tulajdonos nevének formátuma** legyen **Köznapi név**, a **Tulajdonos alternatív neve**pedig legyen **DNS-név** , **E-mail cím** vagy **Egyszerű felhasználónév.**  

 -   **Tanúsítvány érvényességi időtartama**: A certutil - setreg Policy\EditFlags + a kiállító hitelesítésszolgáltató, amely lehetővé teszi az egyéni érvényességi időtartamot, a EDITF_ATTRIBUTEENDDATE parancs futtatásakor, meghatározhatja a tanúsítvány lejáratáig hátralévő időt. Ez a parancs kapcsolatos további információkért lásd: [tanúsítványinfrastruktúra a System Center Configuration Managerben](../../protect/deploy-use/certificate-infrastructure.md) témakör.  

   A megadott tanúsítványsablonban meghatározott érvényességi időszaknál rövidebb értéket is beállíthat, hosszabbat azonban nem. Ha például a tanúsítványsablonban két év van meghatározva a tanúsítvány érvényességi idejeként, akkor egy évet beállíthat értékként, öt évet azonban nem. Az érték is a kiállító hitelesítésszolgáltató tanúsítványának hátralévő érvényességi időszakánál alacsonyabbnak kell lennie.  

 -   **Kulcshasználat**: Adja meg a tanúsítvány kulcshasználati beállításait. Az alábbi lehetőségek közül választhat:  

        -   **Kulcstitkosítás**: Engedélyezi a kulcscserét, csak akkor, ha a kulcs titkosított.  

        -   **Digitális aláírás**: Engedélyezi a kulcscserét, csak akkor, ha a kulcs védelmét digitális aláírás segíti.  

   Ha a **Tallózás**funkcióval választott tanúsítványsablont, előfordulhat, hogy ezek a beállítások csak másik tanúsítványsablon választása esetén módosíthatók.  

   A kijelölt tanúsítványsablont a két fenti kulcshasználati beállítás közül az egyik vagy mindkettő használatával kell konfigurálni. Ha nem ez történik, **A CSR és az ellenőrző kérdés kulcshasználata nem egyezik** üzenet jelenik meg a tanúsítványregisztrációs ponthoz tartozó **Crp.log**naplófájlban.  


   -   **Kulcsméret (bit)**: Adja meg a kulcs bit.  

   -   **Kibővített kulcshasználat**: Kattintson a **válasszon** tanúsítványrendeltetéshez való adja hozzá a tanúsítványhoz tartozó értékeket. A legtöbb esetben a tanúsítványnál szükséges az **Ügyfél-hitelesítés** , hogy a felhasználó vagy az eszköz hitelesíthető legyen egy kiszolgálóval. Szükség szerint azonban tetszőleges más kulcshasználatot is felvehet.  


   -   **Kivonatoló algoritmus**: Válassza ki a tanúsítvánnyal használni kívánt elérhető kivonatoló algoritmus típusok egyikét. Válassza a kapcsolódó eszközöknél használható legerősebb biztonsági szintet.  

   > [!NOTE]  
   > 
   >  **Az SHA-2** támogatja az SHA-256, SHA-384 és SHA-512. Az**SHA-3** csak a következőt támogatja: SHA-3.  

   -   **Legfelső szintű hitelesítésszolgáltató tanúsítványának**: Kattintson a **válasszon** elemre olyan legfelső szintű Hitelesítésszolgáltatói tanúsítványprofil választásához, amelyet korábban konfigurált és központilag telepített a felhasználó vagy eszköz. Ennek a hitelesítésszolgáltatói tanúsítványnak a legfelső szintű tanúsítványnak kell lennie az adott tanúsítványprofilban konfigurált tanúsítványt kiállító hitelesítésszolgáltatónál.  

   > [!IMPORTANT]  
   >  Ha megad egy legfelső szintű Hitelesítésszolgáltatói tanúsítványt, amely a felhasználó vagy eszköz számára nincs telepítve, a System Center Configuration Manager nem fogja elindítani az adott tanúsítványprofilban konfigurált tanúsítványkérelmet.  


###  <a name="specify-supported-platforms-for-the-certificate-profile"></a>Támogatott platformok megadása a tanúsítványprofilról  

1. A Tanúsítványprofil létrehozása varázsló **Támogatott platformok** oldalán adja meg azokat az operációs rendszereket, amelyeken telepíteni szeretné a tanúsítványprofilt. Vagy kattintson az **Összes kiválasztása** elemre a tanúsítványprofil telepítéséhez az összes rendelkezésre álló operációs rendszeren.
2. Tekintse át a **összegzés** a varázsló oldalán válassza **Befejezés**. 
 
 
A tanúsítványprofil megjelenik a **Tanúsítványprofilok** csomópontja a **eszközök és megfelelőség** munkaterület, és a felhasználók vagy eszközök telepítésre kész [profilok a System Center Configuration Manager központi telepítése](deploy-wifi-vpn-email-cert-profiles.md).  
