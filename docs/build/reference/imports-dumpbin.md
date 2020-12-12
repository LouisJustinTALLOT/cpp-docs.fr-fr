---
description: En savoir plus sur:/IMPORTS (DUMPBIN)
title: /IMPORTS (DUMPBIN)
ms.date: 11/04/2016
f1_keywords:
- /imports
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
ms.openlocfilehash: 86c428280bbca3a4957f7d7a0a640482607547de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199790"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Cette option affiche la liste des dll (liées de manière statique et [retardées](linker-support-for-delay-loaded-dlls.md)) qui sont importées dans un fichier exécutable ou une dll et toutes les importations individuelles de chacune de ces dll.

La `file` spécification facultative vous permet de spécifier que les importations de cette dll uniquement seront affichées. Par exemple :

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Notes

La sortie affichée par cette option est semblable à la sortie [/exports](dash-exports.md) .

Seule l’option [/HEADERS](headers.md) DUMPBIN peut être utilisée sur les fichiers générés avec l’option du compilateur [/GL](gl-whole-program-optimization.md).

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)
