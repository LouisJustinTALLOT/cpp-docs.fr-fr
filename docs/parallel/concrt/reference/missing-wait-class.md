---
description: 'En savoir plus sur : classe missing_wait'
title: missing_wait, classe
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: bfbfdf4c2a52573d08c048bac278386aed1dc5a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202182"
---
# <a name="missing_wait-class"></a>missing_wait, classe

Cette classe décrit une exception levée quand il existe des tâches encore planifiées sur un objet `task_group` ou `structured_task_group` au moment où le destructeur d’objet s’exécute. Cette exception n'est jamais levée si le destructeur est atteint en raison d'un déroulement de pile consécutif à une exception.

## <a name="syntax"></a>Syntaxe

```cpp
class missing_wait : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[missing_wait](#ctor)|Surchargé. Construit un objet `missing_wait`.|

## <a name="remarks"></a>Notes

En l’absence de workflow d’exception, vous êtes chargé d’appeler la `wait` `run_and_wait` méthode ou d’un `task_group` `structured_task_group` objet ou avant d’autoriser la destruction de cet objet. Le runtime lève cette exception pour indiquer que vous avez oublié d’appeler la `wait` méthode ou `run_and_wait` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`missing_wait`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="missing_wait"></a><a name="ctor"></a> missing_wait

Construit un objet `missing_wait`.

```cpp
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe task_group](task-group-class.md)<br/>
[wait](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[Classe structured_task_group](structured-task-group-class.md)
