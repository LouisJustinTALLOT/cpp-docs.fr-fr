---
description: 'En savoir plus sur : classe is_nothrow_constructible'
title: is_nothrow_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 0bb822a42d149a552f18ff4d1b1c723ef9b88172
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323578"
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
