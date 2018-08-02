---
title: ComPtrRefBase (classe) | Microsoft Docs
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
ms.openlocfilehash: 0342500fc41c650967e17919ebdc9605d4261cb5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464241"
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
 *T*  
 Un [ComPtr\<T >](../windows/comptr-class.md) type ou un type dérivé, pas simplement l’interface représentée par le **ComPtr**.  
  
## <a name="remarks"></a>Notes  
 Représente la classe de base pour le [ComPtrRef](../windows/comptrref-class.md) classe.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`InterfaceType`|Un synonyme du type de paramètre de modèle *T*.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ComPtrRefBase::operator IInspectable**, opérateur](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Effectue un cast en cours [ptr_](../windows/comptrrefbase-ptr-data-member.md) données membres à un pointeur-à-un-pointeur-à l’interface IInspectable.|  
|[ComPtrRefBase::operator IUnknown**, opérateur](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Effectue un cast en cours [ptr_](../windows/comptrrefbase-ptr-data-member.md) données membres à un pointeur-à-un-pointeur-à l’interface IUnknown.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_, données de membre](../windows/comptrrefbase-ptr-data-member.md)|Pointeur vers le type spécifié par le paramètre de modèle actuel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)