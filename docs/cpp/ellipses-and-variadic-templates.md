---
title: Ellipses et modèles Variadiques | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2eddd87660d996e0d726c4453e0eb732a5553b99
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416656"
---
# <a name="ellipses-and-variadic-templates"></a>Ellipses et modèles variadiques
Cet article explique comment utiliser les points de suspension (`...`) avec des modèles de variadiques C++. Les points de suspension a de nombreuses utilisations en C et C++. Notamment les listes d’arguments variables pour les fonctions. Le `printf()` fonction à partir de la bibliothèque Runtime C est un des exemples plus connus.  
  
 A *modèle variadique* est un modèle de classe ou une fonction qui prend en charge un nombre arbitraire d’arguments. Ce mécanisme est particulièrement utile pour les développeurs de bibliothèques C++, car vous pouvez appliquer aux modèles de classe et les modèles de fonction et ainsi fournir un large éventail de fonctionnalités de type sécurisé et non triviale et de flexibilité.  
  
## <a name="syntax"></a>Syntaxe  
 Points de suspension est utilisé de deux façons par les modèles de variadiques. À gauche du nom du paramètre, il désigne un *pack de paramètre*, et à droite du nom du paramètre, il développe les packs de paramètres dans des noms distincts.  
  
 Voici un exemple de base *classe de modèle variadique* syntaxe de définition :  
  
```cpp  
template<typename... Arguments> class classname;  
```  
  
 Pour les packs de paramètres et les extensions, vous pouvez ajouter des espaces blancs autour des points de suspension, selon votre préférence, comme indiqué dans les exemples suivants :  
  
```cpp  
template<typename ...Arguments> class classname;  
```  
  
 Ou à cela :  
  
```cpp  
template<typename ... Arguments> class classname;  
```  
  
 Notez que cet article utilise la convention est indiquée dans le premier exemple (les points de suspension est attaché à `typename`).  
  
 Dans les exemples précédents, `Arguments` est un package de paramètres. La classe `classname` peut accepter un nombre variable d’arguments, comme dans les exemples suivants :  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
vtclass<long, std::vector<int>, std::string> vtinstance4;  
  
```  
  
 En utilisant une définition de classe de modèle variadique, vous pouvez également exiger au moins un paramètre :  
  
```cpp  
template <typename First, typename... Rest> class classname;  
  
```  
  
 Voici un exemple de base *fonction de modèle variadique* syntaxe :  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments... args);  
```  
  
 Le `Arguments` pack de paramètre est ensuite développée pour l’utilisation, comme indiqué dans la section suivante, **présentation des modèles variadiques**.  
  
 Autres formes de syntaxe de fonction de modèle variadique sont possibles, y compris, mais sans limitation, les exemples suivants :  
  
```cpp  
template <typename... Arguments> returntype functionname(Arguments&... args);   
template <typename... Arguments> returntype functionname(Arguments&&... args);  
template <typename... Arguments> returntype functionname(Arguments*... args);  
```  
  
 Comme les spécificateurs `const` sont également autorisées :  
  
```cpp  
template <typename... Arguments> returntype functionname(const Arguments&... args);  
  
```  
  
 Comme avec les définitions de classe de modèle variadique, vous pouvez apporter des fonctions qui requièrent au moins un paramètre :  
  
```cpp  
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);  
  
```  
  
 Utilisent des modèles Variadiques le `sizeof...()` (opérateur) (non liés à l’ancien `sizeof()` opérateur) :  
  
```cpp  
template<typename... Arguments>  
void tfunc(const Arguments&... args)  
{  
    constexpr auto numargs{ sizeof...(Arguments) };  
  
    X xobj[numargs]; // array of some previously defined type X  
  
    helper_func(xobj, args...);  
}  
  
```  
  
## <a name="more-about-ellipsis-placement"></a>Plus d’informations sur le placement des points de suspension  
 Auparavant, cet article décrit le placement de points de suspension qui définit des packs de paramètres et des extensions en tant que « à gauche du nom du paramètre, il désigne un package de paramètres, et à droite du nom du paramètre, il développe les packs de paramètres dans un des noms distincts ». Cela vaut techniquement, mais peut prêter à confusion pour la traduction au code. Prenez en compte ce qui suit :  
  
-   Dans une liste de paramètres de modèle (`template <parameter-list>`), `typename...` présente un package de paramètres de modèle.  
  
-   Dans une clause de déclaration de paramètre (`func(parameter-list)`), un bouton de sélection de « niveau supérieur » introduit un package de paramètres de fonction et le positionnement des points de suspension est important :  
  
    ```cpp  
    // v1 is NOT a function parameter pack:  
    template <typename... Types> void func1(std::vector<Types...> v1);   
  
    // v2 IS a function parameter pack:  
    template <typename... Types> void func2(std::vector<Types>... v2);   
    ```  
  
-   Lorsque les points de suspension s’affiche immédiatement après un nom de paramètre, vous avez une expansion de paramètre.  
  
## <a name="example"></a>Exemple  
 Un bon moyen pour illustrer le mécanisme de fonction de modèle variadique consiste à utiliser dans une réécriture de certaines des fonctionnalités de `printf`:  
  
```cpp  
#include <iostream>  
  
using namespace std;  
  
void print() {  
    cout << endl;  
}  
  
template <typename T> void print(const T& t) {  
    cout << t << endl;  
}  
  
template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {  
    cout << first << ", ";  
    print(rest...); // recursive call using pack expansion syntax  
}  
  
int main()  
{  
    print(); // calls first overload, outputting only a newline  
    print(1); // calls second overload  
  
    // these call the third overload, the variadic template,   
    // which uses recursion as needed.  
    print(10, 20);  
    print(100, 200, 300);  
    print("first", 2, "third", 3.14159);  
}  
  
```  
  
## <a name="output"></a>Sortie  
  
```  
  
1  
10, 20  
100, 200, 300  
first, 2, third, 3.14159  
```  
  
> [!NOTE]
>  La plupart des implémentations qui intègrent des fonctions de modèle variadique utiliser la récurrence d’une forme, mais il est légèrement différente de la récursivité traditionnelle.  La récursivité traditionnelle implique une fonction appelant elle-même à l’aide de la même signature. (Il est peut-être surchargé ou basé sur un modèle, mais la même signature est choisie à chaque fois.) La récurrence Variadic implique l’appel d’un modèle de fonction variadique par à l’aide des nombres (presque toujours par ordre décroissant) d’arguments et l’horodatage ainsi à une signature différente chaque fois. Un « cas de base » est toujours requis, mais la nature de la récursivité est différente.  
  
