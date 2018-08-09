---
title: Asyncbase::fireprogress, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs:
- C++
helpviewer_keywords:
- FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35faad82357b0f449d407787840c865b798427f1
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642007"
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress, méthode
Appelle le Gestionnaire d’événements de progression actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *arg*  
 La méthode de gestionnaire d’événements à appeler.  
  
## <a name="remarks"></a>Notes  
 `ProgressTraits` est dérivé de [ArgTraitsHelper (Structure)](../windows/argtraitshelper-structure.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)