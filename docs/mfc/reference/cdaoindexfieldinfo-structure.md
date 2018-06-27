---
title: Cdaoindexfieldinfo, Structure | Documents Microsoft
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
ms.openlocfilehash: 759f8e6f9349fdcac61f6aca81d311e3bbc39e1d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957043"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo, structure
Le `CDaoIndexFieldInfo` structure contient des informations sur un objet de champ d’index défini pour les objets d’accès aux données (DAO).  
  
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
 Identifie l’objet de champ d’index. Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
 *m_bDescending*  
 Indique l’ordre d’index défini par l’objet index. **TRUE** si l’ordre est décroissant.  
  
## <a name="remarks"></a>Notes  
 Un objet d’index peut avoir un nombre de champs, qui indique les champs d’un objet tabledef (ou un jeu d’enregistrements basé sur une table) est indexé sur. Les références au principal ci-dessus indiquent la façon dont les informations sont retournées dans le `m_pFieldInfos` membre d’un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objet obtenu en appelant le `GetIndexInfo` fonction membre de classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Objets index et objets de champ d’index ne sont pas représentées par une classe MFC. Au lieu de cela, le DAO des objets MFC sous-jacente de la classe d’objets [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contient une collection d’objets index, appelée la collection d’index. Chaque objet d’index contient à son tour, une collection d’objets de champ. Ces classes fournissent des fonctions de membre pour accéder à des informations sur les index des éléments individuels, ou vous pouvez accéder à la fois avec un `CDaoIndexInfo` objet en appelant le `GetIndexInfo` fonction membre de l’objet conteneur. Le `CDaoIndexInfo` objet, a, un membre de données, `m_pFieldInfos`, qui pointe vers un tableau de `CDaoIndexFieldInfo` objets.  
  
 Appelez le `GetIndexInfo` fonction membre de l’objet conteneur tabledef ou recordset, dont les index collection est stocké l’objet index vous intéressez. Puis accéder à la `m_pFieldInfos` membre de la [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objet. La longueur de la `m_pFieldInfos` tableau est stocké dans `m_nFields`. `CDaoIndexFieldInfo` définit également un `Dump` builds de la fonction membre en mode débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoIndexFieldInfo` objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

