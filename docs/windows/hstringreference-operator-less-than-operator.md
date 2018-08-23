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
ms.openlocfilehash: ee7edbee285df6da752e875ac4d86a74e8f7893d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594139"
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

*LHS*  
Le premier paramètre à comparer. *LHS* peut être une référence à un **HStringReference**.

*terme de droite*  
Le deuxième paramètre à comparer.  *RHS* peut être une référence à un **HStringReference**.

## <a name="return-value"></a>Valeur de retour

**true** si le *lhs* paramètre est inférieure à la *rhs* paramètre ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HStringReference, classe](../windows/hstringreference-class.md)