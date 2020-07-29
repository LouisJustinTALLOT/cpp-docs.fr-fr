---
title: is_trivially_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: 1f835dd348c6ef7f2ca7cd01f04c5afc059a55b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222327"
---
# <a name="is_trivially_constructible-class"></a>is_trivially_constructible, classe

Teste si un type est constructible de façon triviale quand les types d’arguments spécifiés sont utilisés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

*Attend*\
Types d’arguments à faire correspondre dans un constructeur de *T*.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est constructible de façon triviale à l’aide des types d’arguments dans *args*. sinon, sa valeur est false. Le type *T* est constructible de façon triviale si la définition de la variable `T t(std::declval<Args>()...);` est bien formée et s’il est connu pour ne pas appeler d’opérations non triviales. *T* et tous les types dans *args* doivent tous deux être des types complets, **`void`** , ou des tableaux de limites inconnues.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
