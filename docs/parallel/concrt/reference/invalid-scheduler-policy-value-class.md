---
description: 'En savoir plus sur : classe invalid_scheduler_policy_value'
title: invalid_scheduler_policy_value, classe
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
ms.openlocfilehash: c91295646b0bc85ea4ed5ee8f376c1ed029e4f0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334484"
---
# <a name="invalid_scheduler_policy_value-class"></a>invalid_scheduler_policy_value, classe

Cette classe décrit une exception levée quand une clé de stratégie d'un objet `SchedulerPolicy` est défini sur une valeur non valide pour cette clé.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_scheduler_policy_value : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_scheduler_policy_value] (non valide-Scheduler-Policy-thread-Specification-Class. MD # ctor|Surchargé. Construit un objet `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_scheduler_policy_value`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="invalid_scheduler_policy_value"></a><a name="ctor"></a> invalid_scheduler_policy_value

Construit un objet `invalid_scheduler_policy_value`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[SchedulerPolicy, classe](schedulerpolicy-class.md)
