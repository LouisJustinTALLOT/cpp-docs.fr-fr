---
title: Cdaoworkspaceinfo, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoWorkspaceInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 705c855a817f0c6ca342e51258c7d6c1e61fa392
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951076"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo, structure
Le `CDaoWorkspaceInfo` structure contient des informations sur un espace de travail défini pour l’accès de données access (DAO) d’objets de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoWorkspaceInfo  
{  
    CString m_strName;           // Primary  
    CString m_strUserName;       // Secondary  
    BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 *m_strName*  
 Identifie l’objet de l’espace de travail. Pour récupérer la valeur de cette propriété directement, appelez l’objet querydef [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) fonction membre. Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
 *m_strUserName*  
 Une valeur qui représente le propriétaire d’un objet de l’espace de travail. Pour plus d’informations, consultez la rubrique « Propriété de nom d’utilisateur » dans l’aide de DAO.  
  
 *m_bIsolateODBCTrans*  
 Une valeur qui indique si plusieurs transactions qui impliquent la même base de données ODBC sont isolées. Pour plus d’informations, consultez [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Pour plus d’informations, consultez la rubrique « Propriété IsolateODBCTrans » dans l’aide de DAO.  
  
## <a name="remarks"></a>Notes  
 L’espace de travail est un objet de classe [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Les références au principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) fonction membre dans la classe `CDaoWorkspace`.  
  
 Les informations extraites par le [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) fonction membre est stockée dans un `CDaoWorkspaceInfo` structure. `CDaoWorkspaceInfo` définit également un `Dump` builds de la fonction membre en mode débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoWorkspaceInfo` objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace, classe](../../mfc/reference/cdaoworkspace-class.md)
