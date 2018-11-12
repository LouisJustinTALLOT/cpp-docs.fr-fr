---
title: Dépendances cumulatives
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
ms.openlocfilehash: c31740b830993c91568aea6d167fd3113b04fc57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460279"
---
# <a name="cumulative-dependencies"></a>Dépendances cumulatives

Les dépendances sont cumulées dans un bloc de description si une cible est répétée.

Par exemple, ce groupe de règles,

```Output
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

est évalué comme ceci :

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Cibles multiples dans plusieurs lignes de dépendance dans un bloc de description unique sont évaluées comme si chacune était spécifiée dans un bloc de description distinct, mais les cibles qui ne sont pas dans la dernière ligne de dépendance n’utilisent pas le bloc de commandes. NMAKE tente d’utiliser une règle d’inférence pour ces cibles.

Par exemple, ce groupe de règles,

```Output
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

est évalué comme ceci :

```Output

leap.exe : jump.obj
# invokes an inference rule
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
climb.exe : up.obj
   echo Building bounce.exe...
```

## <a name="see-also"></a>Voir aussi

[Targets (Cibles MSBuild)](../build/targets.md)