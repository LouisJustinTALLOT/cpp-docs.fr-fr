---
title: omp_destroy_nest_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_nest_lock OpenMP function
ms.assetid: 0ab1352b-668f-43dd-b441-31ec4cc53e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d5cb4e985c82bec859959f374ffe35f33548228
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377251"
---
# <a name="ompdestroynestlock"></a>omp_destroy_nest_lock

Désinitialise un verrou pouvant être imbriqué.

## <a name="syntax"></a>Syntaxe

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Une variable de type [imbriqué omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) qui a été initialisée avec [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [3.2.2 fonctions omp_destroy_lock et omp_destroy_nest_lock fonctions](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

## <a name="example"></a>Exemple

Consultez [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) pour obtenir un exemple d’utilisation de `omp_destroy_nest_lock`.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../../parallel/openmp/reference/openmp-functions.md)