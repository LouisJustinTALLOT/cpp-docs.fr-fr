---
title: Effets secondaires des dépendances | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a70df679434b187bc2eee4eb4aad5881db0da1c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716517"
---
# <a name="dependency-side-effects"></a>Effets secondaires des dépendances

Si une cible est spécifiée avec un signe deux-points ( :)) sur deux lignes de dépendance dans différents emplacements, et si les commandes apparaissent uniquement après l’une des lignes, NMAKE interprète les dépendances comme si adjacentes ou combinées. Il n’appelle pas une règle d’inférence pour la dépendance qui n’a aucune commande, mais au lieu de cela suppose que les dépendances appartiennent à un bloc d’une description et exécute les commandes spécifiées avec l’autre dépendance. Par exemple, ce groupe de règles :

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

est évalué comme ceci :

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Cet effet ne se produit pas si un double deux-points (`::`) est utilisé. Par exemple, ce groupe de règles :

```Output
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

est évalué comme ceci :

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

## <a name="see-also"></a>Voir aussi

[Targets (Cibles MSBuild)](../build/targets.md)