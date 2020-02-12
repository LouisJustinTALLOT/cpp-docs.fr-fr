---
title: IUMSCompletionList, structure
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: 02382ef4606a6e73804fcbd5ce7735ecf2f0dcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140048"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList, structure

Représente une liste de saisie semi-automatique UMS. Quand un thread UMS se bloque, le contexte de planification désigné du planificateur est distribué afin de déterminer les éléments à planifier sur la racine du processeur virtuel sous-jacent pendant que le thread d'origine est bloqué. Quand le thread d'origine se débloque, le système d'exploitation le met en attente dans la liste de saisie semi-automatique accessible via cette interface. Le planificateur peut interroger la liste de saisie semi-automatique à propos du contexte de planification désigné ou de tout autre emplacement qu'il recherche pour du travail.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[IUMSCompletionList, :: GetUnblockNotifications](#getunblocknotifications)|Récupère une chaîne d’interfaces `IUMSUnblockNotification` représentant des contextes d’exécution dont les proxys de thread associés ont été débloqués depuis la dernière fois que cette méthode a été appelée.|

## <a name="remarks"></a>Notes

Un planificateur doit être très prudent en ce qui concerne les actions effectuées après l’utilisation de cette interface pour défiler des éléments de la liste de saisie semi-automatique. Les éléments doivent être placés dans la liste des contextes exécutables du planificateur et être généralement accessibles dès que possible. Il est tout à fait possible que l’un des éléments de la file d’attente ait reçu la propriété d’un verrou arbitraire. Le planificateur ne peut pas effectuer d’appels de fonction arbitraires qui peuvent bloquer entre l’appel à des éléments de retrait de la file d’attente et le placement de ces éléments sur une liste qui est généralement accessible à partir du planificateur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IUMSCompletionList`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="getunblocknotifications"></a>IUMSCompletionList, :: GetUnblockNotifications, méthode

Récupère une chaîne d’interfaces `IUMSUnblockNotification` représentant des contextes d’exécution dont les proxys de thread associés ont été débloqués depuis la dernière fois que cette méthode a été appelée.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Valeur de retour

Chaîne d’interfaces `IUMSUnblockNotification`.

### <a name="remarks"></a>Notes

Les notifications renvoyées ne sont pas valides une fois que les contextes d’exécution ont été replanifiés.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification, structure](iumsunblocknotification-structure.md)
