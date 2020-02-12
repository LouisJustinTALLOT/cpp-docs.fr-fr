---
title: IVirtualProcessorRoot, structure
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: 60757b0edea6b60d080c2175d4df4830ffec0cc3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139895"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot, structure

Abstraction d'un thread matériel sur laquelle un proxy de thread peut s'exécuter.

## <a name="syntax"></a>Syntaxe

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[IVirtualProcessorRoot :: Activate](#activate)|Provoque le démarrage de l’exécution du proxy de thread associé à l' `pContext` interface du contexte d’exécution sur cette racine de processeur virtuel.|
|[IVirtualProcessorRoot ::D eactivate](#deactivate)|Entraîne l’arrêt de la distribution du contexte d’exécution sur la racine du thread virtuel en cours d’exécution sur cette racine du processeur virtuel. Le proxy de thread reprend l’exécution sur un appel à la méthode `Activate`.|
|[IVirtualProcessorRoot :: EnsureAllTasksVisible](#ensurealltasksvisible)|Fait en sorte que les données stockées dans la hiérarchie de processeurs individuels deviennent visibles par tous les processeurs du système. Elle garantit qu’une barrière de mémoire complète a été exécutée sur tous les processeurs avant le retour de la méthode.|
|[IVirtualProcessorRoot :: GetId](#getid)|Retourne un identificateur unique pour la racine du processeur virtuel.|

## <a name="remarks"></a>Notes

Chaque racine du processeur virtuel a une ressource d’exécution associée. L’interface `IVirtualProcessorRoot` hérite de l’interface [IExecutionResource](iexecutionresource-structure.md) . Plusieurs racines de processeur virtuel peuvent correspondre au même thread matériel sous-jacent.

Le Gestionnaire des ressources accorde des racines de processeur virtuel aux planificateurs en réponse aux demandes de ressources. Un planificateur peut utiliser une racine de processeur virtuel pour effectuer un travail en l’activant avec un contexte d’exécution.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="activate"></a>IVirtualProcessorRoot :: Activate, méthode

Provoque le démarrage de l’exécution du proxy de thread associé à l' `pContext` interface du contexte d’exécution sur cette racine de processeur virtuel.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Interface du contexte d’exécution qui sera distribuée sur cette racine de processeur virtuel.

### <a name="remarks"></a>Notes

Le Gestionnaire des ressources fournit un proxy de thread s’il n’est pas associé à l’interface de contexte d’exécution `pContext`

La méthode `Activate` peut être utilisée pour démarrer l’exécution d’un travail sur une nouvelle racine de processeur virtuel retournée par l’Gestionnaire des ressources ou pour reprendre le proxy de thread sur une racine de processeur virtuel qui a été désactivée ou qui est sur le lieu de désactiver. Pour plus d’informations sur la désactivation, consultez [IVirtualProcessorRoot ::D eactivate](#deactivate) . Lorsque vous reprenez une racine de processeur virtuel désactivée, le paramètre `pContext` doit être le même que le paramètre utilisé pour désactiver la racine du processeur virtuel.

Une fois qu’une racine de processeur virtuel a été activée pour la première fois, les paires d’appels suivants à `Deactivate` et `Activate` peuvent concurrencer les unes avec les autres. Cela signifie qu’il est acceptable pour le Gestionnaire des ressources de recevoir un appel à `Activate` avant de recevoir l’appel de `Deactivate` auquel il était destiné.

Lorsque vous activez une racine de processeur virtuel, vous signalez à la Gestionnaire des ressources que cette racine de processeur virtuel est actuellement occupée. Si votre planificateur ne peut pas trouver de travail à exécuter sur cette racine, il est supposé appeler la méthode `Deactivate` en informant le Gestionnaire des ressources que la racine du processeur virtuel est inactive. Le Gestionnaire des ressources utilise ces données pour équilibrer la charge du système.

`invalid_argument` est levée si l’argument `pContext` a la valeur `NULL`.

`invalid_operation` est levée si l’argument `pContext` ne représente pas le contexte d’exécution qui a été distribué le plus récemment par cette racine de processeur virtuel.

Le fait d’activer une racine de processeur virtuel augmente le niveau d’abonnement du thread matériel sous-jacent d’une unité. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="deactivate"></a>IVirtualProcessorRoot ::D méthode eactivate

Entraîne l’arrêt de la distribution du contexte d’exécution sur la racine du thread virtuel en cours d’exécution sur cette racine du processeur virtuel. Le proxy de thread reprend l’exécution sur un appel à la méthode `Activate`.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Contexte qui est actuellement distribué par cette racine.

### <a name="return-value"></a>Valeur de retour

Une valeur booléenne. La valeur **true** indique que le proxy de thread retourné par la méthode `Deactivate` en réponse à un appel à la méthode `Activate`. La valeur `false` indique que le proxy de thread retourné par la méthode en réponse à un événement de notification dans le Gestionnaire des ressources. Sur un planificateur de threads UMS (user-mode), cela indique que les éléments sont apparus dans la liste de saisie semi-automatique du planificateur et que le planificateur est requis pour les gérer.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour arrêter temporairement l’exécution d’une racine de processeur virtuel lorsque vous ne trouvez pas de travail dans votre planificateur. Un appel à la méthode `Deactivate` doit provenir de l’intérieur de la méthode `Dispatch` du contexte d’exécution avec lequel la racine du processeur virtuel a été activée pour la dernière fois. En d’autres termes, le proxy de thread qui appelle la méthode `Deactivate` doit être celui qui est en cours d’exécution sur la racine du processeur virtuel. L’appel de la méthode sur une racine de processeur virtuel que vous n’exécutez pas peut entraîner un comportement indéfini.

Une racine de processeur virtuel désactivée peut être réveillée avec un appel à la méthode `Activate`, avec le même argument qui a été transmis à la méthode `Deactivate`. Le planificateur est chargé de s’assurer que les appels aux méthodes `Activate` et `Deactivate` sont associés, mais qu’ils n’ont pas besoin d’être reçus dans un ordre spécifique. Le Gestionnaire des ressources peut gérer la réception d’un appel à la méthode `Activate` avant de recevoir un appel à la méthode `Deactivate` à laquelle il a été destiné.

Si la racine d’un processeur virtuel est en éveil et que la valeur de retour de la méthode `Deactivate` est la valeur **false**, le planificateur doit interroger la liste de saisie semi-automatique UMS via la méthode `IUMSCompletionList::GetUnblockNotifications`, agir sur ces informations, puis appeler à nouveau la méthode `Deactivate`. Cette valeur doit être répétée jusqu’à ce que la méthode `Deactivate` retourne la valeur `true`.

`invalid_argument` est levée si l’argument `pContext` a la valeur NULL.

`invalid_operation` est levée si la racine du processeur virtuel n’a jamais été activée, ou si l’argument `pContext` ne représente pas le contexte d’exécution qui a été distribué le plus récemment par cette racine de processeur virtuel.

La désactivation d’une racine de processeur virtuel réduit de 1 le niveau d’abonnement du thread matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ensurealltasksvisible"></a>IVirtualProcessorRoot :: EnsureAllTasksVisible, méthode

Fait en sorte que les données stockées dans la hiérarchie de processeurs individuels deviennent visibles par tous les processeurs du système. Elle garantit qu’une barrière de mémoire complète a été exécutée sur tous les processeurs avant le retour de la méthode.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Contexte actuellement distribué par cette racine de processeur virtuel.

### <a name="remarks"></a>Notes

Cette méthode peut être utile lorsque vous souhaitez synchroniser la désactivation d’une racine de processeur virtuel avec l’ajout d’un nouveau travail dans le planificateur. Pour des raisons de performances, vous pouvez décider d’ajouter des éléments de travail à votre planificateur sans exécuter de barrière de mémoire, ce qui signifie que les éléments de travail ajoutés par un thread qui s’exécute sur un processeur ne sont pas immédiatement visibles par tous les autres processeurs. En utilisant cette méthode avec la méthode `Deactivate`, vous pouvez vous assurer que votre planificateur ne désactive pas toutes ses racines de processeur virtuel tant que les éléments de travail existent dans les collections de votre planificateur.

Un appel à la méthode `EnsureAllTasksVisibleThe` doit provenir de l’intérieur de la méthode `Dispatch` du contexte d’exécution avec lequel la racine du processeur virtuel a été activée pour la dernière fois. En d’autres termes, le proxy de thread qui appelle la méthode `EnsureAllTasksVisible` doit être celui qui est en cours d’exécution sur la racine du processeur virtuel. L’appel de la méthode sur une racine de processeur virtuel que vous n’exécutez pas peut entraîner un comportement indéfini.

`invalid_argument` est levée si l’argument `pContext` a la valeur `NULL`.

`invalid_operation` est levée si la racine du processeur virtuel n’a jamais été activée, ou si l’argument `pContext` ne représente pas le contexte d’exécution qui a été distribué le plus récemment par cette racine de processeur virtuel.

## <a name="getid"></a>IVirtualProcessorRoot :: GetId, méthode

Retourne un identificateur unique pour la racine du processeur virtuel.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur entier.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
