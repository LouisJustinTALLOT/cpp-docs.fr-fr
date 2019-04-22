---
title: static_cast, opérateur
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: dca6d5297379e6ddc1c70dba80f35f2f55672e49
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776919"
---
# <a name="staticcast-operator"></a>static_cast, opérateur

Convertit un *expression* au type de *id de type,* basés uniquement sur les types qui sont présents dans l’expression.

## <a name="syntax"></a>Syntaxe

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Notes

Dans C++ standard, aucun contrôle de type à l'exécution n'est fait pour garantir la sécurité de la conversion. Dans C++/CX, il est procédé à un calcul du temps de compilation et à un contrôle à l'exécution. Pour plus d'informations, consultez [Cast](casting.md).

Le **static_cast** opérateur peut être utilisé pour les opérations telles que la conversion d’un pointeur vers une classe de base en pointeur vers une classe dérivée. Ces conversions ne sont pas toujours sûres.

En règle générale, vous utilisez **static_cast** lorsque vous souhaitez convertir des types de données numériques tels qu’enums en ints ou ints en floats et vous certains des types de données impliqués dans la conversion. **static_cast** conversions ne sont pas aussi sûres que **dynamic_cast** conversions, étant donné que **static_cast** aucun type d’exécution ne vérifie, tandis que **dynamic_cast** fait. Un **dynamic_cast** vers un pointeur ambigu échoue, tandis qu’un **static_cast** retourne comme si rien n’était erroné ; cela peut s’avérer dangereux. Bien que **dynamic_cast** conversions soient plus sûres, **dynamic_cast** seule fonctionne sur les pointeurs ou références et la vérification de type au moment de l’exécution est une surcharge. Pour plus d’informations, consultez [opérateur dynamic_cast](../cpp/dynamic-cast-operator.md).

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

Contrairement à [dynamic_cast](../cpp/dynamic-cast-operator.md), aucune vérification de l’exécution est effectuée sur le **static_cast** conversion de `pb`. L'objet pointé par `pb` peut ne pas être un objet de type `D`, auquel cas l'utilisation de `*pd2` peut être désastreuse. Par exemple, appeler une fonction membre de la classe `D`, mais pas de la classe `B`, peut entraîner une violation d'accès.

Le **dynamic_cast** et **static_cast** opérateurs déplacent un pointeur à travers une hiérarchie de classes. Toutefois, **static_cast** s’appuie exclusivement sur les informations fournies dans l’instruction cast et peut donc être potentiellement dangereux. Exemple :

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

Si `pb` pointe vers un objet de type `B` et non sur la `D` de classe, puis **dynamic_cast** connaîtra suffisamment pour retourner zéro. Toutefois, **static_cast** s’appuie sur l’assertion du programmeur qui `pb` pointe vers un objet de type `D` et renvoie simplement un pointeur à supposés `D` objet.

Par conséquent, **static_cast** peut faire l’inverse de conversions implicites, auquel cas les résultats sont indéfinis. Il est laissé au programmeur pour vérifier que les résultats d’une **static_cast** conversion sont sécurisés.

Ce comportement s'applique également aux types autres que les types de classe. Par exemple, **static_cast** peut être utilisée pour convertir un entier en un **char**. Toutefois, le résultat **char** ne peut pas avoir suffisamment de bits pour conserver toute la **int** valeur. Là encore, il est laissé au programmeur pour vérifier que les résultats d’une **static_cast** conversion sont sécurisés.

Le **static_cast** opérateur peut également être utilisé pour effectuer une conversion implicite, y compris les conversions standard et les conversions définies par l’utilisateur. Exemple :

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

Le **static_cast** opérateur peut convertir explicitement une valeur intégrale à un type d’énumération. Si la valeur du type entier ne fait pas partie de la plage des valeurs d'énumération, la valeur d'énumération résultante n'est pas définie.

Le **static_cast** opérateur convertit une valeur de pointeur null à la valeur de pointeur null du type de destination.

Toute expression peut être explicitement convertie en type vide par le **static_cast** opérateur. Le type void destination peut éventuellement inclure le **const**, **volatile**, ou **__unaligned** attribut.

Le **static_cast** opérateur ne peut pas caster le **const**, **volatile**, ou **__unaligned** attributs. Consultez [const_cast, opérateur](../cpp/const-cast-operator.md) pour plus d’informations sur la suppression de ces attributs.

**C++ / C++ / CLI :** En raison du risque d’effectuer des casts non contrôlés sur le haut du déplacement du garbage collector, l’utilisation de **static_cast** doit être uniquement dans le code critique de performances lorsque vous êtes certain qu’il fonctionne correctement. Si vous devez utiliser **static_cast** en mode de version, substituez-le avec [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) dans vos versions debug pour garantir la réussite.

## <a name="see-also"></a>Voir aussi

[Opérateurs de casting](../cpp/casting-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)