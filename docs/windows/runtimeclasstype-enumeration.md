---
title: RuntimeClassType (énumération) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 43ab0a738af4c6bc92d42c0884827b574946d2ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892401"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (énumération)
Spécifie le type de [RuntimeClass](../windows/runtimeclass-class.md) instance qui est pris en charge.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum RuntimeClassType;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`ClassicCom`|Classe d’exécution COM classique.|  
|`Delegate`|Équivalent à **ClassicCom**.|  
|`InhibitFtmBase`|Désactive `FtmBase` prise en charge lors de la `__WRL_CONFIGURATION_LEGACY__` n’est pas défini.|  
|`InhibitWeakReference`|Désactive la prise en charge de la référence faible.|  
|`WinRt`|Une classe Windows Runtime.|  
|`WinRtClassicComMix`|Combinaison de `WinRt` et `ClassicCom`.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)