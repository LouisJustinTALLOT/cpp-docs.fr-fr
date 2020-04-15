---
title: boyer_moore_horspool_searcher classe
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 4d404b414ad632e02be5f4e9fad0e22cefb86ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366778"
---
# <a name="boyer_moore_horspool_searcher-class"></a>boyer_moore_horspool_searcher classe

La `boyer_moore_horspool_searcher` classe est un type d’objet de fonction qui utilise l’algorithme Boyer-Moore-Horspool pour rechercher une séquence spécifiée dans le constructeur de l’objet. La recherche se fait dans une autre séquence fournie à l’opérateur d’appel de fonction de l’objet. Cette classe est transmise comme un paramètre à l’une des surcharges de [std::search](algorithm-functions.md#search).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    class RandomAccessIterator,
    class Hash = hash<typename iterator_traits<RandomAccessIterator>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_horspool_searcher
{
    boyer_moore_horspool_searcher(
        RandomAccessIterator pat_first,
        RandomAccessIterator pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>Membres

| | |
| - | - |
| **Constructeur** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | |
| **Opérateurs** | |
| [opérateur()](#operator-call) | |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a>boyer_moore_horspool_searcher constructeur

Construit un `boyer_moore_horspool_searcher` objet de fonction en utilisant la séquence à rechercher, un objet de fonction de hachage, et une égalité prédicate.

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Paramètres

*pat_first*\
L’élément initial de la séquence à rechercher.

*pat_last*\
La fin de la séquence à rechercher.

*Hf*\
Un objet callable, utilisé pour hachage des éléments de séquence.

*Pred*\
La comparaison facultative de l’égalité est prévue pour les éléments de séquence. Si un type de comparaison d’égalité `std::equal_to`n’est pas spécifié, la valeur par défaut est .

### <a name="remarks"></a>Notes

Jette toute exception jetée par le constructeur de copie de la *BinaryPredicate*, *Hash*, ou *RandomAccessIterator* types, ou l’opérateur d’appel de *BinaryPredicate* ou *Hash*.

Cette classe est nouvelle en C 17.

## <a name="operator"></a><a name="operator-call"></a>opérateur()

L’opérateur d’appel de l’objet de fonction. Recherches dans la `[first, last)` séquence d’argument pour la séquence spécifiée au constructeur.

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Paramètres

*Première*\
L’élément initial de la séquence à rechercher à l’intérieur.

*Dernière*\
La fin de la séquence à rechercher à l’intérieur.

### <a name="remarks"></a>Notes

Si le `[pat_first, pat_last)` modèle de `make_pair(first, first)`recherche est vide, retourne . Si le modèle de recherche `make_pair(last, last)`n’est pas trouvé, retourne . Sinon, renvoie une paire d’itérateurs au `[first, last)` début et à `[pat_first, pat_last)` la fin d’une séquence dans ce qui est égal à selon le *prédicat préd*.

Cette classe est nouvelle en C 17.

## <a name="see-also"></a>Voir aussi

[\<>fonctionnelles](functional.md)\
[fonctions d’algorithme](algorithm-functions.md)\
[boyer_moore_searcher classe](boyer-moore-searcher-class.md)\
[std::recherche](algorithm-functions.md#search)
