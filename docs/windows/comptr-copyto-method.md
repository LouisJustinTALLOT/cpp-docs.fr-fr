---
title: Comptr::CopyTo, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: baa8c64187be3d1ddf52bf7056a00b7c13abeceb
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo, méthode
Copies de l’interface actuelle ou spécifiée associée à ce ComPtr au pointeur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  

template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `U`  
 Un nom de type.  
  
 `ptr`  
 Lorsque cette opération est terminée, un pointeur vers l’interface demandée.  
  
 `riid`  
 ID d’interface.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, un HRESULT qui indique l’échec de l’opération de QueryInterface implicite.  
  
## <a name="remarks"></a>Notes  
 La première fonction retourne une copie d’un pointeur vers l’interface associée à ce ComPtr. Cette fonction retourne toujours S_OK.  
  
 La deuxième fonction effectue une opération de QueryInterface sur l’interface associée à ce ComPtr pour l’interface spécifiée par le `riid` paramètre.  
  
 La troisième fonction effectue une opération de QueryInterface sur l’interface associée à ce ComPtr de l’interface sous-jacente de le `U` paramètre.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr, classe](../windows/comptr-class.md)