---
title: Hstring::getaddressof, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e327e2818903396c154be7406ec325695b6b6982
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613363"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf, méthode

Récupère un pointeur vers le handle HSTRING sous-jacent.

## <a name="syntax"></a>Syntaxe

```cpp
HSTRING* GetAddressOf() throw()  
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers le handle HSTRING sous-jacent.

## <a name="remarks"></a>Notes

Après cette opération, la valeur de chaîne du handle HSTRING sous-jacent est détruite.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)