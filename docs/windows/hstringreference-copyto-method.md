---
title: Hstringreference::CopyTo, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61474e3891def73114f8efc101e1132d5d2593b1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402731"
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo, méthode

Copie en cours **HStringReference** objet dans un objet HSTRING.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Paramètres

*str*<br/>
HSTRING qui reçoit la copie.

## <a name="remarks"></a>Notes

Cette méthode appelle la [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) (fonction).

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HStringReference, classe](../windows/hstringreference-class.md)