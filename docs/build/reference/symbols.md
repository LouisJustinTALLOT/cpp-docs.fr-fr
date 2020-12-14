---
description: En savoir plus sur:/SYMBOLS
title: /SYMBOLS
ms.date: 09/05/2018
f1_keywords:
- /symbols
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
ms.openlocfilehash: f0cc213a8b37f99e0cb80f6df88967e4eb5204b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230144"
---
# <a name="symbols"></a>/SYMBOLS

```
/SYMBOLS
```

Cette option affiche la table de symboles COFF. Les tables de symboles existent dans tous les fichiers objets. Une table de symboles COFF apparaît dans un fichier image uniquement si elle est liée à/DEBUG.

Vous trouverez ci-dessous une description de la sortie de/SYMBOLS. Vous trouverez des informations supplémentaires sur la signification de la sortie/SYMBOLS en regardant dans la documentation de Winnt. h (IMAGE_SYMBOL et IMAGE_AUX_SYMBOL) ou au format COFF.

À partir de l’exemple de vidage suivant :

```
Dump of file main.obj
File Type: COFF OBJECT

COFF SYMBOL TABLE
000 00000000 DEBUG    notype       Filename     | .file
    main.cpp
002 000B1FDB ABS      notype       Static       | @comp.id
003 00000000 SECT1    notype       Static       | .drectve
    Section length     26, #relocs    0, #linenums    0, checksum 722C964F
005 00000000 SECT2    notype       Static       | .text
    Section length     23, #relocs    1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)
007 00000000 SECT2    notype ()    External     | _main
008 00000000 UNDEF    notype ()    External     | ?MyDump@@YAXXZ (void __cdecl MyDump(void))

String Table Size = 0x10 bytes

  Summary

         26 .drectve
         23 .text
```

## <a name="remarks"></a>Notes

La description suivante, pour les lignes qui commencent par un numéro de symbole, décrit les colonnes qui contiennent des informations pertinentes pour les utilisateurs :

- Le premier numéro à trois chiffres est l’index/numéro de symbole.

- Si la troisième colonne contient SECT *x*, le symbole est défini dans cette section du fichier objet. Toutefois, si UNDEF s’affiche, il n’est pas défini dans cet objet et doit être résolu ailleurs.

- La cinquième colonne (statique, externe) indique si le symbole est visible uniquement dans cet objet, ou s’il est public (visible en externe). Un symbole statique, _sym, ne serait pas lié à un symbole public _sym ; Il s’agit de deux instances différentes de fonctions nommées _sym.

La dernière colonne d’une ligne numérotée est le nom du symbole, à la fois décoré et non décoré.

Seule l’option [/HEADERS](headers.md) DUMPBIN peut être utilisée sur les fichiers générés avec l’option du compilateur [/GL](gl-whole-program-optimization.md).

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)
