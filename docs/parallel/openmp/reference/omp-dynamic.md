---
title: OMP_DYNAMIC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b02a2a4d660057ab83da39add7fd32bcff3e6d90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392136"
---
# <a name="ompdynamic"></a>OMP_DYNAMIC

Spécifie si la durée d’exécution de OpenMP peut ajuster le nombre de threads dans une région parallèle.

## <a name="syntax"></a>Syntaxe

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

## <a name="remarks"></a>Notes

Le `OMP_DYNAMIC` variable d’environnement peut être remplacée par la [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) (fonction).

La valeur par défaut dans l’implémentation Visual C++ de la norme OpenMP est `OMP_DYNAMIC=FALSE`.

Pour plus d’informations, consultez [OMP_DYNAMIC 4.3](../../../parallel/openmp/4-3-omp-dynamic.md).

## <a name="example"></a>Exemple

La commande suivante définit le `OMP_DYNAMIC` variable d’environnement sur TRUE :

```
set OMP_DYNAMIC=TRUE
```

La commande suivante affiche le paramètre actuel de la `OMP_DYNAMIC` variable d’environnement :

```
set OMP_DYNAMIC
```

## <a name="see-also"></a>Voir aussi

[Variables d’environnement](../../../parallel/openmp/reference/openmp-environment-variables.md)