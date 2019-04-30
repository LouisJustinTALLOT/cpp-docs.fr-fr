---
title: common_type, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::common_type
helpviewer_keywords:
- common_type class
- common_type
ms.assetid: 02bc4e7b-c63d-49de-9f8a-511d3a5c1e7f
ms.openlocfilehash: f627705109315d3fee84c1777390f00e1e2010ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405116"
---
# <a name="commontype-class"></a>common_type, classe

Détermine le type commun d'un ou plusieurs types.

## <a name="syntax"></a>Syntaxe

```cpp
template <class... T>
struct common_type;

template <class T>
struct common_type<T> {
    typedef typename decay<T>::type type;
};

template <class T, class U>
struct common_type<T, U> {
    typedef typename decay<decltype(true declval<T>() :
    declval<U>())>::type type;
};

template <class T, class U, class... V>
struct common_type<T, U, V...> {
    typedef typename common_type<typename common_type<T, U>::type, V...>::type type;
};
```

### <a name="parameters"></a>Paramètres

Liste des types qui sont des [types complets](../c-language/incomplete-types.md) ou void.

## <a name="remarks"></a>Notes

Le membre `type` est le type commun vers lequel tous les types dans la liste de paramètres peuvent être convertis.

## <a name="example"></a>Exemple

Le programme suivant illustre certains scénarios d'utilisation correcte et teste les résultats.

```cpp
// Compile using cl.exe /EHsc
// common_type sample
#include <iostream>
#include <type_traits>

struct Base {};
struct Derived : Base {};

int main()
{
    typedef std::common_type<unsigned char, short, int>::type NumericType;
    typedef std::common_type<float, double>::type FloatType;
    typedef std::common_type<const int, volatile int>::type ModifiedIntType;
    typedef std::common_type<Base, Derived>::type ClassType;

    std::cout << std::boolalpha;
    std::cout << "Test for typedefs of common_type int" << std::endl;
    std::cout << "NumericType: "     << std::is_same<int, NumericType>::value << std::endl;
    std::cout << "FloatType: "       << std::is_same<int, FloatType>::value << std::endl;
    std::cout << "ModifiedIntType: " << std::is_same<int, ModifiedIntType>::value << std::endl;
    std::cout << "ClassType: "       << std::is_same<int, ClassType>::value << std::endl;
    std::cout << "---------------------------" << std::endl;
    std::cout << "Test for typedefs of common_type double" << std::endl;
    std::cout << "NumericType: "     << std::is_same<double, NumericType>::value << std::endl;
    std::cout << "FloatType: "       << std::is_same<double, FloatType>::value << std::endl;
    std::cout << "ModifiedIntType: " << std::is_same<double, ModifiedIntType>::value << std::endl;
    std::cout << "ClassType: "       << std::is_same<double, ClassType>::value << std::endl;
    std::cout << "---------------------------" << std::endl;
    std::cout << "Test for typedefs of common_type Base" << std::endl;
    std::cout << "NumericType: "     << std::is_same<Base, NumericType>::value << std::endl;
    std::cout << "FloatType: "       << std::is_same<Base, FloatType>::value << std::endl;
    std::cout << "ModifiedIntType: " << std::is_same<Base, ModifiedIntType>::value << std::endl;
    std::cout << "ClassType: "       << std::is_same<Base, ClassType>::value << std::endl;

    return 0;
}
```

## <a name="output"></a>Sortie

```Output
Test for typedefs of common_type int
NumericType: true
FloatType: false
ModifiedIntType: true
ClassType: false
---------------------------
Test for typedefs of common_type double
NumericType: false
FloatType: true
ModifiedIntType: false
ClassType: false
---------------------------
Test for typedefs of common_type Base
NumericType: false
FloatType: false
ModifiedIntType: false
ClassType: true
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
