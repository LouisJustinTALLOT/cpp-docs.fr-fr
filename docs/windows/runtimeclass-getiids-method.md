---
title: Runtimeclass::getiids, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91d0a082a422657f6716e16c8b53ab33e0313d82
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020133"
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids, méthode
Obtient un tableau qui contient l’interface implémentées par actuel des ID **RuntimeClass** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
### <a name="parameters"></a>Paramètres  
 *iidCount*  
 Lorsque cette opération se termine, le nombre total d’éléments du tableau *IID*.  
  
 *IID*  
 Lorsque cette opération se termine, un pointeur vers un tableau d’ID d’interface.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_OUTOFMEMORY.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [RuntimeClass, classe](../windows/runtimeclass-class.md)