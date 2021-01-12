---
description: 'En savoir plus sur : `auto` (C++)'
title: auto (C++)
ms.date: 12/10/2019
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 061ddac33af4b8e1587b2ab1035d9f96ba18b108
ms.sourcegitcommit: 14d6ae0d527d05d153e26463d4cd5ada0f43e864
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98104750"
---
# <a name="auto-c"></a>`auto` C++

Déduit le type d'une variable déclarée de son expression d'initialisation.

> [!NOTE]
> La norme C++ définit une signification originale et modifiée pour ce mot clé. Avant Visual Studio 2010, le **`auto`** mot clé déclare une variable dans la classe de stockage *automatique* , autrement dit, une variable qui a une durée de vie locale. À compter de Visual Studio 2010, le **`auto`** mot clé déclare une variable dont le type est déduit de l’expression d’initialisation dans sa déclaration. L’option du compilateur [ `/Zc:auto`&#91;-&#93;](../build/reference/zc-auto-deduce-variable-type.md) contrôle la signification du **`auto`** mot clé.

## <a name="syntax"></a>Syntaxe

> **`auto`***initialiseur* de *déclarateur***`;`**

> **`[](auto`***param1* **`, auto`** *param2***`) {};`**

## <a name="remarks"></a>Notes

Le **`auto`** mot clé indique au compilateur d’utiliser l’expression d’initialisation d’une variable déclarée, ou d’un paramètre d’expression lambda, pour déduire son type.

Nous vous recommandons d’utiliser le **`auto`** mot clé dans la plupart des cas, sauf si vous souhaitez vraiment une conversion, car elle offre les avantages suivants :

- **Robustesse :** Si le type de l’expression est modifié, cela comprend le moment où un type de retour de fonction est modifié, mais il fonctionne simplement.

- **Performances :** Vous êtes assuré qu’il n’y aura pas de conversion.

- **Convivialité :** Vous n’avez pas à vous soucier des problèmes d’orthographe des noms de type et des fautes de frappe.

- **Efficacité :** Votre codage peut être plus efficace.

Cas de conversion dans lesquels vous ne souhaitez peut-être pas utiliser **`auto`** :

- Quand vous souhaitez un type spécifique et que rien d'autre ne conviendra.

- Types d’assistance de modèle d’expression, par exemple `(valarray+valarray)` .

Pour utiliser le **`auto`** mot clé, utilisez-le à la place d’un type pour déclarer une variable et spécifiez une expression d’initialisation. En outre, vous pouvez modifier le **`auto`** mot clé à l’aide de spécificateurs et de déclarateurs tels que **`const`** , **`volatile`** , pointeur ( **`*`** ), référence ( **`&`** ) et référence rvalue ( **`&&`** ). Le compilateur évalue l'expression d'initialisation et utilise ensuite ces informations pour déduire le type de la variable.

L' **`auto`** expression d’initialisation peut prendre plusieurs formes :

- Syntaxe d’initialisation universelle, telle que `auto a { 42 };` .
- Syntaxe d’affectation, telle que `auto b = 0;` .
- La syntaxe d’affectation universelle, qui combine les deux formes précédentes, telles que `auto c = { 3.14156 };` .
- Initialisation directe, ou syntaxe de style constructeur, telle que `auto d( 1.41421f );` .

Pour plus d’informations, consultez [initialiseurs](../cpp/initializers.md) et exemples de code plus loin dans ce document.

Lorsque **`auto`** est utilisé pour déclarer le paramètre de boucle dans une instruction basée sur une plage **`for`** , il utilise une syntaxe d’initialisation différente, par exemple `for (auto& i : iterable) do_action(i);` . Pour plus d’informations, consultez [instruction basée sur une plage `for` (C++)](../cpp/range-based-for-statement-cpp.md).

Le **`auto`** mot clé est un espace réservé pour un type, mais il n’est pas lui-même un type. Par conséquent, le **`auto`** mot clé ne peut pas être utilisé dans les casts ou les opérateurs tels que [`sizeof`](../cpp/sizeof-operator.md) et (pour C++/CLI) [`typeid`](../extensions/typeid-cpp-component-extensions.md) .

## <a name="usefulness"></a>Utilité

Le **`auto`** mot clé est un moyen simple de déclarer une variable qui a un type complexe. Par exemple, vous pouvez utiliser **`auto`** pour déclarer une variable dans laquelle l’expression d’initialisation implique des modèles, des pointeurs vers des fonctions ou des pointeurs vers des membres.

Vous pouvez également utiliser **`auto`** pour déclarer et initialiser une variable en tant qu’expression lambda. Vous ne pouvez pas déclarer le type de la variable vous-même, car le type d’une expression lambda est connu uniquement du compilateur. Pour plus d’informations, consultez [exemples d’expressions lambda](../cpp/examples-of-lambda-expressions.md).

## <a name="trailing-return-types"></a>Types de retour de fin

Vous pouvez utiliser **`auto`** , avec le **`decltype`** spécificateur de type, pour faciliter l’écriture de bibliothèques de modèles. Utilisez **`auto`** et **`decltype`** pour déclarer une fonction de modèle dont le type de retour dépend des types de ses arguments template. **`auto`** **`decltype`** Vous pouvez également utiliser et pour déclarer une fonction de modèle qui encapsule un appel à une autre fonction, puis retourne ce qui est le type de retour de cette autre fonction. Pour plus d’informations, consultez [`decltype`](../cpp/decltype-cpp.md).

## <a name="references-and-cv-qualifiers"></a>Références et qualificateurs cv

Notez que l’utilisation de **`auto`** supprime **`const`** les références, les qualificateurs et les **`volatile`** qualificateurs. Prenons l’exemple suivant :

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

Dans l’exemple précédent, myAuto est une **`int`** , et non une **`int`** référence, donc la sortie est `11 11` , et non pas `11 12` comme le cas si le qualificateur de référence n’avait pas été supprimé par **`auto`** .

## <a name="type-deduction-with-braced-initializers-c14"></a>Déduction de type avec des initialiseurs entre accolades (C++ 14)

L’exemple de code suivant montre comment initialiser une **`auto`** variable à l’aide d’accolades. Notez la différence entre B et C et entre A et E.

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

Le tableau suivant répertorie les restrictions sur l’utilisation du **`auto`** mot clé et le message d’erreur de diagnostic correspondant que le compilateur émet.

|Numéro d'erreur|Description|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|Le **`auto`** mot clé ne peut pas être combiné avec un autre spécificateur de type.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Un symbole qui est déclaré avec le **`auto`** mot clé doit avoir un initialiseur.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Vous avez utilisé incorrectement le **`auto`** mot clé pour déclarer un type. Par exemple, vous avez déclaré un type de retour de méthode ou un tableau.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Un paramètre ou un argument de modèle ne peut pas être déclaré avec le **`auto`** mot clé.|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Un paramètre de méthode ou de modèle ne peut pas être déclaré avec le **`auto`** mot clé.|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Un symbole ne peut pas être utilisé avant d'être initialisé. Dans la pratique, cela signifie qu'une variable ne peut pas être utilisée pour s'initialiser.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Vous ne pouvez pas effectuer un cast en un type qui est déclaré avec le **`auto`** mot clé.|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Tous les symboles d’une liste de déclarateurs déclarés avec le **`auto`** mot clé doivent être résolus vers le même type. Pour plus d’informations, consultez [déclarations et définitions](declarations-and-definitions-cpp.md).|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|Les opérateurs [sizeof](../cpp/sizeof-operator.md) et [typeid](../extensions/typeid-cpp-component-extensions.md) ne peuvent pas être appliqués à un symbole qui est déclaré avec le **`auto`** mot clé.|

## <a name="examples"></a>Exemples

Ces fragments de code illustrent quelques-unes des façons dont le **`auto`** mot clé peut être utilisé.

Les déclarations suivantes sont équivalentes. Dans la première instruction, la variable `j` est déclarée comme étant de type **`int`** . Dans la deuxième instruction, `k` la variable est déduite de type, **`int`** car l’expression d’initialisation (0) est un entier.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

Les déclarations suivantes sont équivalentes, mais la seconde déclaration est plus simple que la première. L’une des raisons les plus intéressantes d’utiliser le **`auto`** mot clé est la simplicité.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

Le fragment de code suivant déclare le type des variables `iter` et le `elem` début des boucles de **`for`** plage et **`for`** .

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

Le fragment de code suivant utilise l' **`new`** opérateur et la déclaration de pointeur pour déclarer des pointeurs.

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

Le fragment de code suivant initialise `x` une variable en type **`int`** , `y` une variable à une référence au type **`const int`** et `fp` une variable à un pointeur vers une fonction qui retourne le type **`int`** .

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto& y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[`/Zc:auto` (Déduire le type de variable)](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[`sizeof` And](../cpp/sizeof-operator.md)<br/>
[`typeid`](../extensions/typeid-cpp-component-extensions.md)<br/>
[`operator new`](new-operator-cpp.md)<br/>
[Déclarations et définitions](declarations-and-definitions-cpp.md)<br/>
[Exemples d’expressions lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[Initialiseurs](../cpp/initializers.md)<br/>
[`decltype`](../cpp/decltype-cpp.md)
