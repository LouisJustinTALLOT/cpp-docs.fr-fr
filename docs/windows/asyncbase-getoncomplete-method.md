---
title: Asyncbase::getoncomplete, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnComplete
dev_langs:
- C++
helpviewer_keywords:
- GetOnComplete method
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 15a561924cad314d09209e205ac73430f6d8be01
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466570"
---
# <a name="asyncbasegetoncomplete-method"></a>AsyncBase::GetOnComplete, méthode
Copie l’adresse du Gestionnaire d’événements de saisie semi-automatique actuelle à la variable spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetOnComplete  
)(TComplete** completeHandler);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *completeHandler*  
 L’emplacement de stockage de l’adresse du Gestionnaire d’événements de saisie semi-automatique actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)