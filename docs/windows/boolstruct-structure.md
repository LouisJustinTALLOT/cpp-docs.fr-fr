---
title: BoolStruct (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
dev_langs:
- C++
helpviewer_keywords:
- BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af2827d85a1df647dca2c02c5c6ee5a12a416d51
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860120"
---
# <a name="boolstruct-structure"></a>BoolStruct (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct BoolStruct;  
```  
  
## <a name="remarks"></a>Notes  
 La structure BoolStruct définit si un ComPtr gère la durée de vie d’une interface. BoolStruct est utilisé en interne par le [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) opérateur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[BoolStruct::Member, données de membre](../windows/boolstruct-member-data-member.md)|Spécifie qu’un [ComPtr](../windows/comptr-class.md) est ou n’est pas, la gestion de la durée de vie d’une interface.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `BoolStruct`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** internal.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl::Details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtr::operator Microsoft::WRL::Details::BoolType, opérateur](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)