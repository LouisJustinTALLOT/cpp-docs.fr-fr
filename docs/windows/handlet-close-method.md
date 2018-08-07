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
ms.openlocfilehash: 69f3f2c756d158954676f6fc42941b1b80f4345e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569916"
---
# <a name="handletclose-method"></a>HandleT::Close, méthode
Ferme actuel **HandleT** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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