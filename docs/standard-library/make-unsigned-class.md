---
title: make_unsigned, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 42c722c5250a4989b930d8f1e6fe52f2eccc614a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439648"
---
# <a name="makeunsigned-class"></a>make_unsigned, classe

Rend le type ou le plus petit type non signé supérieur ou égal en taille au type.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*T*|Type à modifier.|

## <a name="remarks"></a>Notes

Une instance du modificateur de type conserve un type modifié qui est *T* si `is_unsigned<T>` contienne la valeur true. Dans le cas contraire, il s'agit du plus petit type signé `ST` pour lequel `sizeof (T) <= sizeof (ST)`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
