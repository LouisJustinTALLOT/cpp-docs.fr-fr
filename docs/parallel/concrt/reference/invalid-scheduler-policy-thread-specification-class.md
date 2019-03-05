---
title: invalid_scheduler_policy_thread_specification, classe
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: 26d09610c6bb9e0c87852c9804e094617b021273
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278871"
---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification, classe

Cette classe décrit une exception levée quand est effectuée une tentative de définir les limites d'accès concurrentiel d'un objet `SchedulerPolicy` de telle sorte que la valeur de la clé `MinConcurrency` est inférieure à celle de la clé `MaxConcurrency`.

## <a name="syntax"></a>Syntaxe

```
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|Surchargé. Construit un objet `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt.h

**Espace de noms :** concurrency
##  <a name="ctor"></a> invalid_scheduler_policy_thread_specification

Construit un objet `invalid_scheduler_policy_value`.

```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[SchedulerPolicy, classe](schedulerpolicy-class.md)
