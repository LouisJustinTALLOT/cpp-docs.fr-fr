---
title: cloisonnement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c220106d62bf65505c9c5b48085a9ee3e67fe0cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415029"
---
# <a name="barrier"></a>barrier

Synchronise tous les threads dans une équipe. tous les threads suspendre à la barrière, jusqu'à ce que tous les threads exécuteront le cloisonnement.

## <a name="syntax"></a>Syntaxe

```
#pragma omp barrier
```

## <a name="remarks"></a>Notes

Le `barrier` directive prend en charge aucune clause OpenMP.

Pour plus d’informations, consultez [2.6.3 Directive barrier](../../../parallel/openmp/2-6-3-barrier-directive.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser `barrier`, consultez [master](../../../parallel/openmp/reference/master.md).

## <a name="see-also"></a>Voir aussi

[Directives](../../../parallel/openmp/reference/openmp-directives.md)