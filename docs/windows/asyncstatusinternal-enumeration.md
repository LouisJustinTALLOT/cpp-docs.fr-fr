---
title: AsyncStatusInternal (énumération) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs:
- C++
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 150169442aa68395b4dc8a4f4c74951e877f18f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863723"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (énumération)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Notes  
 Spécifie un mappage entre des énumérations internes pour l’état des opérations asynchrones et la **Windows::Foundation::AsyncStatus** énumération.  
  
## <a name="members"></a>Membres  
 `_Created`  
 Équivalent à :: Windows::Foundation::AsyncStatus :: créé  
  
 `_Started`  
 Équivalent à :: Windows::Foundation::AsyncStatus :: démarré  
  
 `_Completed`  
 Équivalent à :: Windows::Foundation::AsyncStatus :: terminée  
  
 `_Cancelled`  
 Équivalent à :: Windows::Foundation::AsyncStatus :: annulée  
  
 `_Error`  
 Équivalent à :: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** async.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)