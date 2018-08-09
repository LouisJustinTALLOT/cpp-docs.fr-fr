---
title: Handlet::internalclose, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2190a8e85f81062cc1167aa844fccf4afc819bc9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648800"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose, méthode
Ferme actuel **HandleT** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si actuel **HandleT** fermé avec succès ; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 **InternalClose()** est **protégé**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HandleT, classe](../windows/handlet-class.md)