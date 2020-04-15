---
title: scheduler_interface, structure
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: da2ebc2f9c2878baefcfa792bac08f420dbbb281
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358783"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface, structure

Interface du planificateur

## <a name="syntax"></a>Syntaxe

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[scheduler_interface::calendrier](#schedule)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`scheduler_interface`

## <a name="requirements"></a>Spécifications

**En-tête:** pplinterface.h

**Namespace:** concurrence

## <a name="scheduler_interfaceschedule-method"></a><a name="schedule"></a>scheduler_interface::méthode d’horaire

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
