---
title: is_standard_layout, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: fba77be22796f3cb5495543d262dd270ac13d598
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560593"
---
# <a name="is_standard_layout-class"></a>is_standard_layout, classe

Teste si le type est une disposition standard.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger

## <a name="remarks"></a>Notes

Une instance de ce prédicat de type a la valeur true si le type *Ty* est une classe qui a une disposition standard d’objets membres en mémoire. sinon, sa valeur est false.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
