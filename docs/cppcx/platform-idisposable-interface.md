---
title: Platform::IDisposable (Interface) | Microsoft Docs
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3899c25d71ad08cc058280271080c19d11222ed
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751006"
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
  
### <a name="requirements"></a>Configuration requise  
 **Minimum de client pris en charge :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform