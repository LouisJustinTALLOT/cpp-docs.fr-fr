---
title: WeakReference::decrementstrongreference, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d5605670e05f91f9f1293c8bff0f4d74e458d25
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890334"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>Notes  
 Décrémente le fort décompte de références de l’objet WeakReference actuel.  
  
 Lorsque le nombre de référence forte devient égal à zéro, la référence forte est définie sur `nullptr`.  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre de référence forte décrémenté.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
[WeakReference (classe)](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)