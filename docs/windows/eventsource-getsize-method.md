---
title: EventSource::GetSize, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::GetSize
dev_langs:
- C++
helpviewer_keywords:
- GetSize method
ms.assetid: 7825aab5-1a6b-465f-9159-3a6684142d1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49497c8b33641521a66c3e84dc2dae3dbd993699
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645046"
---
# <a name="eventsourcegetsize-method"></a>EventSource::GetSize, méthode
Récupère le nombre de gestionnaires d’événements associés à l’actuel **EventSource** objet  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
size_t GetSize() const;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre de gestionnaires d’événements dans [targets_](../windows/eventsource-targets-data-member.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [EventSource, classe](../windows/eventsource-class.md)