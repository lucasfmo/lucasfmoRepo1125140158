---
title: "System Center Configuration Manager-alkalmazásokkal kapcsolatos felügyeleti feladatok |} Microsoft Docs"
description: "System Center Configuration Manager-alkalmazások és központi telepítési típusok kezelése."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4041e21-21ff-4d95-ab05-14007e0047cf
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a53f8ca0cc9c4e4f7d91dd4a08eeea76cbd0b142
ms.openlocfilehash: 72f99f0c90951f80de3d6e5ed8786d3fa482107e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="management-tasks-for-system-center-configuration-manager-applications"></a>A System Center Configuration Manager-alkalmazásokkal kapcsolatos felügyeleti feladatok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ebben a cikkben információk használatával alakítsa ki a System Center Configuration Manager-alkalmazások és központi telepítési típusok kezelése.  

Alkalmazások és központi telepítési típusok létrehozásával kapcsolatban lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md).  

> [!IMPORTANT]  
>  Attól függően, hogy az alkalmazás vagy központi telepítési típus egyes felügyeleti lehetőségek nem feltétlenül érhető el.  

##  <a name="manage-applications"></a>Alkalmazások kezelése  
 Az a **szoftverkönyvtár** munkaterületet, bontsa ki a **Alkalmazáskezelés** > **alkalmazások**, és válassza ki a kezelendő alkalmazást, majd válassza a kezelési feladatot.  

|Feladat|Részletek|  
|----------|-------------|  
|**Elérési fiókok kezelése**|Megjeleníti azt a **Hozzáférési fiókok kezelése** párbeszédpanelt, amelyiken megadhatja a kijelölt alkalmazáshoz társított tartalom megengedett hozzáférési szintjét.|  
|**Előkészített tartalom fájljának létrehozása**|Megjeleníti azt a **Manuálisan előkészített tartalomfájl létrehozása varázsló** párbeszédpanelt, amelyik segíti a tartalom távoli terjesztési pontokra terjesztését. Amikor a távoli terjesztési ponthoz az ütemezés és a szabályozás nem biztosít érvényes megoldást, a tartalom előkészíthető a terjesztési ponton.<br /><br /> Lásd: [tartalom és tartalomkezelési infrastruktúra kezelése](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Változat-nyilvántartás**|Megnyitja a **alkalmazás változat-nyilvántartása** , amely lehetővé teszi az alkalmazáson végzett az alkalmazás tulajdonságainak megtekintése, régi alkalmazásváltozatok törlése és az alkalmazás régi változatainak visszaállítása párbeszédpanel.<br /><br /> Lásd: [alkalmazások módosítása és felülírása hogyan](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Központi telepítési típus létrehozása**|Megnyitja a **központi telepítési típus varázsló** , amely lehetővé teszi egy új központi telepítési típus hozzáadni a kijelölt alkalmazáshoz.<br /><br /> Lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md).|  
|**Statisztika frissítése**|Frissíti a jelen alkalmazás központi telepítésére vonatkozó adatok megjelenítését a **Figyelés** munkaterület **Központi telepítések** csomópontjában.<br /><br /> Lásd: [figyelése a System Center Configuration Manager konzolról alkalmazások](../../apps/deploy-use/monitor-applications-from-the-console.md).|  
|**Visszaállítás**|Olyan alkalmazás, amely korábban reinstates a **kivonás** kezelési feladatot.|  
|**Kivonás**|Ha kivont egy alkalmazást, már nem elérhető a telepítéshez, de az alkalmazás és a telepített alkalmazást nem törlődnek. Az alkalmazásnak az ügyfélgépekre telepített példányai nem lesznek eltávolítva. 60 nap után az alkalmazás minden változata törlődik a Configuration Managerből. Azonban, a rendszer nem távolítja el az alkalmazás telepített példánya.<br /><br /> Törli az alkalmazást, akkor kell először kivonása az alkalmazás, összes telepítést törölni, távolítsa el az alkalmazás mutató hivatkozások más központi, és törölje a alkalmazásváltozatok mindegyikét.<br /><br /> Lásd: [felülvizsgálata és az alkalmazások helyettesítéséről](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Exportálásálás**|Megnyitja a **alkalmazás exportálása varázslót** , amely lehetővé olyan .zip fájlba, hogy archiválhat, vagy telepíthet másik helyre a kijelölt alkalmazások exportálását. Szeretné exportálni az alkalmazás tartalmát, ha létrejön egy mappa, amely a tartalmat.<br /><br /> Alkalmazásfüggőség, helyettesítési kapcsolat és feltételek és az alkalmazás és annak függőségeit tartalmának emellett exportálhatja.<br /><br /> A Windows PowerShell-parancsmag **Export-CMApplication**, does ugyanezt a funkciót. További információkért lásd: [Export-CMApplication](http://go.microsoft.com/fwlink/p/?LinkID=258880) a Microsoft System Center 2012 Configuration Manager SP1 parancsmag hivatkozás dokumentációjában.|  
|**Törlés**|Törli az aktuálisan kijelölt alkalmazást.<br /><br /> Nem törölhető az alkalmazás, ha más alkalmazás függ tőle, ha van aktív központi telepítése, illetve ha van függő feladatütemezése.|  
|**Központi telepítés szimulálása**|Megjeleníti az **Alkalmazás-központitelepítés szimulálása varázslót** , amelyikkel az alkalmazás számítógépre telepítése és eltávolítása nélkül lehet tesztelni az alkalmazások központi telepítését.<br /><br /> Lásd: [alkalmazások központi telepítésének szimulálása](../../apps/deploy-use/simulate-application-deployments.md).|  
|**Telepítés**|Megjeleníti a **Szoftver központi telepítése varázslót** , amelyikkel a kijelölt alkalmazást a hierarchiában lévő gyűjtemény számítógépeire lehet központilag telepíteni.<br /><br /> Lásd: [telepíthet központilag alkalmazásokat](../../apps/deploy-use/deploy-applications.md).|  
|**Tartalom terjesztése**|Megjeleníti a **Tartalom terjesztése varázslót** , amelyikkel a kijelölt alkalmazás tartalmát a hierarchiában lévő terjesztési pontokra lehet másolni.<br /><br /> Lásd: [tartalom és tartalomkezelési infrastruktúra kezelése](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Kapcsolatok megtekintése**|A kijelölt alkalmazások más alkalmazások közötti kapcsolatokat ábrázoló diagram grafikus jeleníti meg. Választhatja a következők egyikét:<br><br><ul><li>**A függőségi** – a kijelölt alkalmazás és az alkalmazások, a kijelölt alkalmazástól függőket függő alkalmazásokat jeleníti meg.</li><li>**Helyettesítési** – a kijelölt alkalmazást felülíró alkalmazások és a kijelölt alkalmazást felülíró alkalmazások jeleníti meg.</li><li>**Globális feltételek** – a jelen alkalmazás által hivatkozott globális feltételeket mutatja.</li></ol><br /> Lásd: [felülvizsgálata és az alkalmazások helyettesítéséről](../../apps/deploy-use/revise-and-supersede-applications.md) és [globális feltételek létrehozása](../../apps/deploy-use/create-global-conditions.md).|  

##  <a name="manage-deployment-types"></a>Központi telepítések típusainak kezelése  
 Az a **szoftverkönyvtár** munkaterületet, bontsa ki a **Alkalmazáskezelés**, válassza a **alkalmazások**, és válassza ki a kezelni kívánt központi telepítési típust az alkalmazás. A részleteket tartalmazó ablaktáblán válassza ki a **központi telepítési típusok** lapon válassza ki a kezelni kívánt központi telepítési típust, és válassza a kezelési feladatot.  

|Feladat|Részletek|  
|----------|-------------|  
|**Prioritás növelése**|Növeli a kijelölt központi telepítési típus prioritását. A központi telepítési típusok kiértékelése sorrendben történik. Ha a központi telepítési típus megfelel a megadott követelményeknek, megkezdi a futást, és majd a prioritási listán lévő további központi telepítési típusa akkor lesz kiértékelve.|  
|**Prioritás csökkentése**|Csökkenti a kijelölt központi telepítési típus prioritását.|  
|**Törlés**|Törli a kijelölt központi telepítési típust.<br><br>A kijelölt központi telepítési típus nem törölhető, ha más alkalmazásban lévő központi telepítési típus hivatkozik rá.<br>A központi telepítési típus törléséhez el kell távolítania a központi telepítési típus minden más központi telepítési típusok a függőségeket.<br>Ezenkívül el kell távolítani a korábbi változatait minden alkalmazás, amely egy központi telepítési típus, amely a törölni kívánt központi telepítési típus hivatkozik.|  
|**Tartalom frissítése**|Frissíti a kijelölt központi telepítési típus tartalmát.<br /><br /> Ezt a varázslót a központi telepítési típus, egy virtuális alkalmazást, amelynek elindításakor a **tartalom frissítése varázsló** elindult. Ez a varázsló lehetővé teszi közzétételi beállításainak és követelményszabályainak a kijelölt virtuális alkalmazás. További információkért lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md).<br /><br /> Központi telepítési típus tartalmának frissítésekor létrejön az alkalmazás új változata. Ez azt eredményezheti, hogy az ügyféleszközök frissítve lesznek az új alkalmazással.|  

