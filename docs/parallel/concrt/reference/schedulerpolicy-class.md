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
ms.openlocfilehash: 2eff40b11e4e9a5981ad85c37c8345abefb13fed
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265533"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy, classe

La classe `SchedulerPolicy` contient un jeu de paires clé/valeur, un pour chaque élément de stratégie, qui contrôlent le comportement d'une instance du planificateur.

## <a name="syntax"></a>Syntaxe

```
class SchedulerPolicy;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Surchargé. Construit une nouvelle stratégie de planificateur et la remplit avec des valeurs pour [clés de stratégie](concurrency-namespace-enums.md) pris en charge par les planificateurs de Runtime d’accès concurrentiel et le Gestionnaire de ressources.|
|[~ SchedulerPolicy, destructeur](#dtor)|Détruit une stratégie du planificateur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|Récupère la valeur de la clé de stratégie fournie en tant que le `key` paramètre.|
|[SetConcurrencyLimits](#setconcurrencylimits)|Définit simultanément le `MinConcurrency` et `MaxConcurrency` stratégies sur le `SchedulerPolicy` objet.|
|[SetPolicyValue](#setpolicyvalue)|Définit la valeur de la clé de stratégie fournie en tant que le `key` paramètre et retourne l’ancienne valeur.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Assigne la stratégie du planificateur à partir d’une autre stratégie de planificateur.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les stratégies qui peuvent être contrôlées à l’aide de la `SchedulerPolicy` de classe, consultez [PolicyElementKey](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SchedulerPolicy`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt.h, concrtrm.h

**Espace de noms :** concurrency

##  <a name="getpolicyvalue"></a> GetPolicyValue

Récupère la valeur de la clé de stratégie fournie en tant que le `key` paramètre.

```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé de stratégie pour récupérer une valeur pour.

### <a name="return-value"></a>Valeur de retour

Si la clé spécifiée par le `key` paramètre est pris en charge, la valeur de stratégie pour la clé est casté en un `unsigned int`.

### <a name="remarks"></a>Notes

La méthode lèvera [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pour une clé de stratégie non valide.

##  <a name="operator_eq"></a> operator=

Assigne la stratégie du planificateur à partir d’une autre stratégie de planificateur.

```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Paramètres

*_RhsPolicy*<br/>
La stratégie à attribuer à cette stratégie.

### <a name="return-value"></a>Valeur de retour

Une référence à la stratégie du planificateur.

### <a name="remarks"></a>Notes

Souvent, le plus pratique pour définir une nouvelle stratégie de planificateur consiste à copier une stratégie existante et modifiez-le à l’aide de la `SetPolicyValue` ou `SetConcurrencyLimits` méthodes.

##  <a name="ctor"></a> SchedulerPolicy

Construit une nouvelle stratégie de planificateur et la remplit avec des valeurs pour [clés de stratégie](concurrency-namespace-enums.md) pris en charge par les planificateurs de Runtime d’accès concurrentiel et le Gestionnaire de ressources.

```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Paramètres

*_PolicyKeyCount*<br/>
Nombre de clés/valeurs paires qui suivent le `_PolicyKeyCount` paramètre.

*_SrcPolicy*<br/>
La stratégie de la source à copier.

### <a name="remarks"></a>Notes

Le premier constructeur crée une nouvelle stratégie de planificateur où toutes les stratégies seront initialisés à leurs valeurs par défaut.

Le deuxième constructeur crée une nouvelle stratégie du planificateur qui utilise un style de paramètre nommé de l’initialisation. Valeurs après la `_PolicyKeyCount` paramètre sont fournis sous forme de paires clé/valeur. Toute clé de stratégie qui n’est pas spécifié dans ce constructeur aura sa valeur par défaut. Ce constructeur pourrait lever les exceptions [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) ou [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

Le troisième constructeur est un constructeur de copie. Souvent, le plus pratique pour définir une nouvelle stratégie de planificateur consiste à copier une stratégie existante et modifiez-le à l’aide de la `SetPolicyValue` ou `SetConcurrencyLimits` méthodes.

##  <a name="dtor"></a> ~SchedulerPolicy

Détruit une stratégie du planificateur.

```
~SchedulerPolicy();
```

##  <a name="setconcurrencylimits"></a> SetConcurrencyLimits

Définit simultanément le `MinConcurrency` et `MaxConcurrency` stratégies sur le `SchedulerPolicy` objet.

```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Paramètres

*_MinConcurrency*<br/>
La valeur de la `MinConcurrency` clé de la stratégie.

*_MaxConcurrency*<br/>
La valeur de la `MaxConcurrency` clé de la stratégie.

### <a name="remarks"></a>Notes

La méthode lèvera [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) si la valeur spécifiée pour le `MinConcurrency` stratégie est supérieure à celle spécifiée pour le `MaxConcurrency` stratégie.

La méthode peut également lever [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pour les autres valeurs non valides.

##  <a name="setpolicyvalue"></a> SetPolicyValue

Définit la valeur de la clé de stratégie fournie en tant que le `key` paramètre et retourne l’ancienne valeur.

```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé de stratégie pour définir une valeur pour.

*value*<br/>
Valeur à affecter à la clé de stratégie.

### <a name="return-value"></a>Valeur de retour

Si la clé spécifiée par le `key` paramètre est pris en charge, l’ancienne valeur de stratégie pour la clé est casté en un `unsigned int`.

### <a name="remarks"></a>Notes

La méthode lèvera [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pour une clé de stratégie non valide ou toute clé de stratégie dont la valeur ne peut pas être définie par le `SetPolicyValue` (méthode).

La méthode lèvera [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pour une valeur qui n’est pas pris en charge pour la clé spécifiée par le `key` paramètre.

Notez que cette méthode n’est pas autorisée à définir le `MinConcurrency` ou `MaxConcurrency` stratégies. Pour définir ces valeurs, utilisez le [SetConcurrencyLimits](#setconcurrencylimits) (méthode).

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[CurrentScheduler, classe](currentscheduler-class.md)<br/>
[Scheduler, classe](scheduler-class.md)<br/>
[Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
