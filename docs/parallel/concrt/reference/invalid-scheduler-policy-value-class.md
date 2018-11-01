---
title: invalid_scheduler_policy_value, classe
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
ms.openlocfilehash: 53a4ee37c28cd7d45552cfe4dd7d25ce9fa37a70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439579"
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value, classe

Cette classe décrit une exception levée quand une clé de stratégie d'un objet `SchedulerPolicy` est défini sur une valeur non valide pour cette clé.

## <a name="syntax"></a>Syntaxe

```
class invalid_scheduler_policy_value : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|Surchargé. Construit un objet `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_scheduler_policy_value`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> invalid_scheduler_policy_value

Construit un objet `invalid_scheduler_policy_value`.

```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[SchedulerPolicy, classe](schedulerpolicy-class.md)
