---
title: Effets secondaires des dépendances
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
ms.openlocfilehash: b89306b6e4d85e0e08729fb1d35fb041d69647e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272111"
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

[Cibles](targets.md)
