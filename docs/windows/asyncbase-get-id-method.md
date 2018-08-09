---
title: Asyncbase::get_id, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Id
dev_langs:
- C++
helpviewer_keywords:
- get_Id method
ms.assetid: 591d8366-ea76-4deb-9278-9d3bc394a42b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab02da2dcae788e5eb4b1db15508d2f272ec546a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651556"
---
# <a name="asyncbasegetid-method"></a>AsyncBase::get_Id, méthode
Récupère le handle de l’opération asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   get_Id  
)(unsigned int *id) override;  
```  
  
### <a name="parameters"></a>Paramètres  
 *ID*  
 L’emplacement où le handle doit être stocké.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.  
  
## <a name="remarks"></a>Notes  
 Cette méthode implémente `IAsyncInfo::get_Id`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)