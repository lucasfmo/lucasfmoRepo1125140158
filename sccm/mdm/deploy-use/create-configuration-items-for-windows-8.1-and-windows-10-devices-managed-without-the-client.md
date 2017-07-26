---
title: "Az Intune-nal felügyelt Windows 8.1 és Windows 10-eszközökhöz a konfigurációelemek létrehozása |} Microsoft Docs"
description: "Windows 10 rendszerű számítógépek beállításainak kezelését a System Center Configuration Manager Windows 10 konfigurációelem használatával."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23e1e4dc-623a-4521-ad04-ae9482927097
caps.latest.revision: 20
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: f75bac7887772119f30654fe15c16a8f993cad75
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-windows-81-and-windows-10-devices-managed-without-the-system-center-configuration-manager-client"></a>Konfigurációelemek létrehozása a System Center-ügyfél nélkül felügyelt Windows 8.1 és Windows 10 rendszerű eszközökhöz
||  
|-|  
|Ez a cikk kapcsolatos információkat tartalmaz [1602-es verziójában bevezetett új funkciókkal](https://technet.microsoft.com/library/mt622084.aspx) a System Center Configuration Manager \(aktuális ág\). Az új funkciók használatához [telepítenie kell az 1602-es frissítést](https://technet.microsoft.com/library/mt607046.aspx). Ha még nem frissített a legfrissebb Configuration Manager verzióra, akkor [töltse le az Ön által használt verzióhoz dokumentációjában](https://gallery.technet.microsoft.com/Documentation-for-System-ea90eaf1) a TechNet galériából.|  
  
 A System Center Configuration Manager használata**Windows 8.1 és Windows 10** konfigurációelemével egyszerűen kezelheti a Windows 8.1-és a Microsoft Intune vagy a helyszínen felügyelt regisztrált a Configuration Manager által a Windows 10-eszközökre.  
  
### <a name="to-create-a-windows-81-and-windows-10-configuration-item"></a>Windows 8.1 és Windows 10 konfigurációelem létrehozása  
  
1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség**.  
  
2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a **Megfelelőségi beállítások**csomópontot, majd kattintson a **Konfigurációelemek**lehetőségre.  
  
3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  
  
4.  A **Konfigurációelem létrehozása varázsló** **Általános** lapján adja meg a konfigurációelem nevét, és nem kötelezően leírást is megadhat hozzá.  
  
5.  A **Határozza meg a létrehozandó konfigurációelem típusát** csoportban válassza a **Windows 8.1 és Windows 10** elemet.  
  
6.  Kattintson a **kategóriák** Ha létrehozni és hozzárendelni kategóriákat szeretne kereséséhez és szűréséhez konfigurációs elemek a Configuration Manager konzolon.  
  
7.  A varázsló **Támogatott platformok** lapján jelölje ki azokat a Windows-platformokat, amelyek kiértékelik a konfigurációelemet.  
  
8.  A varázsló **Eszközbeállítások** lapján jelölje ki a konfigurálni kívánt beállításcsoportot. Részletekért tekintse meg ezen témakör [A Windows 8.1 és Windows 10 rendszerű eszközökhöz készült konfigurációelemek beállításainak ismertetése](#BKMK_Setref) című szakaszát, majd kattintson a **Tovább** gombra.  
  
    > [!TIP]  
    >  Ha nem találja a kívánt beállítást, jelölje be a **További olyan beállítások konfigurálása, amelyek nem találhatók meg az alapértelmezett beállítási csoportokban jelölőnégyzetet**.  
  
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
  
##  <a name="windows-81-and-windows-10-configuration-item-settings-reference"></a>A Windows 8.1 és Windows 10 rendszerű eszközökhöz készült konfigurációelemek beállításainak ismertetése  
  
### <a name="password"></a>Jelszó  
 Ezek csak a Windows 10-et és újabb rendszereket futtató eszközök beállításai.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Jelszóbeállítások megkövetelése az eszközökön**|Jelszó kérése a támogatott eszközökön.|  
|**Jelszó minimális hossza (karakter)**|A jelszó minimális hossza.|  
|**Jelszó lejárati ideje napokban**|Azon napok száma, amely után a jelszót kötelező megváltoztatni.|  
|**Megjegyzett jelszavak száma**|Megakadályozza a korábban használt jelszavak használatát.|  
|**Sikertelen bejelentkezési próbálkozások száma az eszköz törlése előtt**|A megadott számú sikertelen bejelentkezési kísérlet után törli az eszközt.|  
|**Üresjárati idő után az eszköz zárolva van**|Adja meg, hogy az eszköz mennyi ideig maradhat tétlen (felhasználói beavatkozás nélkül), mielőtt a zárolás aktiválódna.|  
|**Jelszó bonyolultsága**|Kiválasztja, hogy megadhat-e PIN-kódot (pl. „1234”), vagy erős jelszót kell megadnia.|  
|**Jelszó minősége**|Válassza ki a jelszó erősségének szintjét, valamint hogy használható-e biometrikus eszköz.|  
|**Jelszó-helyreállítási PIN küldése az Exchange Server-kiszolgálónak**||  
  
###  <a name="device"></a>Eszköz  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Képernyőfelvétel**|Képernyőképek készítésének engedélyezése az eszköz kijelzőjéről.<br /><br /> (Csak Windows 10)|  
|**Diagnosztikai adatok beküldése**|Engedélyezi az alkalmazások naplófájljainak elküldését.<br /><br /> (Csak Windows 8.1)|  
|**Diagnosztikai adatok beküldése (Windows 10)**|Engedélyezi az alkalmazások naplófájljainak elküldését.<br /><br /> (Csak Windows 10)|  
|**Földrajzi hely**|Engedélyezi a helymeghatározási szolgáltatások adatainak használatát az eszköz számára.<br /><br /> (Csak Windows 10)|  
|**Másolás és beillesztés**|Az adatok alkalmazások közötti átviteléhez használja a másolás és beillesztés funkciót.<br /><br /> (Csak Windows 10)|
|**Gyári beállítások visszaállítása**|Lehetővé teszi, hogy a végfelhasználó visszaállítja az eszköz kezdeti beállításait.<br /><br /> (Csak Windows 10)|  
|**Bluetooth**|Engedélyezi az eszközök Bluetooth-képességének használatát.|  
|**Bluetooth-észlelhetőség**|Az eszköz más Bluetooth-eszközök általi felderítésének engedélyezése.<br /><br /> (Csak Windows 10)|  
|**Bluetooth-hirdetés**|A Bluetooth-hirdetés használatának engedélyezése.<br /><br /> (Csak Windows 10)|  
|**Hangrögzítés**|Az eszköz hangrögzítési funkciói használatának engedélyezése.<br /><br /> (Csak Windows 10)|
|**A Cortana**|A Cortana beszédfelismerési asszisztens használatának engedélyezése.<br /><br /> (Csak Windows 10)|
|**Műveletközpont értesítéseinek**|Engedélyezi vagy letiltja a Windows 10-es az értesítési ablaktáblát. <br /><br /> (Csak Windows 10)|
  
### <a name="email-management"></a>E-mailek kezelése  
 Ezek a Windows 8.1 és Windows 10 rendszerű eszközök beállításai.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**POP és IMAP levelezés**|A POP és IMAP szabványokat használó e-mail fiókokhoz való csatlakozás engedélyezése.|  
|**E-mailek megtartásának maximális időtartama**|Ennyi idő után törli a rendszer az e-maileket a kiszolgálóról.|  
|**Engedélyezett üzenetformátumok**|Megadhatja, hogy az e-mailek HTML formátumúak is lehetnek-e, vagy csak egyszerű szövegek.|  
|**Egyszerű szöveges e-mailek maximális mérete (automatikusan letöltött)**|Szabályozza az egyszerű szöveges e-mailek maximális méretét automatikus letöltés esetén.|  
|**HTML formátumú e-mailek maximális mérete (automatikusan letöltött)**|Szabályozza a HTML formátumú e-mailek maximális méretét automatikus letöltés esetén.|  
|**Mellékletek maximális mérete (automatikusan letöltött)**|Beállítja az automatikusan letöltött e-mailek maximális méretét.|  
|**Naptár szinkronizálása**|A naptárak szinkronizálásának engedélyezése az eszközzel.|  
|**Egyéni e-mail fiók**|A nem Microsoft-fiókok használatának engedélyezése az eszközön.|  
|**A Microsoft-fiók választhatóvá tétele a Windows Mail alkalmazásban**|A beállítás engedélyezése esetén nem kötelező Microsoft-fiókot használni a Windows Posta alkalmazásban.|  
  
### <a name="store"></a>Áruház  
 Ezek csak a Windows 10-et és újabb rendszereket futtató eszközök beállításai.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Alkalmazás-áruház**|Hozzáférés engedélyezése az alkalmazásáruházhoz az eszközön.|  
|**Adjon meg egy jelszót az alkalmazásáruházhoz való hozzáféréshez**|A felhasználóknak meg kell adniuk egy jelszót az alkalmazásáruházhoz való hozzáféréshez.|  
|**Alkalmazáson belüli vásárlások**|Az alkalmazásokon belüli vásárlás engedélyezése a felhasználók számára.|  
  
### <a name="browser"></a>Böngésző  
 Ezek a Windows 8.1 és Windows 10 rendszerű eszközök beállításai.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Webböngésző engedélyezése**|Engedélyezi a webböngésző használatát az eszközön.|  
|**Automatikus kitöltés**|A felhasználók módosíthatják a böngésző automatikus kiegészítési funkciójának beállításait.|  
|**Active scripting**|A böngésző futtathat parancsfájlokat (pl. Active X-parancsfájlok).|  
|**Beépülő modulok**|A felhasználók hozzáadhatnak beépülő modulokat az Internet Explorerhez.|  
|**Előugróablak-blokkoló**|A böngésző előugróablak-blokkolójának engedélyezése vagy letiltása.|  
|**Cookie-k**|A cookie-k mentésének engedélyezése az eszközön.|  
|**Hamis figyelmeztetés**|A potenciálisan rosszindulatú webhelyekről szóló figyelmeztetések engedélyezése vagy letiltása.|  
  
###  <a name="internet-explorer"></a>Internet Explorer  
 Ezek a Windows 8.1 és Windows 10 rendszerű eszközök beállításai.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**A Nyomkövetés tiltása fejléc elküldése mindig**|Megakadályozza az adatok elküldését harmadik féltől származó webhelyek számára.|  
|**Intranet biztonsági zóna**|Biztonsági szintet rendelhet az intranetes biztonsági zónához.|  
|**Az Internet zóna biztonsági szintje**|Beállíthatja az internet zóna biztonsági szintjét.|  
|**Biztonsági szint az intranet zóna részére**|Beállíthatja az intranet zóna biztonsági szintjét.|  
|**Biztonsági szint a megbízható helyek zóna részére**|Beállíthatja a megbízható helyek zóna biztonsági szintjét.|  
|**Biztonsági szint a tiltott helyek zóna részére**|Beállíthatja a tiltott helyek zóna biztonsági szintjét.|  
|**Névterek az intranet zóna részére**|Beállíthatja az intranetes zónához hozzáadni vagy onnan eltávolítani kívánt webhelyeket.|  
|**Ugrás az intraneti helyre egyetlen szó beírásához**|Annak a beállításnak az engedélyezése vagy letiltása, amely engedélyezi az Internet Explorer számára, hogy automatikusan átugorjon egy intranetes webhelyre, ha érvényes helynevet ír be a felhasználó a HTTP: előtag nélkül.|  
|**Vállalati üzemmód menüopciója**|Engedélyezi a felhasználók számára, hogy aktiválják vagy inaktiválják a vállalati üzemmódot az Internet Explorer **Eszközök** menüjéből.|  
|**Naplózási jelentés helye (URL-cím)**|Megadhatja azt az URL-címet, ahol a webhelyek naplózása történik, ha a Vállalati üzemmód aktív.|  
|**A vállalati üzemmód helylistájának helye (URL)**|Megadhatja azon webhelyek listájának helyét, amelyek a Vállalati üzemmódot használják, ha az aktív.|  
  
###  <a name="cloud"></a>Felhő  
 Ezek a Windows 8.1 és Windows 10 rendszerű eszközök beállításai.  
  
|Beállítás neve|Részletek|Windows 8.1|Windows 10|  
|------------------|-------------|-----------------|----------------|  
|**Beállítások szinkronizálása**|Beállítások szinkronizálásának engedélyezése az eszközök között.|Igen|Igen|  
|**Hitelesítőadatok szinkronizálása**|A hitelesítő adatok szinkronizálásának engedélyezése az eszközök között.|Igen|Igen|  
|**Microsoft-fiók**|Microsoft-fiókok használatának engedélyezése az eszközön.|Igen|Igen|  
|**Beállítások szinkronizálása forgalmi díjas kapcsolaton keresztül**|A beállítások szinkronizálásának engedélyezése, ha az internetkapcsolat forgalmi díjas.|Igen|Igen|  
  
###  <a name="security"></a>Biztonság  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Aláíratlan fájltelepítés**|A nem aláírt fájlok betöltésének engedélyezése.<br /><br /> (Csak Windows 10)|  
|**Aláíratlan alkalmazások**|A nem aláírt alkalmazások betöltésének engedélyezése.<br /><br /> (Csak Windows 10)|  
|**SMS- és MMS-üzenetek**|SMS- és MMS-üzenetek küldésének engedélyezése az eszközről.<br /><br /> (Csak Windows 10)|  
|**Cserélhető tároló**|Cserélhető tárolók (pl. SD-kártya) használatának engedélyezése az eszközön.<br /><br /> (Csak Windows 10)|  
|**Fényképezőgép**|Engedélyezi az eszköz kamerájának használatát.<br /><br /> (Csak Windows 10)|  
|**Kis hatótávolságú kommunikáció (NFC)**|Az NFC segítségével végzett kommunikáció engedélyezése az eszközön.<br /><br /> (Csak Windows 10)|  
|**Lopásgátló üzemmód**|Itt adható meg, hogy engedélyezve van-e a Windows 10 lopásgátló üzemmódja.<br /><br /> (Csak Windows 10)|  
|**USB-kapcsolat engedélyezése**|Lehetővé teszi, hogy az eszközök az eszközt USB kapcsolaton keresztül csatlakozni.<br /><br /> (Csak Windows 10)|
|**Profilfájl**|A Windows RT-alapú eszközök VPN-profilját hozza létre.<br /><br /> Csak Windows 8.1)|  
|**Profilnév**|A Windows RT-alapú eszközök VPN-profilját hozza létre.<br /><br /> Csak Windows 8.1)|  
|**Profil minden felhasználóhoz**|A Windows RT-alapú eszközök VPN-profilját hozza létre.<br /><br /> Csak Windows 8.1)|  
  
###  <a name="peak-synchronization"></a>Csúcsidőszak szinkronizálása  
 Ezek csak a Windows 10-et és újabb rendszereket futtató eszközök beállításai.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Csúcsidő megadása**|Csúcsidőszakot állíthat be a mobileszköz szinkronizálásához.|  
|**Csúcsidőszak szinkronizálási gyakorisága**|Beállíthatja, hogy milyen gyakran történjen szinkronizálás a konfigurált csúcsidőszakban.|  
|**Csúcsidőszakon kívüli szinkronizálás gyakorisága**|Beállíthatja, hogy milyen gyakran történjen szinkronizálás a konfigurált csúcsidőszakon kívül.|  
  
###  <a name="roaming"></a>Barangolás  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Eszköz felügyelete barangolás közben**|Lehetővé teszi az eszköz a Configuration Manager által kezelhető roaming esetén.<br /><br /> (Csak Windows 10)|  
|**Szoftverletöltés barangolás közben**|Alkalmazások és szoftverek letöltésének engedélyezése barangolás közben.<br /><br /> (Csak Windows 10)|  
|**E-mailek letöltése barangolás közben**|E-mailek letöltésének engedélyezése barangolás közben.<br /><br /> (Csak Windows 10)|  
|**Adatroaming**|Hálózatok közötti barangolás engedélyezése adatok elérése közben.| 
|**Mobilhálózati VPN**|Lehetővé teszi, hogy az eszköz VPN-kapcsolatok Ha mobilhálózathoz csatlakozik.<br /><br /> (Csak Windows 10)|
|**VPN mobilhálózati roaming esetén**|Lehetővé teszi, hogy a VPN-eszköz kapcsolatok mobilhálózati roaming közben.<br /><br /> (Csak Windows 10)| 
  
###  <a name="encryption"></a>Titkosítás  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Memóriakártya titkosítása**|Az eszközhöz használt minden tárolókártyának titkosítva kell lennie.<br /><br /> (Csak Windows 10)|  
|**Fájlok titkosítása az eszközön**|Az eszközön található összes fájlnak titkosítva kell lennie.|  
|**E-mail aláírásának igénylése**|E-mailek aláírásának megkövetelése azok elküldéséhez.|  
|**Aláíró algoritmus**|Az aláíró algoritmus kiválasztása az aláírt e-mailekhez.|  
|**E-mail titkosításának igénylése**|E-mailek titkosításának megkövetelése azok elküldéséhez.|  
|**Titkosítási algoritmus**|Az e-mailek titkosításához használt algoritmus kiválasztása.|  
  
###  <a name="wireless-communications"></a>Vezeték nélküli kommunikáció  
 Ezek csak a Windows 10-et és újabb rendszereket futtató eszközök beállításai.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Vezeték nélküli hálózati kapcsolat**|Az eszközök Wi-Fi képességének engedélyezése vagy letiltása.|  
|**Wi-Fi tethering**|Engedélyezi a felhasználók számára, hogy mobil elérési pontként használják eszközeiket.|  
|**Adatok kiszervezése Wi-Fi-re, amikor lehetséges**|Ezzel a beállítással az eszköz minden lehetséges esetben a Wi-Fi-kapcsolatot fogja használni.|  
|**Wi-Fi elérési pont jelentése**||  
|**Manuális Wi-Fi konfiguráció**||  
  
#### <a name="to-configure-a-wireless-network-connection"></a>Vezeték nélküli hálózati kapcsolat konfigurálása  
  
1.  A **Mobileszközök vezeték nélküli kommunikációs beállításainak konfigurálása** lapon kattintson a **Hozzáadás** elemre.  
  
2.  A **Vezeték nélküli hálózati kapcsolat** párbeszédpanelen adja meg a mobileszközön létesítendő vezeték nélküli kapcsolat alábbi adatait:  
  
|Beállítás|További információ|  
|-------------|----------------------|  
|**Hálózatnév (SSID)**|Adja meg a Wi-Fi hálózat nevét.|  
|**Hálózati kapcsolat**|Válasszon az **Internet** vagy **Munkahely**lehetőségek közül.|  
|**Hitelesítés**|Válassza ki a vezeték nélküli kapcsolat hitelesítési módját az alábbiak közül:<br /><br /> - **Nyissa meg**<br /><br /> - **Megosztott**<br /><br /> - **WPA**<br /><br /> - **WPA-ELŐMEGOSZTOTT KULCCSAL**<br /><br /> - **WPA2**<br /><br /> - **WPA2-ELŐMEGOSZTOTT KULCCSAL**|  
|**Adattitkosítás**|Válassza ki a kapcsolat által használt titkosítási módszert. A választható értékek a kiválasztott **Hitelesítési** módszertől függően változhatnak:<br /><br /> - **Letiltva**<br /><br /> - **WEP**<br /><br /> - **TKIP**<br /><br /> - **AES**|  
|**Kulcsindex**|Válasszon egy **1** és **4** közötti kulcsindexet, amely a **WEP** **Adattitkosítás**beállításaként szolgál majd.|  
|**Ez a hálózat csatlakozik az internethez**|Válassza ezt a lehetőséget, ha olyan proxybeállításokat kíván megadni, amelyek lehetővé teszik a vezeték nélküli kapcsolaton lévő mobileszközök csatlakozását az internethez.|  
|**Proxykiszolgáló beállításai**|Adja meg szükség szerint a **HTTP** , a **WAP** és a **Szoftvercsatornák** **Kiszolgáló** és **Port**beállításait.|  
|**802.1X hálózati hozzáférés engedélyezése**|Válassza ezt a lehetőséget, ha szeretné biztonságossá tenni a kapcsolatot egy EAP-típus megadásával.|  
|**EAP-típus**|Válassza ki a használni kívánt EAP-típust az alábbi lehetőségek közül:<br /><br /> - **A PEAP**<br> - **Intelligens kártya vagy tanúsítvány**|  
  
  
  
### <a name="certificates"></a>Tanúsítványok  
 Lehetővé teszi a tanúsítványok importálását a mobileszközökre történő telepítéshez.  
  
 Kattintson az **Importálás** elemre, majd adja meg a következő értékeket:  
  
-   **Tanúsítványfájl** – Kattintson a Tallózás elemre, majd válassza ki az importálni kívánt **.cer** kiterjesztésű tanúsítványfájlt.  
  
-   **Céltár** – Válasszon ki egy vagy több céltárolót az alábbi lehetőségek közül, ahonnan az importált tanúsítványt hozzá szeretné adni a mobileszközhöz:  
  
    -   **Legfelső szintű**  
  
    -   **HITELESÍTÉSSZOLGÁLTATÓ**  
  
    -   **Normál**  
  
    -   **Védett módú használatának**  
  
    -   **SPC**  
  
    -   **Társ**  
  
-   **Szerepkör** – Ha az **SPC** (szoftvergyártói tanúsítvány) lehetőséget választotta céltárnak, válassza ki a tanúsítványhoz társított szerepkört az alábbiak közül:  
  
    -   **Mobilszolgáltató**  
  
    -   **Manager**  
  
    -   **Hitelesített felhasználó**  
  
    -   **Rendszergazda**  
  
    -   **Hitelesítetlen felhasználó**  
  
    -   **Megbízható ellátó kiszolgáló**  
  
### <a name="system-security"></a>Rendszerbiztonság  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Felhasználói fiókok felügyelete**|A Windows Felhasználói fiókok felügyeletének engedélyezése vagy letiltása az eszközön.|  
|**Hálózati tűzfal**|A Windows tűzfal engedélyezése vagy letiltása.<br /><br /> (Csak Windows 8.1)|  
|**Frissítések (Windows 8.1 és korábbi verziók)**|Válassza ki a Windows szoftverfrissítések számítógépre való letöltésének módját. Letöltheti például automatikusan a frissítéseket, de a felhasználóra bízhatja, hogy mikor telepíti őket.|  
|**A frissítések legalacsonyabb besorolása**|Válassza ki a Windows rendszerű számítógépekre letöltött frissítések legalacsonyabb besorolását a **Nincs**, **Fontos**vagy **Ajánlott**lehetőségek közül.|  
|**Frissítések (Windows 10)**|Válassza ki a Windows szoftverfrissítések számítógépre való letöltésének módját. Letöltheti például automatikusan a frissítéseket, de a felhasználóra bízhatja, hogy mikor telepíti őket.<br /><br /> (Csak Windows 10)|  
|**Telepítés napja**|Itt adható meg a frissítések telepítésének napja.<br /><br /> (Csak Windows 10)|  
|**Telepítés időpontja**|Itt adható meg a frissítések telepítésének időpontja.<br /><br /> (Csak Windows 10)|  
|**SmartScreen**|A Windows SmartScreen engedélyezése vagy letiltása.|  
|**Vírusvédelem**|Ezzel a beállítással biztosíthatja, hogy legyen telepítve víruskereső szoftver az eszközön.|  
|**A vírusvédelmi aláírások naprakészek**|Ezzel a beállítással biztosíthatja, hogy a víruskereső szoftver aláírásfájljai naprakészek legyenek.|  
|**Előzetes funkciók**|Lehetővé teszi a Microsoft számára, hogy előzetes verziójú beállításokat és funkciókat telepítsen az eszközre.<br /><br /> (Csak Windows 10)|  
|**Főtanúsítvány manuális telepítése**|(Csak Windows 10)| 
|**Regisztráció manuális törlésének engedélyezése**|Lehetővé teszi, hogy a felhasználó-regisztrációjának törlése magukat a felügyelet alól MDM-megoldás.| 
  
###  <a name="windows-server-work-folders"></a>A Windows Server Munkahelyi mappái  
 Ezek a Windows 8.1 és Windows 10 rendszerű eszközök beállításai.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Munkahelyi mappák URL-címe**|Konfigurálja a Windows Server munkahelyi mappa helyét, amelyhez a felhasználók saját eszközükről csatlakozhatnak.|  
  
### <a name="allowed-and-blocked-apps-windows-phone-only"></a>Engedélyezett és letiltott alkalmazások (csak Windows Phone)  
 Egy listában megadhatja a vállalatban megfelelőnek vagy nem megfelelőnek ítélt, Intune által felügyelt alkalmazásokat. A Windows Phone engedélyezheti vagy letilthatja ezeknek az alkalmazásoknak a telepítését.  
  
 Egyazon konfigurációelemben nem adhatók meg egyszerre megfelelő és nem megfelelő alkalmazások is.  
  
#### <a name="to-specify-apps-that-will-be-allowed-or-blocked"></a>Az engedélyezni vagy letiltani kívánt alkalmazások meghatározása  
  
1.  Az **Engedélyezett és letiltott alkalmazások listája** lapon adja meg a következő információkat:  
  
    |Beállítás|További információ|  
    |-------------|----------------------|  
    |**Tiltott alkalmazások listája**|Ha ezt a beállítást választja, összeállíthatja azon alkalmazások listáját, amelyeket nem telepíthetnek a felhasználók.|  
    |**Engedélyezett alkalmazások listája**|Ha ezt a beállítást választja, összeállíthatja a felhasználók által telepíthető alkalmazások listáját. A rendszer minden más alkalmazás telepítését letiltja.|  
    |**Hozzáadás**|Hozzáadhat egy alkalmazást a kijelölt listához. Meg kell adnia egy szabadon választott nevet, valamint tetszés szerint megadhatja az alkalmazás kiadóját, valamint az alkalmazás alkalmazás-áruházbeli URL-címét.<br /><br /> Az URL-cím megadásához keresse meg a használni kívánt alkalmazást a Windows Áruházban.<br /><br /> Nyissa meg az alkalmazás lapját, és másolja az URL-címet a vágólapra. Ezt a címet az engedélyezett és a tiltott alkalmazások listájában egyaránt használhatja URL-címként.<br /><br /> **Példa:** Keressen rá az áruházban a **Skype** alkalmazást. A használt URL-cím a következő: **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.|  
    |**Szerkesztés**|Segítségével szerkesztheti a kijelölt alkalmazás nevét, kiadóját és URL-címét.|  
    |**Eltávolítás**|Törölheti a kijelölt alkalmazást a listából.|  
    |**Importálásálás**|Importálhatja azokat az alkalmazásokat, amelyeket egy vesszővel tagolt fájlban megadott. Használja a fájlban megadott formátumot, alkalmazásnevet, kiadót és URL-címet.|  
  
### <a name="windows-10-team"></a>Windows 10 Team  
 Ezek csak a Windows 10 Teamet futtató eszközök beállításai.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Lehetővé teszi a képernyő automatikusan felébredhet, ha az érzékelők észlelnek a helyiségben**|Lehetővé teszi az eszköz automatikus felébresztését, ha az érzékelők valakit észlelnek a helyiségben.|  
|**Vezeték nélküli kivetítéshez szükséges PIN-kód**|Meghatározza, hogy meg kell-e adni a PIN-kódot az eszköz vezeték nélküli vetítési funkcióinak használata előtt.|  
|**Karbantartási időszak**|Meghatározza, hogy mely időszakban kerül sor az eszköz frissítéseire. Beállíthatja a kezdési időt és az időtartamot (1-5 óra) is.|
|**Az Azure Operational Insights**|Az Azure Operational Insights, része a Microsoft Operations Manager naplófájladatokat gyűjt, tárol és elemez a naplófájl adatai a Windows 10 Team-eszközökről.<br>Azure Operational insights szolgáltatáshoz való csatlakozásához, meg kell adnia a munkaterület Azonosítóját és kulcsát egy.| 
|**Miracast vezeték nélküli vetítéshez**|Engedélyezze ezt a beállítást, ha azt szeretné, hogy a Windows 10 Team-eszköz miracast technológiát eszközeiket használják, a projekt.<br>Ha engedélyezi ezt a beállítást, a **válasszon Miracast-csatornát** válassza ki a tartalom vetítéséhez használni kívánt Miracast-csatornát.|
|**Az üdvözlőképernyőn megjelenő értekezletadatok**|Ha engedélyezi ezt a lehetőséget, kiválaszthatja az információt, amely nem jelenik meg a **értekezletek** csempéjén a **üdvözlő** képernyő. A következőket teheti:<br><br>- **Csak szervező és időpont megjelenítése**<br>- **Szervező, időpont és tárgy (a tárgy rejtett zártkörű értekezletek esetén) megjelenítése**|
|**Zárolási képernyő háttérképének URL-címe**|Használja ezt a beállítást egy egyéni hátteret megjelenjenek a **üdvözlő** Windows 10 Team eszközök, az itt megadott képernyőjén.<br>A képnek PNG formátumban kell lennie, és az URL-címet a következővel kell kezdődnie **https://**.| 
  
### <a name="windows-information-protection"></a>A Windows információvédelem  

Ahogy a vállalaton belül egyre nő az alkalmazottak tulajdonában álló eszközök száma, úgy nő az adatok véletlen kiszivárgásának kockázata is az olyan alkalmazásokon és szolgáltatásokon keresztül, mint az e-mail, a közösségi média és a nyilvános felhő, amelyek fölött a vállalatnak nincs irányítási lehetősége. Olyan esetekről van szó, mint például amikor egy alkalmazott a személyes e-mail-fiókjából küldi el a legújabb tervrajzokat, termékadatokat másol be egy tweetbe, vagy a nyilvános felhőben található tárhelyére ment egy aktuális értékesítési jelentést.

Windows információk védelme (folyamatban) segít védekezni az esetleges adatszivárgást, ellenkező esetben az alkalmazott munkavégzésébe zavarása nélkül. Befejezetlen is segít megvédeni a vállalati alkalmazások és adatok véletlenül kiszivárogjanak vállalati tulajdonú eszközök és személyes eszközök, alkalmazottak által munkába hozott nem igényel változtatásokat a környezetben vagy más alkalmazások.

 A konfigurációelem-beállításai a Configuration Manager Befejezetlen által védett alkalmazások EDP, a vállalati hálózati helyek, a védelmi szintek és a titkosítási beállítások kezelését.

Nagyvállalati adatvédelem a Configuration Manager konfigurálásával kapcsolatos további információkért lásd: [vállalati adatok védelme a Windows információk védelme (folyamatban)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


### <a name="microsoft-edge"></a>Microsoft Edge  
Ezek a Windows 10-et és újabb rendszereket futtató eszközök beállításai.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Keresési javaslatok engedélyezése a címsorban**|Lehetővé teszi, hogy a keresőmotor webhelyeket javasoljon a keresőkifejezések beírása közben.|  
|**Intranetes adatforgalom küldésének engedélyezése az Internet Explorer**||  
|**Engedélyezése nyomkövetés tiltása**|A Követés letiltása (Do Not Track) fejléc arról tájékoztatja a webhelyeket, hogy nem szeretné, ha követnék a látogatást.|  
|**SmartScreen engedélyezése**|A SmartScreen segítségével ellenőrizheti, hogy a felhasználók által letöltött fájlok nem tartalmaznak-e rosszindulatú kódot.|  
|**Előugró ablakok engedélyezése**|A böngészőben előugró ablakok engedélyezésére vagy letiltására szolgál.|  
|**Cookie-k engedélyezése**|A cookie-k engedélyezésére vagy letiltására szolgál.|  
|**Automatikus kitöltés engedélyezése**|Engedélyezi az Edge böngésző automatikus kitöltési funkciójának használatát.|  
|**Jelszókezelő engedélyezése**|Engedélyezi az Edge böngésző jelszókezelő funkciójának használatát.|  
|**Vállalati üzemmód webhelylistájának helye**|Megadja, hogy hol található a Vállalati üzemmódban megnyitott webhelyek listája. Ezt a listát a felhasználók nem szerkeszthetik.|  


### <a name="windows-defender"></a>A Windows Defender
Ezek a Windows 10-et és újabb rendszereket futtató eszközök beállításai.
 
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Valós idejű figyelés engedélyezése**|Lehetővé teszi, hogy a kártevő szoftverek, kémprogramok és más nemkívánatos szoftverek valós idejű vizsgálatát.|
|**Viselkedésfigyelés engedélyezése**|Engedélyezi a Defender számára eszközök gyanús tevékenységekre utaló ismert mintákat keressen ellenőrzése.|
|**Hálózatfelügyeleti rendszer engedélyezése**|A Hálózatvizsgáló rendszer (NIS) segít, eszközök hálózatalapú biztonsági rések elleni védelmét az ismert biztonsági rések aláírásait használja a Microsoft Endpoint Protection Center észleli és blokkolja a rosszindulatú forgalmat.|
|**Minden letöltött fájl vizsgálata**|Meghatározza, hogy a Defender az internetről letöltött összes fájlt megvizsgálja.|
|**Szkriptek ellenőrzésének engedélyezése**|Engedélyezi a Defender az Internet Explorerben használt parancsfájlok vizsgálatát.|
|**Fájl- és programtevékenység figyelése**|Lehetővé teszi, hogy a Defender fájl- és program tevékenység figyelése az eszközökön.
|**Ártalmatlanított kártevő szoftverek követése (nap)**|Lehetővé teszi, hogy a Defender számára az ártalmatlanított kártevők nyomon követése a napok, megadhatja, hogy manuálisan ellenőrizze a korábban érintett eszközök száma. Ha a napok száma 0, a kártevő a karanténban marad, és a rendszer nem távolítja el automatikusan.|
|**Ügyfél-Kezelőfelület elérésének engedélyezése**|Meghatározza, hogy a Windows Defender kezelőfelülete rejtett legyen-e a felhasználóktól.<br>Amikor módosítja a ezt a beállítást, akkor lép érvénybe a felhasználó számítógép újraindításakor.|
|**Rendszervizsgálat ütemezése**|Lehetővé teszi a teljes vagy gyors rendszervizsgálat ütemezése a megadott napon és időben, rendszeres időközönként.|
|**Napi gyors vizsgálat ütemezése**|Lehetővé teszi, hogy minden nap a választott kiválasztott gyors vizsgálat ütemezése
|**A processzorhasználat korlátozása az ellenőrzések során**|Lehetővé teszi a korlátozását a vizsgálatok (az 1 és 100) használata engedélyezett.|
|**Archív fájlok vizsgálata**|Engedélyezi a Defender számára az archív fájlok – például a .zip és a .cab fájlokat beolvasása.|
|**E-mail üzenetek vizsgálata**|Engedélyezi a Defender megvizsgálja az e-mailek megérkeznek az eszközön.|
|**Cserélhető adathordozók vizsgálata**|Lehetővé teszi, hogy a Defender cserélhető meghajtók, például a pendrive-OK vizsgálatát.|
|**Csatlakoztatott meghajtók ellenőrzése**|Engedélyezi a Defender számára a csatlakoztatott hálózati meghajtókon lévő fájlok vizsgálatára.<br>Ha a meghajtó a fájlok írásvédettek, Defender nem képes eltávolítani a bennük talált kártevőket.|
|**A megosztott hálózati mappákból megnyitott fájlok vizsgálata**|Engedélyezi a Defender számára a megosztott hálózati meghajtókon (például, amelyek UNC-útvonalon érhető el) fájlok vizsgálata<br>Ha a meghajtó a fájlok írásvédettek, Defender nem képes eltávolítani a bennük talált kártevőket.|
|**Aláírás-frissítési időköz**|Meghatározza, mely Defender ellenőrzi új aláírásfájlokat időközét.
|**Felhővédelem engedélyezése**|Lehetővé teszi, vagy letiltja a Microsoft Active Protection Service a rendszer adatokat a felügyelt eszközökön észlelt kártevőkről. Ezeket az információkat a későbbiekben a szolgáltatás továbbfejlesztésére szolgál.|
|**Minták küldésének kérése a felhasználóktól**|Meghatározza, hogy előfordulhat, hogy amelyeken további vizsgálat szükséges annak megállapításához, hogy azok rosszindulatú fájlok automatikus küldése a Microsoftnak.|
|**Vélhetően nem kívánatos alkalmazások észlelése**|Regisztrált Windows asztali eszközök minősítésű a Windows Defender potenciálisan nemkívánatos szoftverek futtatása ellen védi. Ezen alkalmazások futtatása ellen, vagy a vizsgálati üzemmóddal jelentést készíthet a vélhetően nemkívánatos alkalmazások telepítéséről.|
|**Fájl- és kizárások**|Egy vagy több fájlokat és mappákat – például C:\Path vagy %ProgramFiles%\Path\filename.exe ad hozzá a kivételek listájára. Ezek a fájlok és mappák valós idejű és ütemezett vizsgálatok során nem szerepelnek.|
|**Fájl kiterjesztése kizárások**|Egy vagy több kívánt fájlkiterjesztéseket – például jpg vagy txt hozzáadása a kivételek listájára. Az ilyen kiterjesztésű fájlokat nem szerepelnek a valós idejű és ütemezett vizsgálatok során.|
|**Folyamat kizárások**|A típus .exe, .com vagy .scr egy vagy több folyamatához ad hozzá a kivételek listájára. Ezek a folyamatok valós idejű és ütemezett vizsgálatok során nem szerepelnek.|

  
## <a name="see-also"></a>Lásd még:  
 [A System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt eszközök konfigurációelemei](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
