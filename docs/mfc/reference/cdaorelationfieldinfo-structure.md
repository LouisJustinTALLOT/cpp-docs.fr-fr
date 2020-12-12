---
description: 'En savoir plus sur : structure Cdaorelationfieldinfo,'
title: CDaoRelationFieldInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CDaoRelationFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
ms.openlocfilehash: eb470752a9e9da5f610dd59976f2716fa1c4e18a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248162"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo, structure

La `CDaoRelationFieldInfo` structure contient des informations sur un champ dans une relation définie pour les objets d’accès aux données (DAO).

## <a name="syntax"></a>Syntaxe

```
struct CDaoRelationFieldInfo
{
    CString m_strName;           // Primary
    CString m_strForeignName;    // Primary
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Nom du champ dans la table primaire de la relation.

*m_strForeignName*<br/>
Nom du champ dans la table étrangère de la relation.

## <a name="remarks"></a>Notes

Un objet relation DAO spécifie les champs d’une table primaire et les champs d’une table étrangère qui définissent la relation. Les références à Primary dans la définition de structure ci-dessus indiquent comment les informations sont retournées dans le `m_pFieldInfos` membre d’un objet [cdaorelationinfo,](../../mfc/reference/cdaorelationinfo-structure.md) obtenu en appelant la fonction membre [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) de la classe `CDaoDatabase` .

Les objets relation et les objets de champ de relation ne sont pas représentés par une classe MFC. Au lieu de cela, les objets DAO sous-jacents objets MFC de la classe [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) contiennent une collection d’objets relation, appelée collection relations. Chaque objet relation, à son tour, contient une collection d’objets de champ de relation. Chaque objet de champ de relation met en corrélation un champ de la table primaire avec un champ de la table étrangère. Pris ensemble, les objets de champ de relation définissent un groupe de champs dans chaque table, qui définissent ensemble la relation. `CDaoDatabase` vous permet d’accéder aux objets relation avec un `CDaoRelationInfo` objet en appelant la `GetRelationInfo` fonction membre. L' `CDaoRelationInfo` objet, puis, possède un membre de données, `m_pFieldInfos` , qui pointe vers un tableau d' `CDaoRelationFieldInfo` objets.

Appelez la fonction membre [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) de l' `CDaoDatabase` objet conteneur dans dont la collection relations est stockée dans l’objet relation qui vous intéresse. Ensuite, accédez au `m_pFieldInfos` membre de l’objet [cdaorelationinfo,](../../mfc/reference/cdaorelationinfo-structure.md) . `CDaoRelationFieldInfo` définit également une `Dump` fonction membre dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoRelationFieldInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Cdaorelationinfo,, structure](../../mfc/reference/cdaorelationinfo-structure.md)
