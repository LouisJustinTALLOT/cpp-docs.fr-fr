---
description: 'En savoir plus sur : classe is_nothrow_copy_assignable'
title: is_nothrow_copy_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: 43618158e33a393012a9f7a4a3ad14c816e3cd6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230807"
---
# <a name="is_nothrow_copy_assignable-class"></a>is_nothrow_copy_assignable, classe

Teste si le type a un opérateur d’assignation de copie qui est connu du compilateur comme ne levant pas d’exception.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true pour un type référencé *T* où `is_nothrow_assignable<T&, const T&>` contient la valeur true ; sinon, sa valeur est false.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Classe is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)
