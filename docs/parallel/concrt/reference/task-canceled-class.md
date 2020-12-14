---
description: 'En savoir plus sur : classe task_canceled'
title: task_canceled, classe
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: 223a1168464e312c272f770247b3574311ff97ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188402"
---
# <a name="task_canceled-class"></a>task_canceled, classe

Cette classe décrit une exception levée par la couche de tâches PPL pour forcer l’annulation de la tâche actuelle. Elle est également levée par la `get()` méthode sur [Task](/visualstudio/extensibility/debugger/task-class-internal-members), pour une tâche annulée.

## <a name="syntax"></a>Syntaxe

```cpp
class task_canceled : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[task_canceled](#ctor)|Surchargé. Construit un objet `task_canceled`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`task_canceled`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="task_canceled"></a><a name="ctor"></a> task_canceled

Construit un objet `task_canceled`.

```cpp
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
