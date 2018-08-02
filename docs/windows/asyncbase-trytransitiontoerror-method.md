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
ms.openlocfilehash: fc677304ae7ab61e6726366869e85f731cd92484
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463205"
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError, méthode
Indique si le code d’erreur spécifié peut modifier l’état d’erreur interne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
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