---
title: /IMPORTS (DUMPBIN)
ms.date: 11/04/2016
f1_keywords:
- /imports
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
ms.openlocfilehash: 94009670329887a0b8a35e7b8b36996a84c7faa6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417500"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Cette option affiche la liste des DLL (à lien statique et [chargé différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)) qui sont importées vers un fichier exécutable ou une DLL et toutes les instructions imports individuels à partir de chacune de ces DLL.

Le paramètre facultatif `file` spécification vous permet de spécifier que les importations pour seulement cette DLL seront affichées. Exemple :

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Notes

La sortie affichée par cette option est similaire à la [/EXPORTE](../../build/reference/dash-exports.md) sortie.

Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés avec le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](../../build/reference/dumpbin-options.md)
