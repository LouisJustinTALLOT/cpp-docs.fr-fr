---
title: Factorycacheflags, énumération | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
dev_langs:
- C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ba3d9b75ff72399e1b9a027c937c24bba4a6c37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags, énumération
Détermine si les objets de fabrique sont mis en cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, la fabrique de stratégie de mise en cache est spécifiée comme le [ModuleType](../windows/moduletype-enumeration.md) paramètre de modèle lorsque vous créez un [Module](../windows/module-class.md) objet. Pour remplacer cette stratégie, vous devez spécifier un `FactoryCacheFlags` lorsque vous créez un objet de fabrique de valeur.  
  
|||  
|-|-|  
|`FactoryCacheDefault`|La stratégie de mise en cache de la `Module` objet est utilisé.|  
|`FactoryCacheEnabled`|Permet la mise en cache de fabrique, quel que soit le `ModuleType` paramètre de modèle qui est utilisé pour créer un `Module` objet.|  
|`FactoryCacheDisabled`|Désactive la mise en cache de fabrique, quel que soit le `ModuleType` paramètre de modèle qui est utilisé pour créer un `Module` objet.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)