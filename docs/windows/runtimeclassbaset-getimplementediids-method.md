---
title: Runtimeclassbaset::getimplementediids, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ea6ff871ef0ce886b393c948fc45accf3d8e245
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892232"
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Type du paramètre `implements`.  
  
 `implements`  
 Pointeur vers le type spécifié par le paramètre `T`.  
  
 `iidCount`  
 Le nombre maximal d’ID d’interface à récupérer.  
  
 `iids`  
 Si cette opération est terminée avec succès, un tableau de l’interface implémentées par le type des ID `T`.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, un HRESULT qui décrit l’erreur.  
  
## <a name="remarks"></a>Notes  
 Récupère un tableau d’ID qui sont implémentées par un type d’interface.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [RuntimeClassBaseT, structure](../windows/runtimeclassbaset-structure.md)