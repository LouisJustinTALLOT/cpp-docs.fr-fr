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
description: Utiliser les déclarations d’importation et d’exportation pour accéder et publier les types et fonctions définis dans le module spécifié.
ms.openlocfilehash: a765e9a406660d3c945ef3d70754178b0648458c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374115"
---
# <a name="module-import-export"></a>module, importation, exportation

Le **module**, **l’importation**et les déclarations **d’exportation** sont disponibles dans le C 20 et nécessitent le commutateur de compilateur [/expérimental:module](../build/reference/experimental-module.md) avec [/std:c 'latest](../build/reference/std-specify-language-standard-version.md). Pour plus d’informations, voir [Aperçu des modules dans C .](modules-cpp.md)

## <a name="module"></a>module

Placez une déclaration **de module** au début d’un fichier d’implémentation du module pour spécifier que le contenu du fichier appartient au module désigné.

```cpp
module ModuleA;
```

## <a name="export"></a>export

Utilisez une déclaration **de module d’exportation** pour le fichier d’interface principal du module, qui doit avoir extension **.ixx**:

```cpp
export module ModuleA;
```

Dans un fichier d’interface, utilisez le modificateur **d’exportation** sur les noms qui sont destinés à faire partie de l’interface publique :

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

Les noms non exportés ne sont pas visibles au code qui importe le module :

```cpp
//MyProgram.cpp

import module ModuleA;

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Le mot clé **d’exportation** peut ne pas apparaître dans un fichier d’implémentation du module. Lorsque **l’exportation** est appliquée à un nom namespace, tous les noms dans l’espace nom sont exportés.

## <a name="import"></a>importer

Utilisez une déclaration **d’importation** pour rendre les noms d’un module visibles dans votre programme. La déclaration d’importation doit apparaître après la déclaration du module et après toute directive #include, mais avant toute déclaration dans le fichier.

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

**L’importation** et le **module** ne sont traités comme des mots clés que lorsqu’ils apparaissent au début d’une ligne logique :

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

**Microsoft Spécifique**

Dans Microsoft C, **l’importation** et le **module** de jetons sont toujours des identifiants et jamais des mots clés lorsqu’ils sont utilisés comme arguments à une macro.

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
