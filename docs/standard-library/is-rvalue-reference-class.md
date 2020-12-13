---
description: 'En savoir plus sur : classe is_rvalue_reference'
title: is_rvalue_reference, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_rvalue_reference
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
ms.openlocfilehash: 1fb3de556f3a8b1b9aa70034a23e5e487336cd56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339027"
---
# <a name="is_rvalue_reference-class"></a>is_rvalue_reference, classe

Teste si le type est une référence rvalue.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance de ce prédicat de type a la valeur true si le type *Ty* est une [référence rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Lvalues et rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)
