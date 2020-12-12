---
description: 'En savoir plus sur : structure Cdaoindexfieldinfo,'
title: CDaoIndexFieldInfo, structure
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: fe2d6bef3ce44e7418474b7f2c004942935968c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250788"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo, structure

La `CDaoIndexFieldInfo` structure contient des informations sur un objet de champ d’index défini pour les objets d’accès aux données (DAO).

DAO est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.

## <a name="syntax"></a>Syntaxe

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Nomme l’objet de champ d’index de façon unique. Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO.

*m_bDescending*<br/>
Indique l’ordre d’index défini par l’objet index. TRUE si l’ordre est décroissant.

## <a name="remarks"></a>Notes

Un objet index peut avoir un certain nombre de champs, ce qui indique les champs sur lesquels un objet TableDef (ou un jeu d’enregistrements basé sur une table) est indexé. Les références au réplica principal ci-dessus indiquent comment les informations sont retournées dans le `m_pFieldInfos` membre d’un objet [cdaoindexinfo,](../../mfc/reference/cdaoindexinfo-structure.md) obtenu en appelant la `GetIndexInfo` fonction membre de la classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Les objets d’index et les objets de champ d’index ne sont pas représentés par une classe MFC. Au lieu de cela, les objets DAO sous-jacents les objets MFC de la classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contiennent une collection d’objets index, appelée la collection Indexes. Chaque objet d’index, à son tour, contient une collection d’objets Field. Ces classes fournissent des fonctions membres pour accéder aux éléments individuels des informations d’index, ou vous pouvez y accéder en même temps avec un `CDaoIndexInfo` objet en appelant la `GetIndexInfo` fonction membre de l’objet conteneur. L' `CDaoIndexInfo` objet, puis, possède un membre de données, `m_pFieldInfos` , qui pointe vers un tableau d' `CDaoIndexFieldInfo` objets.

Appelez la `GetIndexInfo` fonction membre de l’objet TableDef ou Recordset contenant dans dont la collection Indexes est stockée dans l’objet index qui vous intéresse. Ensuite, accédez au `m_pFieldInfos` membre de l’objet [cdaoindexinfo,](../../mfc/reference/cdaoindexinfo-structure.md) . La longueur du `m_pFieldInfos` tableau est stockée dans `m_nFields` . `CDaoIndexFieldInfo` définit également une `Dump` fonction membre dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoIndexFieldInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef :: GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset :: GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
