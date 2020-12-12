---
description: 'En savoir plus sur : classe value_compare ( &lt; Map &gt; )'
title: value_compare, classe (&lt;map&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: c5b7ba865606e0bc5a5c8238de72824f9061c1b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312811"
---
# <a name="value_compare-class-ltmapgt"></a>value_compare, classe (&lt;map&gt;)

Fournit un objet de fonction qui peut comparer les éléments d'un map en comparant les valeurs de leurs clés pour déterminer leur ordre relatif dans le map.

## <a name="syntax"></a>Syntaxe

```cpp
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```

## <a name="remarks"></a>Notes

Le critère de comparaison fourni par `value_compare` entre les `value_types` éléments entiers contenus dans un mappage est induit à partir d’une comparaison entre les clés des éléments respectifs par la construction de la classe auxiliaire. L’opérateur de fonction membre utilise l’objet `comp` de type `key_compare` stocké dans l’objet de fonction fourni par `value_compare` pour comparer les composants de clé de tri de deux éléments.

Pour les jeux et multijeux, qui sont des conteneurs simples dans lesquels les valeurs de clé sont identiques aux valeurs d’élément, `value_compare` équivaut à `key_compare` ; pour les objets map et multimap, ce n’est pas le cas, car la valeur des éléments `pair` de type n’est pas identique à la valeur de la clé de l’élément.

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [value_comp](../standard-library/map-class.md#value_comp) pour découvrir comment déclarer et utiliser `value_compare`.

## <a name="requirements"></a>Spécifications

**En-tête :**\<map>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Struct binary_function](../standard-library/binary-function-struct.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
