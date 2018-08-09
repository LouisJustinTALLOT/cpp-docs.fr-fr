---
title: WeakReference::incrementstrongreference, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- IncrementStrongReference method
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f564f5d6197a640ef311cda8b2133ed583eec91e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642692"
---
# <a name="weakreferenceincrementstrongreference-method"></a>WeakReference::IncrementStrongReference, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ULONG IncrementStrongReference();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre de référence forte incrémenté.  
  
## <a name="remarks"></a>Notes  
 Incrémente le nombre de référence forte d’actuel **WeakReference** objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [WeakReference (classe)](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)