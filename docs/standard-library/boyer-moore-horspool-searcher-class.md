---
description: 'En savoir plus sur : classe boyer_moore_horspool_searcher'
title: classe boyer_moore_horspool_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 727af034dbb20bd1a0d09ae7de8f88da16a6ba36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325423"
---
# <a name="boyer_moore_horspool_searcher-class"></a>classe boyer_moore_horspool_searcher

La `boyer_moore_horspool_searcher` classe est un type d’objet de fonction qui utilise l’algorithme Boyer-Moore-Horspool pour rechercher une séquence spécifiée dans le constructeur de l’objet. La recherche est effectuée dans une autre séquence fournie à l’opérateur d’appel de fonction de l’objet. Cette classe est passée en tant que paramètre à l’une des surcharges de [std :: Search](algorithm-functions.md#search).

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

| Membre | Description |
| - | - |
| **Constructeur** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | Construit une instance de recherche. |
| **Opérateurs** | |
| [, opérateur ()](#operator-call) | Appelle l’opération sur la séquence. |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a> constructeur boyer_moore_horspool_searcher

Construit un `boyer_moore_horspool_searcher` objet de fonction à l’aide de la séquence à rechercher, d’un objet de fonction de hachage et d’un prédicat d’égalité.

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Paramètres

*pat_first*\
Élément initial de la séquence à rechercher.

*pat_last*\
Fin de la séquence à rechercher.

*haute*\
Objet pouvant être appelé, utilisé pour hacher les éléments de séquence.

*prédit*\
Prédicat de comparaison d’égalité facultatif pour les éléments de séquence. Si un type de comparaison d’égalité n’est pas spécifié, la valeur par défaut est `std::equal_to` .

### <a name="remarks"></a>Notes

Lève toute exception levée par le constructeur de copie des types *BinaryPredicate*, *hash* ou *RandomAccessIterator* , ou l’opérateur d’appel de *BinaryPredicate* ou *hash*.

Cette classe est nouvelle dans C++ 17.

## <a name="operator"></a><a name="operator-call"></a> , opérateur ()

Opérateur d’appel de l’objet de fonction. Recherche dans la séquence `[first, last)` d’arguments la séquence spécifiée pour le constructeur.

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Élément initial de la séquence dans laquelle effectuer la recherche.

*famille*\
Fin de la séquence dans laquelle effectuer la recherche.

### <a name="remarks"></a>Notes

Si le modèle de recherche `[pat_first, pat_last)` est vide, retourne `make_pair(first, first)` . Si le modèle de recherche est introuvable, retourne `make_pair(last, last)` . Sinon, retourne une paire d’itérateurs au début et à la fin d’une séquence dans `[first, last)` qui est égal à `[pat_first, pat_last)` conformément au prédicat *prédit*.

Cette classe est nouvelle dans C++ 17.

## <a name="see-also"></a>Voir aussi

[\<functional>](functional.md)\
[fonctions d’algorithme](algorithm-functions.md)\
[classe boyer_moore_searcher](boyer-moore-searcher-class.md)\
[std :: Search](algorithm-functions.md#search)
