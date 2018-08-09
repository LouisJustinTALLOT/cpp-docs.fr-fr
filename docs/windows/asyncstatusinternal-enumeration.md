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
ms.openlocfilehash: eeaef23178829163725b78685b3460913f53f2c2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652797"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (énumération)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Notes  
 Spécifie un mappage entre des énumérations internes pour l’état des opérations asynchrones et la `Windows::Foundation::AsyncStatus` énumération.  
  
## <a name="members"></a>Membres  
 `_Created`  
 Équivaut à `::Windows::Foundation::AsyncStatus::Created`.  
  
 `_Started`  
 Équivaut à `::Windows::Foundation::AsyncStatus::Started`.  
  
 `_Completed`  
 Équivaut à `::Windows::Foundation::AsyncStatus::Completed`.  
  
 `_Cancelled`  
 Équivaut à `::Windows::Foundation::AsyncStatus::Cancelled`.  
  
 `_Error`  
 Équivaut à `::Windows::Foundation::AsyncStatus::Error`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)