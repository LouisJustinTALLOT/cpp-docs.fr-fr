---
title: '&lt;type_traits&gt;, fonctions'
ms.date: 11/04/2016
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: bc25c82629139c5bc2f6fa53d3555068374dca35
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367985"
---
# <a name="lttype_traitsgt-functions"></a>&lt;type_traits&gt;, fonctions

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a><a name="is_assignable"></a>is_assignable

Teste si une valeur de type *De* peut être attribuée à un *type To.*

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Paramètres

*À*\
Type de l'objet qui reçoit l'assignation.

*De*\
Type de l'objet qui fournit la valeur.

### <a name="remarks"></a>Notes

L’expression non évaluée `declval<To>() = declval<From>()` doit être bien formée. De *From* et *vers* doivent être des types complets, **vides,** ou des tableaux de limite inconnue.

## <a name="is_copy_assignable"></a><a name="is_copy_assignable"></a>is_copy_assignable

Teste si le type peut être copié lors de l'assignation.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

### <a name="remarks"></a>Notes

Un exemple du type de prédicat est vrai si le type *Ty* est une classe qui a un opérateur d’affectation de copie, sinon il détient faux. Équivaut à is_assignable\<Ty&, const Ty&>.

## <a name="is_copy_constructible"></a><a name="is_copy_constructible"></a>is_copy_constructible

Teste si le type a un constructeur de copie.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

### <a name="remarks"></a>Notes

Un exemple du type de prédicat est vrai si le type *Ty* est une classe qui a un constructeur de copie, sinon il détient faux.

### <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a><a name="is_default_constructible"></a>is_default_constructible

Teste si un type a un constructeur par défaut.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

### <a name="remarks"></a>Notes

Une instance du type de prédicat est vrai si le type *T* est un type de classe qui a un constructeur par défaut, sinon il est faux. Cela est équivalent au prédicat `is_constructible<T>`. Le type *T* doit être un type complet, **un vide**ou un tableau de limite inconnue.

### <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a><a name="is_move_assignable"></a>is_move_assignable

Teste si le type peut être assigné par déplacement.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

### <a name="remarks"></a>Notes

Un type est assignable par déplacement si une référence rvalue au type peut être assignée à une référence au type. Le prédicat de type équivaut à `is_assignable<T&, T&&>`. Les types assignables par déplacement incluent les types scalaires référençables et les types de classe qui ont des opérateurs d’assignation par déplacement générés par le compilateur ou définis par l’utilisateur.

## <a name="is_move_constructible"></a><a name="is_move_constructible"></a>is_move_constructible

Teste si le type a un constructeur de déplacement.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à évaluer

### <a name="remarks"></a>Notes

Un type prédicat qui évalue à vrai si le type *T* peut être construit en utilisant une opération de déplacement. Ce prédicat équivaut à `is_constructible<T, T&&>`.

## <a name="is_nothrow_move_assignable"></a><a name="is_nothrow_move_assignable"></a>is_nothrow_move_assignable

Teste si le type a un opérateur d’assignation par déplacement **nothrow**.

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

### <a name="remarks"></a>Notes

Un exemple du prédicat de type est vrai si le type *Ty* a un opérateur d’affectation de déménagement nothrow, sinon il détient faux.

## <a name="is_nothrow_swappable"></a><a name="is_nothrow_swappable"></a>is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a><a name="is_nothrow_swappable_with"></a>is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a><a name="is_swappable"></a>is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a><a name="is_swappable_with"></a>is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a><a name="is_trivially_copy_assignable"></a>is_trivially_copy_assignable

Teste si le type a un opérateur d'assignation de copie trivial.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

### <a name="remarks"></a>Notes

Un exemple du type de prédicat est vrai si le type *T* est une classe qui a un opérateur trivial d’affectation de copie, sinon il est faux.

Un constructeur d’affectation pour une classe *T* est trivial si elle est implicitement fournie, la classe *T* n’a pas de fonctions virtuelles, la classe *T* n’a pas de bases virtuelles, les classes de tous les membres de données non statiques de type classe ont des opérateurs d’affectation triviales, et les classes de tous les membres de données non statiques de type éventail de classe ont des opérateurs d’affectation triviales.

## <a name="is_trivially_move_assignable"></a><a name="is_trivially_move_assignable"></a>is_trivially_move_assignable

Teste si le type a un opérateur d'assignation de déplacement trivial.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

### <a name="remarks"></a>Notes

Un exemple du type de prédicat est vrai si le type *Ty* est une classe qui a un opérateur d’affectation de déménagement trivial, sinon il détient faux.

Un opérateur d’affectation de déménagement pour une classe *Ty* est trivial si :

il est fourni implicitement ;

la classe *Ty* n’a pas de fonctions virtuelles

la classe *Ty* n’a pas de bases virtuelles

les classes de tous les membres de données non statiques de type classe possèdent des opérateurs d'assignation de déplacement triviaux ;

les classes de tous les membres de données non statiques de type tableau de classe possèdent des opérateurs d'assignation de déplacement triviaux.

## <a name="is_trivially_move_constructible"></a><a name="is_trivially_move_constructible"></a>is_trivially_move_constructible

Teste si le type a un constructeur de déplacement trivial.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

### <a name="remarks"></a>Notes

Un exemple du type de prédicat est vrai si le type *Ty* est une classe qui a un constructeur de mouvement trivial, sinon il détient faux.

Un constructeur de déménagement pour une classe *Ty* est trivial si:

il est déclaré implicitement ;

ses types de paramètres sont équivalents à ceux d'une déclaration implicite ;

la classe *Ty* n’a pas de fonctions virtuelles

la classe *Ty* n’a pas de bases virtuelles

la classe n'a aucun membre de données non statique volatile ;

toutes les bases directes de la classe *Ty* ont des constructeurs de mouvement trivial

les classes de tous les membres de données non statiques de type de classe ont des constructeurs de déplacement triviaux ;

les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs de déplacement triviaux.

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
