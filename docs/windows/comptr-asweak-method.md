---
title: Comptr::asweak, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak method
ms.assetid: 23e29dcd-39cb-423f-abe6-6df4428213bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78f6eb9f3d0acf6a28479593d64616fa6881be76
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648088"
---
# <a name="comptrasweak-method"></a>ComPtr::AsWeak, méthode
Récupère une référence faible à l’objet actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AsWeak(  
   _Out_ WeakRef* pWeakRef  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pWeakRef*  
 Lorsque cette opération se termine, un pointeur vers un objet de référence faible.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr, classe](../windows/comptr-class.md)