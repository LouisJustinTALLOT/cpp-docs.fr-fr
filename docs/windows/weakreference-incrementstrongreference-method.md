---
title: WeakReference::incrementstrongreference, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- IncrementStrongReference method
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee53e068c13f52c01e997680b57915051a8efad8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890620"
---
# <a name="weakreferenceincrementstrongreference-method"></a>WeakReference::IncrementStrongReference, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ULONG IncrementStrongReference();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre de référence forte incrémenté.  
  
## <a name="remarks"></a>Notes  
 Incrémente le décompte de références fort de l’objet WeakReference actuel.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
[WeakReference (classe)](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)