---
title: Comptr::PTR, données de membre | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ptr_
dev_langs:
- C++
helpviewer_keywords:
- ptr_ data member
ms.assetid: c84f9dda-8ff9-422d-91f2-1a41206bf9ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d995c8e35ed35d4581d8eec8b74fda1ebbca6519
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880799"
---
# <a name="comptrptr-data-member"></a>ComPtr::ptr_, données de membre
Contient un pointeur vers l’interface associée à ce ComPtr, et gérée par ce dernier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
InterfaceType *ptr_;  
```  
  
## <a name="remarks"></a>Notes  
 `ptr_` est un membre interne des données protégées.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr, classe](../windows/comptr-class.md)