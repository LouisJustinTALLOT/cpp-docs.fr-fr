---
title: invalid_scheduler_policy_key, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a183f0f875c0e4384131828f9929ea0dca2c5f8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411623"
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key, classe

Cette classe décrit une exception levée quand une clé non valide ou inconnue est passée à un constructeur d'objet `SchedulerPolicy`, ou quand la méthode `SetPolicyValue` d'un objet `SchedulerPolicy` est passée à une clé qui doit être modifiée à l'aide d'autres moyens que la méthode `SetConcurrencyLimits`.

## <a name="syntax"></a>Syntaxe

```
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

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> invalid_scheduler_policy_key

Construit un objet `invalid_scheduler_policy_key`.

```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[SchedulerPolicy, classe](schedulerpolicy-class.md)
