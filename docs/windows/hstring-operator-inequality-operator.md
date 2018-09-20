---
title: HString::Operator ! =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs:
- C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5446fb6fa0722018e4ab7734019e677b6acec7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435205"
---
# <a name="hstringoperator-operator"></a>HString::Operator!=, opérateur

Indique si les deux paramètres ne sont pas égales.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Le premier paramètre à comparer. *LHS* peut être un **HString** ou `HStringReference` objet ou un handle HSTRING.

*terme de droite*<br/>
Le deuxième paramètre à comparer. *rhs* peut être un **HString** ou `HStringReference` objet ou un handle HSTRING.

## <a name="return-value"></a>Valeur de retour

**true** si le *lhs* et *rhs* paramètres ne sont pas égales ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)