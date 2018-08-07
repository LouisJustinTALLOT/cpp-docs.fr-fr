---
title: Factorycacheflags, énumération | Microsoft Docs
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
ms.openlocfilehash: cc4bd998368fb325878a81ee4954a2ceec9432fe
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570101"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags, énumération
Détermine si les objets de fabrique sont mis en cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, la fabrique de stratégie de mise en cache est spécifiée comme le [ModuleType](../windows/moduletype-enumeration.md) paramètre de modèle lorsque vous créez un [Module](../windows/module-class.md) objet. Pour remplacer cette stratégie, spécifiez un **FactoryCacheFlags** valeur lorsque vous créez un objet de fabrique.  
  
|||  
|-|-|  
|`FactoryCacheDefault`|La stratégie de mise en cache de la `Module` objet est utilisé.|  
|`FactoryCacheEnabled`|Permet la mise en cache de fabrique, quel que soit le `ModuleType` paramètre de modèle qui est utilisé pour créer un `Module` objet.|  
|`FactoryCacheDisabled`|Désactive la mise en cache de fabrique, quel que soit le `ModuleType` paramètre de modèle qui est utilisé pour créer un `Module` objet.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)