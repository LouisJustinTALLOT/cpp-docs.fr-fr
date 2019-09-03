---
title: include_alias, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: aa3714186e8f95d4044ba5a3b2bc2d5fcfb1fc9c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218906"
---
# <a name="include_alias-pragma"></a>include_alias, pragma

Spécifie que lorsque *alias_filename* est trouvé dans `#include` une directive, le compilateur remplace *actual_filename* à la place.

## <a name="syntax"></a>Syntaxe

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** «*alias_filename*» **,** «*actual_filename*» **)** \
> **#pragma include_alias (** \< *alias_filename*>  **,** *actual_filename*) \<> 

## <a name="remarks"></a>Notes

La directive pragma **include_alias** vous permet de substituer des fichiers ayant des noms ou des chemins d’accès différents pour les noms de fichier inclus par les fichiers sources. Par exemple, certains systèmes de fichiers autorisent des noms de fichiers d’en-tête plus longs que la limite du système de fichiers FAT 8,3. Le compilateur ne peut pas simplement tronquer les noms plus longs à 8,3, car les huit premiers caractères des noms de fichiers d’en-tête plus longs peuvent ne pas être uniques. Chaque fois que le compilateur voit la chaîne alias_filename `#include` dans une directive, il remplace le nom *actual_filename* à la place. Ensuite, il charge le fichier d’en-tête *actual_filename* . Ce pragma doit figurer avant les directives `#include` correspondantes. Par exemple :

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

L’alias à rechercher doit correspondre exactement à la spécification. La casse, l’orthographe et l’utilisation de guillemets doubles ou d’équerres doivent toutes correspondre. Le pragma **include_alias** effectue une correspondance de chaîne simple sur les noms de fichiers. Aucune autre validation de nom de fichier n’est effectuée. Par exemple, avec les directives suivantes,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

aucune substitution d’alias n’est effectuée, car les chaînes du fichier d’en-tête ne correspondent pas exactement. En outre, les noms de fichiers d’en- `/Yu` tête `/Yc` utilisés comme arguments pour les `hdrstop` options du compilateur et, ou le pragma, ne sont pas substitués. Par exemple, si votre fichier source contient la directive suivante,

```cpp
#include <AppleSystemHeaderStop.h>
```

l'option correspondante du compilateur doit être

> **/YcAppleSystemHeaderStop.h**

Vous pouvez utiliser le pragma **include_alias** pour mapper un nom de fichier d’en-tête à un autre. Par exemple :

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Ne mélangez pas les noms de fichiers placés entre guillemets doubles avec les noms de fichiers placés entre crochets pointus. Par exemple, étant donné les deux `#pragma include_alias` directives ci-dessus, le compilateur n’effectue aucune substitution `#include` sur les directives suivantes:

```cpp
#include <api.h>
#include "stdio.h"
```

En outre, la directive suivante génère une erreur :

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Le nom de fichier indiqué dans les messages d’erreur, ou en tant que valeur `__FILE__` de la macro prédéfinie, est le nom du fichier une fois la substitution effectuée. Par exemple, consultez la sortie après les directives suivantes:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

Erreur dans *VERYLONGFILENAME. H* génère le message d’erreur suivant:

```Output
myfile.h(15) : error C2059 : syntax error
```

Notez également que la transitivité n’est pas prise en charge. Avec les directives suivantes,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

le compilateur recherche le fichier *Two. h* au lieu de *trois. h*.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
