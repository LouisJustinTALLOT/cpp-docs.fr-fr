---
title: OMP_NUM_THREADS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NUM_THREADS
dev_langs:
- C++
helpviewer_keywords:
- OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9612eefaf2b5706a4034dc027c0fc43618fd048a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436856"
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS

Définit le nombre maximal de threads dans la région parallèle, sauf substitution par [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) ou [num_threads](../../../parallel/openmp/reference/num-threads.md).

## <a name="syntax"></a>Syntaxe

```
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Paramètres

*num*<br/>
Le nombre maximal de threads souhaité dans la région parallèle, jusqu'à 64 dans l’implémentation Visual C++.

## <a name="remarks"></a>Notes

Le **OMP_NUM_THREADS** variable d’environnement peut être remplacée par la [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) (fonction) ou par [num_threads](../../../parallel/openmp/reference/num-threads.md).

La valeur par défaut `num` dans Visual C++, mise en œuvre de la norme OpenMP est le nombre de processeurs virtuels, y compris les processeurs avec hyperthreading.

Pour plus d’informations, consultez [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

## <a name="example"></a>Exemple

La commande suivante définit le **OMP_NUM_THREADS** variable d’environnement à 16 :

```
set OMP_NUM_THREADS=16
```

La commande suivante affiche le paramètre actuel de la **OMP_NUM_THREADS** variable d’environnement :

```
set OMP_NUM_THREADS
```

## <a name="see-also"></a>Voir aussi

[Variables d’environnement](../../../parallel/openmp/reference/openmp-environment-variables.md)