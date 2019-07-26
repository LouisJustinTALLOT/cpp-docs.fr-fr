---
title: is_trivially_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: 11aed7fbe2540984d8ed69f88b2a95649e8fee70
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457490"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable, classe

Teste si une valeur de type `From` peut être affectée de façon triviale au type `To`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Paramètres

*À*\
Type de l'objet qui reçoit l'assignation.

*De*\
Type de l'objet qui fournit la valeur.

## <a name="remarks"></a>Notes

L’expression `declval<To>() = declval<From>()` doit être bien formée et le compilateur doit savoir qu’elle ne nécessite aucune opération non triviale. Et doivent être des types complets, void ou des tableaux de limites inconnues.  `From` `To`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
