---
title: include_alias | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9844c610a1b5bffab8f5fba67daff90a52412e4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065172"
---
# <a name="includealias"></a>include_alias

Spécifie que *short_filename* doit être utilisé en tant qu’alias pour *long_filename*.

## <a name="syntax"></a>Syntaxe

> #<a name="pragma-includealiaslongfilename-shortfilename"></a>pragma include_alias («*long_filename*«, »*short_filename*»)
> #<a name="pragma-includealiaslongfilename-shortfilename"></a>pragma include_alias (*long_filename*, *short_filename*)

## <a name="remarks"></a>Notes

Certains systèmes de fichiers autorisent l'utilisation de noms de fichiers d'en-tête plus longs que la limite 8.3 du système de fichiers FAT. Le compilateur ne peut pas simplement tronquer les noms plus longs à 8.3, car les huit premiers caractères des noms de fichiers d'en-tête plus longs peuvent ne pas être uniques. Chaque fois que le compilateur rencontre la *long_filename* chaîne, il remplace *short_filename*et recherche le fichier d’en-tête *short_filename* à la place. Ce pragma doit figurer avant les directives `#include` correspondantes. Exemple :

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

L'alias recherché doit correspondre exactement à la spécification, aussi bien pour ce qui est de la casse, de l'orthographe, que de l'utilisation des guillemets doubles et des crochets pointus. Le **include_alias** pragma effectue une correspondance sur les noms de fichiers de chaîne simple ; aucune autre validation de nom de fichier est effectuée. Par exemple, avec les directives suivantes,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

aucune attribution d'alias (substitution) n'est effectuée, puisque les chaînes de fichier d'en-tête ne correspondent pas exactement. En outre, les noms de fichiers en-tête utilisés comme arguments pour le `/Yu` et `/Yc` options du compilateur, ou le `hdrstop` pragma, ne sont pas remplacées. Par exemple, si votre fichier source contient la directive suivante,

```cpp
#include <AppleSystemHeaderStop.h>
```

l'option correspondante du compilateur doit être

> /YcAppleSystemHeaderStop.h

Vous pouvez utiliser la **include_alias** pragma pour mapper un nom de fichier d’en-tête à un autre. Exemple :

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Ne combinez pas les noms de fichiers placés entre guillemets doubles avec des noms de fichiers placés entre crochets pointus. Par exemple, étant donné les deux ci-dessus `#pragma include_alias` directives, le compilateur n’exécute aucune substitution sur ce qui suit `#include` directives :

```cpp
#include <api.h>
#include "stdio.h"
```

En outre, la directive suivante génère une erreur :

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Notez que le nom de fichier signalé dans les messages d’erreur ou comme valeur de prédéfinis `__FILE__` macro, est le nom du fichier après la substitution a été effectuée. Par exemple, voir la sortie après les directives suivantes :

```cpp
#pragma include_alias( "VeryLongFileName.H", "myfile.h" )
#include "VeryLongFileName.H"
```

Une erreur dans VERYLONGFILENAME. H génère le message d’erreur suivant :

```Output
myfile.h(15) : error C2059 : syntax error
```

Notez également que la transitivité n'est pas prise en charge. Avec les directives suivantes,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

le compilateur recherche le fichier TWO.H à la place de THREE.H.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)