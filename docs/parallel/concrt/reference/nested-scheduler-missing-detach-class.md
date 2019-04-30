---
title: nested_scheduler_missing_detach, classe
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: db51f7b083cc0cbd9337fbbe5c672d190208f328
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394388"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach, classe

Cette classe décrit une exception levée quand le runtime d'accès concurrentiel détecte que vous avez omis d'appeler la méthode `CurrentScheduler::Detach` sur un contexte joint à un deuxième planificateur à l'aide de la méthode `Attach` de l'objet `Scheduler`.

## <a name="syntax"></a>Syntaxe

```
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|Surchargé. Construit un objet `nested_scheduler_missing_detach`.|

## <a name="remarks"></a>Notes

Cette exception est levée uniquement lorsque vous imbriquez un planificateur à l’intérieur d’un autre en appelant le `Attach` méthode d’un `Scheduler` objet sur un contexte qui est déjà détenu par ou attaché à un autre planificateur. Le Runtime d’accès concurrentiel lève cette exception de façon opportuniste lorsqu’il peut détecter le scénario comme une aide pour localiser le problème. Pas de chaque instance de négligeant l’appel à la `CurrentScheduler::Detach` la méthode est garantie pour lever cette exception.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> nested_scheduler_missing_detach

Construit un objet `nested_scheduler_missing_detach`.

```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
