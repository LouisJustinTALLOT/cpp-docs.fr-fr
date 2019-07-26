---
title: is_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: dc0596ac7a3fc2bcbcbe49f5fa4b20a971e5e445
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452860"
---
# <a name="isconstructible-class"></a>is_constructible, classe

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

Une instance du prédicat de type a la valeur true si le type *T* est constructible à l’aide des types d’arguments dans *args*. sinon, sa valeur est false. Le type *T* est constructible si la définition `T t(std::declval<Args>()...);` de la variable est bien formée. *T* et tous les types dans *args* doivent tous deux être des types complets, **void**ou des tableaux de limites inconnues.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
