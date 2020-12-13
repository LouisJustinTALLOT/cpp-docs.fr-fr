---
description: 'En savoir plus sur : structure IUMSScheduler'
title: IUMSScheduler, structure
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: e42a2e3d39e568ba12cd681053406ce88c7b5dba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334338"
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
|[IUMSScheduler :: SetCompletionList](#setcompletionlist)|Assigne une `IUMSCompletionList` interface à un planificateur de threads UMS.|

## <a name="remarks"></a>Notes

Si vous implémentez un planificateur personnalisé qui communique avec le Gestionnaire des ressources et que vous souhaitez que les threads UMS soient transmis à votre planificateur au lieu de threads Win32 ordinaires, vous devez fournir une implémentation de l' `IUMSScheduler` interface. En outre, vous devez définir la valeur de la stratégie pour la clé de stratégie du planificateur `SchedulerKind` sur `UmsThreadDefault` . Si la stratégie spécifie le thread UMS, l' `IScheduler` interface qui est passée en tant que paramètre à la méthode [IResourceManager :: RegisterScheduler](iresourcemanager-structure.md#registerscheduler) doit être une `IUMSScheduler` interface.

Le Gestionnaire des ressources est en mesure de transmettre les threads UMS uniquement sur les systèmes d’exploitation qui disposent de la fonctionnalité UMS. les systèmes d’exploitation 64 bits avec version Windows 7 et versions ultérieures prennent en charge les threads UMS. Si vous créez une stratégie de planificateur avec la `SchedulerKind` clé définie sur la valeur `UmsThreadDefault` et que la plateforme sous-jacente ne prend pas en charge UMS, la valeur de la `SchedulerKind` clé de cette stratégie sera remplacée par la valeur `ThreadScheduler` . Vous devez toujours lire cette valeur de stratégie avant de recevoir des threads UMS.

L' `IUMSScheduler` interface est une extrémité d’un canal bidirectionnel de communication entre un planificateur et le gestionnaire des ressources. L’autre terminaison est représentée par les `IResourceManager` `ISchedulerProxy` interfaces et, qui sont implémentées par le gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrence

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a> IUMSScheduler :: SetCompletionList, méthode

Assigne une `IUMSCompletionList` interface à un planificateur de threads UMS.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Paramètres

*pCompletionList*<br/>
Interface de la liste de saisie semi-automatique pour le planificateur. Il n’existe qu’une seule liste par planificateur.

### <a name="remarks"></a>Notes

La Gestionnaire des ressources appellera cette méthode sur un planificateur qui spécifie qu’elle veut des threads UMS, une fois que le planificateur a demandé une allocation initiale des ressources. Le planificateur peut utiliser l' `IUMSCompletionList` interface pour déterminer quand les proxys de thread UMS ont été débloqués. L’accès à cette interface est uniquement valide à partir d’un proxy de thread s’exécutant sur une racine de processeur virtuel affectée au planificateur UMS.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[PolicyElementKey,](concurrency-namespace-enums.md)<br/>
[IScheduler, structure](ischeduler-structure.md)<br/>
[IUMSCompletionList, structure](iumscompletionlist-structure.md)<br/>
[IResourceManager, structure](iresourcemanager-structure.md)
