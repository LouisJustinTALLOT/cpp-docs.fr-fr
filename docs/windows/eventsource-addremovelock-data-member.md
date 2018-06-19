---
title: EventSource::addremovelock, données de membre | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::addRemoveLock_
dev_langs:
- C++
helpviewer_keywords:
- addRemoveLock_ data member
ms.assetid: e2d69256-4891-4aad-ad0b-76479c0bb076
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 46763a6376a18ae469833c3eee6a0d5d9f15ee45
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872651"
---
# <a name="eventsourceaddremovelock-data-member"></a>EventSource::addRemoveLock_, données de membre
Synchronise l’accès à la [targets_](../windows/eventsource-targets-data-member.md) tableau lors de l’ajout, la suppression ou appeler des gestionnaires d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Wrappers::SRWLock addRemoveLock_;  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [EventSource, classe](../windows/eventsource-class.md)