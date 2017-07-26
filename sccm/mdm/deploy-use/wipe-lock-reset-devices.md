---
title: "Távoli törléssel, zárolással vagy PIN-kód cserével System Center Configuration Manager segítségével az adatok védelme |} Microsoft Docs"
description: "Teljes törlést, szelektív törléssel, távoli zárolás vagy PIN-kód alaphelyzetbe állítását a System Center Configuration Manager eszköz adatok védelméhez."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 770da7bd-02dd-474a-9604-93ff1ea0c1e4
caps.latest.revision: 18
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dda2f4c01078fbbd174cbcb30357554c24f6abeb
ms.openlocfilehash: 351fdc6328dd0859d60e00b128963df738e69f81
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="protect-data-with-remote-wipe-lock-or-passcode-reset-by-using-system-center-configuration-manager"></a>Távoli törléssel, zárolással vagy PIN-kód cserével System Center Configuration Manager segítségével az adatok védelme

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

System Center Configuration Manager biztosít a szelektív törlést, teljes törlést, távoli zárolással és PIN-kód alaphelyzetbe állíthatja a. A mobil eszközök bizalmas vállalati adatokat tárolhatnak, és számos vállalati erőforrás elérését tehetik lehetővé. Eszközök védelme érdekében kiadhatja:  

- Teljes törlést kezdeményezhet az eszköz gyári állapotának visszaállításához.  

- Szelektív törlést kedvezményezhet csak a vállalati adatok eltávolításához.  

- Távoli zárolást kezdeményezhet az elveszett eszközök biztonságba helyezéséhez.  

- Az eszköz PIN-kód alaphelyzetbe állítása.  

## <a name="full-wipe"></a>Teljes törlés  
Törlési parancs kiadására akkor lehet szükség, ha szeretné megvédeni egy elveszett eszköz adatait, vagy ha kivon egy eszközt a használatból.  

**Teljes törlés** indításával visszaállíthatja az eszköz gyári állapotát. Ez eltávolítja az összes vállalati és felhasználói adatot, illetve beállítást. A teljes törlést Windows Phone, iOS, Android és Windows 10 rendszerű eszközökön végezhet.  

> [!NOTE]
> Windows 10-eszközök kisebb, mint 4 GB memóriával rendelkező 1511-es verziónál korábbi verzióin törlése Előfordulhat, hogy hagyja meg az eszköz nem válaszol. [További információk](https://technet.microsoft.com/library/mt592024.aspx#full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram).

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Összes adat távoli törlésének kezdeményezése a Configuration Manager konzolról  

1. Kattintson a Configuration Manager konzol **eszközök és megfelelőség** válassza **eszközök**. Választhatja azt is megteheti, **Eszközgyűjtemények** és kiválaszthat egy gyűjteményt.  

2. Válassza ki az eszközt, amelyet ki szeretne vonni, illetve le szeretné törölni az összes adatot róla.  

3. Válasszon **távoli eszközök műveletei** a **eszközcsoport**, és válassza a **eltávolítási és törlési**.  

## <a name="selective-wipe"></a>Szelektív törlés  
**Szelektív törlés** indításával eltávolíthatja csak a vállalati adatokat egy eszközről. A következő táblázat ismerteti, által platformhoz, milyen adatokat távolítja el, és milyen hatása a szelektív eltávolítást követően az eszközön maradó adatokra.  

**iOS**  

|Ön éppen az eszköz kivonásakor törölt tartalmak|iOS|  
|--------------------------------------------|---------|  
|Vállalati alkalmazások és a Configuration Manager és az Intune által telepített egyéb vonatkozó adatok|Törlődnek az alkalmazások. Törlődnek a vállalati alkalmazásadatok.|  
|VPN- és Wi-Fi profilok|Eltávolítva.|  
|Tanúsítványok|Eltávolítva és visszavonva.|  
|Beállítások|Eltávolítva, kivéve a(z): **Hangroaming engedélyezése**, **adatroaming használatának engedélyezése**, és **automatikus szinkronizálás engedélyezése roaming közben**.|  
|Kezelőügynök|Törlődik a felügyeleti profil.|  
|E-mail profilok|Az Intune által létrehozott e-mail-profilok az e-mail fiókot és az e-mailek törlődnek.|  

**Android- és Android Samsung KNOX szabvány**  

|Ön éppen az eszköz kivonásakor törölt tartalmak|Android|Samsung KNOX szabvány|  
|--------------------------------------------|-------------|------------------|  
|Vállalati alkalmazások és a Configuration Manager és az Intune által telepített egyéb vonatkozó adatok|A telepített alkalmazások és azok adatai megmaradnak.|Törlődnek az alkalmazások.|  
|VPN- és Wi-Fi profilok|Eltávolítva.|Eltávolítva.|  
|Tanúsítványok|Visszavonva.|Visszavonva.|  
|Beállítások|A rendszer eltávolítja a követelményeknek.|A rendszer eltávolítja a követelményeknek.|  
|Kezelőügynök|Visszavonódik az eszköz-rendszergazdai jogosultság.|Visszavonódik az eszköz-rendszergazdai jogosultság.|  
|E-mail profilok|Nem alkalmazható.|Az Intune által létrehozott e-mail-profilok az e-mail fiókot és az e-mailek törlődnek.|  

**Android for Work**

Ennek során a szelektív törlést az eszköz munkahelyi egy Android eltávolítja a munkahelyi profil adatok, alkalmazások és beállítások mellett a munkahelyi profil azokon az eszközökön. A Configuration Manager és az Intune-felügyelet ez kivonja az eszközt. Teljes törlés Android for Work nem támogatott.

 **Windows 10, Windows 8.1, Windows RT 8.1 és Windows RT**  

|Ön éppen az eszköz kivonásakor törölt tartalmak|Windows 10, Windows 8.1 és Windows RT 8.1|  
|---------------------------------|-------------|
|Vállalati alkalmazások és a Configuration Manager és az Intune által telepített egyéb vonatkozó adatok|Az alkalmazások és a közvetlen telepítési kulcsok el lesznek távolítva. Alkalmazások, amelyek használják a Windows szelektív törlés lesz a titkosítási kulcs visszavonása, és adatokat már nem lesz elérhető.|  
|VPN- és Wi-Fi profilok|Eltávolítva.|  
|Tanúsítványok|Eltávolítva és visszavonva.|  
|Beállítások|A rendszer eltávolítja a követelményeknek.|
|Kezelőügynök|Nem alkalmazható. Felügyeleti ügynök beépített.|  
|E-mail profilok|E-mailek, az EFS-kompatibilis eltávolítják, mely tartalmazza a Windows e-mailek és mellékletek Posta alkalmazásban.|  

 **A Windows 10 Mobile, Windows Phone 8.0 és Windows Phone 8.1**

|Ön éppen az eszköz kivonásakor törölt tartalmak|A Windows 10 Mobile, Windows Phone 8 és Windows Phone 8.1|  
|-|-|
|Vállalati alkalmazások és a Configuration Manager és az Intune által telepített egyéb vonatkozó adatok|Törlődnek az alkalmazások. Törlődnek a vállalati alkalmazásadatok.|  
|VPN- és Wi-Fi profilok|A Windows 10 Mobile és Windows Phone 8.1 eltávolítva.|  
|Tanúsítványok|A Windows Phone 8.1-ből eltávolítva.|  
|Kezelőügynök|Nem alkalmazható. Felügyeleti ügynök beépített.|  
|E-mail profilok|(Kivéve a Windows Phone 8.0-s) eltávolítása.|  

A következő beállításokat is el lesznek távolítva a Windows 10 Mobile és Windows Phone 8.1 rendszerű eszközökön:  

- **A mobileszközök zárolásának feloldásához jelszó szükséges**  
- **Egyszerű jelszavak engedélyezése**  
- **Jelszó minimális hossza**  
- **Jelszó kötelező típusa**
- **Jelszó lejárata (nap)**  
- **Korábbi jelszavak megjegyzése**  
- **Ismétlődő sikertelen bejelentkezés az eszközön tárolt adatok törléséig való száma**  
- **Ennyi perc inaktivitás után kell jelszót beírni**  
- **Megkövetelt jelszótípus – karakterkészletek minimális száma**  
- **Kamera használatának engedélyezése**
- **Mobileszköz titkosításának kötelezővé tétele**  
- **Cserélhető tároló engedélyezése**  
- **Webböngésző engedélyezése**  
- **Alkalmazás-áruház engedélyezése**  
- **Képernyőfelvétel-készítés engedélyezése**  
- **Földrajzi hely meghatározásának engedélyezése**  
- **Microsoft-fiók használatának engedélyezése**  
- **Másolás és Beillesztés engedélyezése**  
- **Wi-Fi alapú internetmegosztás használatának engedélyezése**  
- **Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése**  
- **Wi-Fi elérési pontok jelentésének engedélyezése**  
- **Gyári beállítások visszaállításának engedélyezése**
- **Bluetooth használatának engedélyezése**  
- **NFC használatának engedélyezése**
- **Wi-Fi használatának engedélyezése**

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Összes adat távoli törlésének kezdeményezése a Configuration Manager konzolról  

1. Kattintson a Configuration Manager konzol **eszközök és megfelelőség** válassza **eszközök**. Választhatja azt is megteheti, **Eszközgyűjtemények** és kiválaszthat egy gyűjteményt.  

2. Válassza ki az eszközt, amelyet ki szeretne vonni, illetve le szeretné törölni az összes adatot róla.  

3. Válasszon **távoli eszközök műveletei** a **eszközcsoport**, és válassza a **eltávolítási és törlési**.  

## <a name="wiping-efs-enabled-content"></a>Az EFS által védett tartalom törlése  
Windows 8.1 és Windows RT 8.1 támogatja a titkosított fájlrendszer EFS által védett tartalom szelektív törlését. Az EFS által védett tartalom szelektív törlése az alábbiak szerint működik:  

- Csak az alkalmazások és az Intune-fiókkal megegyező internetes tartományba keresztül az EFS által védett adatok szelektív törlése. További információ: [Eszközadatok törlése a Windows szelektív törlési funkciójával](http://technet.microsoft.com/library/dn486874.aspx).  

- Ha végzett módosítások EFS társított tartományhoz, a módosítások a előtt alkalmazások akár 48 órát is igénybe vehet, és az új tartományt használó adatok szelektív törlése lehetséges.  

- Az Intune-nal regisztrált valamennyi tartományt törli a tartományban.  

Adatok és alkalmazások, hogy az EFS szelektív törlési jelenleg támogatja a következők:  

- A Windows Posta alkalmazásban.  

- Munkahelyi mappák.

- Az EFS által titkosított fájlok és mappák. További információ: [Gyakorlati tanácsok a titkosított fájlrendszerhez](http://support.microsoft.com/kb/223316)  

### <a name="best-practices-for-selective-wipe"></a>Gyakorlati tanácsok szelektív törléshez  

- E-mailek sikeres törléséhez állítsa be e-mail profilokat az iOS és Windows Phone 8.1 rendszerű eszközökön.  

- Alkalmazások sikeres törléséhez győződjön meg arról, hogy az alkalmazások mobilalkalmazás-felügyeleti keresztül jutnak el.  

- Az iOS, a beállítás konfigurálásával **Icloudba történő biztonsági mentés engedélyezése** való **Disallow** , hogy a felhasználók iCloud segítségével lehessen helyreállítani az adatokat.  

- Ha fiók ki lett kapcsolva, majd egy év után Intune fogja vonni a fiók, és szelektív törlésre kerül sor.  

##  <a name="passcode-reset"></a>Jelszó alaphelyzetbe állítása  
Ha egy felhasználó elfelejti a PIN-kódját, segítségként eltávolíthatja a PIN-kódot az eszközről, vagy új ideiglenes PIN-kódot kényszeríthet az eszközre. Az alábbi táblázatban áttekintheti, hogyan PIN-kód működik az egyes mobilplatformokon.  

|Platform|Jelszó alaphelyzetbe állítása|  
|--------------|--------------------|  
|iOS|Csak a PIN-kód eszközről való törlése támogatott. Nem lehet új ideiglenes PIN-kódot létrehozni.|
|macOS| Nem támogatott.|
|Android|Támogatott, és ideiglenes PIN-kód jön létre.|
|Android for Work | Nem támogatott.|
|Windows 10 rendszerű számítógépek|Nem támogatott.|  
|Windows 10 mobile|Támogatott, kivéve az Azure AD csatlakoztatott eszközök.|
|Windows Phone 8.1|Támogatott.|  
|Windows RT 8.1 |Nem támogatott.|  
|Windows 8.1 rendszerű számítógépek |Nem támogatott.|  

#### <a name="to-reset-the-passcode-on-a-mobile-device-remotely-in-configuration-manager"></a>A PIN-kód cseréje a távoli mobileszközön a Configuration Managerből  

1. Kattintson a Configuration Manager konzol **eszközök és megfelelőség** válassza **eszközök**. Választhatja azt is megteheti, **Eszközgyűjtemények** és kiválaszthat egy gyűjteményt.  

2. Válassza ki azt az eszközt vagy eszközöket, amelye(ke)n le kívánja cserélni a PIN-kódot.  

3. Válasszon **távoli eszközök műveletei** a **eszközcsoport**, és válassza a **jelszó alaphelyzetbe állítása**.  

#### <a name="to-show-the-state-of-the-passcode-reset"></a>A PIN-kódcsere állapotának megjelenítése  

1. Kattintson a Configuration Manager konzol **eszközök és megfelelőség** válassza **eszközök**. Választhatja azt is megteheti, **Eszközgyűjtemények** és kiválaszthat egy gyűjteményt.  

2. Válassza ki azt az eszközt vagy eszközöket, amely(ek) esetében meg szeretné jeleníteni a PIN-kódcsere állapotát.  

3. Válasszon **távoli eszközök műveletei** a **eszközcsoport**, és válassza a **jelszó állapotának megtekintése**.  

## <a name="remote-lock"></a>Távoli zárolás  
Ha a felhasználó elveszíti az eszközeiket, távolról zárolhatja az eszközt. Az alábbi táblázatban áttekintheti, hogy hogyan működik a távoli zárolás az egyes mobilplatformokon.  

|Platform|Távoli zárolás|  
|--------------|-----------------|  
|iOS|Támogatott.|  
|Android|Támogatott.|  
|Windows 10|Jelenleg nem támogatott.|  
|Windows Phone 8 és Windows Phone 8.1|Támogatott.|  
|Windows RT 8.1 |Támogatott, ha az eszköz aktuális felhasználója megegyezik az eszközt beléptető felhasználóval.|  
|Windows 8.1|Támogatott, ha az eszköz aktuális felhasználója megegyezik az eszközt beléptető felhasználóval.|  

#### <a name="to-lock-a-mobile-device-remotely-through-the-configuration-manager-console"></a>Mobileszköz zárolása távolról, a Configuration Manager konzoljáról  

1. Kattintson a Configuration Manager konzol **eszközök és megfelelőség** válassza **eszközök**. Választhatja azt is megteheti, **Eszközgyűjtemények** és kiválaszthat egy gyűjteményt.  

2. Válassza ki a zárolni kívánt eszközt vagy eszközöket.  

3. Válasszon **távoli eszközök műveletei** a **eszközcsoport**, és válassza a **távoli zárolás**.  

#### <a name="to-show-the-state-of-the-remote-lock"></a>A távoli zárolás állapotának megjelenítése  

1. Kattintson a Configuration Manager konzol **eszközök és megfelelőség** válassza **eszközök**. Választhatja azt is megteheti, **Eszközgyűjtemények** és kiválaszthat egy gyűjteményt.  

2. Válassza ki azt az eszközt, amely esetében meg szeretné jeleníteni a távoli zárolás állapotát.  

3. Válasszon **távoli eszközök műveletei** a **eszközcsoport**, és válassza a **távoli zárolás állapotának megjelenítése**.  

### <a name="see-also"></a>További információ  
[A Windows szelektív Törlés az eszközadatok felügyeletéhez](http://technet.microsoft.com/library/dn486874.aspx)   

