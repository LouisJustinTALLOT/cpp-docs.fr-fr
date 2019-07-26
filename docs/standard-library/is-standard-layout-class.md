---
title: is_standard_layout, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: 4f999eaa4a5c1ea7e9672a5efdc6000a4d3d9759
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457412"
---
# <a name="isstandardlayout-class"></a>is_standard_layout, classe

Teste si le type est une disposition standard.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Ty*|Type à interroger|

## <a name="remarks"></a>Notes

Une instance de ce prédicat de type a la valeur true si le type *Ty* est une classe qui a une disposition standard d’objets membres en mémoire. sinon, sa valeur est false.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
