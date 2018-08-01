---
title: constexpr (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- constexpr_cpp
dev_langs:
- C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe13dbe61b0a50226f82ae8fb09ab46c922309d1
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406934"
---
# <a name="constexpr-c"></a>constexpr (C++)

Le mot clé **constexpr** a été introduit dans C ++ 11 et amélioré dans C ++ 14. Cela signifie que *expression constante*. Comme **const**, elle peut être appliquée à des variables afin qu’une erreur du compilateur sera déclenchée si n’importe quel code tente de modifier la valeur. Contrairement aux **const**, **constexpr** peut également être appliqué aux fonctions et constructeurs de classe. **constexpr** indique que la valeur ou la valeur de retour est constante et, si possible, sera calculée au moment de la compilation.

Un **constexpr** valeur intégrale peut être utilisée partout où un entier const est requis, comme dans les arguments de modèle et les déclarations de tableau. Et lorsqu’une valeur peut être calculée au moment de la compilation au lieu de l’exécution, il peut aider votre programme s’exécuter plus rapidement et utilisent moins de mémoire.

Pour limiter la complexité du calcul constantes au moment de compilation et leur impact potentiel sur les temps de compilation, la norme C ++ 14 nécessite que les types impliqués dans les expressions constantes soient limitées à [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

```
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);
```

## <a name="parameters"></a>Paramètres

 *params*  
Un ou plusieurs paramètres qui doivent être un type littéral et doivent elle-même être une expression constante.

## <a name="return-value"></a>Valeur de retour

 Une variable ou fonction constexpr doit retourner un [type littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>Variables constexpr

 La principale différence entre les variables const et constexpr est que l'initialisation d'une variable const peut être différée jusqu'à l'exécution, alors qu'une variable constexpr doit être initialisée au moment de la compilation.  Toutes les variables constexpr sont de type const.

- Une variable peut être déclarée avec **constexpr**, si elle a un type de littéral et est initialisé. Si l’initialisation est effectuée par un constructeur, le constructeur doit être déclaré comme **constexpr**.

- Une référence peut être déclarée avec constexpr si l'objet référencé a été initialisé par une expression constante et que toutes les conversions implicites appelées pendant l'initialisation sont aussi des expressions constantes.

- Toutes les déclarations d’un **constexpr** variable ou une fonction doit avoir le **constexpr** spécificateur.

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> fonctions constexpr

Un **constexpr** fonction est un retournée dont la valeur est calculée à la compilation lorsque la consommation du code l’exige.  Quand ses arguments sont **constexpr** valeurs et code de consommation requiert la valeur de retour au moment de la compilation, par exemple, pour initialiser un **constexpr** variable ou fournissez un argument de modèle sans type, il génère une constante de compilation. Lorsqu’elle est appelée avec non -**constexpr** arguments, ou lorsque sa valeur n’est pas obligatoire au moment de la compilation, il génère la valeur en cours d’exécution comme une fonction régulière.  (Ce double comportement vous évite d’avoir à écrire **constexpr** et non-**constexpr** versions de la même fonction.)

Un **constexpr** fonction ou le constructeur est implicitement **inline**.

Les règles suivantes s’appliquent aux fonctions de constexpr :

- Un **constexpr** fonction doit accepter et retourner uniquement [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

- Un **constexpr** fonction peut être récursives.

- Il ne peut pas être [virtuel](../cpp/virtual-cpp.md). A un constructeur ne peut pas être défini en tant que constexpr si la classe englobante contient des classes de base virtuelles.

- Le corps de la fonction peut être défini avec la valeur `= default` ou `= delete`.

- Le corps ne peut pas contenir **goto** instructions ou des blocs try.

- Une spécialisation explicite d’un modèle non constexpr peut être déclarée comme **constexpr**:

- Une spécialisation explicite d’un **constexpr** modèle ne doit pas être également **constexpr**:

Les règles suivantes s’appliquent aux **constexpr** fonctions dans Visual Studio 2017 et versions ultérieures :

- Il peut contenir **si** et **basculer** instructions et toutes les instructions de boucle, y compris **pour**, basé sur une plage, **tandis que**et **faire-tandis que**.
 
- Il peut contenir des déclarations de variables locales, mais la variable doit être initialisée, doit être un type littéral et ne peut pas être statiques ou locales de thread. La variable déclarés localement ne doit pas être const et peut-être se transformer.

- Une fonction de membre non statique constexpr n’est pas obligée être implicitement const.


```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> Remarque : Dans le débogueur Visual Studio, lorsque le débogage non-optimisé déboguez build, vous pouvez indiquer si un **constexpr** fonction est évaluée au moment de la compilation en plaçant un point d’arrêt qu’il contient. Si le point d'arrêt est atteint, la fonction a été appelée à l'exécution.  Sinon, la fonction a été appelée au moment de la compilation.

## <a name="extern-constexpr"></a>extern constexpr

Le [/Zc : externconstexpr](../build/reference/zc-externconstexpr.md) option du compilateur indique au compilateur d’appliquer [une liaison externe]() aux variables déclarées à l’aide de **extern constexpr**. Dans les versions antérieures de Visual Studio et, par défaut ou si **/Zc:externConstexpr-** est spécifié, Visual Studio applique une liaison interne à **constexpr** même si de variables le **extern** mot clé est utilisé. Le **/Zc : externconstexpr** option est disponible à partir de Visual Studio 2017 mise à jour 15.6. et est désactivée par défaut. La /permissive-option n’active pas/Zc : externconstexpr.

## <a name="example"></a>Exemple

 L’exemple suivant **constexpr** variables, fonctions et un type défini par l’utilisateur. Notez que dans la dernière instruction dans main(), la **constexpr** fonction membre GetValue() est un appel de l’exécution, car la valeur n’est pas obligatoire pour être connu au moment de la compilation.

```cpp
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

// Compile time computation of array length
template<typename T, int N>
constexpr int length(const T(&ary)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n*fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue()
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    //foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    //Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    //Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;

}
```

## <a name="requirements"></a>Configuration requise

Visual Studio 2015

## <a name="see-also"></a>Voir aussi
 [Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)  
 [const](../cpp/const-cpp.md)
