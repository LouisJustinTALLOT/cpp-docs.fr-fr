---
title: HStringReference::Operator ==, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
dev_langs:
- C++
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b07df3dc50704a87883e1a387fe9c842c1732b54
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610531"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator==, opérateur

Indique si les deux paramètres sont égaux.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Paramètres

*LHS*  
Le premier paramètre à comparer. *LHS* peut être un **HStringReference** objet ou un handle HSTRING.

*terme de droite*  
Le deuxième paramètre à comparer.  *RHS* peut être un **HStringReference** objet ou un handle HSTRING.

## <a name="return-value"></a>Valeur de retour

**true** si le *lhs* et *rhs* paramètres sont égaux ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HStringReference, classe](../windows/hstringreference-class.md)