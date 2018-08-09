---
title: ClassFactory::lockserver, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee858346fdb70e136edfbc562c2dfffb1f63e462
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652369"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer, méthode
Incrémente ou décrémente le nombre de sous-jacent objets qui sont suivis par le **ClassFactory** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
### <a name="parameters"></a>Paramètres  
 *Troupeau*  
 **true** pour incrémenter le nombre d’objets suivis. **false** pour décrémenter le nombre d’objets suivis.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_FAIL.  
  
## <a name="remarks"></a>Notes  
 **ClassFactory** effectue le suivi des objets dans une instance sous-jacente de la [Module](../windows/module-class.md) classe.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ClassFactory, classe](../windows/classfactory-class.md)