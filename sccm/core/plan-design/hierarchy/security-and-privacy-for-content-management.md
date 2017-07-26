---
title: "Felügyeleti biztonsági és adatvédelmi |} Microsoft Docs"
description: "Biztonság és adatvédelem a System Center Configuration Manager tartalomkezelési optimalizálásához."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f38b726-dc00-433a-ba05-5b7dbb0d8e99
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 46af86ef8b18a8a7c4dfa593b3daf8235081b104
ms.openlocfilehash: c4b9d13079c313879c6d43b10867c616fa962668
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-content-management-for-system-center-configuration-manager"></a>A System Center Configuration Manager tartalomkezelésének biztonsága és adatvédelme

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a Tartalomkezelés a System Center Configuration Manager biztonsági és adatvédelmi tudnivalókat tartalmazza. Olvassa el ezeket a következő témakörökkel együtt:  

-   [Biztonság és adatvédelem a System Center Configuration Manager felügyelet](../../../apps/plan-design/security-and-privacy-for-application-management.md)  

-   [Biztonság és adatvédelem a szoftverfrissítéseket a System Center Configuration Managerben](/sccm/sum/plan-design/security-and-privacy-for-software-updates)  

-   [Biztonság és adatvédelem az operációs rendszer központi telepítéséhez a System Center Configuration Managerben](../../../osd/plan-design/security-and-privacy-for-operating-system-deployment.md)  

##  <a name="BKMK_Security_ContentManagement"></a> Ajánlott biztonsági eljárások a tartalomkezeléshez  
 Használja a tartalomkezelés biztonsági védelmének következő bevált gyakorlatát:  

 **A terjesztési pontokhoz az intraneten, fontolja meg a előnyeit és hátrányait, HTTPS és a HTTP**: A legtöbb esetben HTTP- és csomag-hozzáférési fiókok használata a hitelesítéshez nagyobb biztonságot nyújt attól az esettől HTTPS titkosítással de hitelesítés nélküli. Azonban, ha a tartalom olyan kényes adatokat tartalmaz, amelyeket az átvitelkor titkosítani kíván, használja a HTTPS protokollt.  

-   **Ha a HTTPS PROTOKOLLT használja a terjesztési pont**, a Configuration Manager nem használ csomag-hozzáférési fiókokat a tartalom elérésének hitelesítéséhez, de a tartalom titkosított a hálózaton keresztül átvitelekor.  

-   **Ha a terjesztési ponton HTTP protokollt használ**, csomaghozzáférési fiókokat is használhat a hitelesítéshez, a rendszer azonban titkosítás nélkül továbbítja a tartalmat a hálózatban.  


**Ha a terjesztési ponton nem önaláírt tanúsítványt, hanem nyilvános kulcsú (PKI) ügyfél-hitelesítési tanúsítványt használ, a tanúsítványfájlt (.pfx) erős jelszóval kell védeni. Ha a fájlt hálózaton tárolja, védeni a hálózati csatornát, amikor importálja a fájlt a Configuration Managerbe**: Ha jelszó kell a terjesztési pont által használt kommunikálni a felügyeleti pontok ügyfél-hitelesítési tanúsítvány importálásához, ez segít megvédeni a tanúsítványt a támadóktól. Megakadályozhatja, hogy a támadók illetéktelenül módosítsák a tanúsítványfájlt a a hálózati hely és a helykiszolgáló között használjon Server Message Block (SMB) aláírás vagy az IPsec.  

**Távolítsa el a terjesztési pont szerepkört a helykiszolgálóról**: Alapértelmezés szerint a terjesztési pont telepítve van a helyrendszer-kiszolgáló ugyanazon a kiszolgálón. Az ügyfélgépeknek nem kell közvetlenül a helykiszolgálóval kommunikálni, ezért a támadási felület csökkentése érdekében a terjesztési ponti szerepkört rendelje más helyrendszerekhez, és távolítsa el a terjesztési pontról.  

**A csomag-hozzáférési szint tartalmat biztonságos**: A terjesztési pont megosztása lehetővé teszi, hogy az olvasási hozzáférést minden felhasználó számára. Az egyes felhasználók tartalomhozzáférésének korlátozásához a csomaghozzáférési fiókokat kell használni, ha a terjesztési pontra a HTTP lett konfigurálva. Ez nem vonatkozik a felhő alapú terjesztési pontokra, amelyek nem támogatják a csomag-hozzáférési fiókokat. További információ a csomag-hozzáférési fiókokról: [tartalom eléréséhez fiókok kezelése](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).


**Ha a Configuration Manager telepíti az IIS a terjesztési pont helyrendszer-szerepkör hozzáadásakor, távolítsa el a HTTP-átirányítás vagy IIS-kezelés parancsfájljai és eszközei a terjesztési pont telepítésének befejezésekor**: A terjesztési pont nem követeli meg a HTTP-átirányítás vagy IIS-kezelés parancsfájljai és eszközei. A támadási felület csökkentése érdekében távolítsa el ezeket a szerepköri szolgáltatásokat a webkiszolgálói (IIS) szerepkörből.  A terjesztési pont a web server (IIS) szerepkörének szerepköri szolgáltatásairól kapcsolatos további információkért lásd: [hely és hely rendszerkövetelmények](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).  

**A csomaghozzáférési engedélyek beállítása a csomag létrehozásakor**: A hozzáférési fiókok számára a csomag fájljaihoz a módosítások érvénybe, csak akkor, ha újraterjeszti azt a csomagot, mert a csomag hozzáférési engedélyek beállítása gondosan a csomag első létrehozásakor. Ez különösen fontos, ha a csomag nagyméretű, ha több terjesztési pontra terjeszti, és ha a hálózat tartalomterjesztéshez igénybe vehető sávszélessége korlátozott.  

**Alkalmazzon hozzáférés-vezérlést a manuálisan előkészített tartalmat tartalmazó média védelméhez**: A manuálisan előkészített tartalom tömörített, de nincs titkosítva. Egy támadó elolvashatja és módosíthatja a fájlokat, amelyeket aztán az eszközök letöltenek. Configuration Manager-ügyfelek elutasítása illetéktelenül tartalmat, de még letöltik.  

**Manuálisan előkészített tartalom importálását azzal a ExtractContent parancssori eszközzel (ExtractContent.exe), amely rendelkezik a Configuration Managerrel, és győződjön meg arról, hogy a Microsoft által aláírt**: Illetéktelen módosítás és a jogok kiterjesztésének elkerülése érdekében csak a hitelesített parancssori eszközt használja, amely rendelkezik a Configuration Managerrel.  

**A kommunikációs csatornát a helykiszolgáló és a csomag forráshelye közötti**: Használja az IPsec vagy az SMB aláírásos a helykiszolgáló és a csomag forráshelye között alkalmazások és csomagok létrehozásakor. Ez segít megakadályozni a forrásfájlok támadó általi illetéktelen módosítását.  

**Ha módosítja a helykonfigurálási lehetőséget, hogy az alapértelmezett webhely helyett egyéni webhelyet használjon, valamelyik terjesztési ponti szerepkör telepítése után, távolítsa el az alapértelmezett virtuális könyvtárakat**: Amikor az alapértelmezett webhelyről egyéni webhely, a Configuration Manager nem távolítja el a régi virtuális könyvtárakat. Távolítsa el a Configuration Manager az alapértelmezett webhelyen eredetileg létrehozott virtuális könyvtárakat:  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**A felhő alapú terjesztési pontok védelme az előfizetési részleteket és tanúsítványokat**: Felhőalapú terjesztési pontok használatakor védelme az értékes elemek, beleértve a felhasználónevet és jelszót az Azure-előfizetéssel, az Azure felügyeleti tanúsítványhoz és a felhőalapú terjesztési pont szolgáltatási tanúsítványa. A tanúsítványokat tárolja biztonságosan, és ha azokat a felhő alapú terjesztési ponton böngészi, a helyrendszer-kiszolgáló és a forráshely között használja az IPsec vagy az SMB aláírásos protokollt.  

**A felhő alapú terjesztési pontok: A szolgáltatás folyamatossága érdekében figyelje a tanúsítványok lejárati idejét**: A Configuration Manager figyelmeztessen, ha az importált tanúsítványok kezelését a felhőalapú terjesztési pont szolgáltatások lejár. A lejárati dátumok egymástól függetlenül a Configuration Manager figyelni kell, és győződjön meg arról, hogy azt mindenképpen megújítani, majd a lejárat dátuma előtt importálni a az új tanúsítványok. Ez különösen fontos Ha megvásárolja a Configuration Manager felhő alapú terjesztési pont szolgáltatásának tanúsítványát külső hitelesítésszolgáltatótól (CA), mert szükség lehet további időt a megújított tanúsítvány megkapásához.  

 Ha a tanúsítványok valamelyike lejár, a felhőalapú szolgáltatások kezelője állít elő, az állapotüzenet azonosítója **9425** és a CloudMgr.log fájl tartalmaz egy, jelezve, hogy a tanúsítvány **lejárt állapotban van**, feltüntetve a lejárat dátumát is bejelentkezett UTC.  

## <a name="security-considerations-for-content-management"></a>Biztonsági megfontolások tartalomkezeléshez  
A Tartalomkezelés tervezése során, vegye figyelembe a következőket:  

-   Az ügyfelek nem ellenőrzik tartalmat, amíg nincs letöltve.  

     A Configuration Manager az ügyfelek ellenőrzik a tartalom kivonatát, csak azt követően, a rendszer letölti az ügyfél gyorsítótárában. Ha egy támadó illetéktelenül módosít a letöltendő fájlok listáját, vagy magán a tartalmon, a letöltési folyamat figyelemre méltóan nagy sávszélességet, csak hogy megsemmisítse a tartalmat, ha érvénytelen kivonatba ütközik az ügyfél is eltarthat.  

-   Felhő alapú terjesztési pontok használatakor a tartalom hozzáférése automatikusan Önök vállalatára korlátozódik, és azt Ön nem tudja tovább korlátozni kiválasztott felhasználókra vagy csoportokra.  

-   Felhőalapú terjesztési pontok használata esetén az ügyfelek a felügyeleti pont hitelesíti, és használhatja a Configuration Manager jogkivonat felhő alapú terjesztési pontok eléréséhez. A lexikális elem érvényes nyolc óra. Ez azt jelenti, hogy ha letilt egy ügyfelet, mert már nem megbízható, az továbbra is a tartalom letöltését a felhő alapú terjesztési pontok, amíg a token érvényességi időszaka lejárt. Ezen a ponton a felügyeleti pont nem ad ki másik tokent az ügyfélnek, mert az ügyfél blokkolva van.  

     A blokkolt ügyfél letöltésének 8-órán belüli megakadályozásához elkerülése érdekében állítsa le a felhőszolgáltatást a a **felhő** csomópont, **Hierarchiakonfiguráció**, a a **felügyeleti** munkaterület a Configuration Manager konzolon.  

##  <a name="BKMK_Privacy_ContentManagement"></a> Adatvédelmi információ a tartalomkezeléshez  
 A Configuration Manager nem vonatkozik semmilyen felhasználói adatot a tartalomfájlokba, bár egy rendszergazda felhasználó ehhez.  

 A tartalomkezelés konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

