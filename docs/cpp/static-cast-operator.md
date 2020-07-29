---
title: static_cast, opérateur
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 8551d41417647ee4f759e2547e2c1909c59d78cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213201"
---
# <a name="static_cast-operator"></a>static_cast, opérateur

Convertit une *expression* en type *ID de type,* en fonction uniquement des types présents dans l’expression.

## <a name="syntax"></a>Syntaxe

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Notes

Dans C++ standard, aucun contrôle de type à l'exécution n'est fait pour garantir la sécurité de la conversion. Dans C++/CX, il est procédé à un calcul du temps de compilation et à un contrôle à l'exécution. Pour plus d'informations, consultez [Cast](casting.md).

L' **`static_cast`** opérateur peut être utilisé pour des opérations telles que la conversion d’un pointeur vers une classe de base en pointeur vers une classe dérivée. Ces conversions ne sont pas toujours sûres.

En général, vous utilisez **`static_cast`** lorsque vous souhaitez convertir des types de données numériques, tels que des enums en ints ou ints en valeurs float, et que vous êtes certain des types de données impliqués dans la conversion. **`static_cast`** les conversions ne sont pas aussi sûres que les **`dynamic_cast`** conversions, car n' **`static_cast`** effectue aucune vérification de type au moment de l’exécution **`dynamic_cast`** . Un **`dynamic_cast`** vers un pointeur ambigu échoue, tandis **`static_cast`** qu’un retourne comme si rien n’était incorrect ; cela peut être dangereux. Bien que **`dynamic_cast`** les conversions soient plus sûres, **`dynamic_cast`** ne fonctionne que sur des pointeurs ou des références, et la vérification de type au moment de l’exécution est une surcharge. Pour plus d’informations, consultez [Dynamic_cast Operator](../cpp/dynamic-cast-operator.md).

Dans l'exemple qui suit, la ligne `D* pd2 = static_cast<D*>(pb);` n'est pas sécurisée car `D` peut avoir des champs et des méthodes qui ne sont pas dans `B`. Toutefois, la ligne `B* pb2 = static_cast<B*>(pd);` est une conversion sûre car `D` contient toujours tout le `B`.

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

Contrairement à [dynamic_cast](../cpp/dynamic-cast-operator.md), aucun contrôle au moment de l’exécution n’est effectué sur la **`static_cast`** conversion de `pb` . L'objet pointé par `pb` peut ne pas être un objet de type `D`, auquel cas l'utilisation de `*pd2` peut être désastreuse. Par exemple, appeler une fonction membre de la classe `D`, mais pas de la classe `B`, peut entraîner une violation d'accès.

Les **`dynamic_cast`** **`static_cast`** opérateurs et déplacent un pointeur dans une hiérarchie de classes. Toutefois, **`static_cast`** s’appuie exclusivement sur les informations fournies dans l’instruction Cast et peut par conséquent être unsafe. Par exemple :

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

Si `pb` pointe vraiment sur un objet de type `D`, alors `pd1` et `pd2` reçoivent la même valeur. Ils auront également la même valeur si `pb == 0`.

Si `pb` pointe vers un objet de type `B` , et non vers la `D` classe complète, **`dynamic_cast`** est suffisamment connu pour retourner zéro. Toutefois, s' **`static_cast`** appuie sur l’assertion du programmeur qui `pb` pointe vers un objet de type `D` et retourne simplement un pointeur vers cet `D` objet supposé.

Par conséquent, **`static_cast`** peut faire l’inverse des conversions implicites, auquel cas les résultats ne sont pas définis. Il est laissé au programmeur de vérifier que les résultats d’une **`static_cast`** conversion sont sécurisés.

Ce comportement s'applique également aux types autres que les types de classe. Par exemple, **`static_cast`** peut être utilisé pour effectuer une conversion d’un int en un **`char`** . Toutefois, le résultat **`char`** peut ne pas avoir suffisamment de bits pour contenir la **`int`** valeur entière. Là encore, il est laissé au programmeur de vérifier que les résultats d’une **`static_cast`** conversion sont sécurisés.

L' **`static_cast`** opérateur peut également être utilisé pour effectuer toute conversion implicite, y compris les conversions standard et les conversions définies par l’utilisateur. Par exemple :

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

L' **`static_cast`** opérateur peut convertir explicitement une valeur intégrale en un type énumération. Si la valeur du type entier ne fait pas partie de la plage des valeurs d'énumération, la valeur d'énumération résultante n'est pas définie.

L' **`static_cast`** opérateur convertit une valeur de pointeur null en valeur de pointeur null du type de destination.

Toute expression peut être convertie explicitement en type void par l' **`static_cast`** opérateur. Le type void de destination peut éventuellement inclure l' **`const`** **`volatile`** attribut, ou **`__unaligned`** .

L' **`static_cast`** opérateur ne peut pas effectuer un cast des **`const`** **`volatile`** attributs, ou **`__unaligned`** . Pour plus d’informations sur la suppression de ces attributs, consultez [Const_cast Operator](../cpp/const-cast-operator.md) .

**C++/CLI :** En raison du risque d’effectuer des conversions non vérifiées sur un garbage collector de relocalisation, l’utilisation de ne **`static_cast`** doit être que dans le code critique de performances lorsque vous êtes certain qu’il fonctionnera correctement. Si vous devez utiliser **`static_cast`** en mode release, remplacez-le par [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) dans vos versions Debug pour garantir la réussite.

## <a name="see-also"></a>Voir aussi

[Opérateurs de cast](../cpp/casting-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
