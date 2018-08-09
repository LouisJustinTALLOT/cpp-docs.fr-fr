---
title: EventSource::targets, données de membre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targets_
dev_langs:
- C++
helpviewer_keywords:
- targets_ data member
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea08cdc8657100e1c1e0157a8a542a44ea34cd4d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642371"
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_, données de membre
Tableau d’un ou plusieurs gestionnaires d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>Notes  
 Lorsque l’événement qui est représenté par l’actuel **EventSource** objet se produit, les gestionnaires d’événements sont appelées.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [EventSource, classe](../windows/eventsource-class.md)