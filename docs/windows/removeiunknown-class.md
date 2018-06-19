---
title: Removeiunknown, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb005bc3cbf411a7d5b5ddbfa44cd6aecf802105
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879540"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown, classe
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Une classe.  
  
## <a name="remarks"></a>Notes  
 Crée un type qui est équivalent à une `IUnknown`-type de base, mais avec non virtuelle `QueryInterface`, `AddRef`, et `Release` fonctions membres.  
  
 Par défaut, les méthodes COM fournissent virtuel `QueryInterface`, `AddRef`et libérer des méthodes. Toutefois, `ComPtr` ne nécessite pas la surcharge de méthodes virtuelles. `RemoveIUnknown` élimine cette surcharge en fournissant privé et non virtuelle `QueryInterface`, `AddRef`, et `Release` méthodes.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`ReturnType`|Un synonyme pour un type qui est équivalent au paramètre de modèle `T` mais comporte des membres de IUnknown non virtuelles.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `T`  
  
 `RemoveIUnknown`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)