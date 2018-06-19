---
title: VerifyInheritanceHelper (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
dev_langs:
- C++
helpviewer_keywords:
- VerifyInheritanceHelper structure
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d758f4b44990d1f03ff698f0740c2aa8491367a5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889701"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I,  
   typename Base  
>  
struct VerifyInheritanceHelper;  
template <  
   typename I  
>  
struct VerifyInheritanceHelper<I, Nil>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `I`  
 Type.  
  
 `Base`  
 Un autre type.  
  
## <a name="remarks"></a>Notes  
 Teste si une interface est dérivée d’une autre interface.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[VerifyInheritanceHelper::Verify, méthode](../windows/verifyinheritancehelper-verify-method.md)|Teste les deux interfaces spécifiées par les paramètres de modèle actuel et détermine si une interface est dérivée de l’autre.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `VerifyInheritanceHelper`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)