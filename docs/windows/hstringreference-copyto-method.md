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
ms.openlocfilehash: bb3a23f53dee82dd83f7b1b096702788d69d1f8e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015886"
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
 *str*  
 HSTRING qui reçoit la copie.  
  
## <a name="remarks"></a>Notes  
 Cette méthode appelle la [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) (fonction).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HStringReference, classe](../windows/hstringreference-class.md)