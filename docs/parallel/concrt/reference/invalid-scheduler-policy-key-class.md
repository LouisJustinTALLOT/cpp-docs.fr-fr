---
description: 'En savoir plus sur : classe invalid_scheduler_policy_key'
title: invalid_scheduler_policy_key, classe
ms.date: 11/04/2016
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
ms.openlocfilehash: d352246cf0fe94f0ba5ee567f353680c89efcddc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334520"
---
# <a name="invalid_scheduler_policy_key-class"></a>invalid_scheduler_policy_key, classe

Cette classe décrit une exception levée quand une clé non valide ou inconnue est passée à un constructeur d'objet `SchedulerPolicy`, ou quand la méthode `SetPolicyValue` d'un objet `SchedulerPolicy` est passée à une clé qui doit être modifiée à l'aide d'autres moyens que la méthode `SetConcurrencyLimits`.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_scheduler_policy_key : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[invalid_scheduler_policy_key](#ctor)|Surchargé. Construit un objet `invalid_scheduler_policy_key`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`invalid_scheduler_policy_key`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="invalid_scheduler_policy_key"></a><a name="ctor"></a> invalid_scheduler_policy_key

Construit un objet `invalid_scheduler_policy_key`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[SchedulerPolicy, classe](schedulerpolicy-class.md)
