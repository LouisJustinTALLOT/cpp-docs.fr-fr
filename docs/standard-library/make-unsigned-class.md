---
title: make_unsigned, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 46b785b20d2ca8ff2de0dfa678b543fa7493aa92
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561750"
---
# <a name="make_unsigned-class"></a>make_unsigned, classe

Rend le type ou le plus petit type non signé supérieur ou égal en taille au type.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance du modificateur de type contient un type modifié qui est *T* si `is_unsigned<T>` contient la valeur true. Dans le cas contraire, il s'agit du plus petit type signé `ST` pour lequel `sizeof (T) <= sizeof (ST)`.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
