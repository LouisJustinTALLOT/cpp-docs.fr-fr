---
title: HString::Operator ==, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
dev_langs:
- C++
ms.assetid: 77ff4c1a-e62a-4256-bf9d-0f017137c630
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed3a93ac964841028b252aa09a6b70c18ed202e9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602986"
---
# <a name="hstringoperator-operator"></a>HString::Operator==, opérateur

Indique si les deux paramètres sont égaux.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Paramètres

*LHS*  
Le premier paramètre à comparer. *LHS* peut être un **HString** ou `HStringReference` objet ou un handle HSTRING.

*terme de droite*  
Le deuxième paramètre à comparer. *rhs* peut être un **HString** ou `HStringReference` objet ou un handle HSTRING.

## <a name="return-value"></a>Valeur de retour

**true** si le *lhs* et *rhs* paramètres sont égaux ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)