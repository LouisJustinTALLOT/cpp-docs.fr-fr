---
title: Platform::IDisposable (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
dev_langs:
- C++
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 68c5425d5d65acc194287a97068df7da15f37275
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086967"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable (interface)
Utilisée pour libérer des ressources non managées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public interface class IDisposable  
```  
  
## <a name="attributes"></a>Attributs  
 **GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")  
  
 **VersionAttribute**(NTDDI_WIN8)  
  
### <a name="members"></a>Membres  
 L’interface IDisposable hérite de l’interface IUnknown. IDisposable a également les types de membre suivants :  
  
 **Méthodes**  
  
 L’interface IDisposable possède les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|Suppression|Utilisée pour libérer des ressources non managées.|  
  
### <a name="requirements"></a>Spécifications  
 **Minimum pris en charge le client :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform