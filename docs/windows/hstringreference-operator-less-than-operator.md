---
title: HStringReference::Operator&lt; opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17acdca8af1250b1f88fa8a6858ffa1854f8ca8c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426404"
---
# <a name="hstringreferenceoperatorlt-operator"></a>HStringReference::Operator&lt; opérateur

Indique si le premier paramètre est inférieur au second.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()  
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Le premier paramètre à comparer. *LHS* peut être une référence à un **HStringReference**.

*terme de droite*<br/>
Le deuxième paramètre à comparer.  *RHS* peut être une référence à un **HStringReference**.

## <a name="return-value"></a>Valeur de retour

**true** si le *lhs* paramètre est inférieure à la *rhs* paramètre ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HStringReference, classe](../windows/hstringreference-class.md)