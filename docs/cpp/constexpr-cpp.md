---
title: constexpr (C++) | Documents Microsoft
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
ms.openlocfilehash: 1f95f6c98138ff1eb52750c1b8593795ca28c784
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417995"
---
# <a name="constexpr-c"></a>constexpr (C++)

Le mot clé **constexpr** a été introduit dans C ++ 11 et amélioré dans C ++ 14. Cela signifie que *expression constante*. Comme **const**, il peut être appliqué aux variables afin qu’une erreur du compilateur sera déclenchée si n’importe quel code tente de modifier la valeur. Contrairement aux **const**, **constexpr** peut également être appliqué aux fonctions et les constructeurs de classe. **constexpr** indique que la valeur ou la valeur de retour est constante et, si possible, sera calculée au moment de la compilation.

A **constexpr** valeur intégrale peut être utilisée partout où un entier const est requis, comme dans les arguments de modèle et les déclarations de tableau. Et, lorsqu’une valeur peut être calculée au moment de la compilation au lieu de l’exécution, il peut aider votre programme de s’exécuter plus rapidement et utilisent moins de mémoire.

Pour limiter la complexité des constantes au moment de compilation informatique et leur impact potentiel sur la durée de compilation, la norme C ++ 14 nécessite que les types impliqués dans les expressions constantes être limité à [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntaxe

```
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);
```

## <a name="parameters"></a>Paramètres

 *params*  
Un ou plusieurs paramètres qui doivent être un type de littéral et doivent elle-même être une expression constante.

## <a name="return-value"></a>Valeur de retour


 Une variable ou fonction constexpr doit retourner un [type de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>Variables constexpr

 La principale différence entre les variables const et constexpr est que l'initialisation d'une variable const peut être différée jusqu'à l'exécution, alors qu'une variable constexpr doit être initialisée au moment de la compilation.  Toutes les variables constexpr sont de type const.

- Une variable peut être déclarée avec **constexpr**, si elle a un type de littéral et est initialisé. Si l’initialisation est effectuée par un constructeur, le constructeur doit être déclaré en tant que **constexpr**.

- Une référence peut être déclarée avec constexpr si l'objet référencé a été initialisé par une expression constante et que toutes les conversions implicites appelées pendant l'initialisation sont aussi des expressions constantes.

- Toutes les déclarations d’une **constexpr** variable ou une fonction doit avoir le **constexpr** spécificateur.

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> fonctions constexpr

A **constexpr** fonction est un dont la valeur de retournée peut être calculée à la compilation lorsque la consommation du code l’exige.  Quand ses arguments sont **constexpr** valeurs et le code de consommation requiert la valeur de retour au moment de la compilation, notamment initialiser un **constexpr** variable ou fournir un argument de modèle sans type, il génère une constante au moment de la compilation. Lorsqu’elle est appelée avec non -**constexpr** arguments, ou lorsque sa valeur n’est pas requise au moment de la compilation, elle génère une valeur au moment de l’exécution comme une fonction régulière.  (Ce double comportement vous évite d’avoir à écrire **constexpr** et non-**constexpr** versions de la même fonction.)

A **constexpr** fonction ou le constructeur est implicitement **inline**.

Les règles suivantes s’appliquent aux fonctions constexpr :

- A **constexpr** fonction doit accepter et retourner uniquement [types de littéral](trivial-standard-layout-and-pod-types.md#literal_types).

- A **constexpr** fonction peut être récursives.

- Il ne peut pas être [virtuels](../cpp/virtual-cpp.md). A un constructeur ne peut pas être défini en tant que constexpr si la classe englobante contient toutes les classes de base virtuelles.

- Le corps peut être défini en tant que **= valeur par défaut** ou **= suppression**.

- Le corps ne peut pas contenir **goto** instructions ou des blocs try.

- Une spécialisation explicite d’un modèle non constexpr peut être déclarée comme **constexpr**:

- Une spécialisation explicite d’un **constexpr** modèle ne possède pas également être **constexpr**:

Les règles suivantes s’appliquent aux **constexpr** fonctions dans Visual Studio 2017 et versions ultérieures :

- Il peut contenir **si** et **commutateur** instructions et toutes les instructions de boucles, y compris **pour**, en fonction de plage, **tandis que**et **faire-tandis que**.
 
- Il peut contenir les déclarations de variable locale, mais la variable doit être initialisée, doit être un type littéral et ne peut pas être statique ou de thread local. La variable locale déclarée n’est pas requis pour être const et peut-être se transformer en.

- Une fonction membre non static de constexpr n’est pas requis pour être implicitement const.


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

Le [/Zc:externConstexpr](../build/reference/zc-externconstexpr.md) option du compilateur, le compilateur applique [une liaison externe]() aux variables déclarées à l’aide de **extern constexpr**. Dans les versions antérieures de Visual Studio et, par défaut ou si **/Zc:externConstexpr-** est spécifié, Visual Studio applique une liaison interne à **constexpr** même si de variables du **extern** mot clé est utilisé. Le **/Zc:externConstexpr** option est disponible à partir de 15,6 de mise à jour de Visual Studio 2017. et est désactivée par défaut. La /permissive-option n’active pas /Zc:externConstexpr.

## <a name="example"></a>Exemple

 L’exemple suivant **constexpr** variables, fonctions et un type défini par l’utilisateur. Notez que dans la dernière instruction dans main(), la **constexpr** la fonction de membre GetValue() est un appel d’exécution, car la valeur n’est pas nécessaire pour être connue au moment de la compilation.

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

## <a name="requirements"></a>Spécifications

Visual Studio 2015

## <a name="see-also"></a>Voir aussi

- [Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)
- [const](../cpp/const-cpp.md)
