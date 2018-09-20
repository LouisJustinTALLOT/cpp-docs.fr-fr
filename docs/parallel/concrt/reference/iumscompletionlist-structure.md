---
title: IUMSCompletionList, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs:
- C++
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aabab7a127fdc072b8d3863a53c02e20139afc5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433686"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList, structure

Représente une liste de saisie semi-automatique UMS. Quand un thread UMS se bloque, le contexte de planification désigné du planificateur est distribué afin de déterminer les éléments à planifier sur la racine du processeur virtuel sous-jacent pendant que le thread d'origine est bloqué. Quand le thread d'origine se débloque, le système d'exploitation le met en attente dans la liste de saisie semi-automatique accessible via cette interface. Le planificateur peut interroger la liste de saisie semi-automatique à propos du contexte de planification désigné ou de tout autre emplacement qu'il recherche pour du travail.

## <a name="syntax"></a>Syntaxe

```
struct IUMSCompletionList;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|Récupère une chaîne de `IUMSUnblockNotification` interfaces qui représentent des contextes d’exécution dont le thread associé proxys avaient débloqué depuis la dernière exécution de cette méthode a été appelé.|

## <a name="remarks"></a>Notes

Un planificateur doit être extraordinairement prudent concernant les actions à effectuer après avoir utilisé cette interface pour la file d’attente des éléments à partir de la liste de saisie semi-automatique. Les éléments doivent être placés sur la liste du Planificateur de contextes exécutables et généralement accessible dès que possible. Il est tout à fait possible qu’un des éléments retirés de l’a reçu la propriété d’un verrou arbitraire. Le planificateur peut appeler aucune fonction arbitraires qui peuvent se bloquer entre l’appel à la file d’attente des éléments et le positionnement de ces éléments sur une liste qui sont généralement accessibles à partir du planificateur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IUMSCompletionList`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrtrm.h

**Espace de noms :** concurrency

##  <a name="getunblocknotifications"></a>  IUMSCompletionList::GetUnblockNotifications, méthode

Récupère une chaîne de `IUMSUnblockNotification` interfaces qui représentent des contextes d’exécution dont le thread associé proxys avaient débloqué depuis la dernière exécution de cette méthode a été appelé.

```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Valeur de retour

Une chaîne de `IUMSUnblockNotification` interfaces.

### <a name="remarks"></a>Notes

Les notifications retournées ne sont pas valides une fois que les contextes d’exécution sont replanifiées.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification, structure](iumsunblocknotification-structure.md)
