---
title: classe default_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 3b5b05dfa2613f9eeaaa18fa8066bcd44f57d1be
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203726"
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

| | |
| - | - |
| **Constructeur** | |
| [default_searcher](#default-searcher-constructor) | |
| **Opérateurs** | |
| [, opérateur ()](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>constructeur default_searcher

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

### <a name="remarks"></a>Notes

Lève toute exception levée par le constructeur de copie des types *BinaryPredicate* ou *ForwardIterator* .

Cette classe est nouvelle dans C++ 17. C++ 20 a effectué le constructeur **`constexpr`** .

## <a name="operator"></a><a name="operator-call"></a>, opérateur ()

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

### <a name="remarks"></a>Notes

Retourne une paire d'itérateurs. L’itérateur initial *i* est le résultat effectif de :

`std::search( first, last, pat_first, pat_last, pred )`.

Le deuxième itérateur de la paire est *Last* si *i** est le *dernier*. Dans le cas contraire, il s’agit du résultat effectif de :

`std::next( i, std::distance( pat_first, pat_last ))`.

Cette classe est nouvelle dans C++ 17. C++ 20 a effectué l’opérateur d’appel **`constexpr`** .

## <a name="see-also"></a>Voir aussi

[\<functional>](functional.md)\
[fonctions d’algorithme](algorithm-functions.md)\
[std :: Search](algorithm-functions.md#search)
