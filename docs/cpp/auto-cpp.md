---
title: automatique (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4564606cd1a4cf6c12c224f6a3725d9f6aca2224
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402774"
---
# <a name="auto-c"></a>automatique (C++)
Déduit le type d'une variable déclarée de son expression d'initialisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
auto declarator initializer;  
```  
  
```  
[](auto param1, auto param2) {};  
```  
  
## <a name="remarks"></a>Notes  
 Le **automatique** mot clé indique au compilateur d’utiliser l’expression d’initialisation d’une variable déclarée, ou un paramètre d’expression lambda, pour déduire son type.  
  
 Nous vous recommandons d’utiliser le **automatique** mot clé pour la plupart des situations —, sauf si vous voulez vraiment une conversion, car elle offre ces avantages :  
  
-   **Robustesse :** si le type de l’expression est modifié, cela inclut les cas de modification d’un type de retour de fonction, elle fonctionne tout simplement.  
  
-   **Performances :** vous êtes certain qu’il n’y aura aucune conversion.  
  
-   **Facilité d’utilisation :** ne pas avoir à vous soucier des fautes de frappe et les difficultés de l’orthographe de nom de type.  
  
-   **L’efficacité :** votre codage peut être plus efficace.  
  
 Cas de conversion dans lesquels vous souhaiterez pas utiliser **automatique**:  
  
-   Quand vous souhaitez un type spécifique et que rien d'autre ne conviendra.  
  
-   Types d’assistance de modèle expression — par exemple, `(valarray+valarray)`.  
  
 Pour utiliser le **automatique** mot clé, utilisez plutôt qu’un type pour déclarer une variable et spécifier une expression d’initialisation. En outre, vous pouvez modifier le **automatique** mot clé à l’aide de spécificateurs et déclarateurs comme **const**, **volatile**, pointeur (`*`), référence (`&`) et la référence rvalue (`&&`). Le compilateur évalue l'expression d'initialisation et utilise ensuite ces informations pour déduire le type de la variable.  
  
 L’expression d’initialisation peut être une assignation (syntaxe avec signe égal), une initialisation directe (syntaxe de style fonction), un [opérateur new](new-operator-cpp.md) expression ou l’expression d’initialisation peut être le  *for-range-declaration* paramètre dans un [Range-based pour instruction (C++)](../cpp/range-based-for-statement-cpp.md) instruction. Pour plus d’informations, consultez [initialiseurs](../cpp/initializers.md) et les exemples de code plus loin dans ce document.  
  
 Le **automatique** mot clé est un espace réservé pour un type, mais il n’est pas lui-même un type. Par conséquent, le **automatique** mot clé ne peut pas être utilisé dans des casts ni des opérateurs tels que [sizeof](../cpp/sizeof-operator.md) et [typeid](../windows/typeid-cpp-component-extensions.md).  
  
## <a name="usefulness"></a>Utilité  
 Le **automatique** mot clé est un moyen simple pour déclarer une variable qui a un type complexe. Par exemple, vous pouvez utiliser **automatique** pour déclarer une variable où l’expression d’initialisation implique des modèles, des pointeurs vers des fonctions ou des pointeurs vers des membres.  
  
 Vous pouvez également utiliser **automatique** pour déclarer et initialiser une variable à une expression lambda. Vous ne pouvez pas déclarer le type de la variable vous-même, car le type d’une expression lambda est connu uniquement du compilateur. Pour plus d’informations, consultez [exemples d’Expressions Lambda](../cpp/examples-of-lambda-expressions.md).  
  
## <a name="trailing-return-types"></a>Types de retour de fin  
 Vous pouvez utiliser **automatique**, avec le **decltype** spécificateur, pour aider à écrire des bibliothèques de modèles de type. Utilisez **automatique** et **decltype** pour déclarer une fonction de modèle dont retour type dépend des types de ses arguments template. Ou, utilisez **automatique** et **decltype** pour déclarer une fonction de modèle qui encapsule un appel à une autre fonction, puis retourne le type de retour de cette autre fonction. Pour plus d’informations, consultez [decltype](../cpp/decltype-cpp.md).  
  
## <a name="references-and-cv-qualifiers"></a>Références et qualificateurs cv  
 Notez que l’utilisation **automatique** supprime les références, qualificateurs constantes et qualificateurs volatiles. Prenons l'exemple suivant :  
  
```cpp  
// cl.exe /analyze /EHsc /W4  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
    int count = 10;  
    int& countRef = count;  
    auto myAuto = countRef;  
  
    countRef = 11;  
    cout << count << " ";  
  
    myAuto = 12;  
    cout << count << endl;  
}  
  
```  
  
 Dans l’exemple précédent, myAuto est de type int, pas une référence de type int, la sortie est `11 11`, et non `11 12` comme ce serait le cas si le qualificateur de référence n’avait pas été supprimé **automatique**.  
  
## <a name="type-deduction-with-braced-initializers-c14"></a>Déduction de type avec initialiseurs entre accolades (C ++ 14)  
 L’exmample de code suivant montre comment initialiser une variable automatique à l’aide d’accolades. Notez la différence entre B et C et entre A et E.  
  
```cpp  
#include <initializer_list>  
  
int main()  
{  
    // std::initializer_list<int>  
    auto A = { 1, 2 };  
  
    // std::initializer_list<int>  
    auto B = { 3 };  
  
    // int  
    auto C{ 4 };  
  
    // C3535: cannot deduce type for 'auto' from initializer list'  
    auto D = { 5, 6.7 };  
  
    // C3518 in a direct-list-initialization context the type for 'auto'  
    // can only be deduced from a single initializer expression  
    auto E{ 8, 9 };  
  
    return 0;  
}  
```  
  
## <a name="restrictions-and-error-messages"></a>Restrictions et messages d'erreur  
 Le tableau suivant répertorie les restrictions sur l’utilisation de la **automatique** mot clé et le message d’erreur de diagnostic correspondant émis par le compilateur.  
  
|Numéro de l'erreur|Description|  
|------------------|-----------------|  
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|Le **automatique** mot clé ne peut pas être combiné avec n’importe quel autre spécificateur de type.|  
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Un symbole qui est déclaré avec le **automatique** mot clé doit avoir un initialiseur.|  
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Vous avez correctement utilisé la **automatique** mot clé pour déclarer un type. Par exemple, vous avez déclaré un type de retour de méthode ou un tableau.|  
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Un paramètre ou un argument template ne peut pas être déclaré avec le **automatique** mot clé.|  
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Une méthode ou paramètre de modèle ne peut pas être déclaré avec le **automatique** mot clé.|  
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Un symbole ne peut pas être utilisé avant d'être initialisé. Dans la pratique, cela signifie qu'une variable ne peut pas être utilisée pour s'initialiser.|  
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Vous ne pouvez pas effectuer un cast en un type qui est déclaré avec le **automatique** mot clé.|  
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Tous les symboles dans une liste de déclarateurs qui est déclaré avec le **automatique** mot clé doit correspondre au même type. Pour plus d’informations, consultez [déclarations et définitions](declarations-and-definitions-cpp.md).|  
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|Le [sizeof](../cpp/sizeof-operator.md) et [typeid](../windows/typeid-cpp-component-extensions.md) opérateurs ne peuvent pas être appliqués à un symbole qui est déclaré avec le **automatique** mot clé.|  
  
## <a name="examples"></a>Exemples  
 Ces fragments de code illustrent certaines des façons dans lequel le **automatique** mot clé peut être utilisé.  
  
 Les déclarations suivantes sont équivalentes. Dans la première instruction, variable `j` est déclaré comme étant de type **int**. Dans la deuxième instruction, variable `k` est déduit pour être de type **int** , car l’expression d’initialisation (0) est un entier.  
  
```cpp  
int j = 0;  // Variable j is explicitly type int.  
auto k = 0; // Variable k is implicitly type int because 0 is an integer.  
```  
  
 Les déclarations suivantes sont équivalentes, mais la seconde déclaration est plus simple que la première. Une des raisons plus convaincantes d’utiliser le **automatique** mot clé est la simplicité.  
  
```cpp  
map<int,list<string>>::iterator i = m.begin();   
auto i = m.begin();   
```  
  
 Le fragment de code suivant déclare le type des variables `iter` et `elem` lorsque le **pour** et plage **pour** effectue une boucle de démarrage.  
  
```cpp  
// cl /EHsc /nologo /W4  
#include <deque>  
using namespace std;  
  
int main()  
{  
    deque<double> dqDoubleData(10, 0.1);  
  
    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)  
    { /* ... */ }  
  
    // prefer range-for loops with the following information in mind  
    // (this applies to any range-for with auto, not just deque)  
  
    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples  
    { /* ... */ }  
  
    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE  
    { /* ... */ }  
  
    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE  
    { /* ... */ }  
}  
```  
  
 Le fragment de code suivant utilise la **nouveau** déclaration d’opérateur et de pointeur pour déclarer des pointeurs.  
  
```cpp  
double x = 12.34;  
auto *y = new auto(x), **z = new auto(&x);  
```  
  
 Le fragment de code suivant déclare plusieurs symboles dans chaque instruction de déclaration. Notez que tous les symboles dans chaque instruction sont résolus en un même type.  
  
```cpp  
auto x = 1, *y = &x, **z = &y; // Resolves to int.  
auto a(2.01), *b (&a);         // Resolves to double.  
auto c = 'a', *d(&c);          // Resolves to char.  
auto m = 1, &n = m;            // Resolves to int.  
```  
  
 Ce fragment de code utilise l'opérateur conditionnel (`?:`) pour déclarer la variable `x` en tant qu'entier avec la valeur 200 :  
  
```cpp  
int v1 = 100, v2 = 200;  
auto x = v1 > v2 ? v1 : v2;  
```  
  
 Le fragment de code suivant initialise la variable `x` à taper **int**, la variable `y` à une référence au type **const int**et la variable `fp` à un pointeur vers une fonction qui retourne le type **int**.  
  
```cpp  
int f(int x) { return x; }  
int main()  
{  
    auto x = f(0);  
    const auto & y = f(1);  
    int (*p)(int x);  
    p = f;  
    auto fp = p;  
    //...  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [auto, mot clé](../cpp/auto-keyword.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [/ Zc : auto (déduire le Type de Variable)](../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof, opérateur](../cpp/sizeof-operator.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)   
 [opérateur new](new-operator-cpp.md)   
 [Déclarations et définitions](declarations-and-definitions-cpp.md)   
 [Exemples d’Expressions Lambda](../cpp/examples-of-lambda-expressions.md)   
 [Initialiseurs](../cpp/initializers.md)   
 [decltype](../cpp/decltype-cpp.md)