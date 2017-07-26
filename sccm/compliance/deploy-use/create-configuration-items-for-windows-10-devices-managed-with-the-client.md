---
title: "Az ügyfél által felügyelt Windows 10 - Configuration Manager-konfigurációelemek létrehozása |} Microsoft Docs"
description: "Használatával a System Center Configuration Manager Windows 10 konfigurációelem beállításait a Configuration Manager-ügyfél által felügyelt Windows 10-es számítógépeken."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14226fbe-dd07-4432-910b-130790624a4e
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: e0a42a1d4706ab29617f3b6f8960ece27672908b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-windows-10-devices-managed-with-the-system-center-configuration-manager-client"></a>A System Center Configuration Manager-ügyfél által felügyelt Windows 10-eszközök konfigurációelemek létrehozása
A System Center Configuration Manager használata **Windows 10** konfigurációelemet használva felügyelheti a Configuration Manager-ügyfél által felügyelt Windows 10-számítógépeket.  
  
> [!IMPORTANT]  
>  Ebben a kiadásban, ha létrehozott egy **jelszó** típusú konfigurációelem részeként beállítás **Windows 10** (az eszköz a Configuration Manager-ügyféllel felügyelt), majd, ha a beállítás már nem létezik, vagy nincs konfigurálva a Windows 10-eszközön, akkor program helytelenül megfelelőnek értékeli azt.  
>   
>  A probléma elkerülése érdekében ezen eszközök beállításainak létrehozásakor ügyeljen arra, hogy a Konfigurációelem létrehozása varázsló beállítási lapjain be legyen jelölve a **Nem megfelelő beállítások szervizelése** jelölőnégyzet. Ezenfelül jelszóbeállításokkal rendelkező Windows 10-es konfigurációelemet tartalmazó referenciakonfiguráció telepítésekor az Alapkonfigurációk központi telepítése párbeszédpanelen jelölje be a **Nem megfelelő szabályok szervizelése (ha támogatott)** jelölőnégyzetet. Ezen a megoldás használata esetén a rendszer figyeli a beállítást, és javítja azt, ha nem bizonyul megfelelőnek. A szervizelés után a beállítást helyesen **Megfelelő** státuszúként jelenti a program (kivéve, ha problémát észlelt, ebben az esetben **Hiba**állapotot fog jelenteni).  
  
### <a name="to-create-a-windows-10-configuration-item"></a>Windows 10-konfigurációelem létrehozása  
  
1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.  
  
2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a **Megfelelőségi beállítások**csomópontot, majd kattintson a **Konfigurációelemek**lehetőségre.  
  
3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  
  
4.  A **Konfigurációelem létrehozása varázsló** **Általános**lapján adja meg a konfigurációelem nevét és leírását (utóbbi nem kötelező).  
  
5.  A **Határozza meg a létrehozandó konfigurációelem típusát**csoportban válassza a **Windows 10**elemet.  
  
6.  Kattintson a **kategóriák** Ha létrehozni és hozzárendelni kategóriákat szeretne kereséséhez és szűréséhez konfigurációs elemek a Configuration Manager konzolon.  
  
7.  A varázsló **Támogatott platformok** lapján jelölje ki azokat a Windows 10-platformokat, amelyek kiértékelik a konfigurációelemet.  
  
8.  A varázsló **Eszközbeállítások** lapján jelölje ki a konfigurálni kívánt beállításcsoportot. Ezután kattintson a [Tovább](#BKMK_Ref) gombra. A részleteket a témakör **Windows 10 configuration item settings reference**című szakaszában találja.  
  
    > [!TIP]  
    >  Ha nem találja a kívánt beállítást, jelölje be a **További olyan beállítások konfigurálása, amelyek nem találhatók meg az alapértelmezett beállítási csoportokban**jelölőnégyzetet.  
  
9. Minden egyes lapon adja meg a szükséges beállításokat, illetve azt, hogy szeretné-e őket kijavítani, ha nem felelnek meg az eszközök követelményeinek (ha ez a lehetőség támogatott).  
  
10. A beállításcsoportokban azt is megadhatja, hogy a nem megfelelőnek ítélt konfigurációelemek esetén a rendszer milyen súlyossági szintről küldjön Önnek értesítést:  
  
    -   **Nincs** – a megfelelőségi szabálynak eleget nem tevő eszközök nem kerül a hiba súlyossága a Configuration Manager-jelentések.  
  
    -   **Információ** – a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **információk** Configuration Manager jelentések.  
  
    -   **Figyelmeztetés** – a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **figyelmeztetés** Configuration Manager jelentések.  
  
    -   **Kritikus** – a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben.  
  
    -   **Kritikus eseménnyel** – a megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.  
  
11. A varázsló **Platform alkalmazhatósága** lapján áttekintheti azokat a beállításokat, amelyek nem kompatibilisek a korábban kiválasztott támogatott platformokkal. Visszaléphet, hogy eltávolítsa ezeket a beállításokat, vagy folytathatja a műveletet.  
  
    > [!TIP]  
    >  A nem támogatott beállítások megfelelőségét a rendszer nem ellenőrzi.  
  
12. Fejezze be a varázslót.  
  
 Az új konfigurációelemet az **Eszközök és megfelelőség** munkaterület **Konfigurációelemek** csomópontjában tekintheti meg.  
  
##  <a name="windows-10-configuration-item-settings-reference"></a>Windows 10 készült konfigurációelemek beállításainak ismertetése  
  
### <a name="password"></a>Jelszó  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Jelszóbeállítások megkövetelése az eszközökön**|Jelszó kérése a támogatott eszközökön.|  
|**Jelszó minimális hossza (karakter)**|A jelszó minimális hosszának karakterszáma.|  
|**Jelszó lejárati ideje napokban**|Azon napok száma, amely után a jelszót kötelező megváltoztatni.|  
|**Megjegyzett jelszavak száma**|Megakadályozza a korábbi jelszavak használatát.|  
|**Sikertelen bejelentkezési próbálkozások száma az eszköz törlése előtt**|Törli az eszközt a megadott számú sikertelen bejelentkezést követően.|  
|**Üresjárati idő után az eszköz zárolva van**|Megadja, hogy az eszköznek hány percig kell inaktívnak lennie az automatikus zároláshoz.|  
|**Jelszó bonyolultsága**|Kiválasztja, hogy megadhat-e PIN-kódot (pl. „1234”), vagy erős jelszót kell megadnia.|
|**Speciális karakterek száma által megkövetelt jelszó beállítása**|Ha kiválasztott egy **erős** jelszót, használja ezt a beállítást, konfigurálhatja a speciális karakterek száma szükséges. Egy erős jelszót, és ez kell állítani legalább **3** betűket és számokat tehát szükség. Válassza ki **4** Ha egy jelszót, amely ezen felül igényel, mint a speciális karakterek kikényszerítéséhez **(% $**.<br>(Csak Windows 10)  |
  
###  <a name="device"></a>Eszköz  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Bluetooth**|A Bluetooth funkció engedélyezése az eszközön.|  
  
### <a name="cloud"></a>Felhő  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Beállítások szinkronizálása**|Beállítások szinkronizálásának engedélyezése az eszközök között.|  
|**Hitelesítőadatok szinkronizálása**|A hitelesítő adatok szinkronizálásának engedélyezése az eszközök között.|  
|**Beállítások szinkronizálása forgalmi díjas kapcsolaton keresztül**|A beállítások szinkronizálásának engedélyezése, ha az internetkapcsolat forgalmi díjas.|  
  
### <a name="roaming"></a>Barangolás  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Adatroaming**|Hálózatok közötti barangolás engedélyezése adatok elérése közben.|  
  
### <a name="encryption"></a>Titkosítás  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Fájlok titkosítása az eszközön**|Az eszközön található összes fájlnak titkosítva kell lennie.|  
  
### <a name="system-security"></a>Rendszerbiztonság  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Felhasználói fiókok felügyelete**|A Windows felhasználói fiókok felügyeletének konfigurálása az eszközön.<br />Például letilthatja, vagy beállíthatja az értesítés szintjét.|  
|**Hálózati tűzfal**|A Windows tűzfal engedélyezése vagy letiltása.|  
|**SmartScreen**|A Windows SmartScreen engedélyezése vagy letiltása.|  
|**Vírusvédelem**|Megköveteli, hogy legyen konfigurált és telepített víruskereső szoftver.|  
|**A vírusvédelmi aláírások naprakészek**|Megköveteli, hogy az eszközön a víruskereső szoftver aláírás fájlok naprakészen kell lennie.|  
  
### <a name="windows-information-protection-wip"></a>A Windows információvédelem (folyamatban)

Ahogy a vállalaton belül egyre nő az alkalmazottak tulajdonában álló eszközök száma, úgy nő az adatok véletlen kiszivárgásának kockázata is az olyan alkalmazásokon és szolgáltatásokon keresztül, mint az e-mail, a közösségi média és a nyilvános felhő, amelyek fölött a vállalatnak nincs irányítási lehetősége. Olyan esetekről van szó, mint például amikor egy alkalmazott a személyes e-mail-fiókjából küldi el a legújabb tervrajzokat, termékadatokat másol be egy tweetbe, vagy a nyilvános felhőben található tárhelyére ment egy aktuális értékesítési jelentést.

A Windows információvédelem (korábbi nevén vállalati adatvédelem) segít védekezni az esetleges adatszivárgást, ellenkező esetben az alkalmazott munkavégzésébe zavarása nélkül. Befejezetlen is segít megvédeni a vállalati alkalmazások és adatok véletlenül kiszivárogjanak vállalati tulajdonú eszközök és személyes eszközök, alkalmazottak által munkába hozott nem igényel változtatásokat a környezetben vagy más alkalmazások.

 A Configuration Manager Windows Information Protection konfigurációs elemek a folyamatban, a vállalati hálózati helyek, a védelmi szintek és a titkosítási beállítások által védett alkalmazások kezelését.
  

A Windows információvédelem konfigurálásával a Configuration Managerrel kapcsolatos információkért lásd: [vállalati adatok védelme a Windows információk védelme (folyamatban)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
  
## <a name="see-also"></a>Lásd még:  
 [A System Center Configuration Manager-ügyféllel felügyelt eszközök konfigurációelemei](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md)

