---
title: Classe de valeur Platform::SizeT | Documents Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs:
- C++
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f3646c07d5f351ac0c357fa99efc0148e643271
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="platformsizet-value-class"></a>Classe de valeur Platform::SizeT
Représente la taille d'un objet. SizeT est un type de données non signé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class SizeT sealed : ValueType  
```  
  
### <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|[SizeT::SizeT, constructeur](#ctor)|Initialise une nouvelle instance de la classe avec la valeur spécifiée.|  
  
### <a name="requirements"></a>Configuration requise  
 **Minimum pris en charge le client :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform  
  
 **Métadonnées :** platform.winmd  

 ## <a name="ctor"></a>  SizeT::SizeT (constructeur)
Initialise une nouvelle instance de SizeT avec la valeur spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
SizeT( uint32 value1 );   SizeT( void* value2 );  
```  
  
### <a name="parameters"></a>Paramètres  
 value1  
 Valeur 32 bits non signée.  
  
 value2  
 Pointeur vers une valeur 32 bits non signée.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)