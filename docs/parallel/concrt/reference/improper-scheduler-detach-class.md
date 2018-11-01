---
title: improper_scheduler_detach, classe
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach::improper_scheduler_detach
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
ms.openlocfilehash: b2fc90656051be62528d0aac600fad67485c81f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643285"
---
# <a name="improperschedulerdetach-class"></a>improper_scheduler_detach, classe

Cette classe décrit une exception levée quand la méthode `CurrentScheduler::Detach` est appelée sur un contexte qui n'a pas été attaché à un planificateur à l'aide de la méthode `Attach` d'un objet `Scheduler`.

## <a name="syntax"></a>Syntaxe

```
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

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> improper_scheduler_detach

Construit un objet `improper_scheduler_detach`.

```
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
