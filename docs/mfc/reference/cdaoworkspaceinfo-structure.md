---
title: Cdaoworkspaceinfo, Structure | Microsoft Docs
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
ms.openlocfilehash: f46bfec2d74b0d1fd292b3c9852ba8ea568329a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441757"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo, structure

Le `CDaoWorkspaceInfo` structure contient des informations sur un espace de travail défini pour l’accès de base de données aux données accès objets (DAO).

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

*m_strName*<br/>
Identifiant de manière unique l’objet de l’espace de travail. Pour récupérer la valeur de cette propriété directement, appelez l’objet querydef [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.

*m_strUserName*<br/>
Une valeur qui représente le propriétaire d’un objet de l’espace de travail. Pour plus d’informations, consultez la rubrique « Propriété de nom d’utilisateur » dans l’aide de DAO.

*m_bIsolateODBCTrans*<br/>
Une valeur qui indique si plusieurs transactions qui impliquent la même base de données ODBC sont isolées. Pour plus d’informations, consultez [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Pour plus d’informations, consultez la rubrique « Propriété IsolateODBCTrans » dans l’aide de DAO.

## <a name="remarks"></a>Notes

L’espace de travail est un objet de classe [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Les références à principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) fonction membre dans la classe `CDaoWorkspace`.

Les informations récupérées par le [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) fonction membre est stockée dans un `CDaoWorkspaceInfo` structure. `CDaoWorkspaceInfo` définit également un `Dump` génère de la fonction membre en mode de débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoWorkspaceInfo` objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace, classe](../../mfc/reference/cdaoworkspace-class.md)
