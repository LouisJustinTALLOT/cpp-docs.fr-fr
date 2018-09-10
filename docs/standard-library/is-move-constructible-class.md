---
title: is_move_constructible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f9c0b381cfbf32327eef4b29a9dbe23f1d991f1
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108770"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible, classe

Teste si le type a un constructeur de déplacement.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à évaluer

## <a name="remarks"></a>Notes

Un prédicat de type qui prend la valeur true si le type *T* peut être construite à l’aide d’une opération de déplacement. Ce prédicat équivaut à `is_constructible<T, T&&>`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
