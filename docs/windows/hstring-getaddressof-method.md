---
title: Hstring::getaddressof, méthode | Documents Microsoft
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
ms.openlocfilehash: 7d4804373045d12c2e251e2de61b7aefd52ec916
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874666"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf, méthode
Récupère un pointeur vers le handle HSTRING sous-jacent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HSTRING* GetAddressOf() throw()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur vers le handle HSTRING sous-jacent.  
  
## <a name="remarks"></a>Notes  
 Après cette opération, la valeur de chaîne du handle HSTRING sous-jacent est détruite.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)