---
description: 'En savoir plus sur : classe tuple_size ;'
title: tuple_size, classe ;
ms.date: 11/04/2016
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
helpviewer_keywords:
- std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
ms.openlocfilehash: e825acc02e27a8d0c1ae29e5bfcf4ac1e0a708b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168876"
---
# <a name="tuple_size-class"></a>tuple_size, classe ;

Indique le nombre d’éléments qu’un `tuple` contient.

## <a name="syntax"></a>Syntaxe

```cpp
// TEMPLATE STRUCT tuple_size
template <class Tuple>
   struct tuple_size;

// number of elements in array
template <class Elem, size_t Size>
   struct tuple_size<array<Elem, Size>>
      : integral_constant<size_t, Size>;

// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>>
      : integral_constant<size_t, 2>

// size of tuple
template <class... Types>
   struct tuple_size<tuple<Types...>>
      : integral_constant<size_t, sizeof...(Types)>;

// size of const tuple
template <class Tuple>
   struct tuple_size<const Tuple>;

// size of volatile tuple
template <class Tuple>
   struct tuple_size<volatile Tuple>;

// size of const volatile tuple
template <class Tuple>
   struct tuple_size<const volatile Tuple>;
```

```cpp
template <class T> inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```

### <a name="parameters"></a>Paramètres

*Passent*\
Type du tuple.

*Elem*\
Type des éléments du tableau.

*Taille*\
Taille du tableau.

*T1*\
Type du premier membre de la paire.

*H2*\
Type du second membre de la paire.

*Modes*\
Types des éléments de tuple.

## <a name="remarks"></a>Notes

Le modèle de classe a un membre `value` qui est une expression constante intégrale dont la valeur est l’étendue du *Tuple* de type de Tuple.

La spécialisation de modèle pour les tableaux a un membre `value` qui est une expression constante intégrale dont la valeur est *taille*, qui est la taille du tableau.

La spécialisation de modèle pour une paire possède un membre `value` qui est une expression constante intégrale dont la valeur est 2.

## <a name="example"></a>Exemple

```cpp
#include <tuple>
#include <iostream>

using namespace std;

typedef tuple<int, double, int, double> MyTuple;
int main()
{
    MyTuple c0(0, 1.5, 2, 3.7);

    // display contents "0 1 2 3"
    cout << get<0>(c0);
    cout << " " << get<1>(c0);
    cout << " " << get<2>(c0);
    cout << " " << get<3>(c0) << endl;

    // display size "4"
    cout << " " << tuple_size<MyTuple>::value << endl;
}
```

```Output
0 1.5 2 3.7
4
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<tuple>

**En-tête :** \<array> (pour la spécialisation de tableau)

**En-tête :** \<utility> (pour la spécialisation des paires)

**Espace de noms :** std
