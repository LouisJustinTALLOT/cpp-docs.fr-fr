---
title: make_signed, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_signed
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
ms.openlocfilehash: c3c35e28dec3270299329c0186273e324effc2bb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453683"
---
# <a name="makesigned-class"></a>make_signed, classe

Rend le type ou le plus petit type signé supérieur ou égal en taille au type.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance du modificateur de type contient un type modifié qui est *T* si `is_signed<T>` contient la valeur true. Dans le cas contraire, il s'agit du plus petit type non signé `UT` pour lequel `sizeof (T) <= sizeof (UT)`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
