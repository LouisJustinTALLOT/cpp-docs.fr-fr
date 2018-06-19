---
title: Structure de _ATL_MODULE70 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a374ee01387c576a5d1a727857badc7ef7139ad
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255464"
---
# <a name="atlmodule70-structure"></a>Structure de _ATL_MODULE70
Contient les données utilisées par chaque module ATL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```  
  
## <a name="members"></a>Membres  
 `cbSize`  
 La taille de la structure utilisée pour le contrôle de version.  
  
 `m_nLockCnt`  
 Nombre de références pour déterminer la durée pendant laquelle le module doit rester actif.  
  
 **m_pTermFuncs**  
 Fonctions de pistes qui ont été inscrits pour être appelée lorsque ATL s’arrête.  
  
 **m_csStaticDataInitAndTypeInfo**  
 Permet de coordonner l’accès aux données internes dans les situations multithreads.  
  
## <a name="remarks"></a>Notes  
 [_ATL_MODULE](atl-typedefs.md#_atl_module) est défini comme un typedef de `_ATL_MODULE70`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
## <a name="see-also"></a>Voir aussi  
  [Les classes et structs](../../atl/reference/atl-classes.md)







