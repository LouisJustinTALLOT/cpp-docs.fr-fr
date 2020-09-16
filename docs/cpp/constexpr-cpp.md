---
title: constexpr C++
description: Guide du mot clé du langage C++ constexpr .
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 57ebf4bf69c768bfcd2e4d26a5c3334ca788b08f
ms.sourcegitcommit: a6b97f5d78299ad93675de2fe0f0561f528d26c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90569563"
---
# <a name="no-locconstexpr-c"></a>constexpr C++

Le mot clé **`constexpr`** a été introduit dans c++ 11 et amélioré en c++ 14. Cela signifie * const expression ant*. Comme **`const`** , il peut être appliqué à des variables : une erreur de compilateur est générée quand un code tente de mod if y la valeur. Contrairement **`const`** **`constexpr`** à, peut également être appliqué aux fonctions et à la classe const ructors. **`constexpr`** indique que la valeur, ou valeur de retour, est const ant et, lorsque cela est possible, est calculé au moment de la compilation.

Une **`constexpr`** valeur intégrale peut être utilisée partout où un const entier est requis, par exemple dans les arguments template et les déclarations de tableau. Et lorsqu’une valeur est calculée au moment de la compilation plutôt qu’au moment de l’exécution, elle permet à votre programme de s’exécuter plus rapidement et d’utiliser moins de mémoire.

Pour limiter la complexité des calculs ant au moment de la compilation const et leur impact potentiel sur la compilation, la norme c++ 14 requiert que les types des const expressions ant soient des [types de littéraux](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

> **`constexpr`***littéral-type* *ident if Ier* **=** * const ant-expression* **;**\
> **`constexpr`***littéral-type* *ident if Ier* **{** * const ant-expression* **}** **;**\
> **`constexpr`***littéral-type* *ident if Ier* **(** *params* **)** **;**\
> **`constexpr`***ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Paramètres

*params*\
Un ou plusieurs paramètres, chacun d’entre eux devant être un type littéral et doit lui-même être une const expression ant.

## <a name="return-value"></a>Valeur retournée

Une **`constexpr`** variable ou une fonction doit retourner un [type de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="no-locconstexpr-variables"></a>Variables constexpr

L' if interférence d primaire entre les **`const`** **`constexpr`** variables et est que l’initialisation d’une **`const`** variable peut être différée jusqu’au moment de l’exécution. Une **`constexpr`** variable doit être initialisée au moment de la compilation.  Toutes les **`constexpr`** variables sont **`const`** .

- Une variable peut être déclarée avec **`constexpr`** , lorsqu’elle a un type littéral et qu’elle est initialisée. Si l’initialisation est par for med par un const ructor, le const ructor doit être déclaré comme **`constexpr`** .

- Une référence peut être déclarée comme **`constexpr`** lorsque ces deux conditions sont remplies : l’objet référencé est initialisé par une const expression ant, et toutes les conversions implicites appelées pendant l’initialisation sont également des const expressions ant.

- Toutes les déclarations d’une **`constexpr`** variable ou d’une fonction doivent avoir la **`constexpr`** spécification if Ier.

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="no-locconstexpr-functions"></a><a name="constexpr_functions"></a>constexprfonctions

Une **`constexpr`** fonction est une fonction dont la valeur de retour est calculée au moment de la compilation lorsque la consommation de code l’exige. La consommation de code requiert la valeur de retour au moment de la compilation pour initialiser une **`constexpr`** variable, ou pour fournir un argument de modèle sans type. Quand ses arguments sont des **`constexpr`** valeurs, une **`constexpr`** fonction génère un ant au moment de la compilation const . Lorsqu’elle est appelée avec des **`constexpr`** arguments non, ou lorsque sa valeur n’est pas requise au moment de la compilation, elle produit une valeur au moment de l’exécution comme une fonction régulière. (Ce comportement double vous évite d’avoir à écrire **`constexpr`** et non **`constexpr`** des versions de la même fonction.)

Une **`constexpr`** fonction ou const ructor est implicitement **`inline`** .

Les règles suivantes s’appliquent aux constexpr fonctions :

- Une **`constexpr`** fonction doit accepter et retourner uniquement des [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

- Une **`constexpr`** fonction peut être récursive.

- Elle ne peut pas être [virtuelle](../cpp/virtual-cpp.md). Un const ructor ne peut pas être défini comme **`constexpr`** lorsque la classe englobante a des classes de base virtuelles.

- Le corps de la fonction peut être défini avec la valeur `= default` ou `= delete`.

- Le corps ne peut pas contenir d' **`goto`** instructions ou de **`try`** blocs.

- Une spécialisation explicite d’un non- **`constexpr`** modèle peut être déclarée comme **`constexpr`** suit :

- Une spécialisation explicite d’un **`constexpr`** modèle ne doit pas nécessairement être **`constexpr`** :

Les règles suivantes s’appliquent aux **`constexpr`** fonctions dans Visual Studio 2017 et versions ultérieures :

- Elle peut contenir **`if`** des **`switch`** instructions et, ainsi que toutes les instructions de bouclage incluant **`for`** , **`for`** , **`while`** et **do- while **.

- Elle peut contenir des déclarations de variables locales, mais la variable doit être initialisée. Il doit s’agir d’un type littéral, et il ne peut pas être **`static`** ou local. La variable déclarée localement ne doit pas être **`const`** et peut muter.

- Une **`constexpr`** fonction non **`static`** membre ne doit pas obligatoirement être implicitement **`const`** .

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}
```

> [!TIP]
> Dans le débogueur Visual Studio, lors du débogage d’une version de débogage non optimisée, vous pouvez déterminer si une **`constexpr`** fonction est évaluée au moment de la compilation en plaçant un point d’arrêt à l’intérieur de celle-ci. Si le point d'arrêt est atteint, la fonction a été appelée à l'exécution.  Sinon, la fonction a été appelée au moment de la compilation.

## <a name="extern-no-locconstexpr"></a>externes constexpr

L’option de compilateur [/Zc : externConstexpr](../build/reference/zc-externconstexpr.md) fait en sorte que le compilateur applique une [liaison externe](../c-language/external-linkage.md) aux variables déclarées à l’aide de **extern constexpr **. Dans les versions antérieures de Visual Studio, soit par défaut, soit quand **/Zc : externConstexpr-** est spec if IED, Visual Studio applique la liaison interne aux **`constexpr`** variables même lorsque le **`extern`** mot clé est utilisé. L’option **/Zc : externConstexpr** est disponible à partir de la mise à jour 15,6 de Visual Studio 2017 et est désactivée par défaut. L’option [/permissive-](../build/reference/permissive-standards-conformance.md) n’active pas **/Zc : externConstexpr**.

## <a name="example"></a> Exemple

L’exemple suivant illustre des **`constexpr`** variables, des fonctions et un type défini par l’utilisateur. Dans la dernière instruction de `main()` , la **`constexpr`** fonction membre `GetValue()` est un appel au moment de l’exécution, car la valeur n’est pas obligatoire pour être connue au moment de la compilation.

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
}

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Spécifications

Visual Studio 2015 ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
