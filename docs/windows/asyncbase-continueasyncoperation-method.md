---
title: Asyncbase::continueasyncoperation, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7b5d2b10b571a3517beab98eaa839d5c7fd86c2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460831"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation, méthode
Détermine si l’opération asynchrone doit poursuivre le traitement ou qu’il doit s’arrêter.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si l’état actuel de l’opération asynchrone est *démarré*, ce qui signifie que l’opération doit continuer. Sinon, **false**, ce qui signifie que l’opération doit s’arrêter.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)