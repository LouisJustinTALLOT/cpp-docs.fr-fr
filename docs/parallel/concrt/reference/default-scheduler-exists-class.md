---
description: 'En savoir plus sur : classe default_scheduler_exists'
title: default_scheduler_exists, classe
ms.date: 11/04/2016
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
ms.openlocfilehash: 6921f7bd820271cf590707c2e56cefa9f576cefe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284848"
---
# <a name="default_scheduler_exists-class"></a>default_scheduler_exists, classe

Cette classe décrit une exception levée quand la méthode `Scheduler::SetDefaultSchedulerPolicy` est appelée alors qu'un planificateur par défaut existe déjà au sein du processus.

## <a name="syntax"></a>Syntaxe

```cpp
class default_scheduler_exists : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[default_scheduler_exists](#ctor)|Surchargé. Construit un objet `default_scheduler_exists`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`default_scheduler_exists`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="default_scheduler_exists"></a><a name="ctor"></a> default_scheduler_exists

Construit un objet `default_scheduler_exists`.

```cpp
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
