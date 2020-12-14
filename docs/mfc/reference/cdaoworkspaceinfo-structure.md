---
description: 'En savoir plus sur : structure Cdaoworkspaceinfo,'
title: CDaoWorkspaceInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: b89e8787c2103244535e9458650f1f104478b748
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222201"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo, structure

La `CDaoWorkspaceInfo` structure contient des informations sur un espace de travail défini pour l’accès aux bases de données DAO (Data Access Objects).

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
Nomme l’objet Workspace de manière unique. Pour récupérer directement la valeur de cette propriété, appelez la fonction membre [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) de l’objet querydef. Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO.

*m_strUserName*<br/>
Valeur qui représente le propriétaire d’un objet Workspace. Pour obtenir des informations connexes, consultez la rubrique « propriété UserName » dans l’aide de DAO.

*m_bIsolateODBCTrans*<br/>
Valeur qui indique si plusieurs transactions qui impliquent la même base de données ODBC sont isolées. Pour plus d’informations, consultez [CDaoWorkspace :: SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Pour obtenir des informations connexes, consultez la rubrique « propriété IsolateODBCTrans » dans l’aide de DAO.

## <a name="remarks"></a>Notes

L’espace de travail est un objet de la classe [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Les références à Primary, Secondary et All ci-dessus indiquent comment les informations sont retournées par la fonction membre [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) dans la classe `CDaoWorkspace` .

Les informations récupérées par la fonction membre [CDaoWorkspace :: GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) sont stockées dans une `CDaoWorkspaceInfo` structure. `CDaoWorkspaceInfo` définit également une `Dump` fonction membre dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoWorkspaceInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace (classe)](../../mfc/reference/cdaoworkspace-class.md)
