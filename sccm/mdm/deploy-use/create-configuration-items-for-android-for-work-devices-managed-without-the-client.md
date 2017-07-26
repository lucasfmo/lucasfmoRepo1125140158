---
title: "Konfigurációelemek létrehozása Androidhoz készült Intune-nal kezelt munkahelyi eszközök"
ms.custom: na
ms.date: 2017-03-28
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab6784fd-8c57-4be9-858f-50fe39f2ff5f
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
translation.priority.ht:
- cs-cz
- de-de
- en-gb
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: e6170339b8f3354c549579f127a5c3c618833943
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-create-configuration-items-for-android-for-work-devices-managed-with-intune"></a>Konfigurációelemek létrehozása Androidhoz készült Intune-nal kezelt munkahelyi eszközök
  
 A System Center Configuration Manager használata **Android for Work** konfigurációs elem beállításait az Androidos munkahelyi regisztrált eszközök esetében a Microsoft Intune vagy a helyszínen felügyelt Configuration Manager kezelheti.  
  
### <a name="to-create-an-android-for-work-configuration-item"></a>Egy Android munkahelyi konfigurációs elem létrehozása  
  
1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség**.  
  
2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki a **Megfelelőségi beállítások**csomópontot, majd kattintson a **Konfigurációelemek**lehetőségre.  
  
3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  
  
4.  A **Konfigurációelem létrehozása varázsló** **Általános**lapján adja meg a konfigurációelem nevét és leírását (utóbbi nem kötelező).  
  
5.  A **adja meg a létrehozandó konfigurációelem típusát**, jelölje be **Android for Work**.  
  
6.  Kattintson a **kategóriák** Ha létrehozni és hozzárendelni kategóriákat szeretne kereséséhez és szűréséhez konfigurációs elemek a Configuration Manager konzolon.  
  
7.  A varázsló **Eszközbeállítások** lapján jelölje ki a konfigurálni kívánt beállításcsoportot. Részletekért tekintse meg ezen témakör **Útmutató az Android- és Samsung KNOX-eszközökhöz készült konfigurációelemek beállításaihoz** című szakaszát, majd kattintson a **Tovább** gombra.  
  
    > [!TIP]  
    >  Ha nem találja a kívánt beállítást, jelölje be a **További olyan beállítások konfigurálása, amelyek nem találhatók meg az alapértelmezett beállítási csoportokban** jelölőnégyzetet.  
  
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
  
##  <a name="android-for-work-configuration-item-settings-reference"></a>Android a munkahelyi konfigurációs elem beállításainak ismertetése  
  
### <a name="password"></a>Jelszó  
   
|Beállítás|Részletek|  
|-------------|-------------|  
|**Jelszóbeállítások megkövetelése az eszközökön**|Jelszó kérése a támogatott eszközökön.|  
|**Jelszó minimális hossza (karakter)**|A jelszó minimális hossza.|  
|**Jelszó lejárati ideje napokban**|Azon napok száma, amely után a jelszót kötelező megváltoztatni.|  
|**Megjegyzett jelszavak száma**|Megakadályozza a korábban használt jelszavak használatát.|  
|**Sikertelen bejelentkezési próbálkozások száma az eszköz törlése előtt**|A megadott számú sikertelen bejelentkezési kísérlet után törli az eszközt.|  
|**Üresjárati idő után az eszköz zárolva van**|Kiválaszthatja, hogy mennyi idő elteltével zárolja a rendszer az eszközt, ha nincs használatban.|
|**Jelszó minősége**|Válassza ki a jelszó erősségének szintjét, valamint hogy használható-e biometrikus eszköz.|  
|**Smart Lock és más megbízhatósági ügynökök engedélyezése**|A kompatibilis Android-eszközökön vezérelheti az intelligens zárolás funkciót. Ez a „megbízhatósági ügynökök” néven is ismert telefonos funkció lehetővé teszi az eszköz zárolási képernyője jelszavának letiltását vagy megkerülését, ha az eszköz megbízható helyen van, például ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címkéhez van közel. Ezzel a beállítással megakadályozhatja a végfelhasználók számára a Smart Lock konfigurálását.|
|**Zárolás feloldása ujjlenyomattal**||
  
###  <a name="work-profile"></a>A munkahelyi profil  
 Ezek a beállítások csak a Samsung KNOX-eszközökre vonatkoznak.  
  
|Beállítás neve|Részletek|  
|------------------|-------------|  
|**Adatok munkahelyi és személyes profilok közötti megosztásának engedélyezése**|A következő lehetőségek közül választhat:<br>- **Nincs konfigurálva**<br>- **Meg kell akadályozni a határokon keresztül történő megosztását**<br>- **Alkalmazások munkahelyi profil képes kezelni a kérést, személyes profilból**<br>- **Nincs korlátozás az megosztása**<br>|  
|**A munkahelyi profil értesítések elrejtése, ha az eszköz zárolt (Android 6.0 +)**||
|**Állítsa be az alapértelmezett engedélyt szabályzat (Android 6.0 +)**|A következő lehetőségek közül választhat:<br>- **Nincs konfigurálva**<br>- **Mindig megkérdezi a felhasználót**<br>- **Automatikus támogatás**<br>- **Automatikus megtagadása**|
  
 
## <a name="see-also"></a>Lásd még:  
 [A System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt eszközök konfigurációelemei](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
