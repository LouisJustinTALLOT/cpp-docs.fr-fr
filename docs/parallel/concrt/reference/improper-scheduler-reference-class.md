---
title: improper_scheduler_reference, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
dev_langs:
- C++
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5a061ca3c7bb39d90608685e04b62da9b2e83fb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410414"
---
# <a name="improperschedulerreference-class"></a>improper_scheduler_reference, classe

Cette classe décrit une exception levée quand la méthode `Reference` est appelée sur un objet `Scheduler` en cours d'arrêt, à partir d'un contexte qui ne fait pas partie de ce planificateur.

## <a name="syntax"></a>Syntaxe

```
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|Surchargé. Construit un objet `improper_scheduler_reference`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> improper_scheduler_reference

Construit un objet `improper_scheduler_reference`.

```
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
