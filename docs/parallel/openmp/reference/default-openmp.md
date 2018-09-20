---
title: par défaut (OpenMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- default
dev_langs:
- C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea32f473d96c8f48c6628d8f71212269bd6d345
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392608"
---
# <a name="default-openmp"></a>default (OpenMP)

Spécifie le comportement de variables non délimitées dans une région parallèle.

## <a name="syntax"></a>Syntaxe

```
default(shared | none)
```

## <a name="remarks"></a>Notes

`shared`, qui est en vigueur si le `default` clause n’est pas spécifiée, signifie que n’importe quelle variable dans une région parallèle sera traité comme s’il a été spécifié avec la [partagé](../../../parallel/openmp/reference/shared-openmp.md) clause. `none` signifie que les variables utilisées dans une région parallèle qui ne sont pas limitées avec le [privé](../../../parallel/openmp/reference/private-openmp.md), [partagé](../../../parallel/openmp/reference/shared-openmp.md), [réduction](../../../parallel/openmp/reference/reduction.md), [firstprivate](../../../parallel/openmp/reference/firstprivate.md), ou [lastprivate](../../../parallel/openmp/reference/lastprivate.md) clause entraîne une erreur du compilateur.

`default` s’applique aux directives suivantes :

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [sections](../../../parallel/openmp/reference/sections-openmp.md)

Pour plus d’informations, consultez [2.7.2.5 par défaut](../../../parallel/openmp/2-7-2-5-default.md).

## <a name="example"></a>Exemple

Consultez [privé](../../../parallel/openmp/reference/private-openmp.md) pour obtenir un exemple d’utilisation de `default`.

## <a name="see-also"></a>Voir aussi

[Clauses](../../../parallel/openmp/reference/openmp-clauses.md)