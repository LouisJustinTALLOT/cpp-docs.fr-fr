---
title: /DEPENDENTS
ms.date: 07/15/2019
f1_keywords:
- /dependents
helpviewer_keywords:
- -DEPENDENTS dumpbin option
- /DEPENDENTS dumpbin option
- DEPENDENTS dumpbin option
ms.assetid: 9b31da2a-75ac-4bbf-a3f1-adf8b0ecbbb4
ms.openlocfilehash: 88f0062a6bbca3f9199a12f739c2ade5f9d912cd
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299745"
---
# <a name="dependents"></a>/DEPENDENTS

Vide les noms des dll à partir desquelles l’image importe des fonctions. Vous pouvez utiliser la liste pour déterminer les dll à redistribuer avec votre application ou Rechercher le nom d’une dépendance manquante.

## <a name="syntax"></a>Syntaxe

> **/DEPENDENTS**

Cette option s’applique à tous les fichiers exécutables spécifiés sur la ligne de commande. Elle ne prend pas d’arguments.

## <a name="remarks"></a>Notes

L’option **/Dependents** ajoute les noms des dll à partir desquelles l’image importe les fonctions dans la sortie. Cette option n’effectue pas de vidage des noms des fonctions importées. Pour afficher les noms des fonctions importées, utilisez l’option [/Imports](imports-dumpbin.md) .

Seule l’option [/HEADERS](headers.md) DUMPBIN peut être utilisée sur les fichiers générés avec l’option du compilateur [/GL](gl-whole-program-optimization.md).

## <a name="example"></a>Exemple

Cet exemple montre la sortie DUMPBIN de l’option **/Dependents** sur l’exécutable client créé dans [la procédure pas à pas: Créez et utilisez votre propre bibliothèque](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)de liens dynamiques:

```cmd
C:\Users\username\Source\Repos\MathClient\Debug>dumpbin /DEPENDENTS MathClient.exe
Microsoft (R) COFF/PE Dumper Version 14.16.27032.1
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file MathClient1322.exe

File Type: EXECUTABLE IMAGE

  Image has the following dependencies:

    MathLibrary.dll
    MSVCP140D.dll
    VCRUNTIME140D.dll
    ucrtbased.dll
    KERNEL32.dll

  Summary

        1000 .00cfg
        1000 .data
        2000 .idata
        1000 .msvcjmc
        3000 .rdata
        1000 .reloc
        1000 .rsrc
        8000 .text
       10000 .textbss
```

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)
