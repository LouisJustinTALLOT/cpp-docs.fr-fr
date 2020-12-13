---
description: 'En savoir plus sur : classe improper_scheduler_reference'
title: improper_scheduler_reference, classe
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
ms.openlocfilehash: 4857418e14908b2d085d52249236d6395284b98a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334599"
---
# <a name="improper_scheduler_reference-class"></a>improper_scheduler_reference, classe

Cette classe décrit une exception levée quand la méthode `Reference` est appelée sur un objet `Scheduler` en cours d'arrêt, à partir d'un contexte qui ne fait pas partie de ce planificateur.

## <a name="syntax"></a>Syntaxe

```cpp
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

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="improper_scheduler_reference"></a><a name="ctor"></a> improper_scheduler_reference

Construit un objet `improper_scheduler_reference`.

```cpp
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
