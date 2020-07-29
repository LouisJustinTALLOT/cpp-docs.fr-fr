---
title: iterator, struct
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: b45cdb5c3d4608296cca34ad6a0be6e25b588d28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222301"
---
# <a name="iterator-struct"></a>iterator, struct

Struct de base vide utilisé pour garantir qu’une classe d’itérateur définie par l’utilisateur fonctionne correctement avec les `iterator_trait` s.

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

Notez que ne `value_type` doit pas être un type de constante même si `pointer` les points d’un objet de **`const`** `Type` et de référence désignent un objet de **`const`** `Type` .

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment déclarer et utiliser les types de la classe de base iterator, consultez [iterator_traits](../standard-library/iterator-traits-struct.md).

## <a name="requirements"></a>Spécifications

**En-tête :**\<iterator>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
