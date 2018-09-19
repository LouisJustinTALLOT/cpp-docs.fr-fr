---
title: decltype (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- decltype_cpp
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c6cab68cd351c64d65eeed1eeffda7bf49385aa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074004"
---
# <a name="decltype--c"></a>decltype (C++)

Le **decltype** spécificateur de type génère le type d’une expression spécifiée. Le **decltype** spécificateur, de type avec le [auto, mot clé](../cpp/auto-cpp.md), est particulièrement utile pour les développeurs qui écrivent des bibliothèques de modèles. Utilisez **automatique** et **decltype** pour déclarer une fonction de modèle dont retour type dépend des types de ses arguments template. Ou, utilisez **automatique** et **decltype** pour déclarer une fonction de modèle qui encapsule un appel à une autre fonction, puis retourne le type de retour de la fonction encapsulée.

## <a name="syntax"></a>Syntaxe

```
decltype( expression )
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Expression*|d'une expression. Pour plus d’informations, consultez [Expressions](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Valeur de retour

Le type de la *expression* paramètre.

## <a name="remarks"></a>Notes

Le **decltype** spécificateur de type est pris en charge dans Visual C++ 2010 ou versions ultérieures et peut être utilisé avec le code natif ou managé. `decltype(auto)` (C++14) est pris en charge dans Visual Studio 2015 et versions ultérieures.

Le compilateur utilise les règles suivantes pour déterminer le type de la *expression* paramètre.

- Si le *expression* paramètre est un identificateur ou un [accès aux membres de classe](../cpp/member-access-operators-dot-and.md), `decltype(expression)` est le type de l’entité nommée par *expression*. S’il n’existe aucune entité n’ou *expression* paramètre nomme un ensemble de fonctions surchargées, le compilateur génère un message d’erreur.

- Si le *expression* paramètre est un appel à une fonction ou une fonction d’opérateur surchargées, `decltype(expression)` est le type de retour de la fonction. Les parenthèses autour d'un opérateur surchargé sont ignorées.

- Si le *expression* paramètre est un [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` est le type de *expression*. Si le *expression* paramètre est un [lvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` est un [référence lvalue](../cpp/lvalue-reference-declarator-amp.md) au type de *expression*.

L’exemple de code suivant montre certaines utilisations de la **decltype** spécificateur de type. Tout d'abord, supposez que vous avez codé les instructions suivantes.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

Ensuite, examinez les types retournés par les quatre **decltype** instructions dans le tableau suivant.

|Instruction|Type|Notes|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|Un [référence rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) à un **const int**.|
|`decltype(var);`|**int**|Type de la variable `var`.|
|`decltype(a->x);`|**double**|Type de l'accès au membre.|
|`decltype((a->x));`|`const double&`|Les parenthèses internes provoquent l'évaluation de l'instruction en tant qu'expression plutôt qu'en tant qu'accès au membre. Et parce que `a` est déclaré comme un `const` pointeur, le type est une référence à **double const**.|

## <a name="decltype-and-auto"></a>Decltype et Auto

Dans C ++ 14, vous pouvez utiliser `decltype(auto)` avec aucun type de retour de fin pour déclarer une fonction de modèle dont le type de retour dépend des types de ses arguments template.

Dans C ++ 11, vous pouvez utiliser la **decltype** tapez spécificateur sur un type de retour de fin, conjointement avec le **automatique** mot clé, pour déclarer une fonction de modèle dont le type de retour dépend des types de son modèle arguments. Considérez l’exemple de code suivant dans lequel le type de retour de la fonction de modèle dépend des types des arguments template. Dans l’exemple de code, le *inconnu* espace réservé indique que le type de retour ne peut pas être spécifié.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

L’introduction de la **decltype** spécificateur de type permet à un développeur obtenir le type de l’expression retournée par la fonction de modèle. Utilisez le *syntaxe de déclaration de fonction autre* qui est présenté plus loin, le **automatique** mot clé et le **decltype** spécificateur pour déclarer de type un  *spécifié à la fin* type de retour. Le type de retour spécifié à la fin est déterminé lors de la compilation de la déclaration, plutôt que lors de son codage.

Le prototype suivant illustre la syntaxe d'une autre déclaration de fonction. Notez que le **const** et **volatile** qualificateurs et le **lever** [spécification d’exception](../cpp/exception-specifications-throw-cpp.md) sont facultatifs. Le *function_body* espace réservé représente une instruction composée qui spécifie ce que fait la fonction. En matière de codage pratique, le *expression* espace réservé dans le **decltype** instruction doit correspondre à l’expression spécifiée par le **retourner** instruction, le cas échéant, dans le *function_body*.

**Auto** *function_name* **(** *paramètres*<sub>opt</sub> **)**  **const**<sub>opt</sub> **volatile**<sub>opt</sub> **->** **decltype (** *expression* **)** **lever**<sub>opt</sub> **{** *function_body* **};**

Dans l'exemple de code suivant, le type de retour spécifié à la fin de la fonction de modèle `myFunc` est déterminé par les types des arguments template de `t` et de `u`. Comme une meilleure pratique de programmation, l’exemple de code utilise également les références rvalue et les `forward` modèle de fonction, qui prennent en charge *un transfert parfait*. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>Decltype et fonctions de transfert (C++11)

Les fonctions de transfert encapsulent les appels à d'autres fonctions. Considérez un modèle de fonction qui transfère ses arguments, ou les résultats d’une expression qui implique ces arguments, à une autre fonction. En outre, la fonction de transfert retourne le résultat de l'appel à l'autre fonction. Dans ce scénario, le type de retour de la fonction de transfert doit être identique au type de retour de la fonction encapsulée.

Dans ce scénario, vous ne pouvez pas écrire une expression de type approprié sans le **decltype** spécificateur de type. Le **decltype** spécificateur de type permet des fonctions génériques de transfert, car il ne perd pas les informations requises si une fonction retourne un type référence. Pour obtenir un exemple de code d'une fonction de transfert, consultez l'exemple de la fonction de modèle `myFunc` précédent.

## <a name="example"></a>Exemple

L'exemple de code suivant déclare le type de retour spécifié à la fin de la fonction de modèle `Plus()`. Le `Plus` fonction traite ses deux opérandes avec le **opérateur +** de surcharge. Par conséquent, l'interprétation de l'opérateur plus (+) et le type de retour de la fonction `Plus` dépend des types des arguments de fonction.

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

## <a name="example"></a>Exemple

**Visual Studio 2017 et versions ultérieur :** le compilateur analyse les arguments decltype quand les modèles sont déclarés et non instanciés. Ainsi, si une spécialisation non dépendante est trouvée dans l’argument decltype, elle n’est pas reportée à l’instanciation et est traitée immédiatement, et toute erreur résultante est diagnostiquée à ce moment-là.

L’exemple suivant montre une erreur de compilateur de ce type générée au moment de la déclaration :

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>Configuration requise

Visual C++ 2010 ou versions ultérieures.

`decltype(auto)` nécessite Visual Studio 2015 ou version ultérieure.