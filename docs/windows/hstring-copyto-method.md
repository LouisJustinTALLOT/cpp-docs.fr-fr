---
title: Hstring::CopyTo, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b44974faf5fc1f068d28d7febe3ed2a266f4869e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874770"
---
# <a name="hstringcopyto-method"></a>HString::CopyTo, méthode
Copie le HString en cours de l’objet à un objet HSTRING.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `str`  
 HSTRING qui reçoit la copie.  
  
## <a name="remarks"></a>Notes  
 Cette méthode appelle la [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) (fonction).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)