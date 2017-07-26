---
title: "Az Intune-nal felügyelt Android és Samsung KNOX Standard eszközökhöz konfigurációelemek létrehozása |} Microsoft Docs"
description: "A System Center Configuration Manager Android és Samsung KNOX Standard konfigurációs elem segítségével kezelheti az eszközök beállításait."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b66f3c4-e3bb-4f6a-abd5-55be649ff90d
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4b9261db93c9bf72c492e3c9be5b30f81835134a
ms.openlocfilehash: c9961c2e9866199571a1b39a7b185cb6bb96f998
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-system-center-configuration-manager-client"></a>Konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt Android- és Samsung KNOX-eszközökhöz.

A System Center Configuration Manager használata **Android és Samsung KNOX** konfigurációelemével egyszerűen kezelheti a Microsoft Intune vagy a helyszínen felügyelt regisztrált a Configuration Manager által Android és Samsung KNOX eszközök beállításai.  

#### <a name="to-create-an-android-and-samsung-knox-configuration-item"></a>Android és Samsung KNOX típusú konfigurációelem létrehozása  

1. Kattintson a Configuration Manager konzol **eszközök és megfelelőség**.  

2. Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **megfelelőségi beállítások**, és válassza a **Konfigurációelemek**.  

3. Az a **Home** lap a **létrehozása** csoportjában válassza **Konfigurációelem létrehozása**.  

4. Az a **általános** lap a Konfigurációelem létrehozása varázsló, adja meg egy nevet és egy leírást a konfigurációs elem számára.  

5. A **adja meg a létrehozandó konfigurációelem típusát**, válassza a **Android és Samsung KNOX**.  

6. Válasszon **kategóriák** Ha létrehozni és hozzárendelni kategóriákat szeretne kereséséhez és szűréséhez konfigurációs elemek a Configuration Manager konzolon.  

7. Az a **által támogatott platformok** lap a varázslóban válassza ki azokat a Android vagy Samsung KNOX-platformokat, amelyek kiértékelik a konfigurációelemet.  

8. Az a **eszközbeállítások** oldalon a varázsló, válassza ki a konfigurálni kívánt beállításcsoportot. Lásd: [Android és Samsung KNOX konfigurációs elem beállításait referencia](#BKMK_setref) a témakör részletes, és válassza a **következő**.  

    > [!TIP]  
    >  Ha nem jelenik meg a kívánt beállítást, ellenőrizze a **további beállításokat, amelyek nincsenek rajta az alapértelmezett beállítási csoportokban** mezőbe.  

9. Egyes beállítások lapon adja meg a beállításokat, amelyekre szüksége van. Válassza ki, hogy szeretné-e őket kijavítani, ha azok nem megfelelőek az eszközökön (Ha ez támogatott).  

10. Az egyes beállítási csoport a súlyosság, amely megjelenik, amikor egy konfigurációs elem található, nem megfelelő is konfigurálhatja:  

    - **Nincs**. A megfelelőségi szabálynak eleget nem tevő eszközök nem kerül a hiba súlyossága a Configuration Manager-jelentések.  

    - **Információ**. A megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **információk** a Configuration Manager jelentésekben.  

    - **Figyelmeztetés**. A megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **figyelmeztetés** Configuration Manager jelentések.  

    - **Kritikus**. A megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben.  

    - **Kritikus eseménnyel**. A megfelelőségi szabálynak eleget nem tevő eszközök adják meg a hiba súlyosságát a **kritikus** a Configuration Manager jelentésekben. Ezt a súlyossági szintet az alkalmazás eseménynaplója is rögzíti Windows-eseményként.  

11. Az a **Platform alkalmazhatósága** lap varázsló áttekintheti az azokat a beállításokat, amelyek nem kompatibilisek a korábban kiválasztott támogatott platformokkal. Visszaléphet, hogy eltávolítsa ezeket a beállításokat, vagy folytathatja a műveletet.  

    > [!TIP]  
    >  A nem támogatott beállítások megfelelőségét a rendszer nem ellenőrzi.  

12. Fejezze be a varázsló futtatását.  

 Az új konfigurációelemet az **Eszközök és megfelelőség** munkaterület **Konfigurációelemek** csomópontjában tekintheti meg.  

## <a name="android-and-samsung-knox-configuration-item-settings-reference"></a>Útmutató az Android- és Samsung KNOX-eszközökhöz készült konfigurációelemek beállításaihoz  

### <a name="password"></a>Jelszó  
Ezek a beállítások az Android- és a Samsung KNOX-eszközökre egyaránt érvényesek.  

|Beállítás|Részletek|  
|-------------|-------------|  
|**Jelszóbeállítások megkövetelése az eszközökön**|A támogatott eszközökön jelszót igényel.|  
|**Jelszó minimális hossza (karakter)**|A jelszó minimális hosszát határozza meg.|  
|**Jelszó lejárati ideje napokban**|Megadja, hány nap után a jelszót kötelező megváltoztatni.|  
|**Megjegyzett jelszavak száma**|Megakadályozza, hogy a korábban használt jelszavak újbóli felhasználása.|  
|**Sikertelen bejelentkezési próbálkozások száma az eszköz törlése előtt**|Ez a szám, a bejelentkezés sikertelen kísérlet után törli az eszközt.|  
|**Üresjárati idő után az eszköz zárolva van**|Megadja azt az időt, amely után az eszköz zárolva lesz, ha nem használja.|
|**Jelszó minősége**|Megadja a jelszó erősségének szintjét, és hogy használható-e biometrikus eszköz.|  
|**Smart Lock és más megbízhatósági ügynökök engedélyezése**|Beállíthatja a kompatibilis Android-eszközökön intelligens zárolás funkciót. A telefonos funkció lehetővé teszi letiltását vagy megkerülését az eszköz zárolási képernyője jelszavának, ha az eszköz megbízható helyen van, például amikor egy adott Bluetooth-eszközhöz, vagy egy bizonyos NFC-címkéhez van közel van csatlakoztatva. Ezzel a beállítással használhatja, hogy a felhasználók az intelligens zárolás konfigurálását.|
|**Ujjlenyomattal történő feloldásának (knox 5.0 +)**|Ujjlenyomattal történő feloldásának kompatibilis eszközök használatának engedélyezése.|

### <a name="device"></a>Eszköz   

|Beállítás|Részletek|  
|------------------|-------------|  
|**Hangtárcsázás**|Engedélyezheti vagy letilthatja a hangtárcsázási funkció engedélyezése az eszközön.|
|**Beszédfelismerési asszisztens**|Beszédfelismerési asszisztens szoftver használatának engedélyezése az eszközön.|
|**Képernyőfelvétel**|Lehetővé teszi, hogy a felhasználó képként a képernyőn látható tartalmat rögzíti.|
|**Diagnosztikai adatok beküldése**|Lehetővé teszi, hogy az eszköz diagnosztikai adatokat küld a Google.|
|**Földrajzi hely**|Lehetővé teszi, hogy az eszköz helyére vonatkozó információkat használja.|
|**Másolás és beillesztés**|Lehetővé teszi, hogy a másolási és beillesztési funkcióinak az eszközön.|
|**Gyári beállítások visszaállítása**|Lehetővé teszi, hogy a felhasználó visszaállítsa a gyári beállításokat az eszközön.|  |
|**Vágólap alkalmazások közötti megosztásának**|Lehetővé teszi a felhasználó számára a vágólap segítségével másolja és illessze be alkalmazások között.|  |
|**Bluetooth**|Az eszköz Bluetooth használatának engedélyezése.|

### <a name="store"></a>Áruház

|Beállítás|Részletek|  
|------------------|-------------|  
|**Alkalmazás-áruház**|Lehetővé teszi a felhasználó számára az eszközön a Google Play áruház használatának.|

### <a name="browser"></a>Böngésző

|Beállítás|Részletek|  
|------------------|-------------|  
|**Webböngésző engedélyezése**|Lehetővé teszi, hogy az eszközök alapértelmezett webböngésző használható.|
|**Automatikus kitöltés**|Lehetővé teszi, hogy a használt böngésző automatikus kitöltési funkciójának.|
|**Active scripting**|Lehetővé teszi, hogy az eszközön található böngésző active Scripting funkciót használjon.|
|**Előugróablak-blokkoló**|Az előugró ablakok engedélyezése a böngészőben.|
|**Cookie-k**|Lehetővé teszi, hogy az eszközön található böngésző cookie-k használatát.|

### <a name="cloud"></a>Felhő  

|Beállítás|Részletek|  
|-------------|-------------|  
|**Google biztonsági mentés**|A Google biztonsági mentés engedélyezése.|  
|**Google-fiók automatikus szinkronizálása**|Google-fiókbeállítások automatikus szinkronizálásának engedélyezése.|  

### <a name="security"></a>Biztonság  

|Beállítás|Részletek|  
|-------------|-------------|  
|**SMS- és MMS-üzenetek**|Engedélyezi, hogy az SMS-és MMS-üzenetek az eszközön.|
|**Cserélhető tároló**|Lehetővé teszi, hogy az eszköz használatát a cserélhető tároló, például SD-kártya.|
|**Fényképezőgép**|Engedélyezi az eszköz kamerájának használatát.<br /><br /> Az Android- és Samsung KNOX-eszközökre vonatkozik.|
|**Kis hatótávolságú kommunikáció (NFC)**|Lehetővé teszi, hogy ha az eszköz támogatja kis hatótávolságú kommunikációt használó feladatok.|
|**A YouTube használatának**|A YouTube alkalmazás használatának engedélyezése az eszközön.<br /><br /> Csak a Samsung KNOX-eszközökre vonatkozik.|  
|**Kikapcsolás**|Az eszköz kikapcsolásának engedélyezése.<br /><br /> Csak a Samsung KNOX-eszközökre vonatkozik.|  

### <a name="roaming"></a>Barangolás

|Beállítás|Részletek|  
|-------------|-------------|  
|Hangroaming|Hangroaming használatának engedélyezése, ha az eszköz mobilhálózathoz.|
|Adatroaming|Ha az eszköz mobilhálózathoz adatroaming használatának engedélyezése.|


### <a name="encryption"></a>Titkosítás  
 Ezek a beállítások az Android- és a Samsung KNOX-eszközökre egyaránt érvényesek.  

|Beállítás|Részletek|  
|-------------|-------------|  
|**Memóriakártya titkosítása**|Megköveteli, hogy az eszköz tárolókártyájának van titkosítva.|
|**Fájlok titkosítása az eszközön**|A mobileszközön található összes fájlnak titkosítva kell lennie.|  

### <a name="wireless-communications"></a>Vezeték nélküli kommunikáció

|Beállítás|Részletek|  
|-------------|-------------|  
|**Vezeték nélküli hálózati kapcsolat**|Lehetővé teszi az eszköz Wi-Fi funkcióinak használatát.|
|**Wi-Fi tethering**|Engedélyezi, hogy a Wi-Fi alapú internetmegosztás az eszközön.|


### <a name="compliant-and-noncompliant-apps-android"></a>Megfelelő és nem megfelelő alkalmazások (Android)  
Megadhatja, hogy a kompatibilis vagy nem felelnek meg vállalata Android-alkalmazások listáját. Jelentések megjelenítése eszközökre, amelyeken nem megfelelő alkalmazásokat telepítettek, és a társított felhasználói majd használni.  

Egyazon konfigurációelemben nem adhatók meg egyszerre megfelelő és nem megfelelő alkalmazások is.  

#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>A megfelelő vagy a nem megfelelő alkalmazások listájának megadása  

A **Megfelelő és nem megfelelő alkalmazások (Android)** lapon adja meg a következő információkat:  

|Beállítás|További információ|  
|-------------|----------------------|  
|**Nem megfelelő alkalmazások listája**|Nem megfelelő, ha a felhasználók által telepített alkalmazásokat, amelyek készül listáját adja meg.|  
|**Megfelelő alkalmazások listája**|Itt adhatja meg azokat az alkalmazásokat, amelyeket a felhasználók telepítéséhez. A listán nem szereplő alkalmazások telepítéséről jelentés készül.|  
|**Hozzáadás**|Hozzáadhat egy alkalmazást a kijelölt listához. Adjon meg egy szabadon választott nevet és opcionálisan az alkalmazás kiadóját, valamint az alkalmazás alkalmazás-áruházbeli URL-címét.<br /><br /> Megadható az URL-címet, a [Google Play alkalmazások szakaszában](https://play.google.com/store/apps), keresse meg a használni kívánt alkalmazást.<br /><br /> Nyissa meg az alkalmazás lapját, és másolja az URL-címet a vágólapra. Most ezt a címet felhasználhatja URL-címként a kompatibilis vagy a nem kompatibilis alkalmazások listájában.<br /><br /> **Példa:** Google Play áruházban a Keresés **Microsoft Office Mobile**. A használt URL-címet fog **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.|  
|**Szerkesztés**|Lehetővé teszi a nevét, kiadóját és URL-címe a kiválasztott alkalmazás szerkesztése.|  
|**Eltávolítás**|Törölheti a kijelölt alkalmazást a listából.|  
|**Importálásálás**|Importálhatja azokat az alkalmazásokat, amelyek egy vesszővel tagolt fájlban megadott. A formátum: Alkalmazásnév, kiadó, alkalmazás URL-CÍMÉT, a fájl használatára.|  

## <a name="android-for-work-configuration-items"></a>Android a munkahelyi konfigurációs elemek
Android for Work van két beállítás a konfigurációelemhez:

- **Jelszó**. Azonos beállítások Android "klasszikus".

- **Munkahelyi profil**. Lehetővé teszi, hogy a következő Android for Work beállításait:
  -    **Adatok munkahelyi és személyes profilok közötti megosztásának engedélyezése**
  - **A munkahelyi profil értesítések elrejtése, amikor az eszköz zárolva van** (Android 6.0 +)
  -    **Állítsa be alapértelmezett engedély alkalmazásszabályzat** (Android 6.0 +)

Az Androidos munkahelyi profil konfigurációs elem létrehozásához válassza a **Android for Work** a a **általános** lapon, és minden beállítás csoport beállításainak konfigurálása. Adja hozzá a konfigurálási elemet alapkonfigurációt, majd a szokásos módon telepítheti. Ezek a beállítások csak Android for Work, regisztrált eszközök megjelenítéséhez, és nem regisztrált, Android-eszközökhöz vonatkoznak.

### <a name="kiosk-mode-samsung-knox-only"></a>Kioszkmód (csak Samsung KNOX)  
Teljes képernyős mód segítségével az eszközök zárolását, hogy csak bizonyos szolgáltatások működjenek rajtuk. Például az eszköz csak egy felügyelt alkalmazás futtatását engedélyezze, vagy letilthatja a hangerő-szabályozó gombok az eszközön. Ezek a beállítások használhatók például egy eszköz bemutató modelljéhez. Vagy előfordulhat, hogy egy eszköz, például egy pénztári eszköz csak egyetlen funkció végrehajtására van kijelölve használni őket.  

#### <a name="to-configure-kiosk-mode-for-a-samsung-knox-device"></a>A kioszkmód konfigurálása Samsung KNOX-eszközön  

1. Az a **kioszk mód beállításainak konfigurálása Samsung KNOX-eszközök** lap a Konfigurációelem létrehozása varázsló, adja meg a következő adatokat:  

   |Beállítás|További információ|  
   |-------------|----------------------|  
   |**Alkalmazás kiválasztása**|Válasszon **Tallózás** Configuration Manager Android alkalmazást választhat ki (kiterjesztésű **.apk**), amelynek engedélyezni szeretné a futtatását, amikor az eszköz kioszk módban van. Az itt megadotton kívül más alkalmazás nem futtatható az eszközön.|  
   |**Hangerőszabályzó gombok**|Engedélyezheti vagy letilthatja a hangerőszabályzó gombok használatát az eszközön.|  
   |**Képernyőalvás és -Ébresztés gomb**|Engedélyezheti vagy letilthatja a képernyő ébresztőgombját az eszközön.|  

2. Ha elkészült, válassza ki a **következő**.  

## <a name="reports-for-monitoring"></a>Figyelés a jelentések
Megfelelő és nem megfelelő alkalmazások figyelése a következő jelentések egyikét használhatja:  

- **Nem megfelelő alkalmazásainak és eszközeinek egy adott felhasználó listája**. Felhasználók és eszközök olyan telepített alkalmazásokkal rendelkeznek, amelyek nem felelnek meg a megadott házirendnek információkat jeleníti meg.  

- **Nem megfelelő alkalmazásokkal rendelkező felhasználók összegzése**. Kik telepítették az alkalmazásokat, amelyek nem felelnek meg a megadott házirendnek információkat jeleníti meg.  

A jelentések használatára vonatkozó információért lásd: [Jelentéskészítés a System Center Configuration Managerben](../../core/servers/manage/reporting.md).  

## <a name="see-also"></a>További információ  
[A System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt eszközök konfigurációelemei](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)

