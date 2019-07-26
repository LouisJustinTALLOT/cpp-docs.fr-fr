---
title: unchecked_array_iterator, classe
ms.date: 11/04/2016
f1_keywords:
- stdext::unchecked_array_iterator
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
ms.openlocfilehash: 5344a108f32b694b9dafac78dbb8eb7064cdf4cc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455005"
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator, classe

La classe `unchecked_array_iterator` vous permet d'encapsuler un tableau ou un pointeur dans un itérateur non vérifié. Utilisez cette classe comme wrapper (à l’aide de la fonction [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)) pour les tableaux ou pointeurs bruts en tant que moyen ciblé de gérer les avertissements de pointeur non vérifiés au lieu de désactiver globalement ces avertissements. Si possible, préférez la version vérifiée de cette classe, [checked_array_iterator](../standard-library/checked-array-iterator-class.md).

> [!NOTE]
> Cette classe est une extension Microsoft de la bibliothèque standard C++. Le code implémenté à l’aide de cette fonction ne peut pas être utilisé dans les environnements de build C++ standard qui ne prennent pas en charge cette extension Microsoft.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Iterator>
class unchecked_array_iterator;
```

## <a name="remarks"></a>Notes

Cette classe est définie dans l’espace de noms [stdext](../standard-library/stdext-namespace.md).

Il s’agit de la version non vérifiée de la [classe checked_array_iterator](../standard-library/checked-array-iterator-class.md) qui prend en charge les mêmes surcharges et les mêmes membres. Pour plus d’informations sur la fonctionnalité d’itérateur vérifié et obtenir des exemples de code, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<iterator>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
