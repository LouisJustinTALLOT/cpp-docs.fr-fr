---
title: value_compare, classe (&lt;map&gt;) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: effa754f50f8c092cef727969a0f4036e765f888
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856044"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare, classe (&lt;map&gt;)

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

Le critère de comparaison fourni par `value_compare` entre des **value_types** d’éléments entiers contenus par un objet map est induit à partir d’une comparaison entre les clés des éléments respectifs par la construction de classe auxiliaire. L’opérateur de fonction membre utilise l’objet **comp** de type `key_compare` stocké dans l’objet de fonction fourni par `value_compare` pour comparer les composants de clé de tri de deux éléments.

Pour les jeux et multijeux, qui sont des conteneurs simples dans lesquels les valeurs de clé sont identiques aux valeurs d’élément, `value_compare` équivaut à `key_compare` ; pour les objets map et multimap, ce n’est pas le cas, car la valeur des éléments `pair` de type n’est pas identique à la valeur de la clé de l’élément.

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [value_comp](../standard-library/map-class.md#value_comp) qui illustre comment déclarer et utiliser `value_compare`.

## <a name="requirements"></a>Spécifications

**En-tête :** \<map>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[binary_function, struct](../standard-library/binary-function-struct.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
