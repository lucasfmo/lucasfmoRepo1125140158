---
title: "Az Intune-nal felügyelt létrehozása a Windows Phone-eszközök konfigurációelemei |} Microsoft Docs"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df10dc4d-c9ff-4574-bb33-8d30eb14cfe3
caps.latest.revision: 13
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: bcb2d14ef097afc2915932fe09f6d83c968aecf9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-windows-phone-devices-managed-without-the-system-center-configuration-manager-client"></a>Konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt Windows Phone-eszközökhöz.
A System Center Configuration Manager használata**Windows Phone** konfigurációelemével egyszerűen kezelheti a Microsoft Intune vagy a helyszínen felügyelt regisztrált a Configuration Manager által Windows Phone-eszközök beállításai.  
  
### <a name="to-create-a-windows-phone-configuration-item"></a>A Windows Phone-konfigurációelem létrehozása  
  
1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség**.  
  
2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a **Megfelelőségi beállítások**csomópontot, majd kattintson a **Konfigurációelemek**lehetőségre.  
  
3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  
  
4.  A **Konfigurációelem létrehozása varázsló** **Általános**lapján adja meg a konfigurációelem nevét és leírását (utóbbi nem kötelező).  
  
5.  A **adja meg a létrehozandó konfigurációelem típusát**, jelölje be **Windows Phone**.  
  
6.  Kattintson a **kategóriák** Ha létrehozni és hozzárendelni kategóriákat szeretne kereséséhez és szűréséhez konfigurációs elemek a Configuration Manager konzolon.  
  
7.  Az a **által támogatott platformok** oldalon a varázsló, válassza ki azokat a Windows Phone-platformokat, amelyek kiértékelik a konfigurációelemet.  
  
8.  A varázsló **Eszközbeállítások** lapján jelölje ki a konfigurálni kívánt beállításcsoportot. A részleteket lásd a jelen témakör [Útmutató a Windows Phone-telefonokhoz készült konfigurációelemek beállításaihoz](#BKMK_Setref) című részébenlehetőségek közül. Kattintson a **Tovább**lehetőségek közül.  
  
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
  
##  <a name="windows-phone-configuration-item-settings-reference"></a>Útmutató a Windows Phone-telefonokhoz készült konfigurációelemek beállításaihoz  
  
### <a name="password"></a>Jelszó  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Jelszóbeállítások megkövetelése az eszközökön**|Jelszó kérése a támogatott eszközökön.|  
|**Jelszó minimális hossza (karakter)**|A jelszó minimális hossza.|  
|**Jelszó lejárati ideje napokban**|Azon napok száma, amely után a jelszót kötelező megváltoztatni.|  
|**Megjegyzett jelszavak száma**|Megakadályozza a korábban használt jelszavak használatát.|  
|**Sikertelen bejelentkezési próbálkozások száma az eszköz törlése előtt**|A megadott számú sikertelen bejelentkezési kísérlet után törli az eszközt.|  
|**Jelszó bonyolultsága**|Kiválasztja, hogy megadhat-e PIN-kódot (pl. „1234”), vagy erős jelszót kell megadnia.|  
|**Jelszó-helyreállítási PIN küldése az Exchange Server-kiszolgálónak**||  
  
### <a name="device"></a>Eszköz  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Képernyőfelvétel**|Engedélyezi a felhasználó számára képernyőképek készítésének az eszköz képernyőjén megjelenő tartalmat.<br /><br /> (Csak Windows Phone 8.1)|  
|**Diagnosztikai adatok beküldése**|Engedélyezi az alkalmazások naplófájljainak elküldését.|  
|**Földrajzi hely**|Engedélyezi a helymeghatározási szolgáltatások adatainak használatát az eszköz számára.<br /><br /> (Csak Windows Phone 8.1)|  
|**Másolás és beillesztés**|Az adatok alkalmazások közötti átviteléhez használja a másolás és beillesztés funkciót.<br /><br /> (Csak Windows Phone 8.1)|  
|**Bluetooth**|Engedélyezi az eszköz Bluetooth-képességének használatát.|  
  
### <a name="email-management"></a>E-mailek kezelése  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**POP és IMAP levelezés**|A POP és IMAP szabványokat használó e-mail fiókokhoz való csatlakozás engedélyezése.|  
|**E-mailek megtartásának maximális időtartama**|Ennyi idő után törli a rendszer az e-maileket a kiszolgálóról.|  
|**Engedélyezett üzenetformátumok**|Megadhatja, hogy az e-mailek HTML formátumúak is lehetnek-e, vagy csak egyszerű szövegek.|  
|**Egyszerű szöveges e-mailek maximális mérete (automatikusan letöltött)**|Szabályozza az egyszerű szöveges e-mailek maximális méretét automatikus letöltés esetén.|  
|**HTML formátumú e-mailek maximális mérete (automatikusan letöltött)**|Szabályozza a HTML formátumú e-mailek maximális méretét automatikus letöltés esetén.|  
|**Mellékletek maximális mérete (automatikusan letöltött)**|Beállítja az automatikusan letöltött e-mailek maximális méretét.|  
|**Naptár szinkronizálása**||  
|**Egyéni e-mail fiók**|A nem Microsoft-fiókok használatának engedélyezése az eszközön.|  
|**A Microsoft-fiók választhatóvá tétele a Windows Mail alkalmazásban**|Nem kötelező Microsoft-fiókkal jelentkezzen be a Windows Mail használata.|  
  
### <a name="store"></a>Áruház  
 Ezek a beállítások csak a Windows Phone 8.1-es eszközökre vonatkoznak.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Alkalmazás-áruház**|Hozzáférés engedélyezése az alkalmazásáruházhoz az eszközön.|  
  
### <a name="browser"></a>Böngésző  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Webböngésző engedélyezése**|Engedélyezi vagy letiltja az alapértelmezett böngészőt.|  
|**Automatikus kitöltés**|A felhasználók módosíthatják a böngésző automatikus kiegészítési funkciójának beállításait.|  
|**Active scripting**|A böngésző futtathat parancsfájlokat (pl. Active X-parancsfájlok).|  
|**Beépülő modulok**|A felhasználók hozzáadhatnak beépülő modulokat az Internet Explorerhez.|  
|**Előugróablak-blokkoló**|A böngésző előugróablak-blokkolójának engedélyezése vagy letiltása.|  
|**Hamis figyelmeztetés**|A potenciálisan rosszindulatú webhelyekről szóló figyelmeztetések engedélyezése vagy letiltása.|  
  
### <a name="internet-explorer"></a>Internet Explorer  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**A Nyomkövetés tiltása fejléc elküldése mindig**|Megakadályozza az adatok elküldését harmadik féltől származó webhelyek számára.|  
|**Intranet biztonsági zóna**||  
|**Az Internet zóna biztonsági szintje**|Beállíthatja az internet zóna biztonsági szintjét.|  
|**Biztonsági szint az intranet zóna részére**|Beállíthatja az intranet zóna biztonsági szintjét.|  
|**Biztonsági szint a megbízható helyek zóna részére**|Beállíthatja a megbízható helyek zóna biztonsági szintjét.|  
|**Biztonsági szint a tiltott helyek zóna részére**|Beállíthatja a tiltott helyek zóna biztonsági szintjét.|  
|**Névterek az intranet zóna részére**||  
|**Ugrás az intraneti helyre egyetlen szó beírásához**|Annak a beállításnak az engedélyezése vagy letiltása, amely engedélyezi az Internet Explorer számára, hogy automatikusan átugorjon egy intranetes webhelyre, ha érvényes helynevet ír be a felhasználó a HTTP: előtag nélkül.|  
|**A vállalati üzemmód menüopciója**|Engedélyezi a felhasználók számára, hogy aktiválják vagy inaktiválják a vállalati üzemmódot az Internet Explorer **Eszközök** menüjéből.|  
|**Naplózási jelentés helye (URL-cím)**|Megadhatja azt az URL-címet, ahol a webhelyek naplózása történik, ha a Vállalati üzemmód aktív.|  
|**A vállalati üzemmód helylistájának helye (URL)**|Megadhatja azon webhelyek listájának helyét, amelyek a Vállalati üzemmódot használják, ha az aktív.|  
  
### <a name="cloud"></a>Felhő  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Beállítások szinkronizálása**|Beállítások szinkronizálásának engedélyezése az eszközök között.|  
|**Hitelesítőadatok szinkronizálása**|A hitelesítő adatok szinkronizálásának engedélyezése az eszközök között.|  
|**Microsoft-fiók**|Microsoft-fiókok használatának engedélyezése az eszközön.<br /><br /> (Csak Windows Phone 8.1)|  
|**Beállítások szinkronizálása forgalmi díjas kapcsolaton keresztül**|A beállítások szinkronizálásának engedélyezése, ha az internetkapcsolat forgalmi díjas.|  
  
### <a name="security"></a>Biztonság  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Aláíratlan fájltelepítés**|A nem aláírt fájlok betöltésének engedélyezése.|  
|**Aláíratlan alkalmazások**|A nem aláírt alkalmazások betöltésének engedélyezése.|  
|**SMS- és MMS-üzenetek**|SMS- és MMS-üzenetek küldésének engedélyezése az eszközről.|  
|**Cserélhető tároló**|Cserélhető tárolók (pl. SD-kártya) használatának engedélyezése az eszközön.|  
|**Fényképezőgép**|Engedélyezi az eszköz kamerájának használatát.|  
|**Kis hatótávolságú kommunikáció (NFC)**|Az NFC segítségével végzett kommunikáció engedélyezése az eszközön.<br /><br /> (Csak Windows Phone 8.1)|  
|**USB-kapcsolat engedélyezése**|Lehetővé teszi a perifériák USB keresztül csatlakozni ehhez az eszközhöz.|
  
### <a name="peak-synchronization"></a>Csúcsidőszak szinkronizálása  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Csúcsidő megadása**|Adja meg, amíg a következő két beállítást használják egy ablakot.|  
|**Csúcsidőszak szinkronizálási gyakorisága**|Válassza ki, milyen gyakran szinkronizálja az az eszköz a megadott maximális idő alatt.|  
|**Csúcsidőszakon kívüli szinkronizálás gyakorisága**|Válassza ki, milyen gyakran szinkronizálja az az eszköz a megadott maximális idő kívül.|  
  
### <a name="roaming"></a>Barangolás  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Eszköz felügyelete barangolás közben**|Lehetővé teszi az eszköz a Configuration Manager által kezelhető roaming esetén.|  
|**Szoftverletöltés barangolás közben**|Alkalmazások és szoftverek letöltésének engedélyezése barangolás közben.|  
|**E-mailek letöltése barangolás közben**|E-mailek letöltésének engedélyezése barangolás közben.|  
|**Adatroaming**|Hálózatok közötti barangolás engedélyezése adatok elérése közben.|  
  
### <a name="encryption"></a>Titkosítás  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Memóriakártya titkosítása**|Az eszközhöz használt minden tárolókártyának titkosítva kell lennie.|  
|**Fájlok titkosítása az eszközön**|A mobileszközön található összes fájlnak titkosítva kell lennie.|  
|**E-mail aláírásának igénylése**|Csak az aláírt e-mailek lesznek elküldve.|  
|**Aláíró algoritmus**|Az e-mailek aláírásához használt algoritmust határozza meg.|  
|**E-mail titkosításának igénylése**|Küldés előtt titkosítja az e-maileket.|  
|**Titkosítási algoritmus**|Az e-mailek titkosításához használt algoritmust határozza meg.|  
  
###  <a name="wireless-communications"></a>Vezeték nélküli kommunikáció  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Vezeték nélküli hálózati kapcsolat**|Az eszközök Wi-Fi képességének engedélyezése vagy letiltása.|  
|**Wi-Fi tethering**|Engedélyezi a felhasználók számára, hogy mobil elérési pontként használják eszközeiket.|  
|**Adatok kiszervezése Wi-Fi-re, amikor lehetséges**||  
|**Wi-Fi elérési pont jelentése**||  
  
##### <a name="to-configure-a-wireless-network-connection"></a>Vezeték nélküli hálózati kapcsolat konfigurálása  
  
1.  A **Mobileszközök vezeték nélküli kommunikációs beállításainak konfigurálása** lapon kattintson a **Hozzáadás** elemre.  
  
2.  A **Vezeték nélküli hálózati kapcsolat** párbeszédpanelen adja meg a mobileszközön létesítendő vezeték nélküli kapcsolat alábbi adatait:  
  
|Beállítás|További információ|  
|-------------|----------------------|  
|**Hálózatnév (SSID)**||  
|**Hálózati kapcsolat**|Válasszon az **Internet** vagy **Munkahely**lehetőségek közül.|  
|**Hitelesítés**|Válassza ki a vezeték nélküli kapcsolat hitelesítési módját az alábbiak közül:<br><br> - **Nyissa meg**<br> - **Megosztott**<br> - **WPA**<br> - **WPA-ELŐMEGOSZTOTT KULCCSAL**<br> - **WPA2**<br> - **WPA2-ELŐMEGOSZTOTT KULCCSAL**|  
|**Adattitkosítás**|Válassza ki a kapcsolat által használt titkosítási módszert. A választható értékek a kiválasztott **Hitelesítési** módszertől függően változhatnak:<br><br> - **Letiltva**<br> - **WEP**<br> - **TKIP**<br> - **AES**|  
|**Kulcsindex**|Válasszon egy **1** és **4** közötti kulcsindexet, amely a **WEP** **Adattitkosítás**beállításaként szolgál majd.|  
|**Ez a hálózat csatlakozik az internethez**|Válassza ezt a lehetőséget, ha olyan proxybeállításokat kíván megadni, amelyek lehetővé teszik a vezeték nélküli kapcsolaton lévő mobileszközök csatlakozását az internethez.|  
|**Proxykiszolgáló beállításai**|Adja meg szükség szerint a **HTTP** , a **WAP** és a **Szoftvercsatornák** **Kiszolgáló** és **Port**beállításait.|  
|**802.1X hálózati hozzáférés engedélyezése**|Válassza ezt a lehetőséget, ha szeretné biztonságossá tenni a kapcsolatot egy EAP-típus megadásával.|  
|**EAP-típus**|Válassza ki a használni kívánt EAP-típust az alábbi lehetőségek közül:<br><br> - **A PEAP**<br> - **Intelligens kártya vagy tanúsítvány**|  
    
  
###  <a name="certificates"></a>Tanúsítványok  
 Lehetővé teszi a tanúsítványok importálását a mobileszközökre történő telepítéshez.  
  
 Kattintson az **Importálás** elemre, majd adja meg a következő értékeket:  
  
-   **Tanúsítványfájl** – kattintson **Tallózás** , és válassza ki a tanúsítványfájl kiterjesztésű **.cer** , amelyeket szeretne importálni.  
  
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
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Felhasználói fiókok felügyelete**|A Windows Felhasználói fiókok felügyeletének engedélyezése vagy letiltása az eszközön.|  
|**Hálózati tűzfal**|A Windows tűzfal engedélyezése vagy letiltása.|  
|**Frissítések**|Válassza ki a Windows szoftverfrissítések számítógépre való letöltésének módját. Letöltheti például automatikusan a frissítéseket, de a felhasználóra bízhatja, hogy mikor telepíti őket.|  
|**A frissítések legalacsonyabb besorolása**|Válassza ki a Windows rendszerű számítógépekre letöltött frissítések legalacsonyabb besorolását a **Nincs**, **Fontos**vagy **Ajánlott**lehetőségek közül.|  
|**SmartScreen**|A Windows SmartScreen engedélyezése vagy letiltása.|  
|**Vírusvédelem**|Győződjön meg arról, hogy az eszközt víruskereső szoftver védi|  
|**A vírusvédelmi aláírások naprakészek**|Győződjön meg arról, hogy a víruskereső szoftver aláírásai naprakészek.|
|**Regisztráció manuális törlésének engedélyezése**|Most a felhasználó eltávolítása eszközüket mobileszköz-kezelést.|  
  
### <a name="windows-server-work-folders"></a>A Windows Server Munkahelyi mappái  
 Ezek a beállítások Windows Phone 8 és Windows Phone 8.1 egyaránt érvényesek.  
  
|Beállítás|Részletek|  
|-------------|-------------|  
|**Munkahelyi mappák URL-címe**|Konfigurálja a Windows Server munkahelyi mappa helyét, amelyhez a felhasználók saját eszközükről csatlakozhatnak.|  
  
### <a name="allowed-and-blocked-apps-list-windows-phone-81-only"></a>Engedélyezett és letiltott alkalmazások listája (csak Windows Phone 8.1 esetén)  
 Egy listában megadhatja a vállalatban megfelelőnek vagy nem megfelelőnek ítélt Windows Phone-alkalmazásokat. A letiltottként meghatározott alkalmazásokat a felhasználók nem tudják telepíteni. Ha meghatározza az engedélyezett alkalmazások listáját, akkor a felhasználók csak a listában szereplő alkalmazásokat tudják telepíteni.  
  
 Nem adható meg egyszerre engedélyezett és tiltott alkalmazások egyazon konfigurációelemben.  
  
> [!IMPORTANT]  
>  Ha megadja a kompatibilis alkalmazások listáját, gondoskodnia kell arról, hogy a vállalati portál alkalmazást, és a Windows Phone 8.1-es eszközökre telepített alkalmazások legyenek az **engedélyezett** alkalmazások listája.  
  
##### <a name="to-specify-an-allowed-or-blocked-apps-list"></a>Az engedélyezett és letiltott alkalmazások listájának megadása  
  
1.  Az a **engedélyezett és letiltott alkalmazások listája (Windows Phone 8.1)** lapján adja meg a következőket:  
  
|||  
|-|-|  
|Beállítás|További információ|  
|**Tiltott alkalmazások listája**|Ha ezt a beállítást választja, összeállíthatja a felhasználók által nem telepíthető alkalmazások listáját.|  
|**Engedélyezett alkalmazások listája**|Ha ezt a beállítást választja, összeállíthatja a felhasználók által telepíthető alkalmazások listáját.|  
|**Hozzáadás**|Hozzáadhat egy alkalmazást a kijelölt listához. Adjon meg egy szabadon választott nevet és opcionálisan az alkalmazás kiadóját, valamint az alkalmazás alkalmazás-áruházbeli URL-címét.<br /><br /> Az URL-cím megadásához keresse meg a használni kívánt alkalmazást a Windows Phone Store áruház lapján.<br /><br /> **Példa:** Keressen rá az áruházban a **Skype** alkalmazást. Az URL cím lesz: http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51.<br /><br /> A vállalati portál alkalmazást, vagy az üzletági alkalmazások esetén nincs teljes URL-cím, csak az alkalmazás GUID azonosítója.|  
|**Szerkesztés**|Segítségével szerkesztheti a kijelölt alkalmazás nevét, kiadóját és URL-címét.|  
|**Eltávolítás**|Törölheti a kijelölt alkalmazást a listából.|  
|**Importálásálás**|Importálhatja azokat az alkalmazásokat, amelyeket egy vesszővel tagolt fájlban megadott. Használja a fájlban megadott formátumot, alkalmazásnevet, kiadót és URL-címet.|  
  
## <a name="see-also"></a>Lásd még:  
 [A System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt eszközök konfigurációelemei](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
