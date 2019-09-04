---
title: hdrstop, pragma
ms.date: 08/29/2019
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: f540f0f01fe654213af15afa8fbf5cbd94e4b7e2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221017"
---
# <a name="hdrstop-pragma"></a>hdrstop, pragma

Vous donne un contrôle supplémentaire sur les noms de fichiers de précompilation et sur l’emplacement où l’état de compilation est enregistré.

## <a name="syntax"></a>Syntaxe

> **#pragma hdrstop** [("*nom_fichier*")]

## <a name="remarks"></a>Notes

*Filename* est le nom du fichier d’en-tête précompilé à utiliser ou à créer (selon que [/Yu](../build/reference/yu-use-precompiled-header-file.md) ou [/Yc](../build/reference/yc-create-precompiled-header-file.md) est spécifié). Si *filename* ne contient pas de spécification de chemin d’accès, il est supposé que le fichier d’en-tête précompilé est dans le même répertoire que le fichier source.

Si un fichier C C++ ou un fichier contient un pragma **hdrstop** quand `/Yc`il est compilé avec, le compilateur enregistre l’état de la compilation jusqu’à l’emplacement du pragma. L’État compilé de tout code qui suit le pragma n’est pas enregistré.

Utilisez *filename* pour nommer le fichier d’en-tête précompilé dans lequel l’État compilé est enregistré. Un espace entre **hdrstop** et *filename* est facultatif. Le nom de fichier spécifié dans le pragma **hdrstop** est une chaîne et est par conséquent soumis aux contraintes d’une chaîne C++ ou d’un C. En particulier, vous devez le placer entre guillemets et utiliser le caractère d'échappement (barre oblique inverse) pour spécifier des noms de répertoires. Par exemple :

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

Le nom du fichier d’en-tête précompilé est déterminé selon les règles suivantes par ordre de priorité :

1. Argument de l' `/Fp` option de compilateur

2. L’argument de *nom de fichier* pour`#pragma hdrstop`

3. Le nom de base du fichier source avec une extension .PCH

Pour les `/Yc` options `/Yu` et, si aucune des deux options de compilation ou le pragma **hdrstop** ne spécifie un nom de fichier, le nom de base du fichier source est utilisé comme nom de base du fichier d’en-tête précompilé.

Vous pouvez également utiliser les commandes de prétraitement pour remplacer une macro comme suit :

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

Les règles suivantes déterminent où le pragma **hdrstop** peut être placé:

- Il doit apparaître hors de toute déclaration ou définition de données ou de fonction.

- Il doit être spécifié dans le fichier source, pas dans un fichier d'en-tête.

## <a name="example"></a>Exemples

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

Dans cet exemple, le pragma **hdrstop** apparaît après l’inclusion de deux fichiers et la définition d’une fonction Inline. Cet emplacement peut, au début, sembler être un positionnement impair pour le pragma. Toutefois, Notez que l’utilisation des options `/Yc` de précompilation manuelles et `/Yu`, avec le pragma **hdrstop** , vous permet de précompiler des fichiers sources entiers, même du code inline. Le compilateur Microsoft ne se limite pas à précompiler uniquement les déclarations de données.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
