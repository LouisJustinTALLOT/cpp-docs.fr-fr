---
title: scheduler_interface, structure
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 9fa51aa5bd1fdea4eb1c35488654f0b5003e2efe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612769"
---
# <a name="schedulerinterface-structure"></a>scheduler_interface, structure

Interface du planificateur

## <a name="syntax"></a>Syntaxe

```
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[scheduler_interface::schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`scheduler_interface`

## <a name="requirements"></a>Configuration requise

**En-tête :** pplinterface.h

**Espace de noms :** concurrency

##  <a name="schedule"></a>  scheduler_interface::Schedule, méthode

```
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
