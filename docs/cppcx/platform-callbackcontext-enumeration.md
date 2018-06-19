---
title: Platform::CallbackContext (énumération) | Documents Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 757de5f686bb809a5d2fb159a3ee547a20edc982
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086944"
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
  
### <a name="requirements"></a>Spécifications  
 **Minimum pris en charge le client :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform  
  
 **Métadonnées :** platform.winmd