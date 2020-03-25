---
title: decltype (C++)
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: 1ed07b8987df7b621ea2809409069cc1121fa24f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180210"
---
# <a name="decltype--c"></a>decltype (C++)

Le spécificateur de type **decltype** produit le type d’une expression spécifiée. Le spécificateur de type **decltype** , avec le [mot clé auto](../cpp/auto-cpp.md), est surtout utile pour les développeurs qui écrivent des bibliothèques de modèles. Utilisez **auto** et **decltype** pour déclarer une fonction de modèle dont le type de retour dépend des types de ses arguments template. Vous pouvez également utiliser **auto** et **decltype** pour déclarer une fonction de modèle qui encapsule un appel à une autre fonction, puis retourne le type de retour de la fonction encapsulée.

## <a name="syntax"></a>Syntaxe

```
decltype( expression )
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*expression*|Expression. Pour plus d’informations, consultez [expressions](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Valeur de retour

Type du paramètre d' *expression* .

## <a name="remarks"></a>Notes

Le spécificateur de type **decltype** est pris en charge dans Visual Studio 2010 ou versions ultérieures et peut être utilisé avec du code natif ou managé. `decltype(auto)` (C++14) est pris en charge dans Visual Studio 2015 et versions ultérieures.

Le compilateur utilise les règles suivantes pour déterminer le type du paramètre d' *expression* .

- Si le paramètre d' *expression* est un identificateur ou un [accès à un membre de classe](../cpp/member-access-operators-dot-and.md), `decltype(expression)` est le type de l’entité nommée par *expression*. S’il n’existe aucune entité de ce type ou si le paramètre d' *expression* nomme un ensemble de fonctions surchargées, le compilateur génère un message d’erreur.

- Si le paramètre d' *expression* est un appel à une fonction ou à une fonction d’opérateur surchargée, `decltype(expression)` est le type de retour de la fonction. Les parenthèses autour d'un opérateur surchargé sont ignorées.

- Si le paramètre d' *expression* est une [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` est le type d' *expression*. Si le paramètre d' *expression* est une [lvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` est une [référence lvalue](../cpp/lvalue-reference-declarator-amp.md) au type d' *expression*.

L’exemple de code suivant illustre certaines utilisations du spécificateur de type **decltype** . Tout d'abord, supposez que vous avez codé les instructions suivantes.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

Examinez ensuite les types retournés par les quatre instructions **decltype** dans le tableau suivant.

|.|Type|Notes|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|[Référence rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) à un **entier const**.|
|`decltype(var);`|**int**|Type de la variable `var`.|
|`decltype(a->x);`|**double**|Type de l'accès au membre.|
|`decltype((a->x));`|`const double&`|Les parenthèses internes provoquent l'évaluation de l'instruction en tant qu'expression plutôt qu'en tant qu'accès au membre. Et étant donné que `a` est déclaré comme pointeur `const`, le type est une référence à **const double**.|

## <a name="decltype-and-auto"></a>Decltype et Auto

En C++ 14, vous pouvez utiliser `decltype(auto)` sans type de retour de fin pour déclarer une fonction de modèle dont le type de retour dépend des types de ses arguments template.

En C++ 11, vous pouvez utiliser le spécificateur de type **decltype** sur un type de retour de fin, ainsi que le mot clé **auto** , pour déclarer une fonction de modèle dont le type de retour dépend des types de ses arguments template. Considérez l’exemple de code suivant dans lequel le type de retour de la fonction de modèle dépend des types des arguments template. Dans l’exemple de code, l’espace réservé *Unknown* indique que le type de retour ne peut pas être spécifié.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

L’introduction du spécificateur de type **decltype** permet à un développeur d’obtenir le type de l’expression retournée par la fonction de modèle. Utilisez l' *autre syntaxe de déclaration de fonction* qui est indiquée ultérieurement, le mot clé **auto** et le spécificateur de type **decltype** pour déclarer un type de retour spécifié à la *fin* . Le type de retour spécifié à la fin est déterminé lors de la compilation de la déclaration, plutôt que lors de son codage.

Le prototype suivant illustre la syntaxe d'une autre déclaration de fonction. Notez que les qualificateurs **const** et **volatile** et la spécification de **levée** d' [exception](../cpp/exception-specifications-throw-cpp.md) sont facultatifs. L’espace réservé *function_body* représente une instruction composée qui spécifie ce que fait la fonction. Pour une meilleure pratique de codage, l’espace réservé d' *expression* dans l’instruction **decltype** doit correspondre à l’expression spécifiée par l’instruction **Return** , le cas échéant, dans la *function_body*.

**auto** *function_name* **automatique (** *paramètres*<sub>OPT</sub> **)** **const**<sub>OPT</sub> **volatile**<sub>OPT</sub> **->** **decltype (** *expression* **)** **levez**<sub>OPT</sub> **{** *function_body* **};**

Dans l'exemple de code suivant, le type de retour spécifié à la fin de la fonction de modèle `myFunc` est déterminé par les types des arguments template de `t` et de `u`. Pour une meilleure pratique de codage, l’exemple de code utilise également des références rvalue et le modèle de fonction `forward`, qui prend en charge le *transfert parfait*. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

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

Les fonctions de transfert encapsulent les appels à d'autres fonctions. Considérez un modèle de fonction qui transfère ses arguments, ou les résultats d'une expression qui implique ces arguments, à une autre fonction. En outre, la fonction de transfert retourne le résultat de l'appel à l'autre fonction. Dans ce scénario, le type de retour de la fonction de transfert doit être identique au type de retour de la fonction encapsulée.

Dans ce scénario, vous ne pouvez pas écrire une expression de type appropriée sans le spécificateur de type **decltype** . Le spécificateur de type **decltype** active les fonctions de transfert génériques, car il ne perd pas les informations requises pour déterminer si une fonction retourne un type référence. Pour obtenir un exemple de code d'une fonction de transfert, consultez l'exemple de la fonction de modèle `myFunc` précédent.

## <a name="example"></a>Exemple

L'exemple de code suivant déclare le type de retour spécifié à la fin de la fonction de modèle `Plus()`. La fonction `Plus` traite ses deux opérandes avec l' **opérateur +** surcharge. Par conséquent, l'interprétation de l'opérateur plus (+) et le type de retour de la fonction `Plus` dépend des types des arguments de fonction.

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

**Visual Studio 2017 et versions ultérieures :** Le compilateur analyse les arguments decltype quand les modèles sont déclarés au lieu d’être instanciés. Ainsi, si une spécialisation non dépendante est trouvée dans l’argument decltype, elle n’est pas reportée à l’instanciation et est traitée immédiatement, et toute erreur résultante est diagnostiquée à ce moment-là.

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

## <a name="requirements"></a>Spécifications

Visual Studio 2010 ou versions ultérieures.

`decltype(auto)` nécessite Visual Studio 2015 ou une version ultérieure.
