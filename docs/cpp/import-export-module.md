---
title: module, importation, exportation
ms.date: 12/12/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Utilisez les déclarations d’importation et d’exportation pour accéder aux types et aux fonctions définies dans le module spécifié et les publier.
ms.openlocfilehash: 5be1618d7e64f6887cf78bd863d428d6710eaf7e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187190"
---
# <a name="module-import-export"></a>module, importation, exportation

Le **module**, l' **importation**et les **`export`** déclarations sont disponibles en c++ 20 et nécessitent le commutateur [/experimental : module](../build/reference/experimental-module.md) compiler avec [/std : C + + latest](../build/reference/std-specify-language-standard-version.md). Pour plus d’informations, consultez [vue d’ensemble des modules en C++](modules-cpp.md).

## <a name="module"></a>module

Placez une déclaration de **module** au début d’un fichier d’implémentation de module pour spécifier que le contenu du fichier appartient au module nommé.

```cpp
module ModuleA;
```

## <a name="export"></a>export

Utilisez une déclaration de **module d’exportation** pour le fichier d’interface principal du module, qui doit avoir l’extension **. IXX**:

```cpp
export module ModuleA;
```

Dans un fichier d’interface, utilisez le **`export`** modificateur sur les noms qui sont destinés à faire partie de l’interface publique :

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

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Le **`export`** mot clé ne peut pas apparaître dans un fichier d’implémentation de module. Lorsque **`export`** est appliqué à un nom d’espace de noms, tous les noms de l’espace de noms sont exportés.

## <a name="import"></a>importer

Utilisez une déclaration d' **importation** pour rendre les noms d’un module visibles dans votre programme. La déclaration d’importation doit apparaître après la déclaration de module et après toutes les directives de #include, mais avant toute déclaration dans le fichier.

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

## <a name="remarks"></a>Notes

L' **importation** et le **module** sont traités comme des mots clés uniquement lorsqu’ils apparaissent au début d’une ligne logique :

```cpp

// OK:
module ;
module module-name
import :
import <
import "
import module-name
export module ;
export module module-name
export import :
export import <
export import "
export import module-name

// Error:
int i; module ;
```

**Spécifique à Microsoft**

Dans Microsoft C++, les jetons **Import** et **module** sont toujours des identificateurs et jamais des mots clés lorsqu’ils sont utilisés comme arguments d’une macro.

### <a name="example"></a>Exemple

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des modules dans C++](modules-cpp.md)
