---
title: Platform::accessdeniedexception, classe | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 808de08163f0f94e4c3d0064fced7cb81f83c931
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767928"
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException, classe
Levée lorsque l'accès à une ressource ou à une fonctionnalité est refusé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable  
```  
  
### <a name="remarks"></a>Notes  
 Si vous rencontrez cette exception, vérifiez que vous avez demandé la fonctionnalité appropriée et que avez effectué les déclarations requises dans le manifeste de package de votre application. Pour plus d'informations, consultez [COMException](../cppcx/platform-comexception-class.md) .  
  
### <a name="requirements"></a>Configuration requise  
 **Minimum de client pris en charge :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform  
  
 **Métadonnées :** platform.winmd  
  
## <a name="see-also"></a>Voir aussi  
 [Platform::COMException, classe](../cppcx/platform-comexception-class.md)