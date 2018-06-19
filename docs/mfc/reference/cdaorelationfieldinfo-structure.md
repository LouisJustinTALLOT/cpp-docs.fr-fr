---
title: Cdaorelationfieldinfo, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRelationFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e53daaaa5ef4997762342cbfb74ae4d5fa96097d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366159"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo, structure
Le `CDaoRelationFieldInfo` structure contient des informations sur un champ dans une relation définie pour les objets d’accès aux données (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoRelationFieldInfo  
{  
    CString m_strName;           // Primary  
    CString m_strForeignName;    // Primary  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 `m_strName`  
 Le nom du champ dans la table primaire de la relation.  
  
 `m_strForeignName`  
 Le nom du champ dans la table étrangère de la relation.  
  
## <a name="remarks"></a>Notes  
 Un objet de relation DAO spécifie les champs dans une table principale et les champs d’une table étrangère qui définissent la relation. Les références au principal dans la définition de la structure indiquent comment les informations sont retournées dans le `m_pFieldInfos` membre d’un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objet obtenu en appelant le [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)fonction membre de classe `CDaoDatabase`.  
  
 Les objets de relation et les objets de champ de relation ne sont pas représentées par une classe MFC. Au lieu de cela, le DAO des objets MFC sous-jacente de la classe d’objets [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) contient une collection d’objets de relation, appelée la collection de Relations. Chaque objet de relation, contient une collection d’objets de champ de relation. Chaque objet de champ de relation met en corrélation un champ dans la table primaire avec un champ dans la table étrangère. Dans leur ensemble, les objets de champ relation définissent un groupe de champs dans chaque table, qui définissent la relation. `CDaoDatabase` Permet d’accéder à des objets de relation avec un `CDaoRelationInfo` objet en appelant le `GetRelationInfo` fonction membre. Le `CDaoRelationInfo` objet, a, un membre de données, `m_pFieldInfos`, qui pointe vers un tableau de `CDaoRelationFieldInfo` objets.  
  
 Appelez le [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) fonction membre de conteneur `CDaoDatabase` dans dont les Relations collection est stocké l’objet de relation que vous êtes intéressé par l’objet. Puis accéder à la `m_pFieldInfos` membre de la [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objet. `CDaoRelationFieldInfo` définit également un `Dump` builds de la fonction membre en mode débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoRelationFieldInfo` objet.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo, structure](../../mfc/reference/cdaorelationinfo-structure.md)
