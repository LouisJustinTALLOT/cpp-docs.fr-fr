---
title: Comptr::CopyTo, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 724803fbbf04bd697dfc85f6576ed5706d708eae
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464439"
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo, méthode
Copie de l’interface actuelle ou spécifiée associée à cet **ComPtr** pour le pointeur spécifié.  
  
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
 *U*  
 Un nom de type.  
  
 *ptr*  
 Lorsque cette opération se termine, un pointeur vers l’interface demandée.  
  
 *riid*  
 ID d’interface.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, un HRESULT qui indique la raison pour laquelle le caractère implicite `QueryInterface` échouée de l’opération.  
  
## <a name="remarks"></a>Notes  
 La première fonction retourne une copie d’un pointeur vers l’interface associée à cet **ComPtr**. Cette fonction retourne toujours S_OK.  
  
 La deuxième fonction effectue une `QueryInterface` opération sur l’interface associée à cet **ComPtr** pour l’interface spécifiée par le *riid* paramètre.  
  
 La troisième fonction effectue une `QueryInterface` opération sur l’interface associée à cet **ComPtr** pour l’interface sous-jacente de la *U* paramètre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr, classe](../windows/comptr-class.md)