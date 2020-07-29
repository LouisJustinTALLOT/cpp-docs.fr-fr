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
ms.openlocfilehash: b7b99dae2ffb58123c05a65872e4c71e149ac12c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219571"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy, classe

La classe `SchedulerPolicy` contient un jeu de paires clé/valeur, un pour chaque élément de stratégie, qui contrôlent le comportement d'une instance du planificateur.

## <a name="syntax"></a>Syntaxe

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Surchargé. Construit une nouvelle stratégie de planificateur et la remplit avec des valeurs pour les [clés de stratégie](concurrency-namespace-enums.md) prises en charge par les planificateurs Runtime d’accès concurrentiel et le gestionnaire des ressources.|
|[~ SchedulerPolicy, destructeur](#dtor)|Détruit une stratégie de planificateur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|Récupère la valeur de la clé de stratégie fournie en tant que `key` paramètre.|
|[SetConcurrencyLimits](#setconcurrencylimits)|Définit simultanément les `MinConcurrency` `MaxConcurrency` stratégies et sur l' `SchedulerPolicy` objet.|
|[SetPolicyValue](#setpolicyvalue)|Définit la valeur de la clé de stratégie fournie en tant que `key` paramètre et retourne l’ancienne valeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur =](#operator_eq)|Affecte la stratégie de planificateur à partir d’une autre stratégie de planificateur.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les stratégies qui peuvent être contrôlées à l’aide de la `SchedulerPolicy` classe, consultez [PolicyElementKey,](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SchedulerPolicy`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h, concrtrm. h

**Espace de noms :** concurrence

## <a name="getpolicyvalue"></a><a name="getpolicyvalue"></a>GetPolicyValue

Récupère la valeur de la clé de stratégie fournie en tant que `key` paramètre.

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé de stratégie pour laquelle récupérer une valeur.

### <a name="return-value"></a>Valeur de retour

Si la clé spécifiée par le `key` paramètre est prise en charge, la valeur de stratégie pour la clé est castée en **`unsigned int`** .

### <a name="remarks"></a>Notes

La méthode lève [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pour une clé de stratégie non valide.

## <a name="operator"></a><a name="operator_eq"></a>opérateur =

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

Souvent, la méthode la plus pratique pour définir une nouvelle stratégie de planificateur consiste à copier une stratégie existante et à la modifier à l’aide des `SetPolicyValue` `SetConcurrencyLimits` méthodes ou.

## <a name="schedulerpolicy"></a><a name="ctor"></a>SchedulerPolicy

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
Nombre de paires clé/valeur qui suivent le `_PolicyKeyCount` paramètre.

*_SrcPolicy*<br/>
Stratégie source à copier.

### <a name="remarks"></a>Notes

Le premier constructeur crée une nouvelle stratégie de planificateur dans laquelle toutes les stratégies seront initialisées à leurs valeurs par défaut.

Le deuxième constructeur crée une nouvelle stratégie de planificateur qui utilise un style de paramètre nommé d’initialisation. Les valeurs qui suivent le `_PolicyKeyCount` paramètre sont fournies en tant que paires clé/valeur. Toute clé de stratégie qui n’est pas spécifiée dans ce constructeur aura sa valeur par défaut. Ce constructeur peut lever les exceptions [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) ou [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

Le troisième constructeur est un constructeur de copie. Souvent, la méthode la plus pratique pour définir une nouvelle stratégie de planificateur consiste à copier une stratégie existante et à la modifier à l’aide des `SetPolicyValue` `SetConcurrencyLimits` méthodes ou.

## <a name="schedulerpolicy"></a><a name="dtor"></a>~ SchedulerPolicy

Détruit une stratégie de planificateur.

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a><a name="setconcurrencylimits"></a>SetConcurrencyLimits

Définit simultanément les `MinConcurrency` `MaxConcurrency` stratégies et sur l' `SchedulerPolicy` objet.

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Paramètres

*_MinConcurrency*<br/>
Valeur de la `MinConcurrency` clé de stratégie.

*_MaxConcurrency*<br/>
Valeur de la `MaxConcurrency` clé de stratégie.

### <a name="remarks"></a>Notes

La méthode lève [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) si la valeur spécifiée pour la `MinConcurrency` stratégie est supérieure à celle spécifiée pour la `MaxConcurrency` stratégie.

La méthode peut également lever [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pour d’autres valeurs non valides.

## <a name="setpolicyvalue"></a><a name="setpolicyvalue"></a>SetPolicyValue

Définit la valeur de la clé de stratégie fournie en tant que `key` paramètre et retourne l’ancienne valeur.

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

Si la clé spécifiée par le `key` paramètre est prise en charge, l’ancienne valeur de stratégie pour la clé est castée en **`unsigned int`** .

### <a name="remarks"></a>Notes

La méthode lève [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pour une clé de stratégie non valide ou une clé de stratégie dont la valeur ne peut pas être définie par la `SetPolicyValue` méthode.

La méthode lève [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pour une valeur qui n’est pas prise en charge pour la clé spécifiée par le `key` paramètre.

Notez que cette méthode n’est pas autorisée à définir `MinConcurrency` les `MaxConcurrency` stratégies ou. Pour définir ces valeurs, utilisez la méthode [SetConcurrencyLimits](#setconcurrencylimits) .

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[PolicyElementKey,](concurrency-namespace-enums.md)<br/>
[CurrentScheduler, classe](currentscheduler-class.md)<br/>
[Scheduler, classe](scheduler-class.md)<br/>
[Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
