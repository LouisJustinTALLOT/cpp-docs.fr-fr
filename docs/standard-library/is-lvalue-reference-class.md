---
title: is_lvalue_reference, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: 5bcd5c8333f011475cb11a452759c8986ab22215
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456201"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference, classe

Teste si le type est une référence lvalue.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance de ce prédicat de type a la valeur true si le type *Ty* est une référence à un objet ou à une fonction. sinon, sa valeur est false. Notez que *Ty* ne peut pas être une référence rvalue. Pour plus d’informations sur les rvalues, consultez [Déclarateur de référence Rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)
