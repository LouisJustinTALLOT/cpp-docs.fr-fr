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
ms.openlocfilehash: 4ea49833107bf58443bf4a8238229d1d63a86742
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010345"
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