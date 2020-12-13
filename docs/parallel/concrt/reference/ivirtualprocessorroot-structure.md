---
description: 'En savoir plus sur : IVirtualProcessorRoot, structure'
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
ms.openlocfilehash: b55aa72e9383447ea8d19e13e1e2aa9bd57d267d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334305"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot, structure

Abstraction d'un thread matériel sur laquelle un proxy de thread peut s'exécuter.

## <a name="syntax"></a>Syntaxe

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IVirtualProcessorRoot :: Activate](#activate)|Entraîne le démarrage de l’exécution du proxy de thread associé à l’interface du contexte d’exécution `pContext` sur cette racine de processeur virtuel.|
|[IVirtualProcessorRoot ::D eactivate](#deactivate)|Entraîne l’arrêt de la distribution du contexte d’exécution sur la racine du thread virtuel en cours d’exécution sur cette racine du processeur virtuel. Le proxy de thread reprend l’exécution sur un appel à la `Activate` méthode.|
|[IVirtualProcessorRoot :: EnsureAllTasksVisible](#ensurealltasksvisible)|Fait en sorte que les données stockées dans la hiérarchie de processeurs individuels deviennent visibles par tous les processeurs du système. Elle garantit qu’une barrière de mémoire complète a été exécutée sur tous les processeurs avant le retour de la méthode.|
|[IVirtualProcessorRoot :: GetId](#getid)|Retourne un identificateur unique pour la racine du processeur virtuel.|

## <a name="remarks"></a>Notes

Chaque racine du processeur virtuel a une ressource d’exécution associée. L' `IVirtualProcessorRoot` interface hérite de l’interface [IExecutionResource](iexecutionresource-structure.md) . Plusieurs racines de processeur virtuel peuvent correspondre au même thread matériel sous-jacent.

Le Gestionnaire des ressources accorde des racines de processeur virtuel aux planificateurs en réponse aux demandes de ressources. Un planificateur peut utiliser une racine de processeur virtuel pour effectuer un travail en l’activant avec un contexte d’exécution.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrence

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a> IVirtualProcessorRoot :: Activate, méthode

Entraîne le démarrage de l’exécution du proxy de thread associé à l’interface du contexte d’exécution `pContext` sur cette racine de processeur virtuel.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Interface du contexte d’exécution qui sera distribuée sur cette racine de processeur virtuel.

### <a name="remarks"></a>Notes

Le Gestionnaire des ressources fournit un proxy de thread s’il n’est pas associé à l’interface de contexte d’exécution `pContext`

La `Activate` méthode peut être utilisée pour démarrer l’exécution du travail sur une nouvelle racine de processeur virtuel retournée par l’gestionnaire des ressources, ou pour reprendre le proxy de thread sur une racine de processeur virtuel qui a été désactivée ou qui est sur le lieu de désactiver. Pour plus d’informations sur la désactivation, consultez [IVirtualProcessorRoot ::D eactivate](#deactivate) . Lorsque vous reprenez une racine de processeur virtuel désactivée, le paramètre `pContext` doit être le même que le paramètre utilisé pour désactiver la racine du processeur virtuel.

Une fois qu’une racine de processeur virtuel a été activée pour la première fois, les paires d’appels suivants à `Deactivate` et `Activate` peuvent concurrencer les unes avec les autres. Cela signifie qu’il est acceptable pour le Gestionnaire des ressources de recevoir un appel à avant de recevoir `Activate` l' `Deactivate` appel dont il était destiné.

Lorsque vous activez une racine de processeur virtuel, vous signalez à la Gestionnaire des ressources que cette racine de processeur virtuel est actuellement occupée. Si votre planificateur ne peut pas trouver de travail à exécuter sur cette racine, il est supposé appeler la `Deactivate` méthode qui informe le gestionnaire des ressources que la racine du processeur virtuel est inactive. Le Gestionnaire des ressources utilise ces données pour équilibrer la charge du système.

`invalid_argument` est levée si l’argument `pContext` a la valeur `NULL` .

`invalid_operation` est levée si l’argument `pContext` ne représente pas le contexte d’exécution qui a été distribué le plus récemment par cette racine de processeur virtuel.

Le fait d’activer une racine de processeur virtuel augmente le niveau d’abonnement du thread matériel sous-jacent d’une unité. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a> IVirtualProcessorRoot ::D méthode eactivate

Entraîne l’arrêt de la distribution du contexte d’exécution sur la racine du thread virtuel en cours d’exécution sur cette racine du processeur virtuel. Le proxy de thread reprend l’exécution sur un appel à la `Activate` méthode.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Contexte qui est actuellement distribué par cette racine.

### <a name="return-value"></a>Valeur renvoyée

Une valeur booléenne. **`true`** La valeur indique que le proxy de thread retourné par la `Deactivate` méthode en réponse à un appel à la `Activate` méthode. **`false`** La valeur indique que le proxy de thread retourné par la méthode en réponse à un événement de notification dans le gestionnaire des ressources. Sur un planificateur de threads UMS (user-mode), cela indique que les éléments sont apparus dans la liste de saisie semi-automatique du planificateur et que le planificateur est requis pour les gérer.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour arrêter temporairement l’exécution d’une racine de processeur virtuel lorsque vous ne trouvez pas de travail dans votre planificateur. Un appel à la `Deactivate` méthode doit provenir de la `Dispatch` méthode du contexte d’exécution avec lequel la racine du processeur virtuel a été activée pour la dernière fois. En d’autres termes, le proxy de thread qui appelle la `Deactivate` méthode doit être celui qui est en cours d’exécution sur la racine du processeur virtuel. L’appel de la méthode sur une racine de processeur virtuel que vous n’exécutez pas peut entraîner un comportement indéfini.

Une racine de processeur virtuel désactivée peut être réveillée avec un appel à la `Activate` méthode, avec le même argument qui a été passé à la `Deactivate` méthode. Le planificateur est chargé de s’assurer que les appels aux `Activate` `Deactivate` méthodes et sont associés, mais ils ne doivent pas être reçus dans un ordre spécifique. La Gestionnaire des ressources peut gérer la réception d’un appel à la `Activate` méthode avant de recevoir un appel à la `Deactivate` méthode à laquelle elle a été destinée.

Si la racine d’un processeur virtuel est en éveil et que la valeur de retour de la `Deactivate` méthode est la valeur **`false`** , le planificateur doit interroger la liste de saisie semi-automatique UMS via la `IUMSCompletionList::GetUnblockNotifications` méthode, agir sur ces informations, puis appeler `Deactivate` à nouveau la méthode. Cette valeur doit être répétée jusqu’à ce que la `Deactivate` méthode retourne la valeur **`true`** .

`invalid_argument` est levée si l’argument `pContext` a la valeur null.

`invalid_operation` est levé si la racine du processeur virtuel n’a jamais été activée, ou si l’argument `pContext` ne représente pas le contexte d’exécution qui a été distribué le plus récemment par cette racine de processeur virtuel.

La désactivation d’une racine de processeur virtuel réduit de 1 le niveau d’abonnement du thread matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a> IVirtualProcessorRoot :: EnsureAllTasksVisible, méthode

Fait en sorte que les données stockées dans la hiérarchie de processeurs individuels deviennent visibles par tous les processeurs du système. Elle garantit qu’une barrière de mémoire complète a été exécutée sur tous les processeurs avant le retour de la méthode.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Contexte actuellement distribué par cette racine de processeur virtuel.

### <a name="remarks"></a>Notes

Cette méthode peut être utile lorsque vous souhaitez synchroniser la désactivation d’une racine de processeur virtuel avec l’ajout d’un nouveau travail dans le planificateur. Pour des raisons de performances, vous pouvez décider d’ajouter des éléments de travail à votre planificateur sans exécuter de barrière de mémoire, ce qui signifie que les éléments de travail ajoutés par un thread qui s’exécute sur un processeur ne sont pas immédiatement visibles par tous les autres processeurs. En utilisant cette méthode conjointement avec la `Deactivate` méthode, vous pouvez vous assurer que votre planificateur ne désactive pas toutes ses racines de processeur virtuel tant que les éléments de travail existent dans les collections de votre planificateur.

Un appel à la `EnsureAllTasksVisibleThe` méthode doit provenir de la `Dispatch` méthode du contexte d’exécution avec lequel la racine du processeur virtuel a été activée pour la dernière fois. En d’autres termes, le proxy de thread qui appelle la `EnsureAllTasksVisible` méthode doit être celui qui est en cours d’exécution sur la racine du processeur virtuel. L’appel de la méthode sur une racine de processeur virtuel que vous n’exécutez pas peut entraîner un comportement indéfini.

`invalid_argument` est levée si l’argument `pContext` a la valeur `NULL` .

`invalid_operation` est levé si la racine du processeur virtuel n’a jamais été activée, ou si l’argument `pContext` ne représente pas le contexte d’exécution qui a été distribué le plus récemment par cette racine de processeur virtuel.

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a> IVirtualProcessorRoot :: GetId, méthode

Retourne un identificateur unique pour la racine du processeur virtuel.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur entier.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
