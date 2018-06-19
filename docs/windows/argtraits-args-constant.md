---
title: Argtraits::args, constante | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f87b29634d5b9acef2e2ccb3f7b4d5f227433d38
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855771"
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args, constante
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const int args = -1; ;  
```  
  
## <a name="remarks"></a>Notes  
 Conserve le décompte du nombre de paramètres dans la méthode Invoke d’une interface de délégué.  
  
## <a name="remarks"></a>Notes  
 Lorsque `args` est égal à -1 indique qu’il ne peut y avoir aucune correspondance pour la signature de méthode Invoke.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [ArgTraits (Structure)](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)