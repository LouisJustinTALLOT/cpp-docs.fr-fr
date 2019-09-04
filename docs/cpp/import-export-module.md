---
title: module, importation, exportation
ms.date: 07/15/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Utilisez l’instruction import pour accéder aux types et aux fonctions définis dans le module spécifié.
ms.openlocfilehash: ee1d50a76a3304359c0771aa0174968439f5faa4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273623"
---
# <a name="module-import-export"></a>module, importation, exportation

Les mots clés **module**, **Import**et **Export** sont disponibles en c++ 20 et nécessitent le commutateur [/experimental : module](../build/reference/experimental-module.md) compiler avec [/std : C + + latest](../build/reference/std-specify-language-standard-version.md). Pour plus d’informations, consultez [vue d’ensemble C++des modules dans ](modules-cpp.md).

## <a name="module"></a>module

Utilisez l’instruction **module** au début d’un fichier d’implémentation de module pour spécifier que le contenu du fichier appartient au module nommé. 

```cpp
module ModuleA;
```

## <a name="export"></a>exporter

Utilisez l’instruction **Export module** pour le fichier d’interface principal du module, qui doit avoir l’extension **. IXX**:

```cpp
export module ModuleA;
```

Dans un fichier d’interface, utilisez le modificateur **Export** sur les noms destinés à faire partie de l’interface publique :

```cpp
// ModuleA.ixx

export module ModuleA;

namespace Bar
{
   export int f();
   export double d();
   double internal_f(); // not exported
}
```

Les noms non exportés ne sont pas visibles pour le code qui importe le module :

```cpp
//MyProgram.cpp

import module ModuleA;

void main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Le mot clé **Export** peut ne pas apparaître dans un fichier d’implémentation de module. Quand le modificateur **Export** est appliqué à un nom d’espace de noms, tous les noms de l’espace de noms sont exportés.

## <a name="import"></a>d'importation

Utilisez l’instruction **Import** pour rendre les noms d’un module visibles dans votre programme. L’instruction import doit apparaître après l’instruction module et après toutes les directives #include, mais avant toute déclaration dans le fichier.

```cpp
module ModuleA;

#include "custom-lib.h"
import std.core;
import std.regex;
import ModuleB;

// begin declarations here:
template <class T>
class Baz
{...};
```

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des modules dansC++](modules-cpp.md)
