---
title: InterfaceListHelper (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs:
- C++
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8ad091114d6be6f35f1a0341961dc5122840ace8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878045"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T0,  
   typename T1 = Nil,  
   typename T2 = Nil,  
   typename T3 = Nil,  
   typename T4 = Nil,  
   typename T5 = Nil,  
   typename T6 = Nil,  
   typename T7 = Nil,  
   typename T8 = Nil,  
   typename T9 = Nil  
>  
struct InterfaceListHelper;  
  
template <  
   typename T0  
>  
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T0`  
 Paramètre de modèle 0, ce qui est nécessaire.  
  
 `T1`  
 Paramètre de modèle 1, qui par défaut n’est pas spécifié.  
  
 `T2`  
 Paramètre de modèle 2, qui par défaut n’est pas spécifié. Le troisième paramètre de modèle.  
  
 `T3`  
 Paramètre de modèle 3, qui par défaut n’est pas spécifié.  
  
 `T4`  
 Paramètre de modèle 4, qui par défaut n’est pas spécifié.  
  
 `T5`  
 Paramètre de modèle 5, qui par défaut n’est pas spécifié.  
  
 `T6`  
 Paramètre de modèle 6, qui par défaut n’est pas spécifié.  
  
 `T7`  
 Paramètre de modèle 7, qui par défaut n’est pas spécifié.  
  
 `T8`  
 Paramètre de modèle 8, qui par défaut n’est pas spécifié.  
  
 `T9`  
 Paramètre de modèle 9, qui par défaut n’est pas spécifié.  
  
## <a name="remarks"></a>Notes  
 Crée un type InterfaceList en appliquant les arguments de paramètre de modèle spécifié de manière récursive.  
  
 Le modèle InterfaceListHelper utilise le paramètre de modèle `T0` pour définir les données du premier membre dans un InterfaceList (structure), puis de manière récursive s’applique le modèle InterfaceListHelper pour toutes les autres paramètres de modèle. InterfaceListHelper s’arrête lorsqu’il n’y a aucun paramètre de modèle restants.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`TypeT`|Un synonyme du type InterfaceList.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `InterfaceListHelper`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)