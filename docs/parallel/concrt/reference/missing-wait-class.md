---
title: missing_wait, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs:
- C++
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0363b7dd1e4840b7afb6c013c5d439e64fbbb2ef
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425897"
---
# <a name="missingwait-class"></a>missing_wait, classe

Cette classe décrit une exception levée quand il existe des tâches encore planifiées sur un objet `task_group` ou `structured_task_group` au moment où le destructeur d'objet s'exécute. Cette exception n'est jamais levée si le destructeur est atteint en raison d'un déroulement de pile consécutif à une exception.

## <a name="syntax"></a>Syntaxe

```
class missing_wait : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[missing_wait](#ctor)|Surchargé. Construit un objet `missing_wait`.|

## <a name="remarks"></a>Notes

Absence de flux d’exception, vous êtes chargé de l’appel le `wait` ou `run_and_wait` méthode d’un `task_group` ou `structured_task_group` objet avant d’autoriser la destruction de cet objet. Le runtime lève cette exception pour indiquer que vous avez oublié d’appeler le `wait` ou `run_and_wait` (méthode).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`missing_wait`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> missing_wait

Construit un objet `missing_wait`.

```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[task_group, classe](task-group-class.md)<br/>
[attente](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group, classe](structured-task-group-class.md)
