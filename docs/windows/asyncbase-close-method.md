---
title: Asyncbase::Close, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d0798a6ef593e388ce7867ee9a55763be9ae890
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463357"
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close, méthode
Ferme l’opération asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si l’opération se ferme ou est déjà fermé ; Sinon, E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Notes  
 **Close()** est une implémentation par défaut de `IAsyncInfo::Close`, et n’effectue aucun travail réel. Pour fermer réellement une opération asynchrone, remplacer le `OnClose()` méthode virtuelle pure.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)