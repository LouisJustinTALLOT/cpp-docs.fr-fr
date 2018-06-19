---
title: HandleT::operator =, opérateur | Documents Microsoft
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
ms.openlocfilehash: 6a13e8eb7e74625e185b59816b5794b0390e95e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873925"
---
# <a name="handletoperator-operator"></a>HandleT::operator=, opérateur
Déplace la valeur de l’objet HandleT spécifié à l’objet HandleT actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `h`  
 Une référence rvalue à un handle.  
  
## <a name="return-value"></a>Valeur de retour  
 Une référence à l’objet HandleT actuel.  
  
## <a name="remarks"></a>Notes  
 Cette opération rend non valide l’objet HandleT spécifié par le paramètre `h`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HandleT, classe](../windows/handlet-class.md)