---
title: Tableaux (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
- declaring arrays, about declaring arrays
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a17649402fa6ebe9c98d768badcf36e5700f5b75
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862720"
---
# <a name="arrays-c-component-extensions"></a>Tableaux (extensions du composant C++)
Le `Platform::Array<T>` type dans C + c++ / CX, ou le `array` mot clé dans C + c++ / CLI, déclare un tableau d’un type spécifié et la valeur initiale.  
  
## <a name="all-platforms"></a>Toutes les plateformes  
 Le tableau doit être déclaré à l’aide du modificateur handle-to-object (^) après le crochet fermant (>) dans la déclaration.  
 Le nombre d’éléments du tableau n’est pas partie du type. Une variable tableau peut faire référence à des groupes de tailles différentes.  
  
 Contrairement à C++ standard, la mise en indice n’est pas un synonyme pour une opération arithmétique de pointeur et n’est pas commutative.  
  
 Pour plus d’informations sur les tableaux, consultez :  
  
-   [Guide pratique pour utiliser des tableaux dans C++-CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
    
-   [Listes d’arguments de variable (...) (C++-CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Les tableaux sont des membres de la `Platform` espace de noms. Tableaux peuvent uniquement être unidimensionnels.  
  
### <a name="syntax"></a>Syntaxe  
  
 Le premier exemple de la syntaxe de la `ref new` mot clé d’agrégation pour allouer un tableau. Le deuxième exemple déclare un tableau local.  
  
```  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *qualificateurs* [facultatif]  
 Un ou plusieurs de ces spécificateurs de classe de stockage : [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [statique](../cpp/static-members-cpp.md).  
  
 `array-type`  
 Le type de la variable tableau. Les types valides sont les classes Windows Runtime et types fondamentaux, les classes ref et les structures, les classes de valeur structs et des pointeurs natifs (`type*`).  
  
 `rank` [facultatif]  
 Le nombre de dimensions du tableau. Doit être 1.  
  
 `identifier`  
 Le nom de la variable tableau.  
  
 `initialization-type`  
 Le type des valeurs qui initialiser le tableau. En règle générale, `array-type` et `initialization-type` sont du même type. Toutefois, les types peuvent être différents s’il existe une conversion à partir de `initialization-type` à `array-type`— par exemple, si `initialization-type` est dérivée de `array-type`.  
  
 `initialization-list` [facultatif]  
 Une liste délimitée par des virgules des valeurs dans des accolades qui initialise les éléments du tableau. Par exemple, si `rank-size-list` ont été `(3)`, qui déclare un tableau unidimensionnel de 3 éléments, `initialization list` peut être `{1,2,3}`.  
  
### <a name="remarks"></a>Notes  
  
 Vous pouvez détecter au moment de la compilation si un type est un tableau de décompte avec `__is_ref_array(type)`. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
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
  
 Le premier exemple de la syntaxe de la `gcnew` (mot clé) à allouer un tableau. Le deuxième exemple déclare un tableau local.  
  
```  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *qualificateurs* [facultatif]  
 Un ou plusieurs de ces spécificateurs de classe de stockage : [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [statique](../cpp/static-members-cpp.md).  
  
 `array-type`  
 Le type de la variable tableau. Les types valides sont les classes Windows Runtime et types fondamentaux, les classes ref et les structures, les classes de valeur et les structures, les pointeurs natifs (`type*`) et les types POD (plain anciennes données) natifs.  
  
 `rank` [facultatif]  
 Le nombre de dimensions du tableau. La valeur par défaut est 1 ; la valeur maximale est 32. Chaque dimension du tableau lui-même est un tableau.  
  
 `identifier`  
 Le nom de la variable tableau.  
  
 `initialization-type`  
 Le type des valeurs qui initialiser le tableau. En règle générale, `array-type` et `initialization-type` sont du même type. Toutefois, les types peuvent être différents s’il existe une conversion à partir de `initialization-type` à `array-type`— par exemple, si `initialization-type` est dérivée de `array-type`.  
  
 `rank-size-list`  
 Une liste délimitée par des virgules de la taille de chaque dimension du tableau. Vous pouvez également, si le `initialization-list` paramètre est spécifié, le compilateur peut déduire la taille de chaque dimension et `rank-size-list` peut être omis. 
  
 `initialization-list` [facultatif]  
 Une liste délimitée par des virgules des valeurs dans des accolades qui initialise les éléments du tableau. Ou une liste délimitée par des virgules d’imbriqués *-liste d’initialisation* éléments initialiser les éléments dans un tableau multidimensionnel.  
  
 Par exemple, si `rank-size-list` ont été `(3)`, qui déclare un tableau unidimensionnel de 3 éléments, `initialization list` peut être `{1,2,3}`. If `rank-size-list` ont été `(3,2,4)`, qui déclare un tableau à trois dimensions de 3 éléments dans la première dimension, 2 éléments dans la seconde et 4 des éléments dans la troisième, `initialization-list` peut être `{{1,2,3},{0,0},{-5,10,-21,99}}`.)  
  
### <a name="remarks"></a>Notes  
  
 `array` est dans le [plateforme, par défaut et espaces de noms cli](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) espace de noms.  
  
 Comme C++ standard, les index de tableau sont de base zéro et l’indicées de tableau à l’aide de crochets ([]). Contrairement à C++ standard, les index d’un tableau multidimensionnel sont spécifiés dans une liste d’index pour chaque dimension au lieu d’un ensemble d’opérateurs de crochets ([]) pour chaque dimension. Par exemple, *identificateur*[*index1*, *index2*] à la place de *identificateur*[*index1*] [ *index2*].  
  
 Héritent de tous les tableaux managés `System::Array`. Toute méthode ou propriété de `System::Array` peut être appliqué directement à la variable tableau.  
  
 Lorsque vous allouez un tableau dont le type d’élément est pointeur-à une classe managée, les éléments sont initialisés à 0.  
  
 Lorsque vous allouez un tableau dont le type d’élément est un type valeur `V`, le constructeur par défaut `V` est appliquée à chaque élément du tableau. Pour plus d’informations, consultez [équivalents .NET Framework des Types natifs C++ (C + c++ / CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).  
  
 Au moment de la compilation, vous pouvez détecter si un type est une common language runtime (CLR) `__is_ref_array(type)`. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 L’exemple suivant crée un tableau unidimensionnel qui comporte 100 éléments et un tableau à trois dimensions dont les 3 éléments dans la première dimension, 5 éléments dans la seconde et 6 éléments dans le troisième.  
  
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
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)