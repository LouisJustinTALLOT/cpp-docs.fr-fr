---
title: Modèles de thread et Classes de Sections critiques (ATL) | Microsoft Docs
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
ms.openlocfilehash: b87fdac5220ede47f1acf19088e952fde408a413
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755955"
---
# <a name="threading-models-and-critical-sections-classes"></a>Modèles de thread et Classes de Sections critiques

Les classes suivantes définissent un threading modèle et la section critique :

- [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) implémente un serveur COM mis en pool de thread, le modèle de cloisonnement.

- [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) fournit des méthodes pour l’implémentation d’un serveur COM mis en pool de thread, le modèle de cloisonnement.

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) fournit des méthodes de thread-safe pour incrémenter et décrémenter une variable. Fournit une section critique.

- [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) fournit des méthodes de thread-safe pour incrémenter et décrémenter une variable. Ne fournit pas une section critique.

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) fournit des méthodes pour incrémenter et décrémenter une variable. Ne fournit pas une section critique.

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) détermine la classe de modèle de thread appropriée pour une classe d’objet unique.

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) détermine la classe de modèle de thread appropriée pour un objet qui est disponible dans le monde entier.

- [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) contient des méthodes pour obtenir et de libérer une section critique. La section critique est initialisée automatiquement.

- [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) contient des méthodes pour obtenir et de libérer une section critique. La section critique doit être initialisée explicitement.

- [La classe CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) reflète les méthodes dans `CComCriticalSection` sans fournir une section critique. Les méthodes dans `CComFakeCriticalSection` ne rien faire.

- [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) fournit la fonction de création d’un thread de CRT. Utilisez cette classe si le thread utilise des fonctions CRT.

- [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) fournit la fonction de création d’un thread Windows. Utilisez cette classe si le thread ne doit pas utiliser de fonctions CRT.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)

