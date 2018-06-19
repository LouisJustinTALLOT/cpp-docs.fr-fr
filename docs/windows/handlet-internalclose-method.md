---
title: Handlet::internalclose, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b0aef97645d515a03dcf2cab90eedc06f07971c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874143"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose, méthode
Ferme l’objet HandleT en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si le HandleT actuel a été fermé avec succès ; dans le cas contraire, `false`.  
  
## <a name="remarks"></a>Notes  
 InternalClose() est protégé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HandleT, classe](../windows/handlet-class.md)