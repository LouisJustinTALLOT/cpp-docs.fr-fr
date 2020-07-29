---
title: is_move_constructible, classe
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 5495ac39a98f5c194f19d28ba85a1d59f47dfbb4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222379"
---
# <a name="is_move_constructible-class"></a>is_move_constructible, classe

Teste si le type peut être construit à l’aide d’une opération de déplacement.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à évaluer.

## <a name="remarks"></a>Notes

Prédicat de type qui prend **`true`** la valeur si le type *T* peut être construit à l’aide d’une opération de déplacement. Ce prédicat équivaut à `is_constructible<T, T&&>`. Type *T* qui n’a pas de constructeur de déplacement, mais qui a un constructeur de copie qui accepte un `const T&` argument, correspond à `std::is_move_constructible` .

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
