---
title: Runtimeclasstype, énumération | Microsoft Docs
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
ms.openlocfilehash: 1b54813a41a8857e4533f21d1eb0adaf8dcecd25
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010819"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType (énumération)
Spécifie le type de [RuntimeClass](../windows/runtimeclass-class.md) instance qui est pris en charge.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum RuntimeClassType;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`ClassicCom`|Une classe d’exécution COM classique.|  
|`Delegate`|Équivalent à `ClassicCom`.|  
|`InhibitFtmBase`|Désactive `FtmBase` prise en charge de `__WRL_CONFIGURATION_LEGACY__` n’est pas défini.|  
|`InhibitWeakReference`|Désactive la prise en charge de la référence faible.|  
|`WinRt`|Une classe Windows Runtime.|  
|`WinRtClassicComMix`|Combinaison de `WinRt` et `ClassicCom`.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)