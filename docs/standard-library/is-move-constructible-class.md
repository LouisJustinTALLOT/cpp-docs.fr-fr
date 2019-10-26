---
title: is_move_constructible, classe
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 9585a932a34a24769201aaa379525a9b4c181e41
ms.sourcegitcommit: 33a898bf976c65f998b4e88a84765a0cef4193a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920087"
---
# <a name="is_move_constructible-class"></a>is_move_constructible, classe

Teste si le type peut être construit à l’aide d’une opération de déplacement.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Paramètres

*T* \
Type à évaluer.

## <a name="remarks"></a>Notes

Prédicat de type qui prend la **valeur true** si le type *T* peut être construit à l’aide d’une opération de déplacement. Ce prédicat équivaut à `is_constructible<T, T&&>`. Type *T* qui n’a pas de constructeur de déplacement, mais qui a un constructeur de copie qui accepte un argument `const T&`, satisfait `std::is_move_constructible`.

## <a name="requirements"></a>spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
