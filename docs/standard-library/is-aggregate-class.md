---
title: is_aggregate, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 7d979d4e4019ada12b72fb563c0b969fffe2c12d
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268981"
---
# <a name="isaggregate-class"></a>is_aggregate, classe

Teste si le type est un type de classe marqué `aggregate`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_aggregate;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type de classe marqué `aggregate`, sinon, sa valeur est false. Si *T* est un type de classe, il doit être un type complet.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
