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
ms.openlocfilehash: 8c9553b036890c4ce28f1060bfe2f58ee1904935
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138865"
---
# <a name="nested_scheduler_missing_detach-class"></a>nested_scheduler_missing_detach, classe

Cette classe décrit une exception levée quand le runtime d'accès concurrentiel détecte que vous avez omis d'appeler la méthode `CurrentScheduler::Detach` sur un contexte joint à un deuxième planificateur à l'aide de la méthode `Attach` de l'objet `Scheduler`.

## <a name="syntax"></a>Syntaxe

```cpp
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|Surchargé. Construit un objet `nested_scheduler_missing_detach`.|

## <a name="remarks"></a>Notes

Cette exception est levée uniquement lorsque vous imbriquez un planificateur à l’intérieur d’un autre en appelant la méthode `Attach` d’un objet `Scheduler` sur un contexte qui appartient déjà à un autre planificateur ou qui lui est associé. L’runtime d’accès concurrentiel lève cette exception associer façon opportuniste lorsqu’il peut détecter le scénario comme une aide pour localiser le problème. Il est garanti que la levée de cette exception ne se produise pas chaque fois que l’appel de la méthode `CurrentScheduler::Detach` est garanti.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>nested_scheduler_missing_detach

Construit un objet `nested_scheduler_missing_detach`.

```cpp
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>Paramètres

*_Message*<br/>
Message descriptif de l'erreur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Scheduler, classe](scheduler-class.md)
