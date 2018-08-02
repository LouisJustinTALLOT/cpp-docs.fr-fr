---
title: ComPtrRefBase::operator IUnknown**, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
dev_langs:
- C++
helpviewer_keywords:
- operator IUnknown** operator
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2ec20dca7bb0a37adae576a8b5a9adfad027b21
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465813"
---
# <a name="comptrrefbaseoperator-iunknown-operator"></a>ComPtrRefBase::operator IUnknown**, opérateur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator IUnknown**() const;  
```  
  
## <a name="remarks"></a>Notes  
 Effectue un cast en cours [ptr_](../windows/comptrrefbase-ptr-data-member.md) données membres à un pointeur-à-un-pointeur-to la `IUnknown` interface.  
  
 Une erreur est générée si actuel **ComPtrRefBase** ne dérive pas de `IUnknown`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtrRefBase (classe)](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)