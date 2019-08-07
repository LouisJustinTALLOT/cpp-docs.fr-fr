---
title: constexpr (C++)
ms.date: 08/05/2019
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
ms.openlocfilehash: 5c98436f537b34b1c9050e057971938d48792db1
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821099"
---
# <a name="constexpr-c"></a>constexpr (C++)

Le mot clé **constexpr** a été introduit dans c++ 11 et amélioré dans c++ 14. Il s’agit d’une *expression constante*. Comme **const**, elle peut être appliquée à des variables afin qu’une erreur de compilateur soit déclenchée si un code tente de modifier la valeur. Contrairementà const, **constexpr** peut également être appliqué aux fonctions et aux constructeurs de classe. **constexpr** indique que la valeur, ou valeur de retour, est constante et, si possible, est calculée au moment de la compilation.

Une valeur intégrale **constexpr** peut être utilisée partout où un entier const est requis, par exemple dans les arguments template et les déclarations de tableau. Et lorsqu’une valeur peut être calculée au moment de la compilation plutôt qu’au moment de l’exécution, elle peut aider votre programme à s’exécuter plus rapidement et utiliser moins de mémoire.

Pour limiter la complexité des calculs de constantes au moment de la compilation et leurs impacts potentiels sur la compilation, la norme C++ 14 requiert que les types des expressions constantes soient des [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

> **constexpr** *type de littéral* *identificateur* **=** *expression constante* **;** 
>  **constexpr** *type de littéral* *identificateur* **{** *expression constante* **}** **;** 
>  **constexpr** *type de littéral* *identificateur* **(** *params* **)** **;** 
>  **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Paramètres

*params*<br/>
Un ou plusieurs paramètres, chacun d’entre eux devant être un type littéral et doit lui-même être une expression constante.

## <a name="return-value"></a>Valeur de retour

Une variable ou une fonction constexpr doit retourner un [type de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>Variables constexpr

La principale différence entre les variables const et constexpr est que l’initialisation d’une variable const peut être différée jusqu’au moment de l’exécution. Une variable constexpr doit être initialisée au moment de la compilation.  Toutes les variables constexpr sont de type const.

- Une variable peut être déclarée avec **constexpr**, si elle a un type littéral et est initialisée. Si l’initialisation est effectuée par un constructeur, le constructeur doit être déclaré en tant que **constexpr**.

- Une référence peut être déclarée avec constexpr si l'objet référencé a été initialisé par une expression constante et que toutes les conversions implicites appelées pendant l'initialisation sont aussi des expressions constantes.

- Toutes les déclarations d’une fonction ou d’une variable **constexpr** doivent avoir le spécificateur **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>constexpr, fonctions

Une fonction **constexpr** est une fonction dont la valeur de retour peut être calculée au moment de la compilation lorsque la consommation de code l’exige. La consommation de code requiert la valeur de retour au moment de la compilation, par exemple, pour initialiser une variable **constexpr** ou fournir un argument de modèle sans type. Quand ses arguments sont des valeurs **constexpr** , une fonction **constexpr** produit une constante au moment de la compilation. Lorsqu’elle est appelée avec des arguments non**constexpr** , ou lorsque sa valeur n’est pas requise au moment de la compilation, elle produit une valeur au moment de l’exécution comme une fonction régulière. (Ce comportement double vous évite d’avoir à écrire des versions **constexpr** et non-**constexpr** de la même fonction.)

Une fonction ou un constructeur **constexpr** est implicitement Inline.

Les règles suivantes s’appliquent aux fonctions constexpr:

- Une fonction **constexpr** doit accepter et retourner uniquement des [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

- Une fonction **constexpr** peut être récursive.

- Elle ne peut pas être [virtuelle](../cpp/virtual-cpp.md). Un constructeur ne peut pas être défini comme constexpr si la classe englobante a des classes de base virtuelles.

- Le corps de la fonction peut être défini avec la valeur `= default` ou `= delete`.

- Le corps ne peut contenir aucune instruction **goto** ni aucun bloc try.

- Une spécialisation explicite d’un modèle non constexpr peut être déclarée comme **constexpr**:

- Une spécialisation explicite d’un modèle **constexpr** n’a pas besoin d’être également **constexpr**:

Les règles suivantes s’appliquent aux fonctions **constexpr** dans Visual Studio 2017 et versions ultérieures:

- Elle peut contenir des instructions **If** et **switch** , et toutes les instructions de bouclage, y compris **for**, for, while et **do-while**.

- Elle peut contenir des déclarations de variables locales, mais la variable doit être initialisée, doit être un type littéral et ne peut pas être static ou un thread local. La variable déclarée localement ne doit pas obligatoirement être const et peut muter.

- Une fonction membre non statique constexpr ne doit pas obligatoirement être const implicitement.

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> Dans le débogueur Visual Studio, lors du débogage d’une version de débogage non optimisée, vous pouvez déterminer si une fonction **constexpr** est évaluée au moment de la compilation en plaçant un point d’arrêt à l’intérieur de celle-ci. Si le point d'arrêt est atteint, la fonction a été appelée à l'exécution.  Sinon, la fonction a été appelée au moment de la compilation.

## <a name="extern-constexpr"></a>constexpr extern

L’option de compilateur [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) fait en sorte que le compilateur applique une [liaison externe](../c-language/external-linkage.md) aux variables déclarées à l’aide de **extern constexpr**. Dans les versions antérieures de Visual Studio, et par défaut, ou si **/Zc: externConstexpr-** est spécifié, Visual Studio applique la liaison interne aux variables **constexpr** même si le mot clé **extern** est utilisé. L’option **/Zc: externConstexpr** est disponible à partir de la mise à jour 15,6 de Visual Studio 2017 et est désactivée par défaut. L’option/permissive-n’active pas **/Zc: externConstexpr**.

## <a name="example"></a>Exemple

L’exemple suivant montre des variables **constexpr** , des fonctions et un type défini par l’utilisateur. Dans la dernière instruction de main (), la fonction membre **Constexpr** GetValue () est un appel au moment de l’exécution, car la valeur n’est pas nécessairement connue au moment de la compilation.

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

## <a name="requirements"></a>Configuration requise

Visual Studio 2015 ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
