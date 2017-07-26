---
title: "Karbantartási időszakok használata |} Microsoft Docs"
description: "Gyűjtemények és a karbantartási időszakok használatával hatékonyan a System Center Configuration Manager ügyfelek kezelésére."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4564ebcb-41a8-4eb0-afdb-2e1f0795cfa2
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: fa67cf597c73bab47209c9b98539f97e174ae70b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-use-maintenance-windows-in-system-center-configuration-manager"></a>A System Center Configuration Manager karbantartási időszakok használata

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Karbantartási időszakok lehetővé teszik egy időpontot, amikor a Configuration Manager műveleteket lehet elvégezni adja meg egy eszközgyűjteményt. Karbantartási időszakok használatával biztosítható, hogy ügyfelek konfigurálási változtatásai olyan időszakban történjenek, amikor nincsenek hatással a termelékenység.  

 A következő műveletei támogatják a karbantartási időszakok:  

-   Szoftverek központi telepítése  

-   Szoftverfrissítések telepítése  

-   Megfelelőségi beállítások telepítése és kiértékelése  

-   Operációs rendszerek központi telepítése  

-   Feladatütemezések központi telepítése  

 Karbantartási időszakok konfigurálása időpontjával, a kezdés és a Befejezés időpontja, valamint az ismétlődésük beállításával. A időszak maximális időtartama nem lehet kisebb, mint 24 óra. Alapértelmezés szerint a központi telepítés miatti számítógép-újraindításokra nem engedélyezettek a karbantartási időszakon kívül, de az alapértelmezett érték felülírható. A karbantartási időszaknak csak arra az időre mikor fusson a központi telepítési program; hatása letöltésre és helyi futtatásra konfigurált alkalmazások letöltheti a tartalmat a időszakon kívül.  

 Ha egy ügyfélszámítógép tagja egy eszközgyűjteményt, amely a karbantartási időszak van, a telepítési program fut, csak akkor, ha a maximálisan engedélyezett futási idő nem haladja meg a az ablak konfigurált időtartamot. Ha a program futása sikertelen, riasztás áll elő, és a telepítés újra fut a következő olyan karbantartási időszakban, amelyikben erre van idő.  

## <a name="using-multiple-maintenance-windows"></a>Több karbantartási időszak használata  
 Ha egy ügyfélszámítógép több olyan eszközgyűjtemény, amelyek a karbantartási időszakok tagja, az alábbi szabályok vonatkoznak:  

-   Ha a karbantartási időszakok nem fedik át egymást, akkor azok független karbantartási időszakoknak tekintendők.  

-   Ha a karbantartási időszakok átfedik egymást, akkor azok egyetlen, mindkét karbantartási időszakot magába foglaló karbantartási időszaknak tekintendők. Ha például két windows, minden egyes egy órával fedik 30 perc, a tényleges időtartama a karbantartási időszak 90 perc lesz.  

 Amikor egy felhasználó alkalmazástelepítést kezdeményez a Szoftverközpontból, az alkalmazás telepítése azonnal, függetlenül bármilyen karbantartási időszakok.  

 Ha egy **Kötelező** jellegű alkalmazás telepítése a felhasználó által a Szoftverközpontban konfigurált munkaidőn kívüli időszakban éri el a telepítési határidejét, a rendszer telepíti az alkalmazást.  

### <a name="how-to-configure-maintenance-windows"></a>A karbantartási időszakok konfigurálása  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség**>  **Eszközgyűjtemények**.  

3.  Az a **Eszközgyűjtemények** listában, válasszon ki egy gyűjteményt. A **Minden rendszer** gyűjteményhez nem hozható létre karbantartási időszak.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  A a **karbantartási időszakok** lapján a  **&lt;gyűjteménynév\> tulajdonságok** párbeszédpanelen válassza ki a **új** ikonra.  

6.  Fejezze be a  **&lt;új\> ütemezés** párbeszédpanel.  

7.  Válasszon a **ütemezés alkalmazása a következőre** legördülő listából.  

8.  Válasszon **OK** , majd zárja be a  **&lt;gyűjteménynév\> tulajdonságok** párbeszédpanel megnyitásához.  

