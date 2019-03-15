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
ms.openlocfilehash: c8b0f88b38eb657fe4d3916ef0df13972e985cbe
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810339"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Cette option affiche la liste des DLL (à lien statique et [chargé différé](linker-support-for-delay-loaded-dlls.md)) qui sont importées vers un fichier exécutable ou une DLL et toutes les instructions imports individuels à partir de chacune de ces DLL.

Le paramètre facultatif `file` spécification vous permet de spécifier que les importations pour seulement cette DLL seront affichées. Exemple :

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Notes

La sortie affichée par cette option est similaire à la [/EXPORTE](dash-exports.md) sortie.

Uniquement les [/HEADERS](headers.md) (option DUMPBIN) est disponible pour les fichiers générés avec le [/GL](gl-whole-program-optimization.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)
