---
title: Macros de l’état de l’objet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eddfc28c659d0c1eb54794d8fc76a9f3a4f9e73b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360872"
---
# <a name="object-status-macros"></a>Objet état Macros
Cette macro définit des indicateurs qui appartiennent à des contrôles ActiveX.  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Utilisé dans les contrôles ActiveX ATL pour définir le **OLEMISC** indicateurs.|  

## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS  
 Utilisé dans les contrôles ActiveX ATL pour définir les indicateurs OLEMISC.  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>Paramètres  
 *MiscStatus*  
 Indicateurs OLEMISC toutes applicables.  
  
### <a name="remarks"></a>Notes  
 Cette macro est utilisée pour définir les indicateurs OLEMISC pour un contrôle ActiveX. Reportez-vous à [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) pour plus d’informations.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>Voir aussi  
 [Macros](../../atl/reference/atl-macros.md)
