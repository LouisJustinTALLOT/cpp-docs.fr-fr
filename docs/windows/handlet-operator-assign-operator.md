---
title: HandleT::operator =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa253bec9f150d08f699333cd5d5f6d4538fc2d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653155"
---
# <a name="handletoperator-operator"></a>HandleT::operator=, opérateur
Déplace la valeur de l’objet **HandleT** objet actuel **HandleT** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *h*  
 Une référence rvalue à un handle.  
  
## <a name="return-value"></a>Valeur de retour  
 Une référence à l’actuel **HandleT** objet.  
  
## <a name="remarks"></a>Notes  
 Cette opération invalide le **HandleT** objet spécifié par le paramètre *h*.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HandleT, classe](../windows/handlet-class.md)