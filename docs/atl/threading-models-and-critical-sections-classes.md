---
title: Les Classes de Sections critiques (ATL) et les modèles de thread | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- vc.atl.threads.models
dev_langs:
- C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37172c0080664f496bdf5d5c7c0ebecbd8f77898
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359916"
---
# <a name="threading-models-and-critical-sections-classes"></a>Les Classes de Sections critiques et les modèles de thread
Les classes suivantes définissent un modèle de thread modèle et la section critique :  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) implémente un serveur COM mis en pool de threads, le modèle de cloisonnement.  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) fournit des méthodes pour l’implémentation d’un serveur COM mis en pool de threads, le modèle de cloisonnement.  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) fournit des méthodes thread-safe pour incrémenter et décrémenter une variable. Fournit une section critique.  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) fournit des méthodes thread-safe pour incrémenter et décrémenter une variable. Ne fournit pas une section critique.  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) fournit des méthodes pour incrémenter et décrémenter une variable. Ne fournit pas une section critique.  
  
-   [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) détermine la classe de modèle de thread appropriée pour une classe d’objet unique.  
  
-   [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) détermine la classe de modèle de thread appropriée pour un objet qui est disponible globalement.  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) contient des méthodes permettant d’obtenir et libérer une section critique. La section critique est automatiquement initialisée.  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) contient des méthodes permettant d’obtenir et libérer une section critique. La section critique doit être initialisée explicitement.  
  
-   [La classe CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) reflète les méthodes de `CComCriticalSection` sans fournir une section critique. Les méthodes de `CComFakeCriticalSection` ne rien faire.  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) fournit la fonction de création d’un thread de CRT. Utilisez cette classe si le thread utilisent des fonctions CRT.  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) fournit la fonction de création d’un thread Windows. Utilisez cette classe si le thread ne doit pas utiliser de fonctions CRT.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../atl/atl-class-overview.md)

