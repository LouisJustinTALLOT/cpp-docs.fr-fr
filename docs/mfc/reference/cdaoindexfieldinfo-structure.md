---
title: CDaoIndexFieldInfo, structure
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: 10c786ef4fed9ecb3bbbb93526cd68a11e18d58c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303666"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo, structure

La structure `CDaoIndexFieldInfo` contient des informations sur un objet de champ d’index défini pour les objets d’accès aux données (DAO).

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

Un objet index peut avoir un certain nombre de champs, ce qui indique les champs sur lesquels un objet TableDef (ou un jeu d’enregistrements basé sur une table) est indexé. Les références au réplica principal ci-dessus indiquent comment les informations sont retournées dans le membre `m_pFieldInfos` d’un objet [cdaoindexinfo,](../../mfc/reference/cdaoindexinfo-structure.md) obtenu en appelant la fonction membre `GetIndexInfo` de la classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Les objets d’index et les objets de champ d’index ne sont pas représentés par une classe MFC. Au lieu de cela, les objets DAO sous-jacents les objets MFC de la classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contiennent une collection d’objets index, appelée la collection Indexes. Chaque objet d’index, à son tour, contient une collection d’objets Field. Ces classes fournissent des fonctions membres pour accéder aux éléments individuels des informations d’index, ou vous pouvez y accéder en même temps avec un objet `CDaoIndexInfo` en appelant la fonction membre `GetIndexInfo` de l’objet conteneur. L’objet `CDaoIndexInfo`, puis, a un membre de données, `m_pFieldInfos`, qui pointe vers un tableau d’objets `CDaoIndexFieldInfo`.

Appelez la fonction membre `GetIndexInfo` de l’objet TableDef ou Recordset contenant dans dont la collection d’index est stockée dans l’objet index qui vous intéresse. Ensuite, accédez au membre `m_pFieldInfos` de l’objet [cdaoindexinfo,](../../mfc/reference/cdaoindexinfo-structure.md) . La longueur du tableau de `m_pFieldInfos` est stockée dans `m_nFields`. `CDaoIndexFieldInfo` définit également une fonction membre `Dump` dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un objet `CDaoIndexFieldInfo`.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef :: GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset :: GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
