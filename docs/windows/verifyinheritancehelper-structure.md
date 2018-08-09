---
title: VerifyInheritanceHelper (Structure) | Microsoft Docs
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
ms.openlocfilehash: 7ed375a30ddadf72b7eee8a2cc852dec6620a992
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011115"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
### <a name="parameters"></a>Paramètres  
 *I*  
 Type.  
  
 *base de*  
 Un autre type.  
  
## <a name="remarks"></a>Notes  
 Teste si une interface est dérivée d’une autre interface.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[VerifyInheritanceHelper::Verify, méthode](../windows/verifyinheritancehelper-verify-method.md)|Teste les deux interfaces spécifiées par les paramètres de modèle actuelle et détermine si une interface est dérivée de l’autre.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `VerifyInheritanceHelper`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)