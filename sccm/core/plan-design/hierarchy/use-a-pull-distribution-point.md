---
title: "Lekéréses terjesztési pont |} Microsoft Docs"
description: "Ismerje meg, valamint a lekéréses terjesztési pontok a System Center Configuration Manager használatára vonatkozó korlátozások."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d8f530b-1a39-4a9d-a2f0-675b516da7e4
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9b366262ae59a8cb57c0f1760b961194d17bcf52
ms.openlocfilehash: db5039ff6cb93e3099b096196d49a1f06c315a6b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="use-a-pull-distribution-point-with-system-center-configuration-manager"></a>Lekéréses terjesztési pont használata a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A lekéréses terjesztési pontok a System Center Configuration Manager normál terjesztési pontot, amely egy forráshelyről, például ügyfélről, ahelyett, hogy a tartalmat a helykiszolgálótól leküldve letöltésével olvassa be a terjesztett tartalom.  

 Ha a terjesztési pontok egy helyen sok Telepítse központilag a tartalmakat, a lekéréses terjesztési pontok segítségével, a helykiszolgáló feldolgozási terhelésének csökkentése és a tartalom átvitelét sebessége az egyes terjesztési pontokra. Ez a hatékonyság annak köszönhető, hogy az egyes terjesztési pontokra történő tartalomátvitel folyamatát nem a helykiszolgálón lévő terjesztéskezelő folyamat végzi.  

-   Konfigurálja az egyes terjesztési pontokat a lekéréses terjesztési pontok.  

-   Az egyes lekéréses terjesztési pontok meg kell adnia egy vagy több forrás terjesztési pontokat, amelyből az beszerezheti a központi telepítéseket (a lekéréses terjesztési pontok csak szerezhet be tartalmat egy terjesztési pontról, amely egy forrás terjesztési pontként van megadva).  

-   A lekéréses terjesztési pontra tartalom terjesztésekor a helykiszolgáló értesíti a lekéréses terjesztési pont, amely ezután kezdeményezi a forrásként szolgáló terjesztési pont a tartalom letöltését (átvitelét). A lekéréses terjesztési pont maga kezeli a tartalomátvitelt úgy, hogy letölti a tartalmat egy olyan terjesztési pontról, amely már rendelkezik a tartalom egy példányával.  

A lekéréses terjesztési pontok ugyanazokat a konfigurációkat és funkciókat jellemző a Configuration Manager terjesztési pontok támogatják. Így például lekéréses terjesztési pontként konfigurált terjesztési pont támogatja a csoportos küldés és a PXE-konfigurációk használatát, a tartalomérvényesítést, valamint az igény szerinti tartalomterjesztést. A lekéréses terjesztési pontok támogatják az ügyfelekkel való HTTP- vagy HTTPS-alapú kommunikációt, ugyanazokat a tanúsítványbeállításokat tartalmazzák, mint más terjesztési pontok, továbbá egyedileg vagy terjesztésipont-csoport részeként is kezelhetők.  

> [!IMPORTANT]
> Bár a lekéréses terjesztési pontok támogatják a kommunikációt a HTTP és HTTPS protokollt, a Configuration Manager használatakor, csak a HTTP-Kapcsolatra beállított forrás terjesztési pontok lehet megadni. A Configuration Manager SDK segítségével adja meg a forrásként szolgáló terjesztési pont, amely a HTTPS használatára konfigurált.  

 **Amikor lekéréses terjesztési pontra végez tartalomterjesztést, a következő eseményekre kerül sor:**  

-   Miután megtörtént a tartalom lekéréses terjesztési pontra történő terjesztése, a Package Transfer Manager a helykiszolgálón ellenőrzi a helyadatbázisban, hogy a tartalom elérhető-e forrásként szolgáló terjesztési ponton. Ha a tartalom nem érhető el a lekéréses terjesztési pont forrásként szolgáló terjesztési pontján, az ellenőrzés 20 percenként megismétlődik, amíg a tartalom elérhetővé nem válik.  

-   Amikor a Package Transfer Manager megbizonyosodott a tartalom elérhetőségéről, értesíti a lekéréses terjesztési pontot, hogy letöltheti a tartalmat. Amikor a lekéréses terjesztési pont megkapja ezt az értesítést, megpróbálja letölteni a tartalmat saját forrásként szolgáló terjesztési pontjairól.  

-   Miután a lekéréses terjesztési pont befejezte a tartalom letöltését, jelentést küld erről az állapotról egy felügyeleti pontnak. Ha 60 perc elteltével Ez az állapot nem érkezett, a Package Transfer Manager felébred, és győződjön meg arról, hogy a lekéréses terjesztési pont letöltötte-e a tartalom a lekéréses terjesztési pont ellenőrzi. Ha a tartalom letöltése éppen folyamatban van, a Package Transfer Manager további 60 percig alvó állapotban marad, mielőtt ismét ellenőrzi a lekéréses terjesztési pontot. A ciklus addig folytatódik, amíg a lekéréses terjesztési pont be nem fejezi a tartalomátvitelt.  

**A lekéréses terjesztési pont a terjesztési pont telepítésekor vagy azt követően konfigurálható** a terjesztési pont helyrendszerszerepkör tulajdonságainak szerkesztésével.  

**A lekéréses terjesztési pontként konfiguráció eltávolítása** a terjesztési pont tulajdonságainak szerkesztésével. Ha eltávolítja a lekéréses terjesztési pontként való beállítást, a terjesztési pont visszatér a normál működés, és a helykiszolgáló kezeli a jövőbeli tartalmat a terjesztési pontra továbbítja.  

## <a name="limitations-for-pull-distribution-points"></a>A lekéréses terjesztési pontok korlátozásai  

-   Felhőalapú terjesztési pont nem konfigurálható lekéréses terjesztési pontként.  

-   Helykiszolgálón lévő terjesztési pont nem konfigurálható lekéréses terjesztési pontként.  

-   **A manuális előkészítési konfiguráció felülírja a lekéréses terjesztési pont konfigurációját**. A manuálisan előkészített tartalomra konfigurált lekéréses terjesztési pont várakozik a tartalomra. Nem kér le tartalmat a forrásként szolgáló terjesztési pontról, és mint egy normál terjesztési pontot, amelyen a manuális előkészítési konfiguráció nem kap a helykiszolgálóról.  

-   **A lekéréses terjesztési pontok nem használnak sebességhatár-beállításokat** a tartalom átvitele során. Ha egy korábban telepített terjesztési pontot lekéréses terjesztési pontként konfigurál, a rendszer menti a sebességhatár-beállításokat, de nem használja őket. Ha később eltávolítja a lekéréses terjesztési pont konfigurációját, a sebességhatár-beállítások megvalósított korábban beállított.  

    > [!NOTE]  
    >  Ha egy terjesztési pontot lekéréses terjesztési pontként konfigurálnak, a **Sebességhatárok** lap nem látható a terjesztési pont tulajdonságai között.  

-   A lekéréses terjesztési pontok nem használják az **Ismétlés beállításai** lehetőséget a tartalomterjesztéshez. Az**Ismétlés beállításai** a **Szoftverterjesztési összetevő tulajdonságai** részeként konfigurálhatók az egyes helyekhez. Megtekintéséhez, vagy konfigurálja ezeket a tulajdonságokat a **felügyeleti** a Configuration Manager konzol munkaterületén bontsa ki a **Helykonfiguráció**, majd válassza ki **helyek**. Ezután az eredmények ablaktábláján jelöljön ki egy helyet, majd a a **Home** lapon jelölje be **Helyösszetevők**. Végül válassza ki **szoftverterjesztés**.  

-   Tartalom átvitele egy forrás terjesztési pont olyan távoli erdőbe, a számítógép, amely futtatja, a lekéréses terjesztési pont rendelkeznie kell a Configuration Manager-ügyfél telepítve. A hálózatelérési fiók a forrásként szolgáló terjesztési ponthoz hozzáférő használatra kell konfigurálni.  

-   Egy olyan számítógépen, van konfigurálva, a lekéréses terjesztési pont és a Configuration Manager-ügyfelet futtató, az ügyfél verzióját kell lennie, amely a lekéréses terjesztési pontot telepítő Configuration Manager-hely verziójával megegyező verzióra. Ez feltétele a lekéréses terjesztési pont használhassa a CCMFramework, amely a lekéréses terjesztési pont és a Configuration Manager-ügyfél egyaránt.  

## <a name="about-source-distribution-points"></a>Forrásként szolgáló terjesztési pontok  
 A lekéréses terjesztési pont konfigurálásakor egy vagy több, forrásként szolgáló terjesztési pontot kell megadni:  

-   Csak a forrásként szolgáló terjesztési pont szerepére alkalmas terjesztési pontok jelennek meg.  

-   Lekéréses terjesztési pont beállítható egy másik lekéréses terjesztési pont forrásként szolgáló terjesztési pontjaként.  

-   Csak a HTTP-t támogató terjesztési pontok is adhatók meg forrásként szolgáló terjesztési pontokat a Configuration Manager használatakor.  

-   A Configuration Manager SDK segítségével adja meg a forrásként szolgáló terjesztési pont, amely a HTTPS használatára konfigurált. A forrásként szolgáló terjesztési pont, amely a HTTPS használatára konfigurált használatához a lekéréses terjesztési pont közös elhelyezése szükséges a Configuration Manager-ügyfelet futtató számítógépen.  

A lekéréses terjesztési pontok forráslistáján szereplő terjesztési pontok mindegyikéhez prioritás rendelhető:  

-   Minden egyes forrásként szolgáló terjesztési ponthoz külön prioritás adható meg, illetve több elemhez is hozzárendelhető ugyanaz a prioritás.  

-   A prioritás határozza meg azt a sorrendet, amelyben a lekéréses terjesztési pont a tartalom lekérését végzi a forrásként szolgáló terjesztési pontoktól.  

-   A lekéréses terjesztési pont először a legalacsonyabb prioritással rendelkező forrásként szolgáló terjesztési ponthoz kapcsolódik.  Ha több forrásként szolgáló terjesztési ponthoz is azonos prioritás van beállítva, a lekéréses terjesztési pont véletlenszerűen kiválaszt közülük egyet.  

-   Ha a tartalom a kiválasztott forráson nem érhető el, a lekéréses terjesztési pont egy másik, azonos prioritással rendelkező terjesztési pontról próbálja meg letölteni a tartalmat.  

-   Ha az adott prioritással rendelkező terjesztési pontok egyike sem rendelkezik a tartalommal, a lekéréses terjesztési pont az eggyel magasabb prioritású terjesztési pontról vagy pontokról folytatja a letöltési kísérletet, amíg meg nem találja a tartalmat. Ellenkező esetben a lekéréses terjesztési pont 30 percig alvó állapotba lép, mielőtt újrakezdené a folyamatot.  

Amikor egy lekéréses terjesztési pont tartalmat tölt le egy forrásként szolgáló terjesztési pontról, a lekéréses terjesztési pont ügyfélként jelenik meg a **Terjesztési pontok használatának összegzése** jelentés **Elért ügyfelek (egyedi)** oszlopában.  

 Alapértelmezés szerint a lekéréses terjesztési pontok saját **számítógépfiókjukat** használják a forrásként szolgáló terjesztési pontról történő tartalomátvitelhez. A forrásként szolgáló terjesztési pontról, amely egy távoli erdőben lévő tartalmat a lekéréses terjesztési pont küld, ha az a lekéréses terjesztési pont mindig használja a hálózatelérési fiókot. Ehhez a folyamathoz szükséges, hogy a számítógép rendelkezik-e telepítve a Configuration Manager-ügyfél, és, hogy a hálózatelérési fiók konfigurálva legyen a használatra, és hozzáfér a forrásként szolgáló terjesztési ponthoz.  

## <a name="about-content-transfers"></a>Tartalomátvitel  
 A tartalomátvitel kezeléséhez, a lekéréses terjesztési pontok használatával a **CCMFramework** összetevőt a Configuration Manager ügyfélszoftver.  

-   Ezt a keretrendszert a **Pulldp.msi** a terjesztési pont lekéréses terjesztési pontként való konfigurálásakor. A keretrendszer a Configuration Manager-ügyfél nem igényel.  

-   A lekéréses terjesztési pont telepítését követően a terjesztési pont számítógépén futnia kell a CCMExec szolgáltatásnak, hogy a lekéréses terjesztési pont működjön.  

-   A lekéréses terjesztési pont a **háttérben futó intelligens átviteli szolgáltatás** (BITS) használatával végzi a tartalomátvitelt, működését pedig a **datatransferservice.log** és a **pulldp.log** fájlba naplózza a terjesztési pont számítógépén.  

## <a name="see-also"></a>További információ  
 [A System Center Configuration Manager tartalomkezelésének alapvető fogalmai](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)   

