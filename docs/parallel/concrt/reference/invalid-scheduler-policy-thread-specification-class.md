---
description: 'En savoir plus sur : classe invalid_scheduler_policy_thread_specification'
title: invalid_scheduler_policy_thread_specification, classe
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: 97a3910fc83e741c54ece51ed8e20686bbd6c66b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334503"
---
# <a name="invalid_scheduler_policy_thread_specification-class"></a>invalid_scheduler_policy_thread_specification, classe

Cette classe décrit une exception levée quand est effectuée une tentative de définir les limites d'accès concurrentiel d'un objet `SchedulerPolicy` de telle sorte que la valeur de la clé `MinConcurrency` est inférieure à celle de la clé `MaxConcurrency`.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification] (non valide-Scheduler-Policy-value-class. MD # ctor|Surchargé. Construit un objet `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="invalid_scheduler_policy_thread_specification"></a><a name="ctor"></a> invalid_scheduler_policy_thread_specification

Construit un objet `invalid_scheduler_policy_value`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[SchedulerPolicy, classe](schedulerpolicy-class.md)
