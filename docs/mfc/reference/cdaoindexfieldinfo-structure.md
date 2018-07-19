---
title: Cdaoindexfieldinfo, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37149e2a4a2780c97cc7c2774c64e9a6037d37a7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337877"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo, structure
Le `CDaoIndexFieldInfo` structure contient des informations sur un objet de champ index défini pour les objets d’accès aux données (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoIndexFieldInfo  
{  
    CString m_strName;          // Primary  
    BOOL m_bDescending;         // Primary  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 *m_strName*  
 Identifie l’objet de champ d’index. Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.  
  
 *m_bDescending*  
 Indique l’ordre d’index défini par l’objet index. TRUE si l’ordre est décroissant.  
  
## <a name="remarks"></a>Notes  
 Un objet de l’index peut avoir un nombre de champs, indiquant les champs d’un objet tabledef (ou un jeu d’enregistrements basé sur une table) est indexé sur. Les références dans la région primaire ci-dessus indiquent la façon dont les informations sont retournées dans le `m_pFieldInfos` membre d’un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objet obtenu en appelant le `GetIndexInfo` fonction membre de classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Objets index et objets de champ d’index ne sont pas représentées par une classe MFC. Au lieu de cela, le DAO des objets MFC sous-jacente de la classe d’objets [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contiennent une collection d’objets index, appelée la collection d’index. Chaque objet d’index contient à son tour, une collection d’objets de champ. Ces classes fournissent des fonctions de membre pour accéder à des éléments individuels des informations d’index, ou vous pouvez y accéder à la fois avec un `CDaoIndexInfo` objet en appelant le `GetIndexInfo` fonction membre de l’objet conteneur. Le `CDaoIndexInfo` objet, a ensuite, un membre de données, `m_pFieldInfos`, qui pointe vers un tableau de `CDaoIndexFieldInfo` objets.  
  
 Appelez le `GetIndexInfo` fonction membre de l’objet recordset ou tabledef contenant dans les index dont la collection est stocké l’objet index vous intéresse. Ensuite accéder à la `m_pFieldInfos` membre de la [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objet. La longueur de la `m_pFieldInfos` tableau est stocké dans `m_nFields`. `CDaoIndexFieldInfo` définit également un `Dump` génère de la fonction membre en mode de débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoIndexFieldInfo` objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

