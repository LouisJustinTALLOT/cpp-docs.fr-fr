---
title: Platform::callbackcontext, énumération | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b80fe7749fdb2f91e300cff007c01001edfa557
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603036"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext (énumération)
Spécifie le contexte de thread dans lequel s’exécute une fonction de rappel (Gestionnaire d’événements).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum class CallbackContext {};  
```  
  
### <a name="members"></a>Membres  
  
|Code de type|Description|  
|---------------|-----------------|  
|Any|La fonction de rappel peut s’exécuter sur n’importe quel contexte de thread.|  
|Identique|La fonction de rappel peut s’exécuter uniquement sur le contexte de thread qui a démarré l’opération asynchrone.|  
  
### <a name="requirements"></a>Configuration requise  
 **Minimum de client pris en charge :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform  
  
 **Métadonnées :** platform.winmd