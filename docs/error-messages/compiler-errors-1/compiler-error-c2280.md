---
description: 'En savoir plus sur : erreur du compilateur C2280'
title: Erreur du compilateur C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: 74ed554006faa20046571971e080e0c0a2054b72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295053"
---
# <a name="compiler-error-c2280"></a>Erreur du compilateur C2280

'*déclaration*' : tentative de référencement d’une fonction supprimée

Le compilateur a détecté une tentative de référencement d’une `deleted` fonction. Cette erreur peut être causée par un appel à une fonction membre qui a été explicitement marquée comme `= deleted` dans le code source. Cette erreur peut également être causée par un appel à une fonction membre spéciale implicite d’un struct ou d’une classe qui est automatiquement déclarée et marquée comme `deleted` par le compilateur. Pour plus d’informations sur le moment où le compilateur génère automatiquement **`default`** ou des `deleted` fonctions membres spéciales, consultez [fonctions membres spéciales](../../cpp/special-member-functions.md).

## <a name="example-explicitly-deleted-functions"></a>Exemple : fonctions supprimées explicitement

Un appel à une `deleted` fonction explicite provoque cette erreur. Une `deleted` fonction membre explicite implique que la classe ou le struct est intentionnellement conçu pour empêcher son utilisation. par conséquent, pour résoudre ce problème, vous devez modifier votre code pour l’éviter.

```cpp
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```

## <a name="example-uninitialized-data-members"></a>Exemple : membres de données non initialisés

Un membre de données ou un membre de données de type référence non initialisé **`const`** fait en sorte que le compilateur déclare implicitement un `deleted` constructeur par défaut. Pour résoudre ce problème, initialisez le membre de données lorsqu’il est déclaré.

```cpp
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```

## <a name="example-reference-and-const-data-members"></a>Exemple : référence et const Data Members

Un **`const`** membre de données de type référence ou fait en sorte que le compilateur déclare un `deleted` opérateur d’assignation de copie. Une fois initialisés, ces membres ne peuvent pas être affectés à, de sorte qu’une copie ou un déplacement simple ne peut pas fonctionner. Pour résoudre ce problème, nous vous recommandons de modifier votre logique pour supprimer les opérations d’assignation qui provoquent l’erreur.

```cpp
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```

## <a name="example-movable-deletes-implicit-copy"></a>Exemple : Removable supprime une copie implicite

Si une classe déclare un constructeur de déplacement ou un opérateur d’assignation de déplacement, mais ne déclare pas explicitement un constructeur de copie, le compilateur déclare implicitement un constructeur de copie et le définit comme `deleted` . De même, si une classe déclare un constructeur de déplacement ou un opérateur d’assignation de déplacement, mais ne déclare pas explicitement un opérateur d’assignation de copie, le compilateur déclare implicitement un opérateur d’assignation de copie et le définit en tant que `deleted` . Pour résoudre ce problème, vous devez déclarer explicitement ces membres.

Quand vous voyez l’erreur C2280 dans la connexion avec un `unique_ptr` , cela est presque certainement dû au fait que vous essayez d’appeler son constructeur de copie, qui est une `deleted` fonction. Par défaut, un `unique_ptr` ne peut pas être copié. Utilisez un constructeur de déplacement pour transférer la propriété à la place.

```cpp
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base
{
public:
    base();
    ~base();
    base(base&&);
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};

void copy(base *p)
{
    base b{*p};  // C2280
}
```

## <a name="example-variant-and-volatile-members"></a>Exemple : des membres variants et volatiles

Les versions du compilateur antérieures à Visual Studio 2015 Update 2 étaient non conformes et générait des constructeurs et des destructeurs par défaut pour les unions anonymes. Ils sont désormais implicitement déclarés comme `deleted` . Ces versions permettaient également une définition implicite non conforme des **`default`** constructeurs de copie et de déplacement, ainsi **`default`** que des opérateurs d’assignation de copie et de déplacement dans les classes et les structures qui ont des **`volatile`** variables membres. Désormais, le compilateur considère qu’ils ont des constructeurs et des opérateurs d’assignation non triviales, et ne génère pas d' **`default`** implémentations. Quand une telle classe est membre d’une Union ou d’une Union anonyme à l’intérieur d’une classe, les constructeurs de copie et de déplacement et les opérateurs d’assignation de copie et de déplacement de l’Union ou de la classe sont implicitement définis comme `deleted` . Pour résoudre ce problème, vous devez déclarer explicitement les fonctions membres spéciales requises.

```cpp
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {
    A() = default;
    A(const A&);
};

struct B {
    union {
        A a;
        int i;
    };
    // To fix this issue, declare the required
    // special member functions:
    // B();
    // B(const B& b);
};

int main() {
    B b1;
    B b2(b1);  // C2280
}
```

## <a name="example-indirect-base-members-deleted"></a>Exemple : membres de base indirects supprimés

Les versions du compilateur antérieures à Visual Studio 2015 Update 2 étaient non conformes et permettaient à une classe dérivée d’appeler des fonctions membres spéciales de classes de base indirectement dérivées `private virtual` . Le compilateur émet désormais une erreur de compilation C2280 quand un tel appel est effectué.

Dans cet exemple, `top` la classe dérive indirectement de la classe virtuelle privée `base` . Dans le code conforme, cela rend les membres `base` inaccessibles à `top` ; un objet de type `top` ne peut pas être construit ou détruit par défaut. Pour résoudre ce problème dans le code qui s’appuyait sur l’ancien comportement du compilateur, modifiez la classe intermédiaire pour utiliser la `protected virtual` dérivation ou modifiez la `top` classe pour qu’elle utilise la dérivation directe :

```cpp
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base
{
protected:
    base();
    ~base();
};

class middle : private virtual base {};
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};

void destroy(top *p)
{
    delete p;  // C2280
}
```
