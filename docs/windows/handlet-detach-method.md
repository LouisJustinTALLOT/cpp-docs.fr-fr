---
title: Handlet::Detach, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 100d215099494c9b2714fd2c42dee69644a5006c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878461"
---
# <a name="handletdetach-method"></a>HandleT::Detach, méthode
Dissocie l’objet HandleT actuel à partir de son handle sous-jacent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le handle sous-jacent.  
  
## <a name="remarks"></a>Notes  
 Lorsque cette opération est terminée, le HandleT actuelle est définie sur l’état non valide.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HandleT, classe](../windows/handlet-class.md)