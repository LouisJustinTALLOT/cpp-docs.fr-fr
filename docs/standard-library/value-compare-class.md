---
title: value_compare, classe
ms.date: 11/04/2016
f1_keywords:
- value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: 0e057a6229c903402a51b34a8f4e844e80ace187
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452367"
---
# <a name="valuecompare-class"></a>value_compare, classe

Fournit un objet de fonction qui peut comparer les éléments d’un hash_map en comparant les valeurs de leurs clés pour déterminer leur ordre relatif dans le hash_map.

## <a name="syntax"></a>Syntaxe

```cpp
class value_compare
    : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
        const value_type& left,
        const value_type& right) const
    {
        return (comp(left.first, right.first));
    }

protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>Notes

Les critères de comparaison fournis par value_compare `value_types` entre les éléments entiers contenus par un hash_map sont induits d’une comparaison entre les clés des éléments respectifs par la construction de la classe auxiliaire. L’opérateur de fonction membre utilise l' `comp` objet de `key_compare` type stocké dans l’objet de fonction fourni par value_compare pour comparer les composants de clé de tri de deux éléments.

Pour les objets hash_set et hash_multiset, qui sont des conteneurs simples dans lesquels les valeurs de clé sont identiques aux valeurs d’élément, value_compare équivaut à `key_compare` ; pour les objets hash_map et hash_multimap, ce n’est pas le cas, car la valeur des éléments `pair` de type n’est pas identique à la valeur de la clé de l’élément.

## <a name="example"></a>Exemple

Consultez l’exemple [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) qui illustre comment déclarer et utiliser value_compare.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<hash_map>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[binary_function, struct](../standard-library/binary-function-struct.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
