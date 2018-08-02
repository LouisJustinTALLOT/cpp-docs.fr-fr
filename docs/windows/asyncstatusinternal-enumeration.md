---
title: AsyncStatusInternal (énumération) | Microsoft Docs
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
ms.openlocfilehash: a68189c461453dc72585ff4034df5ba69bb41bd5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464874"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (énumération)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Notes  
 Spécifie un mappage entre des énumérations internes pour l’état des opérations asynchrones et la `Windows::Foundation::AsyncStatus` énumération.  
  
## <a name="members"></a>Membres  
 *_Created*  
 Équivalent à :: Windows::Foundation::AsyncStatus :: créé  
  
 *_Started*  
 Équivalent à :: Windows::Foundation::AsyncStatus :: démarré  
  
 *_Terminée*  
 Équivalent à :: Windows::Foundation::AsyncStatus :: terminée  
  
 *_Cancelled*  
 Équivalent à :: Windows::Foundation::AsyncStatus :: annulée  
  
 *_Erreur*  
 Équivalent à :: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)