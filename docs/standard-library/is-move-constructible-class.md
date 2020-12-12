---
description: 'En savoir plus sur : classe is_move_constructible'
title: is_move_constructible, classe
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 05ef640b2841eb3ab66f6d5a6d3b8ede7acf2754
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323631"
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
