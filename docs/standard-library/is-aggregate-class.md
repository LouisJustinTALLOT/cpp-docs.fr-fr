---
description: 'En savoir plus sur : classe is_aggregate'
title: Classe is_aggregate
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 6ca27e6edea42b6c0ae3f0c89749a586adac857b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231366"
---
# <a name="is_aggregate-class"></a>Classe is_aggregate

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

Une instance du prédicat de type a la valeur true si le type *T* est un type de classe marqué `aggregate` ; sinon, sa valeur est false. Si *T* est un type de classe, il doit s’agir d’un type complet.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
