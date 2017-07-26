---
title: "Forgatókönyv Endpoint Protection védi a számítógépek kártevők elleni |} Microsoft Docs"
description: "Megtudhatja, hogyan valósítja meg az Endpoint Protection a Configuration Manager számítógépei védve legyenek a kártevőktől."
ms.custom: na
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 539c7a89-3c03-4571-9cb4-02d455064eeb
caps.latest.revision: 8
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: af0aafb4b7209d840676d16723509f399c662aad
ms.openlocfilehash: b98684d44874ff246e4d675039c6e443aee82a62
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="example-scenario-using-system-center-endpoint-protection-to-protect-computers-from-malware-in-system-center-configuration-manager"></a>Példa: System Center Endpoint Protection használata a számítógépek a System Center Configuration Managerben kártevők elleni védelméhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör egy példán keresztül az, hogy miként implementálható az Endpoint Protection a Configuration Manager egy szervezet számítógépei védve legyenek a kártevőktől.  

 John a Configuration Manager rendszergazdája a Woodgrove bankban. A bank jelenleg használja a System Center Endpoint Protection számítógépek kártevőtámadások elleni védelméhez. Emellett a bank Windows-csoportházirend segítségével biztosítja, hogy a Windows tűzfal engedélyezve legyen a vállalat összes számítógépén, és a felhasználók értesítést kapjanak arról, ha a Windows tűzfal új programot blokkol.  

 Jánost megkérték, a Woodgrove Bank kártevőirtó szoftverek frissítése a System Center Endpoint Protection, hogy a bank kihasználhassa a legújabb kártevőirtó funkciók, és központilag kezelhesse a kártevőirtó megoldást a Configuration Manager konzoljáról lehet. A megvalósítás követelményei az alábbiak:  

-   A Configuration Manager segítségével kezelheti a jelenleg csoportházirend által felügyelt Windows tűzfal beállításait.  

-   Használja a Configuration Manager szoftverfrissítései által letöltheti a kártevő-definíciókat a számítógépekre. Ha nem állnak rendelkezésre szoftverfrissítések, például amikor a számítógép nem csatlakozik a vállalati hálózathoz, a számítógépeknek a Microsoft Update szolgáltatásból kell definíciófrissítéseket letöltenie.  

-   A felhasználók számítógépeinek minden nap gyors kártevő-ellenőrzés kell végrehajtania. A kiszolgálóknak azonban minden szombaton 1 órakor, a munkaidőn kívül teljes vizsgálatot kell futtatniuk.  

-   Értesítő e-mail küldése, valahányszor az alábbi események bármelyike bekövetkezik:  

    -   A kártevőirtó szoftver kártevőt észlelt valamelyik számítógépen  

    -   A kártevőirtó szoftver azonos kártevőt észlelt a számítógépek több mint 5 százalékán  

    -   A kártevőirtó szoftver több mint 5-ször ugyanazt a kártevőt észlelte egy 24 órás időszakban  

    -   A kártevőirtó szoftver 3 különböző típusú kártevőt észlelt egy 24 órás időszakban  

-   A meglévő kártevőirtó megoldás eltávolítása.  

 János az alábbi lépéseket az Endpoint Protection implementálásának hajtja végre:  

##  <a name="steps-to-implement-endpoint-protection"></a>Az Endpoint Protection implementálásának lépései  

|Folyamat|Hivatkozás|  
|-------------|---------------|  
|János áttekinti a rendelkezésre álló információkat főbb fogalmait és kifejezéseit az Endpoint Protection a Configuration Manager alkalmazásban.|Az Endpoint Protection kapcsolatos áttekintő információkat, lásd: [a System Center Configuration Managerben az Endpoint Protection](endpoint-protection.md).|  
|János ellenőrzi és megvalósítja az Endpoint Protection használatához szükséges előfeltételeket.|Az Endpoint Protection előfeltételeivel kapcsolatos további információkért lásd: [az Endpoint Protection tervezése](../plan-design/planning-for-endpoint-protection.md).|  
|John a Woodgrove Bank hierarchiájának tetején a, ha egy helyrendszer-kiszolgálón, csak az Endpoint Protection helyrendszerszerepkör telepítése.|Az Endpoint Protection helyrendszerszerepkör telepítésével kapcsolatos további információkért lásd az "Előfeltételek" [konfigurálása az Endpoint Protection](configure-endpoint-protection.md).|  
|John úgy konfigurálja az e-mail értesítések küldése az SMTP-kiszolgáló segítségével a Configuration Manager.<br /><br /> **Megjegyzés:** Konfigurálnia kell egy SMTP-kiszolgáló csak akkor, ha azt szeretné, az e-mailben értesíti, ha az Endpoint Protection-riasztás jön létre.|További információkért lásd: [riasztások konfigurálása az Endpoint Protection](endpoint-configure-alerts.md).|  
|John létrehoz egy eszközgyűjteményt, amely tartalmazza az összes számítógépet és kiszolgálót az Endpoint Protection-ügyfél telepítéséhez. A gyűjteményt elnevezi **Endpoint Protection által védett összes számítógép**.<br /><br /> **Tipp:** Felhasználógyűjteményekre vonatkozóan nem lehet riasztásokat konfigurálni.|Gyűjtemények létrehozásával kapcsolatos további információkért lásd: [gyűjtemények létrehozása a System Center Configuration Managerben](../../core/clients/manage/collections/create-collections.md)|  
|A gyűjtemény az alábbi riasztásokat konfigurálja: <br /><br />1.) **észlelt kártevő**: John úgy konfigurálja a riasztás fontosságát **kritikus**. <br /><br />2.) **ugyanazt a típusú kártevő észlelhető több számítógépen is előfordult** : John úgy konfigurálja a riasztás fontosságát **kritikus** és megadja, hogy a riasztás akkor jöjjön létre, ha több mint 5 %-a számítógépek kártevő észlelhető. <br /><br />3.) **ugyanazt a típusú kártevő ismételten észlelve egy számítógép adott időszakán belül**: John úgy konfigurálja a riasztás fontosságát **kritikus** és megadja, hogy a riasztás akkor jöjjön létre, amikor a kártevőt több mint 5-ször egy 24 órás időszakban. <br /><br />4.) **több típusú kártevőt észlel az ugyanazon a számítógépen a megadott időtartamon belül**: John úgy konfigurálja a riasztás fontosságát **kritikus** és megadja, hogy a riasztás akkor jöjjön létre, ha egy 24 órás időszakban több mint 3 típusú kártevő akkor jönnek létre.<br /><br /> A következő **riasztás súlyossága** , amely a Configuration Manager konzolon, és az e-mailekben kapott e-mailt megjelenik riasztási szintjét jelzi.<br /><br /> Kiválasztja emellett beállítás **az Endpoint Protection irányítópultjában tekintse meg a gyűjteményt** , hogy figyelhesse a riasztásokat a Configuration Manager konzolon.|Lásd: "Riasztásainak beállítása az Endpoint Protection" [az Endpoint Protection konfigurálása a System Center Configuration Managerben](endpoint-configure-alerts.md).|  
|John úgy konfigurálja a Configuration Manager szoftverfrissítések letöltésére és telepítésére a definíciófrissítések napi háromszori egy automatikus központi telepítési szabály segítségével.|További információkért lásd: a "Használata a Configuration Manager szoftver frissítések to Deliver Definition Updates" című szakaszában [használata a Configuration Manager szoftverfrissítések a definíciófrissítések](endpoint-definitions-configmgr.md).|  
|János megvizsgálja az alapértelmezett kártevőirtó-szabályzat beállításait, amelyek között a Microsoft ajánlott biztonsági beállításai is megtalálhatók. Annak érdekében, hogy a számítógépek minden nap elvégezzenek egy gyors vizsgálatot, az alábbi beállításokat módosítja:<br /><br /> 1.) **napi Gyorsvizsgálat futtatása az ügyfélszámítógépeken**: **Yes**.<br /><br /> 2.) **napi Gyorsvizsgálat ütemezett időpontja**:  **9:00-KOR**.<br /><br /> János látja, hogy **A Microsoft Update rendszerből terjesztett frissítések** a definíciófrissítés forrásaként alapértelmezés szerint ki van választva. Ez teljesíti azt az üzleti követelményt, hogy számítógépeket definíciók letöltése a Microsoft Update amikor nem kapnak a Configuration Manager szoftverfrissítések.|Lásd: [létrehozása és a System Center Configuration Managerben az Endpoint Protection kártevőirtó-házirendek telepítése](endpoint-antimalware-policies.md).|  
|János **Woodgrove Bank-kiszolgálók**néven létrehoz egy gyűjteményt, amelyben csak a Woodgrove Bank kiszolgálói találhatók.|Lásd: [Gyűjtemények létrehozása a System Center Configuration Managerben](../../core/clients/manage/collections/create-collections.md)|  
|János létrehoz egy **Woodgrove Bank-kiszolgálószabályzat**nevű egyéni kártevőirtó-szabályzatot. Csak az **Ütemezett vizsgálatok** beállításait adja meg, és az alábbi módosításokat végzi el:<br /><br /> **Vizsgálat típusa**:  **Teljes**<br /><br /> **Vizsgálat napja**:  **Szombat**<br /><br /> **Vizsgálat ideje**: **13:00:00**<br /><br /> **Napi Gyorsvizsgálat futtatása az ügyfélszámítógépeken**:  **No**.|Lásd: [létrehozása és a System Center Configuration Managerben az Endpoint Protection kártevőirtó-házirendek telepítése](endpoint-antimalware-policies.md).|  
|János telepíti a **Woodgrove Bank-kiszolgálószabályzat** egyéni kártevőirtó-szabályzatot a **Woodgrove Bank-kiszolgálók** gyűjteményhez.|Lásd "a kártevőirtó-házirend központi telepítése ügyfélszámítógépekre" [létrehozásáról és az Endpoint Protection kártevőirtó-házirendek telepítése](endpoint-antimalware-policies.md) témakör.|  
|John hoz létre új egyéni ügyfélbeállításokat az Endpoint Protection eszközbeállítások és elnevezi **Woodgrove Bank Endpoint Protection-beállítások**.<br /><br /> **Megjegyzés:** Ha nem szeretné telepíteni és engedélyezni az Endpoint Protection a hierarchiában található összes ügyfélen, győződjön meg arról, hogy a beállítások **Endpoint Protection ügyfél kezelése az ügyfélszámítógépeken** és **Endpoint Protection ügyfél telepítése az ügyfélszámítógépeken** értéke **nem** az alapértelmezett ügyfélbeállításokban.|További információkért lásd: [egyéni ügyfélbeállítások konfigurálása az Endpoint Protection](endpoint-protection-configure-client.md).|  
|Konfigurálja azokat az Endpoint Protection a következő beállításokat:<br /><br /> **Az Endpoint Protection ügyfél kezelése az ügyfélszámítógépeken**:  **igen**<br /><br /> Ez a beállítás és érték biztosítja, hogy a meglévő Endpoint Protection-ügyfél telepítve van a Configuration Manager által kezelt.<br /><br /> **Endpoint Protection-ügyfél telepítése az ügyfélszámítógépeken**:  **Yes**.<br /><br /> **Automatikusan korábban telepített kártevőirtó szoftver eltávolítása az Endpoint Protection telepítése előtt**:  **Yes**.<br /><br /> Ez teljesíti azt az üzleti követelményt, hogy a meglévő kártevőirtó szoftver eltávolítása, mielőtt az Endpoint Protection telepítve és engedélyezve van.|További információkért lásd: [egyéni ügyfélbeállítások konfigurálása az Endpoint Protection](endpoint-protection-configure-client.md).|  
|János telepíti a **Woodgrove Bank Endpoint Protection-beállítások** ügyfélbeállításokat a **Endpoint Protection által védett összes számítógép** gyűjtemény.|Lásd "Az Endpoint Protection egyéni ügyfélbeállítások konfigurálása" a [az Endpoint Protection konfigurálása a Configuration Manager](endpoint-antimalware-policies.md).|  
|János a Windows tűzfal házirend létrehozása varázslót használva létrehoz egy szabályzatot a tartományprofil alábbi beállításainak konfigurálásával:<br /><br /> 1.) **a Windows tűzfal engedélyezése**: **igen**<br /><br /> 2)<br />                    **A felhasználó értesítése, ha a Windows tűzfal új programot blokkol**: **igen**|Lásd: [létrehozásáról és központi telepítése a Windows tűzfal házirendek Endpoint Protection a System Center Configuration Managerben](../../protect/deploy-use/create-windows-firewall-policies.md)|  
|János telepíti az új tűzfalházirend a gyűjteményben **Endpoint Protection által védett összes számítógép** korábban létrehozott.|"A Windows tűzfal házirend telepítése" című a [létrehozásáról és központi telepítése a Windows tűzfal házirendek Endpoint Protection a System Center Configuration Managerben](create-windows-firewall-policies.md)|  
|János az elérhető felügyeleti feladatait az Endpoint Protection kártevőirtó- és Windows tűzfal házirendek kezelése, hajtsa végre a szükség esetén számítógépek kézi indítású vizsgálatait, kötelezi a számítógépeket a legújabb definíciók letöltésére, és a kártevők észlelésekor végrehajtandó további műveleteket adja meg.|Lásd: [kártevőirtó-házirendek kezelése, és tűzfalbeállítások az Endpoint Protection a System Center Configuration Managerben](endpoint-antimalware-firewall.md)|  
|John a következő módszereket használja, az Endpoint Protection és az Endpoint Protection által végzett műveletek állapotának figyelése:<br /><br /> 1.) segítségével a **Endpoint Protection állapota** csomópontjából **biztonsági** a a **figyelés** munkaterületen.<br /><br /> 2.) segítségével a **Endpoint Protection** csomópontja a **eszközök és megfelelőség** munkaterületen.<br /><br /> 3.) a beépített Configuration Manager használatával jelentéseket.|Lásd: [a System Center Configuration Managerben az Endpoint Protection figyelése](monitor-endpoint-protection.md)|  

 John sikeres végrehajtása az Endpoint Protection-jelentést a felettesének, és megerősíti, hogy a Woodgrove Bank számítógépei védettek a kártevőkkel szemben megadott üzleti követelményeknek megfelelően.

