---
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
ms.openlocfilehash: d71f0e0ce02bca1e50d177ffbfd7ffe61e9e8998
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667597"
---
# <a name="symbols"></a>/SYMBOLS

```
/SYMBOLS
```

Cette option affiche la table de symboles COFF. Tables de symboles existent dans tous les fichiers de l’objet. Une table de symboles COFF apparaît dans un fichier image uniquement s’il est lié avec/Debug.

Voici une description de la sortie /SYMBOLS. Vous trouverez plus d’informations sur la signification de la sortie /SYMBOLS en consultant winnt.h (IMAGE_SYMBOL et IMAGE_AUX_SYMBOL) ou la documentation COFF.

Étant donné le vidage de l’exemple suivant :

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

La description suivante, pour les lignes qui commencent par un nombre de symboles, décrit les colonnes qui contiennent des informations pertinentes pour les utilisateurs :

- Le premier nombre à trois chiffres est l’index/nombre de symboles.

- Si la troisième colonne contient SECT*x*, le symbole est défini dans cette section du fichier objet. Mais si UNDEF apparaît, il n’est pas défini dans cet objet et doit être résolu en un autre emplacement.

- La cinquième colonne (Static, External) indique si le symbole est visible uniquement dans cet objet, ou s’il est public (visible en externe). Un symbole statique _sym, pas lié à un symbole Public _sym ; Il s’agit de deux instances différentes de fonctions nommées _sym.

La dernière colonne dans une ligne numérotée est le nom du symbole, à la fois décoré et non décoré.

Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés avec le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](../../build/reference/dumpbin-options.md)