---
title: classe default_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 307fc6da3b383690e0b65bff2a72f386a37d6711
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039688"
---
# <a name="default_searcher-class"></a>Classe default_searcher

Un `default_searcher` est un type d’objet de fonction pour les opérations qui recherchent une séquence spécifiée dans le constructeur de l’objet. La recherche est effectuée dans une autre séquence fournie à l’opérateur d’appel de fonction de l’objet. `default_searcher`Appelle [std :: Search](algorithm-functions.md#search) pour effectuer la recherche.

## <a name="syntax"></a>Syntaxe

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>Membres

| Membre | Description |
| - | - |
| **Constructeur** | |
| [default_searcher](#default-searcher-constructor) | Construit une instance de recherche. |
| **Opérateurs** | |
| [, opérateur ()](#operator-call) | Appelle l’opération sur la séquence. |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a> constructeur default_searcher

Construit un `default_searcher` objet de fonction à l’aide de la séquence à rechercher et d’un prédicat d’égalité.

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Paramètres

*pat_first*\
Élément initial de la séquence à rechercher.

*pat_last*\
Fin de la séquence à rechercher.

*prédit*\
Prédicat de comparaison d’égalité facultatif pour les éléments de séquence. Si un type de comparaison d’égalité n’est pas spécifié, la valeur par défaut est `std::equal_to` .

### <a name="remarks"></a>Remarques

Lève toute exception levée par le constructeur de copie des types *BinaryPredicate* ou *ForwardIterator* .

Cette classe est nouvelle dans C++ 17. C++ 20 a effectué le constructeur **`constexpr`** .

## <a name="operator"></a><a name="operator-call"></a> , opérateur ()

Opérateur d’appel de l’opérateur de fonction. Recherche dans la séquence `[first, last)` d’arguments la séquence spécifiée pour le constructeur.

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Élément initial de la séquence dans laquelle effectuer la recherche.

*famille*\
Fin de la séquence dans laquelle effectuer la recherche.

### <a name="remarks"></a>Remarques

Retourne une paire d'itérateurs. L’itérateur initial *i* est le résultat effectif de :

`std::search( first, last, pat_first, pat_last, pred )`.

Le deuxième itérateur de la paire est *Last* si *i** est le *dernier*. Dans le cas contraire, il s’agit du résultat effectif de :

`std::next( i, std::distance( pat_first, pat_last ))`.

Cette classe est nouvelle dans C++ 17. C++ 20 a effectué l’opérateur d’appel **`constexpr`** .

## <a name="see-also"></a>Voir aussi

[\<functional>](functional.md)\
[fonctions d’algorithme](algorithm-functions.md)\
[std :: Search](algorithm-functions.md#search)
