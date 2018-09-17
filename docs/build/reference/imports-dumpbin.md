---
title: -IMPORTS (DUMPBIN) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /imports
dev_langs:
- C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5b3b1e3a74fea278bc142d02f793308b6b0e054
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713568"
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