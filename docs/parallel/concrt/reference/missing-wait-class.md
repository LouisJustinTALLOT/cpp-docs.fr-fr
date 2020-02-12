---
title: missing_wait, classe
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: cf81d1ee6c144da210da5b1f37aca7910ae37bc8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142389"
---
# <a name="missing_wait-class"></a>missing_wait, classe

Cette classe décrit une exception levée quand il existe des tâches encore planifiées sur un objet `task_group` ou `structured_task_group` au moment où le destructeur d’objet s’exécute. Cette exception n'est jamais levée si le destructeur est atteint en raison d'un déroulement de pile consécutif à une exception.

## <a name="syntax"></a>Syntaxe

```cpp
class missing_wait : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[missing_wait](#ctor)|Surchargé. Construit un objet `missing_wait`.|

## <a name="remarks"></a>Notes

En l’absence de workflow d’exception, vous êtes chargé d’appeler la méthode `wait` ou `run_and_wait` d’un objet `task_group` ou `structured_task_group` avant d’autoriser la destruction de cet objet. Le runtime lève cette exception pour indiquer que vous avez oublié d’appeler la méthode `wait` ou `run_and_wait`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`missing_wait`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>missing_wait

Construit un objet `missing_wait`.

```cpp
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Classe task_group](task-group-class.md)<br/>
[qu'](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group, classe](structured-task-group-class.md)
