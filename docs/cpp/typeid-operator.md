---
description: 'En savoir plus sur : opérateur typeid'
title: typeid, opérateur
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: 8e036cbdcc540eca224b97b09d174362c454da6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145858"
---
# <a name="typeid-operator"></a>typeid, opérateur

## <a name="syntax"></a>Syntaxe

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>Notes

L' **`typeid`** opérateur autorise la détermination du type d’un objet au moment de l’exécution.

Le résultat de **`typeid`** est un `const type_info&` . La valeur est une référence à un `type_info` objet qui représente soit l' *ID de type* , soit le type de l' *expression*, en fonction de la forme de **`typeid`** utilisée. Pour plus d’informations, consultez [Type_info classe](../cpp/type-info-class.md).

L' **`typeid`** opérateur ne fonctionne pas avec les types managés (déclarateurs ou instances Abstract). Pour plus d’informations sur l’obtention du <xref:System.Type> d’un type spécifié, consultez [typeid](../extensions/typeid-cpp-component-extensions.md).

L' **`typeid`** opérateur effectue un contrôle au moment de l’exécution lorsqu’il est appliqué à une l-value d’un type de classe polymorphe, où le type réel de l’objet ne peut pas être déterminé par les informations statiques fournies. Dans les cas suivants par exemple :

- Une référence à une classe

- Pointeur, déréférencé avec `*`

- Pointeur sous-script ( `[ ]` ). (Il n’est pas possible d’utiliser un indice avec un pointeur vers un type polymorphe.)

Si l' *expression* pointe vers un type de classe de base, mais que l’objet est en fait d’un type dérivé de cette classe de base, une `type_info` référence pour la classe dérivée est le résultat. L' *expression* doit pointer vers un type polymorphe (une classe avec des fonctions virtuelles). Dans le cas contraire, le résultat est le `type_info` de la classe statique référencée dans l' *expression*. En outre, le pointeur doit être déréférencé afin que l’objet utilisé soit celui vers lequel il pointe. Sans déréférencer le pointeur, le résultat sera le `type_info` pour le pointeur, pas le point vers lequel il pointe. Par exemple :

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

Si l' *expression* déréférence un pointeur et que la valeur de ce pointeur est égale à zéro, **`typeid`** lève une [exception bad_typeid](../cpp/bad-typeid-exception.md). Si le pointeur ne pointe pas vers un objet valide, une `__non_rtti_object` exception est levée. Elle indique une tentative d’analyse du RTTI qui a déclenché une erreur, car l’objet n’est pas valide. (Par exemple, il s’agit d’un pointeur incorrect, ou le code n’a pas été compilé avec [/GR](../build/reference/gr-enable-run-time-type-information.md)).

Si l' *expression* n’est pas un pointeur, et non une référence à une classe de base de l’objet, le résultat est une `type_info` référence représentant le type statique de l' *expression*. Le *type statique* d’une expression fait référence au type d’une expression telle qu’elle est connue au moment de la compilation. Les sémantiques d'exécution sont ignorées en évaluant le type statique d'une expression. De plus, les références sont ignorées si possible lors de la détermination du type statique d'une expression :

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

**`typeid`** peut également être utilisé dans les modèles pour déterminer le type d’un paramètre de modèle :

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>Voir aussi

[Informations de type au moment de l’exécution](../cpp/run-time-type-information.md)\
[Mots clés](../cpp/keywords-cpp.md)
