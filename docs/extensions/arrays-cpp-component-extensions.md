---
title: Tableaux (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: e4173c16e13c08a54b36e42183e6e18b6ed4fdc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516194"
---
# <a name="arrays-ccli-and-ccx"></a>Tableaux (C++/CLI et C++/CX)

Le type `Platform::Array<T>` dans C++/CX, ou le mot clé **array** dans C++/CLI, déclare un tableau d’un type et d’une valeur initiale spécifiés.

## <a name="all-platforms"></a>Toutes les plateformes

Le tableau doit être déclaré à l’aide du modificateur handle-to-object (^) après le crochet fermant (>) de la déclaration.
Le nombre d’éléments du tableau ne fait pas partie du type. Une variable array peut faire référence à des tableaux de tailles différentes.

Contrairement au C++ standard, l’indice n’est pas synonyme de pointeur arithmétique et n’est pas commutatif.

Pour plus d’informations sur les tableaux, consultez :

- [Guide pratique pour utiliser des tableaux dans C++/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [Listes d’arguments de variable (...) (C++-CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows Runtime

Les tableaux sont des membres de l’espace de noms `Platform`. Les tableaux peuvent uniquement être unidimensionnels.

### <a name="syntax"></a>Syntaxe

Le premier exemple de syntaxe utilise le mot clé d’agrégation **ref new** pour allouer un tableau. Le deuxième exemple déclare un tableau local.

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*qualifiers*<br/>
(Facultatif) Un ou plusieurs des spécificateurs de classe de stockage suivants : [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [static](../cpp/static-members-cpp.md).

*array-type*<br/>
Le type de la variable de tableau. Les types valides sont les classes Windows Runtime et les types fondamentaux, les classes et les structs de référence, les classes et les structs de valeur, ainsi que les pointeurs natifs (`type*`).

*rank*<br/>
(Facultatif) Nombre de dimensions du tableau. Doit être égal à 1.

*identifier*<br/>
Nom de la variable de tableau.

*initialization-type*<br/>
Le type des valeurs qui initialisent le tableau. En règle générale, *array-type* et *initialization-type* sont du même type. Toutefois, les types peuvent être différents s’il existe une conversion entre *initialization-type* et *array-type* ; par exemple, si *initialization-type* est dérivé de *array-type*.

*initialization-list*<br/>
(Facultatif) Une liste délimitée par des virgules de valeurs entre accolades qui initialisent les éléments du tableau. Par exemple, si *rank-size-list* est de `(3)`, ce qui déclare un tableau unidimensionnel de 3 éléments, *initialization-list* peut valoir `{1,2,3}`.

### <a name="remarks"></a>Remarques

Vous pouvez détecter au moment de la compilation si un type est un tableau de références comptées à l’aide de `__is_ref_array(type)`. Pour plus d’informations, consultez [Compiler Support for Type Traits](compiler-support-for-type-traits-cpp-component-extensions.md) (Prise en charge du compilateur pour les caractéristiques de type).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

### <a name="examples"></a>Exemples

L’exemple suivant crée un tableau unidimensionnel qui comporte 100 éléments.

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntaxe

Le premier exemple de syntaxe utilise le mot clé **gcnew** pour allouer un tableau. Le deuxième exemple déclare un tableau local.

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*qualifiers*<br/>
(Facultatif) Un ou plusieurs des spécificateurs de classe de stockage suivants : [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [static](../cpp/static-members-cpp.md).

*array-type*<br/>
Le type de la variable de tableau. Les types valides sont les classes Windows Runtime et les types fondamentaux, les classes et les structs de référence, les classes et les structs de valeur, les pointeurs natifs (`type*`), ainsi que les types POD (Plain old data).

*rank*<br/>
(Facultatif) Nombre de dimensions du tableau. La valeur par défaut est 1 ; la valeur maximale est 32. Chaque dimension du tableau est elle-même un tableau.

*identifier*<br/>
Nom de la variable de tableau.

*initialization-type*<br/>
Le type des valeurs qui initialisent le tableau. En règle générale, *array-type* et *initialization-type* sont du même type. Toutefois, les types peuvent être différents s’il existe une conversion entre *initialization-type* et *array-type* ; par exemple, si *initialization-type* est dérivé de *array-type*.

*rank-size-list*<br/>
Une liste délimitée par des virgules de la taille de chaque dimension du tableau. Sinon, si le paramètre *initialization-list* est spécifié, le compilateur peut déduire la taille de chaque dimension et *rank-size-list* peut être omis.

*initialization-list*<br/>
(Facultatif) Une liste délimitée par des virgules de valeurs entre accolades qui initialisent les éléments du tableau. Ou une liste délimitée par des virgules d’éléments *initialization-list* imbriqués qui initialisent les éléments dans un tableau multidimensionnel.

Par exemple, si *rank-size-list* est de `(3)`, ce qui déclare un tableau unidimensionnel de 3 éléments, *initialization-list* peut valoir `{1,2,3}`. Si *rank-size-list* a la valeur `(3,2,4)`, ce qui déclare un tableau tridimensionnel de 3 éléments dans la première dimension, 2 éléments dans la seconde et 4 éléments dans la troisième, *initialization-list* peut valoir `{{1,2,3},{0,0},{-5,10,-21,99}}`.)

### <a name="remarks"></a>Remarques

**array** appartient à l’espace de noms [Plateforme, valeurs par défaut et espaces de noms CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Comme pour le C++ standard, les indices d’un tableau sont de base zéro et un tableau est indicé en utilisant des crochets ([]). Contrairement au C++ standard, les indices d’un tableau multidimensionnel sont spécifiés dans une liste d’indices pour chaque dimension au lieu d’un ensemble d’opérateurs crochets ([]) pour chaque dimension. Par exemple, *identifier*[*index1*, *index2*] au lieu de *identifier*[*index1*][ *index2*].

Tous les tableaux managés héritent de `System::Array`. Toute méthode ou propriété de `System::Array` peut être appliquée directement à la variable array.

Lorsque vous allouez un tableau dont le type d’élément est un pointeur vers une classe managée, les éléments sont initialisés à 0.

Lorsque vous allouez un tableau dont le type élément est un type valeur `V`, le constructeur par défaut `V` est appliqué à chaque élément du tableau. Pour plus d’informations, consultez [Équivalents .NET Framework des types natifs C++ (C++-CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).

Au moment de la compilation, vous pouvez détecter si un type est un tableau common language runtime (CLR) grâce à `__is_ref_array(type)`. Pour plus d’informations, consultez [Compiler Support for Type Traits](compiler-support-for-type-traits-cpp-component-extensions.md) (Prise en charge du compilateur pour les caractéristiques de type).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant crée un tableau unidimensionnel qui comporte 100 éléments et un tableau tridimensionnel qui comporte 3 éléments dans la première dimension, 5 éléments dans la seconde et 6 éléments dans la troisième.

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)