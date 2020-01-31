---
title: constexpr (C++)
description: Guide du mot C++ clé constexpr du langage.
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
ms.openlocfilehash: 4f34eef3217377ab50a2d80d42b5bea4b054c5be
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821777"
---
# <a name="opno-locconstexpr-c"></a>constexpr (C++)

Le mot clé **constexpr** a été introduit dans c++ 11 et amélioré dans c++ 14. Il s’agit d’une *expression constante*. Comme **const** , elle peut être appliquée à des variables : une erreur de compilateur est générée quand un code tente de modifier la valeur. Contrairement à **const** , **constexpr** peut également être appliqué aux fonctions et aux constructeurs de classe. **constexpr** indique que la valeur, ou valeur de retour, est constante et, dans la mesure du possible, est calculée au moment de la compilation.

Une **constexpr** valeur intégrale peut être utilisée partout où un entier const est requis, par exemple dans les arguments template et les déclarations de tableau. Et lorsqu’une valeur est calculée au moment de la compilation plutôt qu’au moment de l’exécution, elle permet à votre programme de s’exécuter plus rapidement et d’utiliser moins de mémoire.

Pour limiter la complexité des calculs de constantes au moment de la compilation et leurs impacts potentiels sur la compilation, la norme C++ 14 requiert que les types des expressions constantes soient des [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

> **constexpr** *identificateur de type littéral* **=** *expression constante* **;** \
> **constexpr** l’identificateur *de type littéral* **{** *constant-expression* **}** **;** \
> **constexpr** identificateur de *type littéral* **(** *params* **)** **;** \
> **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parameters

*params*\
Un ou plusieurs paramètres, chacun d’entre eux devant être un type littéral et doit lui-même être une expression constante.

## <a name="return-value"></a>Valeur de retour

Une variable ou une fonction **constexpr** doit retourner un [type de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="opno-locconstexpr-variables"></a>Variables constexpr

La principale différence entre les variables **const** et **constexpr** est que l’initialisation d’une variable **const** peut être différée jusqu’au moment de l’exécution. Une variable de **constexpr** doit être initialisée au moment de la compilation.  Toutes les variables de **constexpr** sont **const** .

- Une variable peut être déclarée avec **constexpr** , lorsqu’elle a un type littéral et est initialisée. Si l’initialisation est effectuée par un constructeur, le constructeur doit être déclaré comme **constexpr** .

- Une référence peut être déclarée comme **constexpr** lorsque ces deux conditions sont remplies : l’objet référencé est initialisé par une expression constante, et toutes les conversions implicites appelées pendant l’initialisation sont également des expressions constantes.

- Toutes les déclarations d’une variable ou d’une fonction **constexpr** doivent avoir le spécificateur **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>fonctions constexpr

Une fonction de **constexpr** est une fonction dont la valeur de retour peut être calculée au moment de la compilation lorsque la consommation de code l’exige. La consommation de code requiert la valeur de retour au moment de la compilation pour initialiser une variable **constexpr** ou pour fournir un argument de modèle sans type. Quand ses arguments sont **constexpr** des valeurs, une fonction **constexpr** produit une constante au moment de la compilation. Lorsqu’elle est appelée avec des arguments non **constexpr** , ou lorsque sa valeur n’est pas requise au moment de la compilation, elle produit une valeur au moment de l’exécution comme une fonction régulière. (Ce comportement double vous évite d’avoir à écrire des versions **constexpr** et non **constexpr** de la même fonction.)

Une fonction ou un constructeur **constexpr** est implicitement **inline** .

Les règles suivantes s’appliquent aux fonctions de constexpr :

- Une fonction **constexpr** doit accepter et retourner uniquement des [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

- Une fonction **constexpr** peut être récursive.

- Elle ne peut pas être [virtuelle](../cpp/virtual-cpp.md). Un constructeur ne peut pas être défini comme **constexpr** lorsque la classe englobante a des classes de base virtuelles.

- Le corps de la fonction peut être défini avec la valeur `= default` ou `= delete`.

- Le corps ne peut pas contenir d’instructions **goto** ou de blocs **try** .

- Une spécialisation explicite d’un modèle non **constexpr** peut être déclarée comme **constexpr** :

- Une spécialisation explicite d’un modèle de **constexpr** ne doit pas nécessairement être **constexpr** :

Les règles suivantes s’appliquent aux fonctions de **constexpr** dans Visual Studio 2017 et versions ultérieures :

- Elle peut contenir des instructions **if** et **switch** , ainsi que toutes les instructions de bouclage incluant des **for** , des **for** basés sur une plage, des **while** et des **while** .

- Elle peut contenir des déclarations de variables locales, mais la variable doit être initialisée. Il doit s’agir d’un type littéral et ne peut pas être **statique** ou de thread local. La variable déclarée localement n’a pas besoin d’être **const** et peut muter.

- Une fonction membre non**statique** **constexpr** n’est pas obligatoirement **const** implicitement.

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> Dans le débogueur Visual Studio, lors du débogage d’une version de débogage non optimisée, vous pouvez savoir si une **constexpr** fonction est évaluée au moment de la compilation en plaçant un point d’arrêt à l’intérieur de celle-ci. Si le point d'arrêt est atteint, la fonction a été appelée à l'exécution.  Sinon, la fonction a été appelée au moment de la compilation.

## <a name="extern-opno-locconstexpr"></a>constexpr extern

L’option de compilateur [/Zc : externConstexpr](../build/reference/zc-externconstexpr.md) fait en sorte que le compilateur applique une [liaison externe](../c-language/external-linkage.md) aux variables déclarées à l’aide de **extern constexpr** . Dans les versions antérieures de Visual Studio, soit par défaut, soit quand **/Zc : externConstexpr-** est spécifié, Visual Studio applique la liaison interne aux variables de **constexpr** même lorsque le mot clé **extern** est utilisé. L’option **/Zc : externConstexpr** est disponible à partir de la mise à jour 15,6 de Visual Studio 2017 et est désactivée par défaut. L’option [/permissive-](../build/reference/permissive-standards-conformance.md) n’active pas **/Zc : externConstexpr**.

## <a name="example"></a>Exemple

L’exemple suivant montre **constexpr** variables, les fonctions et un type défini par l’utilisateur. Dans la dernière instruction de `main()`, la fonction membre **constexpr** `GetValue()` est un appel au moment de l’exécution, car la valeur n’est pas obligatoire pour être connue au moment de la compilation.

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
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

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

## <a name="requirements"></a>Configuration requise pour

Visual Studio 2015 ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
