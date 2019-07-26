---
title: is_aggregate, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 89749e2b4c0e6aaf00de074718cfb598333bc739
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456691"
---
# <a name="isaggregate-class"></a>is_aggregate, classe

Teste si le type est un type de classe marqué `aggregate`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_aggregate;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type de `aggregate`classe marqué; sinon, sa valeur est false. Si *T* est un type de classe, il doit s’agir d’un type complet.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
