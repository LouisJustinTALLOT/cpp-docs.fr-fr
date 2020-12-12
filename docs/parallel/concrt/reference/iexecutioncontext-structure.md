---
description: 'En savoir plus sur : IExecutionContext, structure'
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
ms.openlocfilehash: 90802229e878546383f683bc99ffedc9cb5411af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122185"
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
|[IExecutionContext ::D ispatch](#dispatch)|Méthode appelée lorsqu’un proxy de thread commence à exécuter un contexte d’exécution particulier. Il doit s’agir de la principale routine de travail de votre planificateur.|
|[IExecutionContext :: GetId](#getid)|Retourne un identificateur unique pour le contexte d’exécution.|
|[IExecutionContext :: GetProxy](#getproxy)|Retourne une interface au proxy de thread qui exécute ce contexte.|
|[IExecutionContext :: GetScheduler](#getscheduler)|Retourne une interface au planificateur auquel ce contexte d’exécution appartient.|
|[IExecutionContext :: SetProxy](#setproxy)|Associe un proxy de thread à ce contexte d’exécution. Le proxy de thread associé appelle cette méthode juste avant de commencer à exécuter la méthode du contexte `Dispatch` .|

## <a name="remarks"></a>Notes

Si vous implémentez un planificateur personnalisé qui interagit avec le Gestionnaire des ressources du runtime d’accès concurrentiel, vous devez implémenter l' `IExecutionContext` interface. Les threads créés par l’Gestionnaire des ressources exécutent le travail au nom de votre planificateur en exécutant la `IExecutionContext::Dispatch` méthode.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IExecutionContext`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrence

## <a name="iexecutioncontextdispatch-method"></a><a name="dispatch"></a> IExecutionContext ::D méthode ispatch

Méthode appelée lorsqu’un proxy de thread commence à exécuter un contexte d’exécution particulier. Il doit s’agir de la principale routine de travail de votre planificateur.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Paramètres

*pDispatchState*<br/>
Pointeur vers l’État sous lequel ce contexte d’exécution est distribué. Pour plus d’informations sur l’état de répartition, consultez [DispatchState](dispatchstate-structure.md).

## <a name="iexecutioncontextgetid-method"></a><a name="getid"></a> IExecutionContext :: GetId, méthode

Retourne un identificateur unique pour le contexte d’exécution.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur entier unique.

### <a name="remarks"></a>Notes

Vous devez utiliser la méthode `GetExecutionContextId` pour obtenir un identificateur unique pour l’objet qui implémente l' `IExecutionContext` interface, avant d’utiliser l’interface en tant que paramètre pour les méthodes fournies par l’gestionnaire des ressources. Vous êtes censé retourner le même identificateur lorsque la `GetId` fonction est appelée.

Un identificateur obtenu à partir d’une source différente peut entraîner un comportement indéfini.

## <a name="iexecutioncontextgetproxy-method"></a><a name="getproxy"></a> IExecutionContext :: GetProxy, méthode

Retourne une interface au proxy de thread qui exécute ce contexte.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Interface `IThreadProxy`. Si le proxy de thread du contexte d’exécution n’a pas été initialisé avec un appel à `SetProxy` , la fonction doit retourner `NULL` .

### <a name="remarks"></a>Notes

Le Gestionnaire des ressources appellera la `SetProxy` méthode sur un contexte d’exécution, avec une `IThreadProxy` interface comme paramètre, avant d’entrer la `Dispatch` méthode sur le contexte. Vous êtes censé stocker cet argument et le retourner sur les appels à `GetProxy()` .

## <a name="iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a> IExecutionContext :: GetScheduler, méthode

Retourne une interface au planificateur auquel ce contexte d’exécution appartient.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Interface `IScheduler`.

### <a name="remarks"></a>Notes

Vous devez initialiser le contexte d’exécution avec une interface valide `IScheduler` avant de l’utiliser comme paramètre pour les méthodes fournies par le gestionnaire des ressources.

## <a name="iexecutioncontextsetproxy-method"></a><a name="setproxy"></a> IExecutionContext :: SetProxy, méthode

Associe un proxy de thread à ce contexte d’exécution. Le proxy de thread associé appelle cette méthode juste avant de commencer à exécuter la méthode du contexte `Dispatch` .

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Paramètres

*pThreadProxy*<br/>
Interface vers le proxy de thread qui va entrer dans la `Dispatch` méthode sur ce contexte d’exécution.

### <a name="remarks"></a>Notes

Vous êtes censé enregistrer le paramètre `pThreadProxy` et le retourner sur un appel à la `GetProxy` méthode. Le Gestionnaire des ressources garantit que le proxy de thread associé au contexte d’exécution ne changera pas pendant que le proxy de thread exécute la `Dispatch` méthode.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[IScheduler, structure](ischeduler-structure.md)<br/>
[IThreadProxy, structure](ithreadproxy-structure.md)
