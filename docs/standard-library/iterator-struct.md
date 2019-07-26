---
title: iterator, struct
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 64c9be76cb92d818e40714dd141ded3a8cc17c8a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455619"
---
# <a name="iterator-struct"></a>iterator, struct

Struct de base vide utilisé pour garantir qu’une classe d’itérateur définie par l’utilisateur fonctionne `iterator_trait`correctement avec les s.

## <a name="syntax"></a>Syntaxe

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>Notes

Le struct de modèle sert de type de base pour tous les itérateurs. Il définit les types de membres

- `iterator_category` (synonyme du paramètre du modèle `Category`).

- `value_type` (synonyme du paramètre du modèle `Type`).

- `difference_type` (synonyme du paramètre du modèle `Distance`).

- `distance_type` (synonyme du paramètre du modèle `Distance`)

- `pointer` (synonyme du paramètre du modèle `Pointer`).

- `reference` (synonyme du paramètre du modèle `Reference`).

Notez que `value_type` ne doit pas être un type de constante `pointer` même si  `Type` les points d’un objet de const et de référence désignent un objet **const** `Type`.

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment déclarer et utiliser les types de la classe de base iterator, consultez [iterator_traits](../standard-library/iterator-traits-struct.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<iterator>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
