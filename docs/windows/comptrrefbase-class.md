---
title: Comptrrefbase, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13744a1629ede5575dc992ea15b90e22961a8570
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883578"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase (classe)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md) type ou un type dérivé, pas simplement l’interface représentée par le ComPtr.  
  
## <a name="remarks"></a>Notes  
 Représente la classe de base pour le [ComPtrRef](../windows/comptrref-class.md) classe.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`InterfaceType`|Un synonyme pour le type de paramètre de modèle `T`.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtrRefBase::operator IInspectable**, opérateur](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Convertit en cours [ptr_](../windows/comptrrefbase-ptr-data-member.md) membre de données pour un pointeur à une-pointeur-à l’interface IInspectable.|  
|[ComPtrRefBase::operator IUnknown**, opérateur](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Convertit en cours [ptr_](../windows/comptrrefbase-ptr-data-member.md) membre de données pour un pointeur à une-pointeur-à l’interface IUnknown.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_, données de membre](../windows/comptrrefbase-ptr-data-member.md)|Pointeur vers le type spécifié par le paramètre de modèle actuel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)