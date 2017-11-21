---
title: Structure de _ATL_COM_MODULE70 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs: C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a269820c5a0965553989bc57d7c239aa95e527ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="atlcommodule70-structure"></a>Structure de _ATL_COM_MODULE70
Utilisé par le code relatif à COM dans ATL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```  
  
## <a name="members"></a>Membres  
 `cbSize`  
 La taille de la structure utilisée pour le contrôle de version.  
  
 `m_hInstTypeLib`  
 L’instance de la poignée dans la bibliothèque de type pour ce module.  
  
 **m_ppAutoObjMapFirst**  
 Adresse de l’élément de tableau indiquant le début des entrées de mappage d’objet pour ce module.  
  
 **m_ppAutoObjMapLast**  
 Adresse de l’élément de tableau indiquant la fin des entrées de mappage d’objet pour ce module.  
  
 `m_csObjMap`  
 Section critique pour sérialiser l’accès pour les entrées de mappage d’objet. Utilisé en interne par ATL.  
  
## <a name="remarks"></a>Remarques  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) est défini comme un typedef de `_ATL_COM_MODULE70`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures](../../atl/reference/atl-structures.md)





