---
title: SchedulerPolicy (classe) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
dev_langs:
- C++
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: a00f7d9cafbd84fc3bbf6b10f322fad6166110cd
ms.contentlocale: fr-fr
ms.lasthandoff: 03/17/2017

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
|[SchedulerPolicy](#ctor)|Surchargé. Construit une nouvelle stratégie du planificateur et la remplit avec des valeurs pour [clés de stratégie](concurrency-namespace-enums.md) pris en charge par les planificateurs de Runtime d’accès concurrentiel et le Gestionnaire de ressources.|  
|[~ SchedulerPolicy, destructeur](#dtor)|Détruit une stratégie du planificateur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[GetPolicyValue](#getpolicyvalue)|Récupère la valeur de la clé de stratégie fournie comme le `key` paramètre.|  
|[SetConcurrencyLimits](#setconcurrencylimits)|Définit en même temps les `MinConcurrency` et `MaxConcurrency` stratégies sur le `SchedulerPolicy` objet.|  
|[SetPolicyValue](#setpolicyvalue)|Définit la valeur de la clé de stratégie fournie comme le `key` paramètre et retourne l’ancienne valeur.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator=](#operator_eq)|Assigne la stratégie du planificateur à partir d’une autre stratégie de planificateur.|  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur les stratégies qui peuvent être contrôlées à l’aide de la `SchedulerPolicy` de classe, consultez la page [PolicyElementKey](concurrency-namespace-enums.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 `SchedulerPolicy`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrt.h, concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="getpolicyvalue"></a>GetPolicyValue 

 Récupère la valeur de la clé de stratégie fournie comme le `key` paramètre.  
  
```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Clé pour récupérer une valeur de stratégie.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la clé spécifiée par le `key` paramètre est pris en charge, la valeur de stratégie pour la clé est effectué en une `unsigned int`.  
  
### <a name="remarks"></a>Notes  
 La méthode lèvera [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) une clé de stratégie non valide.  
  
##  <a name="operator_eq"></a>opérateur = 

 Assigne la stratégie du planificateur à partir d’une autre stratégie de planificateur.  
  
```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```  
  
### <a name="parameters"></a>Paramètres  
 `_RhsPolicy`  
 La stratégie à attribuer à cette stratégie.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à la stratégie du planificateur.  
  
### <a name="remarks"></a>Notes  
 Souvent, la méthode la plus commode pour définir une nouvelle stratégie du planificateur est de copier une stratégie existante et modifier à l’aide de la `SetPolicyValue` ou `SetConcurrencyLimits` méthodes.  
  
##  <a name="ctor"></a>SchedulerPolicy 

 Construit une nouvelle stratégie du planificateur et la remplit avec des valeurs pour [clés de stratégie](concurrency-namespace-enums.md) pris en charge par les planificateurs de Runtime d’accès concurrentiel et le Gestionnaire de ressources.  
  
```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
 ...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PolicyKeyCount`  
 Le nombre de clés/valeurs paires qui suivent le `_PolicyKeyCount` paramètre.  
  
 `_SrcPolicy`  
 Stratégie source à copier.  
  
### <a name="remarks"></a>Notes  
 Le premier constructeur crée une nouvelle stratégie du Planificateur où toutes les stratégies sont initialisés avec leurs valeurs par défaut.  
  
 Le deuxième constructeur crée une nouvelle stratégie du planificateur qui utilise un style de paramètre nommé d’initialisation. Valeurs après le `_PolicyKeyCount` paramètre sont fournis sous forme de paires clé/valeur. Toute clé de stratégie n’est pas spécifié dans ce constructeur aura sa valeur par défaut. Ce constructeur peut lever les exceptions [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) ou [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).  
  
 Le troisième constructeur est un constructeur de copie. Souvent, la méthode la plus commode pour définir une nouvelle stratégie du planificateur est de copier une stratégie existante et modifier à l’aide de la `SetPolicyValue` ou `SetConcurrencyLimits` méthodes.  
  
##  <a name="dtor"></a>~ SchedulerPolicy 

 Détruit une stratégie du planificateur.  
  
```
~SchedulerPolicy();
```  
  
##  <a name="setconcurrencylimits"></a>SetConcurrencyLimits 

 Définit en même temps les `MinConcurrency` et `MaxConcurrency` stratégies sur le `SchedulerPolicy` objet.  
  
```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MinConcurrency`  
 La valeur de la `MinConcurrency` clé de la stratégie.  
  
 `_MaxConcurrency`  
 La valeur de la `MaxConcurrency` clé de la stratégie.  
  
### <a name="remarks"></a>Notes  
 La méthode lèvera [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) si la valeur spécifiée pour le `MinConcurrency` stratégie est supérieure à celle spécifiée pour le `MaxConcurrency` stratégie.  
  
 La méthode peut également lever [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pour d’autres valeurs non valides.  
  
##  <a name="setpolicyvalue"></a>SetPolicyValue 

 Définit la valeur de la clé de stratégie fournie comme le `key` paramètre et retourne l’ancienne valeur.  
  
```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 La clé de stratégie pour définir une valeur pour.  
  
 `value`  
 Valeur à affecter à la clé de stratégie.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la clé spécifiée par le `key` paramètre est pris en charge, l’ancienne valeur de stratégie pour la clé est effectué en une `unsigned int`.  
  
### <a name="remarks"></a>Remarques  
 La méthode lèvera [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pour une clé de stratégie non valide ou toute clé de stratégie dont la valeur ne peut pas être définie par le `SetPolicyValue` (méthode).  
  
 La méthode lèvera [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pour une valeur qui n’est pas pris en charge pour la clé spécifiée par le `key` paramètre.  
  
 Notez que cette méthode n’est pas autorisée à définir la `MinConcurrency` ou `MaxConcurrency` stratégies. Pour définir ces valeurs, utilisez la [SetConcurrencyLimits](#setconcurrencylimits) méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [CurrentScheduler, classe](currentscheduler-class.md)   
 [Scheduler (classe)](scheduler-class.md)   
 [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




