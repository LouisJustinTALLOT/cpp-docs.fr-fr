---
title: is_nothrow_copy_assignable, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e540d6fe4c00772af01b187d24efae18fd62357f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957556"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable, classe

Teste si le type a un opérateur d’assignation de copie qui est connu du compilateur comme ne levant pas d’exception.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*T* type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type contienne la valeur true pour un type référençable *T* où `is_nothrow_assignable<T&, const T&>` contient true ; sinon, sa valeur est false.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable, classe](../standard-library/is-nothrow-assignable-class.md)<br/>
