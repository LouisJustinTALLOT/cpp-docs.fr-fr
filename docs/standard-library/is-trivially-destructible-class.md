---
title: is_trivially_destructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_destructible
helpviewer_keywords:
- is_trivially_destructible
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
ms.openlocfilehash: 6a978b7cc32e6de3d4b1d811b9aa6f52cf0370d7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459638"
---
# <a name="istriviallydestructible-class"></a>is_trivially_destructible, classe

Teste si le type peut être détruit de façon triviale.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_destructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type destructible et que le destructeur est connu du compilateur pour n’utiliser aucune opération non triviale. Sinon, sa valeur est false.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
