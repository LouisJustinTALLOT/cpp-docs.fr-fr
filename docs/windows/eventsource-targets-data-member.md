---
title: EventSource::targets, données de membre | Documents Microsoft
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
ms.openlocfilehash: a35992a5579bf852323f4c01396fab56542f40cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871742"
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_, données de membre
Tableau d’un ou plusieurs gestionnaires d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>Notes  
 Lorsque l’événement représenté par l’objet en cours de la source d’événement se produit, les gestionnaires d’événements sont appelés.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [EventSource, classe](../windows/eventsource-class.md)