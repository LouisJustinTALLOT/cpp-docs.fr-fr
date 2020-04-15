---
title: IUMSScheduler, structure
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 70954906122c048e5199a801632626d35a8e3f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368097"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler, structure

Interface avec une abstraction d'un planificateur de tâches qui veut que le gestionnaire des ressources du runtime d'accès concurrentiel lui remette des threads UMS (User-Mode Scheduling). Le gestionnaire des ressources utilise cette interface pour communiquer avec les planificateurs de threads UMS. L'interface `IUMSScheduler` hérite de l'interface `IScheduler` .

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Assigne `IUMSCompletionList` une interface à un planificateur de thread UMS.|

## <a name="remarks"></a>Notes

Si vous implémentez un planificateur personnalisé qui communique avec le gestionnaire de ressources, et que vous souhaitez que les threads UMS `IUMSScheduler` soient remis à votre planificateur au lieu de threads Win32 ordinaires, vous devez fournir une implémentation de l’interface. En outre, vous devez définir la valeur `SchedulerKind` de `UmsThreadDefault`la stratégie pour la clé de la stratégie de planificateur d’être . Si la stratégie spécifie `IScheduler` le thread UMS, l’interface qui est passée comme paramètre à `IUMSScheduler` [l’IResourceManager::La méthode RegisterScheduler](iresourcemanager-structure.md#registerscheduler) doit être une interface.

Le gestionnaire de ressources est en mesure de vous remettre des threads UMS uniquement sur les systèmes d’exploitation qui ont la fonctionnalité UMS. Systèmes d’exploitation 64 bits avec version Windows 7 et threads UMS de prise en charge plus élevée. Si vous créez une stratégie `SchedulerKind` de planificateur `UmsThreadDefault` avec l’ensemble clé de la valeur `SchedulerKind` et que la plate-forme `ThreadScheduler`sous-jacente ne prend pas en charge UMS, la valeur de la clé sur cette politique sera changée en valeur . Vous devez toujours relire cette valeur de stratégie avant de vous attendre à recevoir des threads UMS.

L’interface `IUMSScheduler` est l’une des extrémités d’un canal de communication bidirectionnel entre un planificateur et le gestionnaire des ressources. L’autre extrémité est `IResourceManager` représentée `ISchedulerProxy` par les interfaces et les interfaces, qui sont mises en œuvre par le gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[IScheduler (IScheduler)](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a>IUMSScheduler::SetCompletionList Méthode

Assigne `IUMSCompletionList` une interface à un planificateur de thread UMS.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Paramètres

*pCompletionList (en)*<br/>
L’interface de liste d’achèvement pour le planificateur. Il y a une liste unique par planificateur.

### <a name="remarks"></a>Notes

Le gestionnaire des ressources invoquera cette méthode sur un planificateur qui spécifie qu’il veut des threads UMS, après que le planificateur a demandé une allocation initiale des ressources. Le planificateur peut `IUMSCompletionList` utiliser l’interface pour déterminer quand les procurations de thread UMS ont débloqué. Il est uniquement valable d’accéder à cette interface à partir d’un proxy de thread fonctionnant sur une racine de processeur virtuel assignée au planificateur UMS.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[PolitiqueElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler, structure](ischeduler-structure.md)<br/>
[IUMSCompletionList, structure](iumscompletionlist-structure.md)<br/>
[IResourceManager, structure](iresourcemanager-structure.md)
