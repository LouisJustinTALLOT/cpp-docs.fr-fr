---
title: is_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: a968efa5a867a3fd0e60594784cdb11122a974b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222405"
---
# <a name="is_constructible-class"></a>is_constructible, classe

Teste si un type est constructible quand les types d’arguments spécifiés sont utilisés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

*Attend*\
Types d’arguments à faire correspondre dans un constructeur de *T*.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est constructible à l’aide des types d’arguments dans *args*. sinon, sa valeur est false. Le type *T* est constructible si la définition de la variable `T t(std::declval<Args>()...);` est bien formée. *T* et tous les types dans *args* doivent tous deux être des types complets, **`void`** , ou des tableaux de limites inconnues.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
