---
title: Handlenulltraits::Close, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0206433d2b329501b10a8262e7b487ec83e99302
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642108"
---
# <a name="handlenulltraitsclose-method"></a>HANDLENullTraits::Close, méthode
Ferme le handle spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *h*  
 Le handle à fermer.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si gérer *h* fermé avec succès ; sinon, **false**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [HANDLENullTraits, structure](../windows/handlenulltraits-structure.md)