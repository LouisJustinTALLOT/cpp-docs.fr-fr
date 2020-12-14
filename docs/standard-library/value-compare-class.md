---
description: 'En savoir plus sur : classe value_compare'
title: value_compare, classe
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: d77412b2d979ef4db84621df1b0c94191f3d2a5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211711"
---
# <a name="value_compare-class"></a>value_compare, classe

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

Les critères de comparaison fournis par value_compare entre les `value_types` éléments entiers contenus dans une hash_map sont induits par la comparaison entre les clés des éléments respectifs et la construction de la classe auxiliaire. L’opérateur de fonction membre utilise l’objet `comp` de type `key_compare` stocké dans l’objet de fonction fourni par value_compare pour comparer les composants de clé de tri de deux éléments.

Pour les objets hash_set et hash_multiset, qui sont des conteneurs simples dans lesquels les valeurs de clé sont identiques aux valeurs d’élément, value_compare équivaut à `key_compare` ; pour les objets hash_map et hash_multimap, ce n’est pas le cas, car la valeur des éléments `pair` de type n’est pas identique à la valeur de la clé de l’élément.

## <a name="example"></a>Exemple

Consultez l’exemple [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) qui illustre comment déclarer et utiliser value_compare.

## <a name="requirements"></a>Spécifications

**En-tête :**\<hash_map>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[Struct binary_function](../standard-library/binary-function-struct.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
