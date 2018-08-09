---
title: Handlet::Close, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7cbe76cdea5c8fadef818ede1d63d88e4437bdae
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651065"
---
# <a name="handletclose-method"></a>HandleT::Close, méthode
Ferme actuel **HandleT** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void Close();  
```  
  
## <a name="remarks"></a>Notes  
 Le handle sous-jacent actuel **HandleT** est fermée et le **HandleT** est défini sur l’état non valide.  
  
 Si le handle ne ferme pas correctement, une exception est levée dans le thread appelant.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HandleT, classe](../windows/handlet-class.md)