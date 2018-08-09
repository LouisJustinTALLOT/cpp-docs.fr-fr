---
title: Asyncbase::put_id, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::put_Id
dev_langs:
- C++
helpviewer_keywords:
- put_Id method
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f55896ac0bca162df9f17703225552cdb70c079c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647084"
---
# <a name="asyncbaseputid-method"></a>AsyncBase::put_Id, méthode
Définit le handle de l’opération asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   put_Id  
)(const unsigned int id);  
```  
  
### <a name="parameters"></a>Paramètres  
 *ID*  
 Un handle différente de zéro.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_INVALIDARG ou E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)