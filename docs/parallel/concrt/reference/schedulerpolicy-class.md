---
title: SchedulerPolicy, classe
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: fed33c198502b75e824bcaf698227d283f4b85f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142752"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy, classe

La classe `SchedulerPolicy` contient un jeu de paires clé/valeur, un pour chaque élément de stratégie, qui contrôlent le comportement d'une instance du planificateur.

## <a name="syntax"></a>Syntaxe

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Surchargé. Construit une nouvelle stratégie de planificateur et la remplit avec des valeurs pour les [clés de stratégie](concurrency-namespace-enums.md) prises en charge par les planificateurs Runtime d’accès concurrentiel et le gestionnaire des ressources.|
|[~ SchedulerPolicy, destructeur](#dtor)|Détruit une stratégie de planificateur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|Récupère la valeur de la clé de stratégie fournie en tant que paramètre `key`.|
|[SetConcurrencyLimits](#setconcurrencylimits)|Définit simultanément les stratégies `MinConcurrency` et `MaxConcurrency` sur l’objet `SchedulerPolicy`.|
|[SetPolicyValue](#setpolicyvalue)|Définit la valeur de la clé de stratégie fournie en tant que paramètre `key` et retourne l’ancienne valeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Affecte la stratégie de planificateur à partir d’une autre stratégie de planificateur.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les stratégies qui peuvent être contrôlées à l’aide de la classe `SchedulerPolicy`, consultez [PolicyElementKey,](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SchedulerPolicy`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h, concrtrm. h

**Espace de noms :** concurrency

## <a name="getpolicyvalue"></a>GetPolicyValue

Récupère la valeur de la clé de stratégie fournie en tant que paramètre `key`.

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé de stratégie pour laquelle récupérer une valeur.

### <a name="return-value"></a>Valeur de retour

Si la clé spécifiée par le paramètre `key` est prise en charge, la valeur de la stratégie pour la clé est castée en `unsigned int`.

### <a name="remarks"></a>Notes

La méthode lève [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pour une clé de stratégie non valide.

## <a name="operator_eq"></a>opérateur =

Affecte la stratégie de planificateur à partir d’une autre stratégie de planificateur.

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Paramètres

*_RhsPolicy*<br/>
Stratégie à assigner à cette stratégie.

### <a name="return-value"></a>Valeur de retour

Référence à la stratégie du planificateur.

### <a name="remarks"></a>Notes

Souvent, la méthode la plus pratique pour définir une nouvelle stratégie de planificateur consiste à copier une stratégie existante et à la modifier à l’aide des méthodes `SetPolicyValue` ou `SetConcurrencyLimits`.

## <a name="ctor"></a>SchedulerPolicy

Construit une nouvelle stratégie de planificateur et la remplit avec des valeurs pour les [clés de stratégie](concurrency-namespace-enums.md) prises en charge par les planificateurs Runtime d’accès concurrentiel et le gestionnaire des ressources.

```cpp
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Paramètres

*_PolicyKeyCount*<br/>
Nombre de paires clé/valeur qui suivent le paramètre `_PolicyKeyCount`.

*_SrcPolicy*<br/>
Stratégie source à copier.

### <a name="remarks"></a>Notes

Le premier constructeur crée une nouvelle stratégie de planificateur dans laquelle toutes les stratégies seront initialisées à leurs valeurs par défaut.

Le deuxième constructeur crée une nouvelle stratégie de planificateur qui utilise un style de paramètre nommé d’initialisation. Les valeurs qui suivent le paramètre `_PolicyKeyCount` sont fournies en tant que paires clé/valeur. Toute clé de stratégie qui n’est pas spécifiée dans ce constructeur aura sa valeur par défaut. Ce constructeur peut lever les exceptions [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) ou [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

Le troisième constructeur est un constructeur de copie. Souvent, la méthode la plus pratique pour définir une nouvelle stratégie de planificateur consiste à copier une stratégie existante et à la modifier à l’aide des méthodes `SetPolicyValue` ou `SetConcurrencyLimits`.

## <a name="dtor"></a>~ SchedulerPolicy

Détruit une stratégie de planificateur.

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a>SetConcurrencyLimits

Définit simultanément les stratégies `MinConcurrency` et `MaxConcurrency` sur l’objet `SchedulerPolicy`.

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Paramètres

*_MinConcurrency*<br/>
Valeur de la clé de stratégie de `MinConcurrency`.

*_MaxConcurrency*<br/>
Valeur de la clé de stratégie de `MaxConcurrency`.

### <a name="remarks"></a>Notes

La méthode lève [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) si la valeur spécifiée pour la stratégie de `MinConcurrency` est supérieure à celle spécifiée pour la stratégie de `MaxConcurrency`.

La méthode peut également lever [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pour d’autres valeurs non valides.

## <a name="setpolicyvalue"></a>SetPolicyValue

Définit la valeur de la clé de stratégie fournie en tant que paramètre `key` et retourne l’ancienne valeur.

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé de stratégie pour laquelle définir une valeur.

*value*<br/>
Valeur à affecter à la clé de stratégie.

### <a name="return-value"></a>Valeur de retour

Si la clé spécifiée par le paramètre `key` est prise en charge, l’ancienne valeur de stratégie pour la clé est convertie en `unsigned int`.

### <a name="remarks"></a>Notes

La méthode lève [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pour une clé de stratégie non valide ou une clé de stratégie dont la valeur ne peut pas être définie par la méthode `SetPolicyValue`.

La méthode lève [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pour une valeur qui n’est pas prise en charge pour la clé spécifiée par le paramètre `key`.

Notez que cette méthode n’est pas autorisée à définir les stratégies de `MinConcurrency` ou de `MaxConcurrency`. Pour définir ces valeurs, utilisez la méthode [SetConcurrencyLimits](#setconcurrencylimits) .

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[PolicyElementKey,](concurrency-namespace-enums.md)<br/>
[CurrentScheduler, classe](currentscheduler-class.md)<br/>
[Scheduler, classe](scheduler-class.md)<br/>
[Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
