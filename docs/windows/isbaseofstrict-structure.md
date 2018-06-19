---
title: IsBaseOfStrict (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db8f315c0589ceb7cd9411873152fe644985818e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876889"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Base`  
 Type de base.  
  
 `Derived`  
 Le type dérivé.  
  
## <a name="remarks"></a>Notes  
 Teste si un type est la base d'un autre.  
  
 Le premier modèle teste si un type est dérivé d’un type de base, ce qui peut produire **true** ou **false**. Le deuxième modèle teste si un type est dérivé lui-même, ce qui entraîne toujours une valeur **false**.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[IsBaseOfStrict::value, constante](../windows/isbaseofstrict-value-constant.md)|Indique si un type est la base d’un autre.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IsBaseOfStrict`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** internal.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)