---
title: Asyncbase::putonprogress, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnProgress
dev_langs:
- C++
helpviewer_keywords:
- PutOnProgress method
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a9460664ed58cf39f7b295e1406649ad1d66ca9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467415"
---
# <a name="asyncbaseputonprogress-method"></a>AsyncBase::PutOnProgress, méthode
Définit l’adresse du Gestionnaire d’événements de progression à la valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *progressHandler*  
 L’adresse à laquelle le Gestionnaire d’événements de progression est défini.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)