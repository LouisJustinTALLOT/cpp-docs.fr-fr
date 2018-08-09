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
ms.openlocfilehash: 3ce391e95aa9e08ae7d99e3cbdf064721ce21dbe
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643535"
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close, méthode
Ferme l’opération asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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