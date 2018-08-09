---
title: Runtimeclassbaset::asiid, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96b97bf2afa8897063e8303a04445f9957cc42c3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016637"
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Un type qui implémente l’ID d’interface spécifié par le paramètre *riid*.  
  
 *Implémente*  
 Une variable du type spécifié par le paramètre de modèle *T*.  
  
 *riid*  
 L’ID d’interface à récupérer.  
  
 *ppvObject*  
 Si cette opération réussite, un pointeur-à-un-pointeur vers l’interface spécifiée par le paramètre *riid*.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, une valeur HRESULT qui décrit l’erreur.  
  
## <a name="remarks"></a>Notes  
 Récupère un pointeur vers l’ID de l’interface spécifiée.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Runtimeclassbaset, Structure](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)