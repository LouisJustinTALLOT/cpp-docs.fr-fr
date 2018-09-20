---
title: omp_get_nested | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20a7378ba7e7f6dcec55cfe265dd0873bdc1fd38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371951"
---
# <a name="ompgetnested"></a>omp_get_nested

Retourne une valeur qui indique si le parallélisme imbriquée est activée.

## <a name="syntax"></a>Syntaxe

```
int omp_get_nested( );
```

## <a name="return-value"></a>Valeur de retour

Si différent de zéro, le parallélisme imbriquée est activée.

## <a name="remarks"></a>Notes

Parallélisme imbriquée est spécifié avec [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) et [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md).

Pour plus d’informations, consultez [3.1.10 fonction omp_get_nested](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

## <a name="example"></a>Exemple

Consultez [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) pour obtenir un exemple d’utilisation de `omp_get_nested`.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../../parallel/openmp/reference/openmp-functions.md)