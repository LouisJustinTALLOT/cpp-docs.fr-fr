---
title: default_searcher classe
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 2c8b93b83b271f787c993f789e1a68f84a60f016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368923"
---
# <a name="default_searcher-class"></a>Classe default_searcher

A `default_searcher` est un type d’objet de fonction pour les opérations qui recherchent une séquence spécifiée dans le constructeur de l’objet. La recherche se fait dans une autre séquence fournie à l’opérateur d’appel de fonction de l’objet. Les `default_searcher` invoque [std::recherche](algorithm-functions.md#search) pour effectuer la recherche.

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
| [opérateur()](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>default_searcher constructeur

Construit un `default_searcher` objet de fonction en utilisant la séquence à rechercher et une égalité prédicate.

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
L’élément initial de la séquence à rechercher.

*pat_last*\
La fin de la séquence à rechercher.

*Pred*\
La comparaison facultative de l’égalité est prévue pour les éléments de séquence. Si un type de comparaison d’égalité `std::equal_to`n’est pas spécifié, la valeur par défaut est .

### <a name="remarks"></a>Notes

Jette toute exception lancée par le constructeur de copie des types *BinaryPredicate* ou *ForwardIterator.*

Cette classe est nouvelle en C 17. C 20 a fait `constexpr`le constructeur .

## <a name="operator"></a><a name="operator-call"></a>opérateur()

L’opérateur d’appel de l’opérateur de fonction. Recherches dans la `[first, last)` séquence d’argument pour la séquence spécifiée au constructeur.

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

*Première*\
L’élément initial de la séquence à rechercher à l’intérieur.

*Dernière*\
La fin de la séquence à rechercher à l’intérieur.

### <a name="remarks"></a>Notes

Retourne une paire d'itérateurs. L’itérateur initial *i* est le résultat effectif de:

`std::search( first, last, pat_first, pat_last, pred )`.

Le deuxième itérateur de la paire est le *dernier* si *je*- est *le dernier*. Sinon, c’est le résultat effectif de:

`std::next( i, std::distance( pat_first, pat_last ))`.

Cette classe est nouvelle en C 17. L’opérateur d’appel a `constexpr`fait C 20.

## <a name="see-also"></a>Voir aussi

[\<>fonctionnelles](functional.md)\
[fonctions d’algorithme](algorithm-functions.md)\
[std::recherche](algorithm-functions.md#search)
