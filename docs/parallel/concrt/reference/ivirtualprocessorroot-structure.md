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
ms.openlocfilehash: f642a29d0a80568f7a5f2a5e89f6951d4819243e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364263"
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
|[IVirtualProcessorRoot::Activer](#activate)|Provoque le proxy de thread `pContext` associé à l’interface contextuelle d’exécution de commencer à exécuter sur cette racine de processeur virtuel.|
|[IVirtualProcessorRoot::Deactivate](#deactivate)|Provoque le proxy de thread actuellement exécutant sur cette racine de processeur virtuel pour arrêter d’envoyer le contexte d’exécution. Le proxy de thread reprendra l’exécution sur un appel à la `Activate` méthode.|
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|Les données stockées dans la hiérarchie de la mémoire des processeurs individuels deviennent visibles par tous les processeurs du système. Il garantit qu’une clôture mémoire complète a été exécutée sur tous les processeurs avant le retour de la méthode.|
|[IVirtualProcessorRoot::GetId](#getid)|Retourne un identifiant unique pour la racine du processeur virtuel.|

## <a name="remarks"></a>Notes

Chaque racine de processeur virtuel a une ressource d’exécution associée. L’interface `IVirtualProcessorRoot` hérite de l’interface [IExecutionResource.](iexecutionresource-structure.md) Plusieurs racines de processeur virtuel peuvent correspondre au même fil matériel sous-jacent.

Le gestionnaire des ressources accorde des racines de processeur virtuel aux planificateurs en réponse aux demandes de ressources. Un planificateur peut utiliser une racine de processeur virtuel pour effectuer des travaux en l’activant dans un contexte d’exécution.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>IVirtualProcessorRoot::Active Méthode

Provoque le proxy de thread `pContext` associé à l’interface contextuelle d’exécution de commencer à exécuter sur cette racine de processeur virtuel.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Une interface au contexte d’exécution qui sera expédiée sur cette racine de processeur virtuel.

### <a name="remarks"></a>Notes

Le gestionnaire de ressources fournira un proxy de thread si l’on n’est pas associé à l’interface contextuelle d’exécution`pContext`

La `Activate` méthode peut être utilisée pour commencer à exécuter les travaux sur une nouvelle racine de processeur virtuel retournée par le gestionnaire de ressources, ou pour reprendre le proxy de fil sur une racine de processeur virtuel qui a désactivé ou est sur le point de désactiver. Voir [IVirtualProcessorRoot::Deactivate](#deactivate) pour plus d’informations sur la désactivation. Lorsque vous reprenez une racine de processeur virtuel `pContext` désactivé, le paramètre doit être le même que le paramètre utilisé pour désactiver la racine du processeur virtuel.

Une fois qu’une racine de processeur virtuel a `Deactivate` été `Activate` activée pour la première fois, des paires d’appels ultérieures peuvent courir les unes avec les autres. Cela signifie qu’il est acceptable que `Activate` le gestionnaire `Deactivate` des ressources reçoive un appel avant de recevoir l’appel pour qui il était destiné.

Lorsque vous activez une racine de processeur virtuel, vous signalez au gestionnaire de ressources que cette racine de processeur virtuel est actuellement occupée par le travail. Si votre planificateur ne trouve aucun travail à exécuter sur `Deactivate` cette racine, il est prévu d’invoquer la méthode informant le gestionnaire de ressources que la racine de processeur virtuel est inactive. Le gestionnaire des ressources utilise ces données pour charger l’équilibre du système.

`invalid_argument`est jeté si `pContext` l’argument a la valeur `NULL`.

`invalid_operation`est jeté si `pContext` l’argument ne représente pas le contexte d’exécution qui a été le plus récemment envoyé par cette racine de processeur virtuel.

L’acte d’activer une racine de processeur virtuel augmente d’un seul le niveau d’abonnement du fil matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, voir [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>IVirtualProcessorRoot::Deactivate Méthode

Provoque le proxy de thread actuellement exécutant sur cette racine de processeur virtuel pour arrêter d’envoyer le contexte d’exécution. Le proxy de thread reprendra l’exécution sur un appel à la `Activate` méthode.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Le contexte qui est actuellement expédié par cette racine.

### <a name="return-value"></a>Valeur de retour

Une valeur booléenne. Une valeur **de vrai** indique que `Deactivate` le proxy de thread `Activate` est revenu de la méthode en réponse à un appel à la méthode. Une valeur `false` de indique que le proxy de thread est revenu de la méthode en réponse à un événement de notification dans le gestionnaire de ressources. Sur un planificateur de thread schedulable en mode utilisateur (UMS), cela indique que les éléments sont apparus sur la liste d’achèvement du planificateur, et le planificateur est tenu de les gérer.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour arrêter temporairement l’exécution d’une racine de processeur virtuel lorsque vous ne trouvez aucun travail dans votre planificateur. Un appel `Deactivate` à la méthode doit `Dispatch` provenir de la méthode du contexte d’exécution avec laquelle la racine du processeur virtuel a été activée pour la dernière fois. En d’autres termes, le `Deactivate` proxy de thread invoquant la méthode doit être celui qui est actuellement en exécution sur la racine de processeur virtuel. Appeler la méthode sur une racine de processeur virtuel que vous n’exécutez pas sur pourrait entraîner un comportement indéfini.

Une racine de processeur virtuel désactivée peut être `Activate` réveillée avec un appel à la `Deactivate` méthode, avec le même argument qui a été transmis à la méthode. Le planificateur est chargé de s’assurer que les appels vers les appels et `Activate` `Deactivate` les méthodes sont appariés, mais ils ne sont pas tenus d’être reçus dans un ordre spécifique. Le gestionnaire des ressources peut `Activate` s’occuper de recevoir `Deactivate` un appel à la méthode avant de recevoir un appel à la méthode pour laquelle elle était destinée.

Si une racine de processeur virtuel se `Deactivate` réveille et que la valeur de retour de la `IUMSCompletionList::GetUnblockNotifications` méthode est fausse **de**valeur, le planificateur doit interroger la liste d’achèvement umS via la méthode, agir sur ces informations, puis appeler la `Deactivate` méthode à nouveau. Cela doit être répété jusqu’à ce que la `Deactivate` méthode retourne la valeur `true`.

`invalid_argument`est jeté si `pContext` l’argument a la valeur NULL.

`invalid_operation`est jeté si la racine du processeur virtuel `pContext` n’a jamais été activée, ou l’argument ne représente pas le contexte d’exécution qui a été le plus récemment expédié par cette racine de processeur virtuel.

L’acte de désactiver une racine de processeur virtuel diminue le niveau d’abonnement du fil matériel sous-jacent par un. Pour plus d’informations sur les niveaux d’abonnement, voir [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>IVirtualProcessorRoot::EnsureAllTasksVisible Méthode

Les données stockées dans la hiérarchie de la mémoire des processeurs individuels deviennent visibles par tous les processeurs du système. Il garantit qu’une clôture mémoire complète a été exécutée sur tous les processeurs avant le retour de la méthode.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Le contexte qui est actuellement expédié par cette racine de processeur virtuel.

### <a name="remarks"></a>Notes

Vous pouvez trouver cette méthode utile lorsque vous souhaitez synchroniser la désactivation d’une racine de processeur virtuel avec l’ajout de nouveaux travaux dans le planificateur. Pour des raisons de performance, vous pouvez décider d’ajouter des éléments de travail à votre planificateur sans exécuter une barrière de mémoire, ce qui signifie que les éléments de travail ajoutés par un thread exécutant sur un processeur ne sont pas immédiatement visibles par tous les autres processeurs. En utilisant cette méthode `Deactivate` en conjonction avec la méthode, vous pouvez vous assurer que votre planificateur ne désactive pas toutes ses racines de processeur virtuel pendant que des éléments de travail existent dans les collections de votre planificateur.

Un appel `EnsureAllTasksVisibleThe` à la méthode doit `Dispatch` provenir de la méthode du contexte d’exécution avec laquelle la racine du processeur virtuel a été activée pour la dernière fois. En d’autres termes, le `EnsureAllTasksVisible` proxy de thread invoquant la méthode doit être celui qui est actuellement en exécution sur la racine de processeur virtuel. Appeler la méthode sur une racine de processeur virtuel que vous n’exécutez pas sur pourrait entraîner un comportement indéfini.

`invalid_argument`est jeté si `pContext` l’argument a la valeur `NULL`.

`invalid_operation`est jeté si la racine du processeur virtuel `pContext` n’a jamais été activée, ou l’argument ne représente pas le contexte d’exécution qui a été le plus récemment expédié par cette racine de processeur virtuel.

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>IVirtualProcessorRoot::GetId Méthode

Retourne un identifiant unique pour la racine du processeur virtuel.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Un identificateur d’intégrant.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
