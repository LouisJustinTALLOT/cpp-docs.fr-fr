---
title: is_nothrow_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: e52b16965d849f992731c4ff4254fd218b944269
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217751"
---
# <a name="is_nothrow_constructible-class"></a>is_nothrow_constructible, classe

Teste si un type est constructible et est connu comme ne levant pas d’exception quand les types d’arguments spécifiés sont utilisés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

*Attend*\
Types d’arguments à faire correspondre dans un constructeur de *T*.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est constructible à l’aide des types d’arguments dans *args*, et que le constructeur est connu du fait que le compilateur ne lève pas d’exception. Sinon, sa valeur est false. Le type *T* est constructible si la définition de la variable `T t(std::declval<Args>()...);` est bien formée. *T* et tous les types dans *args* doivent tous deux être des types complets, **`void`** , ou des tableaux de limites inconnues.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
