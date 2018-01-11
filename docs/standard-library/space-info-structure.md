---
title: space_info, structure | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: filesystem/std::tr2::sys::space_info
dev_langs: C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50657e33becd0fb2dae94d515f82120d6a71e342
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="spaceinfo-structure"></a>space_info, structure
Contient des informations sur un volume.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|`unsigned long long available`|Représente le nombre d’octets qui sont disponibles pour représenter des données sur le volume.|  
|`unsigned long long capacity`|Représente le nombre total d’octets que le volume peut représenter.|  
|`unsigned long long free`|Représente le nombre d’octets qui ne sont pas utilisés pour représenter des données sur le volume.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<filesystem >  
  
 **Espace de noms :** std::experimental::filesystem  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)   
 [espace](http://msdn.microsoft.com/en-us/7fce0b0e-523b-4598-b218-47245d0204ca)   
 [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)

