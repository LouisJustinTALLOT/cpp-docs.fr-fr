---
title: default_scheduler_exists, classe
ms.date: 11/04/2016
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
ms.openlocfilehash: 326a2dfc6837665adb4d46a6aaa8780052ad2b22
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275270"
---
# <a name="defaultschedulerexists-class"></a>default_scheduler_exists, classe

Cette classe décrit une exception levée quand la méthode `Scheduler::SetDefaultSchedulerPolicy` est appelée alors qu'un planificateur par défaut existe déjà au sein du processus.

## <a name="syntax"></a>Syntaxe

```
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

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> default_scheduler_exists

Construit un objet `default_scheduler_exists`.

```
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
