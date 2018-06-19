---
title: Dontusenewusemake, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f343d0b47d50cd375d186c29ff55b91898aa9c61
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872326"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (classe)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>Notes  
 Empêche l’utilisation d’opérateur `new` dans RuntimeClass. Par conséquent, vous devez utiliser le [fonction](../windows/make-function.md) à la place.  
  
## <a name="members"></a>Membres  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new, opérateur](../windows/dontusenewusemake-operator-new-operator.md)|Surcharge d’opérateur `new` et empêche l’utilisation de RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl::Details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Make, fonction](../windows/make-function.md)