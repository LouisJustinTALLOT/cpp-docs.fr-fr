---
title: Vue d'ensemble des modules dans C++
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Les modules en C++ 20 fournissent une alternative moderne aux fichiers d’en-tête.
ms.openlocfilehash: fe5beee92ed257cca8143fa95f8f59bc9308fd5d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233676"
---
# <a name="overview-of-modules-in-c"></a>Vue d'ensemble des modules dans C++

C++ 20 introduit les *modules*, une solution moderne pour la composante des bibliothèques et des programmes C++. Un module est un ensemble de fichiers de code source qui sont compilés indépendamment des [unités de traduction](https://wikipedia.org/wiki/Translation_unit_(programming)) qui les importent. Les modules éliminent ou réduisent beaucoup les problèmes associés à l’utilisation des fichiers d’en-tête, et peuvent également réduire les délais de compilation. Les macros, les directives de préprocesseur et les noms non exportés déclarés dans un module ne sont pas visibles et, par conséquent, n’ont aucun effet sur la compilation de l’unité de traduction qui importe le module. Vous pouvez importer des modules dans n’importe quel ordre, sans vous soucier des redéfinitions de macros. Les déclarations de l’unité de traduction d’importation ne participent pas à la résolution de surcharge ou à la recherche de nom dans le module importé. Une fois qu’un module est compilé une seule fois, les résultats sont stockés dans un fichier binaire qui décrit tous les types, fonctions et modèles exportés. Ce fichier peut être traité beaucoup plus rapidement qu’un fichier d’en-tête et peut être réutilisé par le compilateur chaque fois que le module est importé dans un projet.

Les modules peuvent être utilisés côte à côte avec des fichiers d’en-tête. Un fichier source C++ peut importer des modules et également #include fichiers d’en-tête. Dans certains cas, un fichier d’en-tête peut être importé en tant que module plutôt que textuellement #included par le préprocesseur. Nous recommandons aux nouveaux projets d’utiliser autant que possible des modules plutôt que des fichiers d’en-tête. Pour les projets existants plus volumineux dans le cadre d’un développement actif, nous vous suggérons d’expérimenter la conversion d’en-têtes hérités en modules pour voir si vous obtenez une réduction significative des temps de compilation.

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Activer les modules dans le compilateur Microsoft C++

Depuis Visual Studio 2019 version 16,2, les modules ne sont pas entièrement implémentés dans le compilateur Microsoft C++. Vous pouvez utiliser la fonctionnalité Modules pour créer des modules à partition unique et importer les modules de bibliothèque standard fournis par Microsoft. Pour activer la prise en charge des modules, compilez avec [/experimental : module](../build/reference/experimental-module.md) et [/std : c + + latest](../build/reference/std-specify-language-standard-version.md). Dans un projet Visual Studio, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** , puis choisissez **Propriétés**. Définissez la liste déroulante de **configuration** sur **toutes les configurations**, puis choisissez **Propriétés de configuration**  >  **C/c++**  >  **langage**  >  **activer les modules c++ (expérimental)**.

Un module et le code qui le consomme doivent être compilés avec les mêmes options de compilateur.

## <a name="consume-the-c-standard-library-as-modules"></a>Utiliser la bibliothèque standard C++ comme modules

Bien que cela ne soit pas spécifié par la norme C++ 20, Microsoft Active son implémentation de la bibliothèque C++ standard en tant que modules. En important la bibliothèque C++ standard sous forme de modules plutôt que de la #including à l’aide de fichiers d’en-tête, vous pouvez potentiellement accélérer la compilation en fonction de la taille de votre projet. La bibliothèque est composant dans les modules suivants :

- STD. Regex fournit le contenu de l’en-tête\<regex>
- STD. FileSystem fournit le contenu de l’en-tête\<filesystem>
- STD. Memory fournit le contenu de l’en-tête\<memory>
- STD. Threading fournit le contenu des en-têtes,,,, \<atomic> \<condition_variable> \<future> \<mutex> \<shared_mutex> et\<thread>
- STD. Core fournit tout le reste dans la bibliothèque standard C++

Pour utiliser ces modules, ajoutez simplement une déclaration d’importation au début du fichier de code source. Par exemple :

```cpp
import std.core;
import std.regex;
```

Pour utiliser le module Microsoft standard Library, compilez votre programme avec les options [/EHsc](../build/reference/eh-exception-handling-model.md) et [/MD](../build/reference/md-mt-ld-use-run-time-library.md) .

## <a name="basic-example"></a>Exemple de base

L’exemple suivant montre une définition de module simple dans un fichier source appelé **foo. IXX**. L’extension **. IXX** est requise pour les fichiers d’interface de module dans Visual Studio. Dans cet exemple, le fichier d’interface contient la définition de fonction ainsi que la déclaration. Toutefois, les définitions peuvent également être placées dans un ou plusieurs fichiers distincts (comme indiqué dans un exemple ultérieur). L’instruction **foo du module d’exportation** indique que ce fichier est l’interface principale d’un module appelé `Foo` . Le **`export`** modificateur on `f()` indique que cette fonction sera visible quand `Foo` est importé par un autre programme ou module. Notez que le module référence un espace de noms `Bar` .

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

Le fichier **MyProgram. cpp** utilise la déclaration d' **importation** pour accéder au nom exporté par `Foo` . Notez que le nom `Bar` est visible ici, mais pas à tous ses membres. Notez également que la macro `ANSWER` n’est pas visible.

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

La déclaration d’importation peut apparaître uniquement au niveau de la portée globale.

## <a name="implementing-modules"></a>Implémentation de modules

Vous pouvez créer un module avec un fichier d’interface unique (. IXX) qui exporte des noms et comprend des implémentations de toutes les fonctions et de tous les types. Vous pouvez également placer les implémentations dans un ou plusieurs fichiers d’implémentation distincts, de la même façon que les fichiers. h et. cpp sont utilisés. Le **`export`** mot clé est utilisé uniquement dans le fichier d’interface. Un fichier d’implémentation peut **Importer** un autre module, mais ne peut pas avoir **`export`** de noms. Les fichiers d’implémentation peuvent être nommés avec n’importe quelle extension. Un fichier d’interface et l’ensemble de fichiers d’implémentation qui le replacent sont traités comme un type spécial d’unité de traduction appelé *unité de module*. Un nom qui est déclaré dans un fichier d’implémentation est automatiquement visible dans tous les autres fichiers de la même unité de module.

Pour les modules plus volumineux, vous pouvez fractionner le module en plusieurs unités de module appelées *partitions*. Chaque partition se compose d’un fichier d’interface sauvegardé par un ou plusieurs fichiers d’implémentation. (À compter de Visual Studio 2019 version 16,2, les partitions ne sont pas encore entièrement implémentées.)

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Modules, espaces de noms et recherche dépendante d’un argument

Les règles pour les espaces de noms dans les modules sont les mêmes que dans tout autre code. Si une déclaration dans un espace de noms est exportée, l’espace de noms englobant (à l’exception des membres non exportés) est également exporté implicitement. Si un espace de noms est exporté explicitement, toutes les déclarations au sein de cette définition d’espace de noms sont exportées.

Lorsque vous effectuez une recherche dépendante d’un argument pour des résolutions de surcharge dans l’unité de traduction d’importation, le compilateur considère les fonctions déclarées dans la même unité de traduction (y compris les interfaces de module) que l’emplacement où le type des arguments de la fonction est défini.

### <a name="module-partitions"></a>Partitions de module

> [!NOTE]
> Cette section est fournie à des fins d’exhaustivité. Les partitions ne sont pas encore implémentées dans le compilateur Microsoft C++.

Un module peut être mis en composant dans des *partitions*, chacune contenant un fichier d’interface et zéro, un ou plusieurs fichiers d’implémentation. Une partition de module est similaire à un module, à ceci près qu’elle partage la propriété de toutes les déclarations dans le module entier. Tous les noms exportés par les fichiers d’interface de partition sont importés et réexportés par le fichier d’interface principal. Le nom d’une partition doit commencer par le nom du module suivi d’un signe deux-points. Les déclarations dans l’une des partitions sont visibles dans l’ensemble du module. Aucune précaution spéciale n’est nécessaire pour éviter les erreurs de règle de ODR. Vous pouvez déclarer un nom (fonction, classe, etc.) dans une partition et le définir dans une autre. Un fichier d’implémentation de partition commence comme suit :

```cpp
module Foo:part1
```

et le fichier d’interface de partition commence comme suit :

```cpp
export module Foo:part1
```

Pour accéder aux déclarations d’une autre partition, une partition doit l’importer, mais elle ne peut utiliser que le nom de la partition, pas le nom du module :

```cpp
module Foo:part2;
import :part1;
```

L’unité d’interface principale doit importer et réexporter tous les fichiers de partition d’interface du module comme suit :

```cpp
export import :part1
export import :part2
...
```

L’unité d’interface principale peut importer des fichiers d’implémentation de partition, mais ne peut pas les exporter, car ces fichiers ne sont pas autorisés à exporter des noms. Cela permet à un module de conserver des détails d’implémentation internes au module.

## <a name="modules-and-header-files"></a>Modules et fichiers d’en-tête

Vous pouvez inclure des fichiers d’en-tête dans un fichier source de module en plaçant la `#include` directive avant la déclaration de module. Ces fichiers sont considérés comme étant dans le *fragment de module global*. Un module ne peut voir que les noms dans le *fragment de module global* qui se trouvent dans les en-têtes qu’il comprend explicitement. Le fragment de module global contient uniquement les symboles qui sont réellement utilisés.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

Vous pouvez utiliser un fichier d’en-tête traditionnel pour contrôler les modules qui sont importés :

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Fichiers d’en-tête importés

> [!NOTE]
> Cette section est fournie à titre d’information uniquement. Les importations héritées ne sont pas encore implémentées dans le compilateur Microsoft C++.

Certains en-têtes sont suffisamment autonomes pour pouvoir être mis en relation avec le mot clé **Import** . La principale différence entre un en-tête importé et un module importé est que toutes les définitions de préprocesseur dans l’en-tête sont visibles dans le programme d’importation immédiatement après l’instruction import. (Les définitions de préprocesseur de tous les fichiers inclus dans cet en-tête ne sont *pas* visibles.)

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Voir aussi

[module, importation, exportation](import-export-module.md)
