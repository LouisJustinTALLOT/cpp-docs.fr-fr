---
title: is_destructible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5b2c9237c7f17217d28e489edef4ab65863b54b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964110"
---
# <a name="isdestructible-class"></a>is_destructible, classe

Teste si le type est destructible.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Paramètres

*T* type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type destructible, sinon, sa valeur est false. Les types destructibles sont des types référence, des types d’objets et des types pour lesquels, pour un type `U` égal à `remove_all_extents_t<T>` , l’opérande non évalué `std::declval<U&>.~U()` est bien formé. Autres types, y compris les types incomplets, **void**et les types de fonction, ne sont pas des types destructibles.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
