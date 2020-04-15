---
title: IExecutionContext, structure
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 532247ca1776452ad32476d2bcdfafcee3481058
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358800"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext, structure

Interface avec un contexte d'exécution qui peut s'exécuter sur un processeur virtuel donné et dont le contexte peut être commuté de manière coopérative.

## <a name="syntax"></a>Syntaxe

```cpp
struct IExecutionContext;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IExecutionContexte::Dispatch](#dispatch)|La méthode qui s’appelle lorsqu’un proxy thread commence à exécuter un contexte d’exécution particulier. Cela devrait être la routine principale du travailleur pour votre planificateur.|
|[IExecutionContexte::GetId](#getid)|Retourne un identifiant unique pour le contexte d’exécution.|
|[IExecutionContexte::GetProxy](#getproxy)|Retourne une interface au proxy de thread qui exécute ce contexte.|
|[IExecutionContexte::GetScheduler](#getscheduler)|Retourne une interface au planificateur auquel appartient ce contexte d’exécution.|
|[IExecutionContexte::SetProxy](#setproxy)|Associe un proxy de fil à ce contexte d’exécution. Le proxy de thread associé invoque cette méthode `Dispatch` juste avant qu’elle ne commence à exécuter la méthode du contexte.|

## <a name="remarks"></a>Notes

Si vous implémentez un planificateur personnalisé qui s’interface avec le gestionnaire de ressources `IExecutionContext` de Concurrency Runtime, vous devrez implémenter l’interface. Les fils créés par le gestionnaire de ressources effectuent `IExecutionContext::Dispatch` le travail au nom de votre planificateur en exécutant la méthode.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IExecutionContext`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="iexecutioncontextdispatch-method"></a><a name="dispatch"></a>IExecutionContext::Dispatch Méthode

La méthode qui s’appelle lorsqu’un proxy thread commence à exécuter un contexte d’exécution particulier. Cela devrait être la routine principale du travailleur pour votre planificateur.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Paramètres

*pDispatchState (États-Unis)*<br/>
Un pointeur à l’état dans lequel ce contexte d’exécution est envoyé. Pour plus d’informations sur l’état de répartition, voir [DispatchState](dispatchstate-structure.md).

## <a name="iexecutioncontextgetid-method"></a><a name="getid"></a>IExecutionContext:GetId Méthode

Retourne un identifiant unique pour le contexte d’exécution.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Un identificateur integer unique.

### <a name="remarks"></a>Notes

Vous devez utiliser `GetExecutionContextId` la méthode pour obtenir un identifiant `IExecutionContext` unique pour l’objet qui implémente l’interface, avant d’utiliser l’interface comme paramètre aux méthodes fournies par le gestionnaire de ressources. On s’attend à ce `GetId` que vous retournons le même identifiant lorsque la fonction est invoquée.

Un identifiant obtenu à partir d’une autre source pourrait entraîner un comportement indéfini.

## <a name="iexecutioncontextgetproxy-method"></a><a name="getproxy"></a>IExecutionContext:GetProxy Méthode

Retourne une interface au proxy de thread qui exécute ce contexte.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Valeur de retour

Interface `IThreadProxy`. Si le proxy de fil du contexte d’exécution `SetProxy`n’a `NULL`pas été paralé avec un appel à , la fonction doit revenir .

### <a name="remarks"></a>Notes

Le gestionnaire des `SetProxy` ressources invoquera la `IThreadProxy` méthode dans un contexte `Dispatch` d’exécution, avec une interface comme paramètre, avant d’entrer la méthode sur le contexte. On s’attend à ce que vous `GetProxy()`stockiez cet argument et le retour sur les appels à .

## <a name="iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a>IExecutionContext:GetScheduler Méthode

Retourne une interface au planificateur auquel appartient ce contexte d’exécution.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Valeur de retour

Interface `IScheduler`.

### <a name="remarks"></a>Notes

Vous êtes tenu d’initialiser le `IScheduler` contexte d’exécution avec une interface valide avant de l’utiliser comme paramètre aux méthodes fournies par le gestionnaire de ressources.

## <a name="iexecutioncontextsetproxy-method"></a><a name="setproxy"></a>IExecutionContext:Méthode SetProxy

Associe un proxy de fil à ce contexte d’exécution. Le proxy de thread associé invoque cette méthode `Dispatch` juste avant qu’elle ne commence à exécuter la méthode du contexte.

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Paramètres

*pThreadProxy*<br/>
Une interface au proxy de thread `Dispatch` qui est sur le point d’entrer la méthode sur ce contexte d’exécution.

### <a name="remarks"></a>Notes

On s’attend à `pThreadProxy` ce que vous sauviez le paramètre et le retour sur un appel à la `GetProxy` méthode. Le gestionnaire de ressources garantit que le proxy de thread associé au `Dispatch` contexte d’exécution ne changera pas pendant que le proxy de thread exécute la méthode.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IScheduler, structure](ischeduler-structure.md)<br/>
[IThreadProxy, structure](ithreadproxy-structure.md)
