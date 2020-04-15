---
title: Vue d'ensemble des modules dans C++
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Les modules dans le C 20 offrent une alternative moderne aux fichiers d’en-tête.
ms.openlocfilehash: cd45be1dee888c8caeb65b7ff002ac8fee1ecbe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370758"
---
# <a name="overview-of-modules-in-c"></a>Vue d'ensemble des modules dans C++

Le C 20 introduit des *modules,* une solution moderne pour la composante des bibliothèques et des programmes de C. Un module est un ensemble de fichiers de code source qui sont compilés indépendamment des unités de [traduction](https://wikipedia.org/wiki/Translation_unit_(programming)) qui les importent. Les modules éliminent ou réduisent considérablement bon nombre des problèmes associés à l’utilisation de fichiers d’en-tête, et réduisent potentiellement les temps de compilation. Les macros, les directives de préprocesseur et les noms non exportés déclarés dans un module ne sont pas visibles et n’ont donc aucun effet sur la compilation de l’unité de traduction qui importe le module. Vous pouvez importer des modules dans n’importe quel ordre sans se soucier des redéfinitions macro. Les déclarations de l’unité de traduction importatrice ne participent pas à la résolution de surcharge ou à la recherche de nom dans le module importé. Une fois qu’un module est compilé une fois, les résultats sont stockés dans un fichier binaire qui décrit tous les types, fonctions et modèles exportés. Ce fichier peut être traité beaucoup plus rapidement qu’un fichier d’en-tête, et peut être réutilisé par le compilateur chaque endroit où le module est importé dans un projet.

Les modules peuvent être utilisés côte à côte avec des fichiers d’en-tête. Un fichier source CMD peut importer des modules et #include également des fichiers d’en-tête. Dans certains cas, un fichier d’en-tête peut être importé sous forme de module plutôt que textuellement #included par le préprocesseur. Nous recommandons que les nouveaux projets utilisent des modules plutôt que des fichiers d’en-tête autant que possible. Pour les grands projets existants en cours de développement actif, nous vous suggérons d’expérimenter la conversion des en-têtes hérités en modules pour voir si vous obtenez une réduction significative des temps de compilation.

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Activez les modules dans le compilateur Microsoft CMD

En date de la version 16.2 de Visual Studio 2019, les modules ne sont pas entièrement implémenté dans le compilateur Microsoft C. Vous pouvez utiliser la fonction modules pour créer des modules à partition unique et pour importer les modules Standard Library fournis par Microsoft. Pour permettre le support des modules, compilez avec [/expérimental:module](../build/reference/experimental-module.md) et [/std:c 'latest](../build/reference/std-specify-language-standard-version.md). Dans un projet Visual Studio, cliquez à droite sur le nœud du projet dans **Solution Explorer** et choisissez **Properties**. Réglez la **configuration** drop-down à **toutes les configurations,** puis choisissez **Configuration Properties** > **C/CMD** > **Language** > **Enable MODULEs CMD (expérimental)**.

Un module et le code qui le consomme doivent être compilés avec les mêmes options de compilateur.

## <a name="consume-the-c-standard-library-as-modules"></a>Consommer la bibliothèque standard de CMD en modules

Bien qu’il ne soit pas précisé par la norme C-20, Microsoft permet d’importer sa mise en œuvre de la bibliothèque standard CMD sous forme de modules. En important la Bibliothèque standard de Cmd comme modules plutôt que de la #including à travers des fichiers d’en-tête, vous pouvez potentiellement accélérer les temps de compilation en fonction de la taille de votre projet. La bibliothèque est intégrée aux modules suivants :

- std.regex fournit le \<contenu de l’en-tête regex>
- std.filesystem fournit le \<contenu du système de fichiers d’en-tête>
- std.memory fournit le \<contenu de la mémoire d’en-tête>
- std.threading fournit le contenu \<des en-têtes \<> atomiques, condition_variable \<>,> \<futur,> mutex, \<shared_mutex>, et \<>
- std.core fournit tout le reste de la bibliothèque standard de C

Pour consommer ces modules, il suffit d’ajouter une déclaration d’importation en haut du fichier de code source. Par exemple :

```cpp
import std.core;
import std.regex;
```

Pour consommer le module Microsoft Standard Library, compilez votre programme avec [/EHsc](../build/reference/eh-exception-handling-model.md) et [/MD](../build/reference/md-mt-ld-use-run-time-library.md) options.

## <a name="basic-example"></a>Exemple de base

L’exemple suivant montre une définition de module simple dans un fichier source appelé **Foo.ixx**. **L’extension .ixx** est nécessaire pour les fichiers d’interface de module dans Visual Studio. Dans cet exemple, le fichier d’interface contient la définition de fonction ainsi que la déclaration. Toutefois, les définitions peuvent également être placées dans un ou plusieurs fichiers distincts (comme indiqué dans un exemple ultérieur). Le **module d’exportation Foo** indique que ce fichier `Foo`est l’interface principale pour un module appelé . Le modificateur **d’exportation** indique `f()` que `Foo` cette fonction sera visible lorsqu’elle sera importée par un autre programme ou module. Notez que le module `Bar`fait référence à un namespace .

```cpp
export module Foo;

#define ANSWER 42

namespace Bar
{
   int f_internal() {
        return ANSWER;
      }

   export int f() {
      return f_internal();
   }
}
```

Le fichier **MyProgram.cpp** utilise la déclaration **d’importation** pour accéder au nom qui est exporté par `Foo`. Notez que `Bar` le nom est visible ici, mais pas tous ses membres. Notez également `ANSWER` que la macro n’est pas visible.

```cpp

import Foo;
import std.core;

using namespace std;

int main()
{
   cout << "The result of f() is " << Bar::f() << endl; // 42
   // int i = Bar::f_internal(); // C2039
   // int j = ANSWER; //C2065
}

```

La déclaration d’importation ne peut apparaître qu’à portée globale.

## <a name="implementing-modules"></a>Mise en œuvre de modules

Vous pouvez créer un module avec un fichier d’interface unique (.ixx) qui exporte des noms et inclut des implémentations de toutes les fonctions et types. Vous pouvez également mettre les implémentations dans un ou plusieurs fichiers de mise en œuvre distincts, similaires à la façon dont les fichiers .h et .cpp sont utilisés. Le mot clé **d’exportation** est utilisé uniquement dans le fichier d’interface. Un fichier de mise en œuvre peut **importer** un autre module, mais ne peut **pas exporter** de noms. Les fichiers de mise en œuvre peuvent être nommés avec n’importe quelle extension. Un fichier d’interface et l’ensemble de fichiers de implémentation qui le soutiennent sont traités comme un type spécial d’unité de traduction appelée *unité de module*. Un nom qui est déclaré dans n’importe quel fichier de mise en œuvre est automatiquement visible dans tous les autres fichiers dans la même unité de module.

Pour les modules plus grands, vous pouvez diviser le module en plusieurs unités de module *appelées partitions*. Chaque partition se compose d’un fichier d’interface soutenu par un ou plusieurs fichiers de implémentation. (En date de Visual Studio 2019 version 16.2, les partitions ne sont pas encore entièrement mises en œuvre.)

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Modules, espaces nominaux et lookup dépendant de l’argument

Les règles pour les espaces de nom dans les modules sont les mêmes que dans n’importe quel autre code. Si une déclaration dans un espace nom est exportée, l’espace nominant (à l’exclusion des membres non exportés) est également implicitement exporté. Si un espace nom est explicitement exporté, toutes les déclarations dans cette définition d’espace nom sont exportées.

Lorsqu’il effectue une recherche dépendante des arguments pour les résolutions de surcharge dans l’unité de traduction d’importation, le compilateur tient compte des fonctions qui sont déclarées dans la même unité de traduction (y compris les interfaces de module) que lorsque le type d’arguments de la fonction est défini.

### <a name="module-partitions"></a>Partitions de modules

> [!NOTE]
> Cette section est prévue pour l’exhaustivité. Les partitions ne sont pas encore implémentées dans le compilateur Microsoft C.

Un module peut être intégré en *partitions,* chacun composé d’un fichier d’interface et de fichiers de implémentation nuls ou plus. Une partition de module est similaire à un module, sauf qu’il partage la propriété de toutes les déclarations dans l’ensemble du module. Tous les noms qui sont exportés par des fichiers d’interface de partition sont importés et réexportés par le fichier d’interface primaire. Le nom d’une partition doit commencer par le nom du module suivi d’un côlon. Les déclarations dans l’une des cloisons sont visibles dans l’ensemble du module. Aucune précaution particulière n’est nécessaire pour éviter les erreurs d’une règle de définition (ODR). Vous pouvez déclarer un nom (fonction, classe, etc.) dans une partition et le définir dans une autre. Un fichier de mise en œuvre de partition commence comme ceci :

```cpp
module Foo:part1
```

et le fichier d’interface de partition commence comme ceci :

```cpp
export module Foo:part1
```

Pour accéder aux déclarations dans une autre partition, une partition doit l’importer, mais elle ne peut utiliser que le nom de partition, et non le nom du module :

```cpp
module Foo:part2;
import :part1;
```

L’unité d’interface principale doit importer et réé exportation tous les fichiers de partition d’interface du module comme ceci :

```cpp
export import :part1
export import :part2
...
```

L’unité d’interface principale peut importer des fichiers de mise en œuvre de partition, mais ne peut pas les exporter parce que ces fichiers ne sont pas autorisés à exporter des noms. Cela permet à un module de garder les détails de implémentation internes au module.

## <a name="modules-and-header-files"></a>Modules et fichiers en-tête

Vous pouvez inclure des fichiers d’en-tête dans un fichier source de module en plaçant la `#include` directive avant la déclaration du module. Ces fichiers sont considérés comme étant dans le *fragment du module global*. Un module ne peut voir que les noms dans le *fragment de module global* qui sont en en-têtes qu’il inclut explicitement. Le fragment global du module ne contient que des symboles qui sont réellement utilisés.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

Vous pouvez utiliser un fichier d’en-tête traditionnel pour contrôler les modules importés :

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Fichiers d’en-tête importés

> [!NOTE]
> Cette section n’est informationnelle que. Les importations héritées ne sont pas encore mises en œuvre dans le compilateur Microsoft C.

Certains en-têtes sont suffisamment autonomes pour qu’ils soient amenés à l’aide du mot clé **d’importation.** La principale différence entre un en-tête importé et un module importé est que toutes les définitions de préprocesseur dans l’en-tête sont visibles dans le programme d’importation immédiatement après l’énoncé d’importation. (Les définitions de préprocesseur dans tous les fichiers inclus par cet en-tête ne sont *pas* visibles.)

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Voir aussi

[module, importation, exportation](import-export-module.md)
