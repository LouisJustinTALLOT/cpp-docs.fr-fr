---
description: 'En savoir plus sur : classe improper_scheduler_detach'
title: improper_scheduler_detach, classe
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach::improper_scheduler_detach
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
ms.openlocfilehash: 62def23a4a3459c4cb8268b3b0f4df4a77025668
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334608"
---
# <a name="improper_scheduler_detach-class"></a>improper_scheduler_detach, classe

Cette classe décrit une exception levée quand la méthode `CurrentScheduler::Detach` est appelée sur un contexte qui n'a pas été attaché à un planificateur à l'aide de la méthode `Attach` d'un objet `Scheduler`.

## <a name="syntax"></a>Syntaxe

```cpp
class improper_scheduler_detach : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[improper_scheduler_detach](#ctor)|Surchargé. Construit un objet `improper_scheduler_detach`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`improper_scheduler_detach`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="improper_scheduler_detach"></a><a name="ctor"></a> improper_scheduler_detach

Construit un objet `improper_scheduler_detach`.

```cpp
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
