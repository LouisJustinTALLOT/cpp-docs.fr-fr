---
title: hdrstop
ms.date: 11/04/2016
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: 1590b5916a8d9c00b6e988bacc7cd857c29d6775
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384086"
---
# <a name="hdrstop"></a>hdrstop
Vous permet de mieux contrôler les noms des fichiers de précompilation et l'emplacement auquel l'état de compilation est enregistré.

## <a name="syntax"></a>Syntaxe

```
#pragma hdrstop [( "filename" )]
```

## <a name="remarks"></a>Notes

Le *filename* est le nom du fichier d’en-tête précompilé à utiliser ou créer (selon que [/Yu](../build/reference/yu-use-precompiled-header-file.md) ou [/Yc](../build/reference/yc-create-precompiled-header-file.md) est spécifié). Si *filename* ne contient pas une spécification de chemin d’accès, le fichier d’en-tête précompilé est censé pour être dans le même répertoire que le fichier source.

Si un fichier C ou C++ contient un **hdrstop** pragma lors de la compilation avec `/Yc`, le compilateur enregistre l’état de la compilation jusqu'à l’emplacement du pragma. L'état compilé de tout code qui suit le pragma n'est pas enregistré.

Utilisez *filename* pour nommer le fichier d’en-tête précompilé dans lequel l’état compilé est enregistré. Un espace entre **hdrstop** et *filename* est facultatif. Le nom de fichier spécifié dans le **hdrstop** pragma est une chaîne et est donc soumis aux contraintes de n’importe quelle chaîne C ou C++. En particulier, vous devez le placer entre guillemets et utiliser le caractère d'échappement (barre oblique inverse) pour spécifier des noms de répertoires. Exemple :

```
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

Le nom du fichier d’en-tête précompilé est déterminé selon les règles suivantes par ordre de priorité :

1. L’argument à la `/Fp` option du compilateur

2. Le *filename* argument `#pragma hdrstop`

3. Le nom de base du fichier source avec une extension .PCH

Pour le `/Yc` et `/Yu` options, si aucune des options de compilation, ni le **hdrstop** pragma spécifie un nom de fichier, le nom de base du fichier source est utilisé comme nom de base du fichier d’en-tête précompilé.

Vous pouvez également utiliser les commandes de prétraitement pour remplacer une macro comme suit :

```
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

Les règles suivantes régissent l’emplacement où le **hdrstop** pragma peut être placé :

- Il doit apparaître hors de toute déclaration ou définition de données ou de fonction.

- Il doit être spécifié dans le fichier source, pas dans un fichier d'en-tête.

## <a name="example"></a>Exemple

```
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    ...                              // Some code to display string
}
#pragma hdrstop
```

Dans cet exemple, le **hdrstop** pragma apparaît une fois que deux fichiers ont été ajoutés et une fonction inline a été définie. Au départ, cela peut sembler être un positionnement étrange pour le pragma. Tenez compte des points, toutefois, à l’aide des options de précompilation manuelles, `/Yc` et `/Yu`, avec le **hdrstop** pragma permet à vous permet de précompiler des fichiers source entiers — même du code incorporé. Le compilateur Microsoft ne se limite pas à précompiler uniquement les déclarations de données.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)