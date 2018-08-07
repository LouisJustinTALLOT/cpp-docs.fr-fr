---
title: DontUseNewUseMake (classe) | Microsoft Docs
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
ms.openlocfilehash: 351b38a002c470dcd3f53e8336e393f845fdb3cf
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569567"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (classe)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>Notes  
 Empêche l’utilisation d’opérateur **nouveau** dans RuntimeClass. Par conséquent, vous devez utiliser le [Make, fonction](../windows/make-function.md) à la place.  
  
## <a name="members"></a>Membres  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new, opérateur](../windows/dontusenewusemake-operator-new-operator.md)|Surcharge d’opérateur **nouveau** et empêche l’utilisation dans RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl::Details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Make, fonction](../windows/make-function.md)