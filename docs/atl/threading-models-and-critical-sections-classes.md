---
description: 'En savoir plus sur : modèles de thread et classes de sections critiques'
title: Modèles de thread et classes de sections critiques (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
ms.openlocfilehash: 51ad5a5f2f03bfe080395966d0c480615c49a109
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138279"
---
# <a name="threading-models-and-critical-sections-classes"></a>Modèles de thread et classes de sections critiques

Les classes suivantes définissent un modèle de thread et une section critique :

- [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) Implémente un serveur COM de modèle cloisonné et à pool de threads.

- [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) Fournit des méthodes pour implémenter un serveur COM de modèle cloisonné et à pool de threads.

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) Fournit des méthodes thread-safe pour l’incrémentation et la décrémentation d’une variable. Fournit une section critique.

- [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) Fournit des méthodes thread-safe pour l’incrémentation et la décrémentation d’une variable. Ne fournit pas de section critique.

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) Fournit des méthodes pour incrémenter et décrémenter une variable. Ne fournit pas de section critique.

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) Détermine la classe de modèle de thread appropriée pour une classe d’objet unique.

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) Détermine la classe de modèle de thread appropriée pour un objet qui est globalement disponible.

- [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) Contient des méthodes pour obtenir et libérer une section critique. La section critique est initialisée automatiquement.

- [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) Contient des méthodes pour obtenir et libérer une section critique. La section critique doit être initialisée explicitement.

- [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) Met en miroir les méthodes dans `CComCriticalSection` sans fournir de section critique. Les méthodes de `CComFakeCriticalSection` ne font rien.

- [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) Fournit la fonction de création d’un thread CRT. Utilisez cette classe si le thread utilise des fonctions CRT.

- [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) Fournit la fonction de création d’un thread Windows. Utilisez cette classe si le thread n’utilise pas de fonctions CRT.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../atl/atl-class-overview.md)
