---
description: 'En savoir plus sur : classe make_signed'
title: make_signed, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_signed
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
ms.openlocfilehash: 2f11fe3223e6193613772d2c4abbf0182215a17d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277555"
---
# <a name="make_signed-class"></a>make_signed, classe

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

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
