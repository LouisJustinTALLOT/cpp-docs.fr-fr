---
title: Handlet::Close, méthode | Documents Microsoft
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
ms.openlocfilehash: 4f0c1e47420106651cfe0526d6d212e9819a72ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873249"
---
# <a name="handletclose-method"></a>HandleT::Close, méthode
Ferme l’objet HandleT en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>Notes  
 Le handle sous-jacent du HandleT actuel est fermé et la HandleT est définie sur l’état non valide.  
  
 Si le handle ne se ferme pas correctement, une exception est levée dans le thread appelant.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HandleT, classe](../windows/handlet-class.md)