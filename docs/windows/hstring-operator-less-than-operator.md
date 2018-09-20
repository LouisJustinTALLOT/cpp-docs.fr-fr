---
title: HString::Operator&lt; opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa4a10235f37a3ea174965ad56f63d078e3cbde2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403575"
---
# <a name="hstringoperatorlt-operator"></a>HString::Operator&lt; opérateur

Indique si le premier paramètre est inférieur au second.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()  
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Le premier paramètre à comparer. *LHS* peut être une référence à un **HString**.

*terme de droite*<br/>
Le deuxième paramètre à comparer. *RHS* peut être une référence à un **HString**.

## <a name="return-value"></a>Valeur de retour

**true** si le *lhs* paramètre est inférieure à la *rhs* paramètre ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)