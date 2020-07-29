---
title: :::no-loc(constexpr):::C++
description: 'Guide du mot clé du langage C++ :::no-loc(constexpr)::: .'
ms.date: 01/28/2020
f1_keywords:
- :::no-loc(constexpr):::_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- ':::no-loc(constexpr):::'
- ':::no-loc(const):::'
- ':::no-loc(inline):::'
- ':::no-loc(goto):::'
- ':::no-loc(try):::'
- ':::no-loc(if):::'
- ':::no-loc(switch):::'
- ':::no-loc(for):::'
- ':::no-loc(while):::'
ms.openlocfilehash: d66dc333b7ac9fba94221dc4efa723c7919ef88f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229023"
---
# <a name="no-locconstexpr-c"></a>:::no-loc(constexpr):::C++

Le mot clé **`:::no-loc(constexpr):::`** a été introduit dans c++ 11 et amélioré en c++ 14. Cela signifie * :::no-loc(const)::: expression ant*. Comme **`:::no-loc(const):::`** , il peut être appliqué à des variables : une erreur de compilateur est générée quand un code tente de mod :::no-loc(if)::: y la valeur. Contrairement **`:::no-loc(const):::`** **`:::no-loc(constexpr):::`** à, peut également être appliqué aux fonctions et à la classe :::no-loc(const)::: ructors. **`:::no-loc(constexpr):::`** indique que la valeur, ou valeur de retour, est :::no-loc(const)::: ant et, lorsque cela est possible, est calculé au moment de la compilation.

Une **`:::no-loc(constexpr):::`** valeur intégrale peut être utilisée partout où un :::no-loc(const)::: entier est requis, par exemple dans les arguments template et les déclarations de tableau. Et lorsqu’une valeur est calculée au moment de la compilation plutôt qu’au moment de l’exécution, elle permet à votre programme de s’exécuter plus rapidement et d’utiliser moins de mémoire.

Pour limiter la complexité des calculs ant au moment de la compilation :::no-loc(const)::: et leur impact potentiel sur la compilation, la norme c++ 14 requiert que les types des :::no-loc(const)::: expressions ant soient des [types de littéraux](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

> **`:::no-loc(constexpr):::`***littéral-type* *ident :::no-loc(if)::: Ier* **=** * :::no-loc(const)::: ant-expression* **;**\
> **`:::no-loc(constexpr):::`***littéral-type* *ident :::no-loc(if)::: Ier* **{** * :::no-loc(const)::: ant-expression* **}** **;**\
> **`:::no-loc(constexpr):::`***littéral-type* *ident :::no-loc(if)::: Ier* **(** *params* **)** **;**\
> **`:::no-loc(constexpr):::`***ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Paramètres

*params*\
Un ou plusieurs paramètres, chacun d’entre eux devant être un type littéral et doit lui-même être une :::no-loc(const)::: expression ant.

## <a name="return-value"></a>Valeur retournée

Une **`:::no-loc(constexpr):::`** variable ou une fonction doit retourner un [type de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="no-locconstexpr-variables"></a>Variables :::no-loc(constexpr):::

L' :::no-loc(if)::: interférence d primaire entre les **`:::no-loc(const):::`** **`:::no-loc(constexpr):::`** variables et est que l’initialisation d’une **`:::no-loc(const):::`** variable peut être différée jusqu’au moment de l’exécution. Une **`:::no-loc(constexpr):::`** variable doit être initialisée au moment de la compilation.  Toutes les **`:::no-loc(constexpr):::`** variables sont **`:::no-loc(const):::`** .

- Une variable peut être déclarée avec **`:::no-loc(constexpr):::`** , lorsqu’elle a un type littéral et qu’elle est initialisée. Si l’initialisation est par :::no-loc(for)::: med par un :::no-loc(const)::: ructor, le :::no-loc(const)::: ructor doit être déclaré comme **`:::no-loc(constexpr):::`** .

- Une référence peut être déclarée comme **`:::no-loc(constexpr):::`** lorsque ces deux conditions sont remplies : l’objet référencé est initialisé par une :::no-loc(const)::: expression ant, et toutes les conversions implicites appelées pendant l’initialisation sont également des :::no-loc(const)::: expressions ant.

- Toutes les déclarations d’une **`:::no-loc(constexpr):::`** variable ou d’une fonction doivent avoir la **`:::no-loc(constexpr):::`** spécification :::no-loc(if)::: Ier.

```cpp
:::no-loc(constexpr)::: float x = 42.0;
:::no-loc(constexpr)::: float y{108};
:::no-loc(constexpr)::: float z = exp(5, 3);
:::no-loc(constexpr)::: int i; // Error! Not initialized
int j = 0;
:::no-loc(constexpr)::: int k = j + 1; //Error! j not a :::no-loc(const):::ant expression
```

## <a name="no-locconstexpr-functions"></a><a name=":::no-loc(constexpr):::_functions"></a>:::no-loc(constexpr):::fonctions

Une **`:::no-loc(constexpr):::`** fonction est une fonction dont la valeur de retour est calculée au moment de la compilation lorsque la consommation de code l’exige. La consommation de code requiert la valeur de retour au moment de la compilation pour initialiser une **`:::no-loc(constexpr):::`** variable, ou pour fournir un argument de modèle sans type. Quand ses arguments sont des **`:::no-loc(constexpr):::`** valeurs, une **`:::no-loc(constexpr):::`** fonction génère un ant au moment de la compilation :::no-loc(const)::: . Lorsqu’elle est appelée avec des **`:::no-loc(constexpr):::`** arguments non, ou lorsque sa valeur n’est pas requise au moment de la compilation, elle produit une valeur au moment de l’exécution comme une fonction régulière. (Ce comportement double vous évite d’avoir à écrire **`:::no-loc(constexpr):::`** et non **`:::no-loc(constexpr):::`** des versions de la même fonction.)

Une **`:::no-loc(constexpr):::`** fonction ou :::no-loc(const)::: ructor est implicitement **`:::no-loc(inline):::`** .

Les règles suivantes s’appliquent aux :::no-loc(constexpr)::: fonctions :

- Une **`:::no-loc(constexpr):::`** fonction doit accepter et retourner uniquement des [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

- Une **`:::no-loc(constexpr):::`** fonction peut être récursive.

- Elle ne peut pas être [virtuelle](../cpp/virtual-cpp.md). Un :::no-loc(const)::: ructor ne peut pas être défini comme **`:::no-loc(constexpr):::`** lorsque la classe englobante a des classes de base virtuelles.

- Le corps de la fonction peut être défini avec la valeur `= default` ou `= delete`.

- Le corps ne peut pas contenir d' **`:::no-loc(goto):::`** instructions ou de **`:::no-loc(try):::`** blocs.

- Une spécialisation explicite d’un non- **`:::no-loc(constexpr):::`** modèle peut être déclarée comme **`:::no-loc(constexpr):::`** suit :

- Une spécialisation explicite d’un **`:::no-loc(constexpr):::`** modèle ne doit pas nécessairement être **`:::no-loc(constexpr):::`** :

Les règles suivantes s’appliquent aux **`:::no-loc(constexpr):::`** fonctions dans Visual Studio 2017 et versions ultérieures :

- Elle peut contenir **`:::no-loc(if):::`** des **`:::no-loc(switch):::`** instructions et, ainsi que toutes les instructions de bouclage incluant **`:::no-loc(for):::`** , **`:::no-loc(for):::`** , **`:::no-loc(while):::`** et **do- :::no-loc(while)::: **.

- Elle peut contenir des déclarations de variables locales, mais la variable doit être initialisée. Il doit s’agir d’un type littéral, et il ne peut pas être **`static`** ou local. La variable déclarée localement ne doit pas être **`:::no-loc(const):::`** et peut muter.

- Une **`:::no-loc(constexpr):::`** fonction non **`static`** membre ne doit pas obligatoirement être implicitement **`:::no-loc(const):::`** .

```cpp
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> Dans le débogueur Visual Studio, lors du débogage d’une version de débogage non optimisée, vous pouvez déterminer si une **`:::no-loc(constexpr):::`** fonction est évaluée au moment de la compilation en plaçant un point d’arrêt à l’intérieur de celle-ci. Si le point d'arrêt est atteint, la fonction a été appelée à l'exécution.  Sinon, la fonction a été appelée au moment de la compilation.

## <a name="extern-no-locconstexpr"></a>externes:::no-loc(constexpr):::

L’option de compilateur [/Zc : externConstexpr](../build/reference/zc-extern:::no-loc(constexpr):::.md) fait en sorte que le compilateur applique une [liaison externe](../c-language/external-linkage.md) aux variables déclarées à l’aide de **extern :::no-loc(constexpr)::: **. Dans les versions antérieures de Visual Studio, soit par défaut, soit quand **/Zc : externConstexpr-** est spec :::no-loc(if)::: IED, Visual Studio applique la liaison interne aux **`:::no-loc(constexpr):::`** variables même lorsque le **`extern`** mot clé est utilisé. L’option **/Zc : externConstexpr** est disponible à partir de la mise à jour 15,6 de Visual Studio 2017 et est désactivée par défaut. L’option [/permissive-](../build/reference/permissive-standards-con:::no-loc(for):::mance.md) n’active pas **/Zc : externConstexpr**.

## <a name="example"></a>Exemple

L’exemple suivant illustre des **`:::no-loc(constexpr):::`** variables, des fonctions et un type défini par l’utilisateur. Dans la dernière instruction de `main()` , la **`:::no-loc(constexpr):::`** fonction membre `GetValue()` est un appel au moment de l’exécution, car la valeur n’est pas obligatoire pour être connue au moment de la compilation.

```cpp
// :::no-loc(constexpr):::.cpp
// Compile with: cl /EHsc /W4 :::no-loc(constexpr):::.cpp
#include <iostream>

using namespace std;

// Pass by value
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
:::no-loc(constexpr)::: float exp2(:::no-loc(const)::: float& x, :::no-loc(const)::: int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
:::no-loc(constexpr)::: int length(:::no-loc(const)::: T(&)[N])
{
    return N;
}

// Recursive :::no-loc(constexpr)::: function
:::no-loc(constexpr)::: int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    :::no-loc(constexpr)::: explicit Foo(int i) : _i(i) {}
    :::no-loc(constexpr)::: int GetValue() :::no-loc(const):::
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is :::no-loc(const)::::
    :::no-loc(constexpr)::: Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    :::no-loc(constexpr)::: float x = exp(5, 3);
    :::no-loc(constexpr)::: float y { exp(2, 5) };
    :::no-loc(constexpr)::: int val = foo.GetValue();
    :::no-loc(constexpr)::: int f5 = fac(5);
    :::no-loc(const)::: int nums[] { 1, 2, 3, 4 };
    :::no-loc(const)::: int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Spécifications

Visual Studio 2015 ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)\
[:::no-loc(const):::](../cpp/:::no-loc(const):::-cpp.md)
