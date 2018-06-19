---
title: -SYMBOLS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /symbols
dev_langs:
- C++
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a0cc59ee730fcfad47d758dec73cb8646210934
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375781"
---
# <a name="symbols"></a>/SYMBOLS
```  
/SYMBOLS  
```  
  
 Cette option affiche la table de symboles COFF. Tables de symboles existent dans tous les fichiers objets. Une table de symboles COFF apparaît dans un fichier image uniquement si elle est liée avec/Debug.  
  
 Voici une description de la sortie /SYMBOLS. Vous trouverez plus d’informations sur la signification de la sortie /SYMBOLS en consultant winnt.h (IMAGE_SYMBOL et IMAGE_AUX_SYMBOL) ou la documentation COFF.  
  
 Étant donné le vidage de l’exemple suivant :  
  
```  
Dump of file main.obj  
File Type: COFF OBJECT  
  
COFF    SYMBOL    TABLE  
000    00000000   DEBUG      notype      Filename      | .file  
      main.cpp  
002   000B1FDB   ABS      notype      Static      | @comp.id  
003   00000000   SECT1      notype      Static      | .drectve  
      Section length       26, #relocs   0, #linenums    0, checksum 722C964F  
005   00000000   SECT2      notype      Static      | .text  
      Section length      23, #relocs      1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)  
007   00000000   SECT2      notype ()   External      | _main  
008   00000000   UNDEF      notype ()   External      | ?MyDump@@YAXXZ (void __cdecl MyDump(void))  
  
String Table Size = 0x10 bytes  
  
Summary  
  
      26 .drectve  
      23 .text  
```  
  
## <a name="remarks"></a>Notes  
 La description suivante, les lignes qui commencent par un numéro de symbole, décrit les colonnes contenant des informations pertinentes pour les utilisateurs :  
  
-   Le premier numéro de trois chiffres est le numéro d’index symbole /.  
  
-   Si la troisième colonne contient SECT*x*, le symbole est défini dans cette section du fichier objet. Mais si UNDEF apparaît, il n’est pas défini dans cet objet et doit être résolu ailleurs.  
  
-   La cinquième colonne (Static, External) indique si le symbole est visible uniquement dans cet objet, ou s’il est public (visible en externe). Un symbole statique _sym, pas lié à un symbole Public _sym ; Il s’agit de deux instances différentes de fonctions nommées _sym.  
  
 La dernière colonne dans une ligne numérotée est le nom du symbole, à la fois décoré et non décoré.  
  
 Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés par le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur.  
  
## <a name="see-also"></a>Voir aussi  
 [DUMPBIN, options](../../build/reference/dumpbin-options.md)