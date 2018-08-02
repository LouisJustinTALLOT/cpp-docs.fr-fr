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
ms.openlocfilehash: faa2e1af556f0184fa88055bcbf154eb783e24e5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463595"
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress, méthode
Appelle le Gestionnaire d’événements de progression actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *arg*  
 La méthode de gestionnaire d’événements à appeler.  
  
## <a name="remarks"></a>Notes  
 `ProgressTraits` est dérivé de [ArgTraitsHelper (Structure)](../windows/argtraitshelper-structure.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)