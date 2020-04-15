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
ms.openlocfilehash: c388cc98aedbd35b2d0e00a4653a85a47abcb838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368118"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList, structure

Représente une liste de saisie semi-automatique UMS. Quand un thread UMS se bloque, le contexte de planification désigné du planificateur est distribué afin de déterminer les éléments à planifier sur la racine du processeur virtuel sous-jacent pendant que le thread d'origine est bloqué. Quand le thread d'origine se débloque, le système d'exploitation le met en attente dans la liste de saisie semi-automatique accessible via cette interface. Le planificateur peut interroger la liste de saisie semi-automatique à propos du contexte de planification désigné ou de tout autre emplacement qu'il recherche pour du travail.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|Récupère une chaîne `IUMSUnblockNotification` d’interfaces représentant des contextes d’exécution dont les procurations de thread associées se sont débloquées depuis la dernière fois que cette méthode a été invoquée.|

## <a name="remarks"></a>Notes

Un planificateur doit être extraordinairement prudent sur les actions effectuées après avoir utilisé cette interface pour déquer les éléments de la liste d’achèvement. Les éléments doivent être placés sur la liste des contextes runnables du planificateur et être généralement accessibles dès que possible. Il est tout à fait possible que l’un des éléments déqueued a été donné la propriété d’un verrou arbitraire. Le planificateur ne peut pas faire d’appels de fonction arbitraire qui peuvent bloquer entre l’appel à déqueuer les éléments et le placement de ces éléments sur une liste qui peut être généralement consulté à partir de l’annexe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IUMSCompletionList`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="iumscompletionlistgetunblocknotifications-method"></a><a name="getunblocknotifications"></a>IUMSCompletionList::GetUnblockNotifications Méthode

Récupère une chaîne `IUMSUnblockNotification` d’interfaces représentant des contextes d’exécution dont les procurations de thread associées se sont débloquées depuis la dernière fois que cette méthode a été invoquée.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Valeur de retour

Une chaîne `IUMSUnblockNotification` d’interfaces.

### <a name="remarks"></a>Notes

Les notifications retournées sont invalides une fois les contextes d’exécution reportés.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler, structure](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification, structure](iumsunblocknotification-structure.md)
