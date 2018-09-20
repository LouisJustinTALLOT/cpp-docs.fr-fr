---
title: omp_set_nest_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nest_lock OpenMP function
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7ca097219297038728adc3924980e8c91e25ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438585"
---
# <a name="ompsetnestlock"></a>omp_set_nest_lock

Blocs d’exécution de thread jusqu'à ce qu’un verrou est disponible.

## <a name="syntax"></a>Syntaxe

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type [imbriqué omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) qui a été initialisée avec [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.3 fonctions omp_set_lock et omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

## <a name="examples"></a>Exemples

Consultez [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) pour obtenir un exemple d’utilisation de `omp_set_nest_lock`.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../../parallel/openmp/reference/openmp-functions.md)