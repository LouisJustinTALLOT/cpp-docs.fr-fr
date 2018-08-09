---
title: EventSource::targetspointerlock, données de membre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targetsPointerLock_
dev_langs:
- C++
helpviewer_keywords:
- targetsPointerLock_ data member
ms.assetid: 8f08409f-5262-4be7-9cf1-2ed15f19684a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 718a62d627f99eff24fd7c10e0280607a52e2be7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646885"
---
# <a name="eventsourcetargetspointerlock-data-member"></a>EventSource::targetsPointerLock_, données de membre
Synchronise l’accès aux membres de données internes même lorsque les gestionnaires d’événements pour ce **EventSource** sont ajoutés, supprimés ou appelée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Wrappers::SRWLock targetsPointerLock_;  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [EventSource, classe](../windows/eventsource-class.md)