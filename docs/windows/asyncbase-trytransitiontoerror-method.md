---
title: Asyncbase::trytransitiontoerror, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61b56472e490d95e22c1013595c5c088d2b58dcd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643028"
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError, méthode
Indique si le code d’erreur spécifié peut modifier l’état d’erreur interne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *Erreur*  
 Une erreur HRESULT.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si l’état d’erreur interne a été modifié ; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Cette opération modifie l’état d’erreur uniquement si l’état d’erreur est déjà définie à S_OK. Cette opération n’a aucun effet si l’état d’erreur est déjà erreur, annulé, terminé ou fermé.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)