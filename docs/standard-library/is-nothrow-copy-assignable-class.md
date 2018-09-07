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
ms.openlocfilehash: 90b63179156b1bd3d9f2dc1594f51bfa10586522
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102167"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable, classe

Teste si le type a un opérateur d’assignation de copie qui est connu du compilateur comme ne levant pas d’exception.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type contienne la valeur true pour un type référençable *T* où `is_nothrow_assignable<T&, const T&>` contient true ; sinon, sa valeur est false.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable, classe](../standard-library/is-nothrow-assignable-class.md)<br/>
