---
description: 'En savoir plus sur : structure Cdaorelationinfo,'
title: CDaoRelationInfo, structure
ms.date: 06/25/2018
f1_keywords:
- CDaoRelationInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
ms.openlocfilehash: efcc880d30dd18108005d9c4f265238b81551532
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222240"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo, structure

La `CDaoRelationInfo` structure contient des informations sur une relation définie entre les champs de deux tables dans un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
struct CDaoRelationInfo
{
    CDaoRelationInfo();                     // Constructor
    CString m_strName;                      // Primary
    CString m_strTable;                     // Primary
    CString m_strForeignTable;              // Primary
    long m_lAttributes;                     // Secondary
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary
    short m_nFields;                        // Secondary
    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Nomme l’objet relation de manière unique. Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO.

*m_strTable*<br/>
Nomme la table primaire dans la relation.

*m_strForeignTable*<br/>
Nomme la table étrangère dans la relation. Une table étrangère est une table utilisée pour contenir des clés étrangères. En règle générale, vous utilisez une table étrangère pour établir ou appliquer l’intégrité référentielle. La table étrangère est généralement du côté « plusieurs » d’une relation un-à-plusieurs. Exemples de tables étrangères : tables contenant des codes pour les États américains, les provinces canadiennes ou les commandes client.

*m_lAttributes*<br/>
Contient des informations sur le type de relation. La valeur de ce membre peut être l’une des suivantes :

- `dbRelationUnique` La relation est un-à-un.

- `dbRelationDontEnforce` La relation n’est pas appliquée (aucune intégrité référentielle).

- `dbRelationInherited` La relation existe dans une base de données non active qui contient les deux tables attachées.

- `dbRelationLeft` La relation est une jointure de gauche. Une jointure externe gauche inclut tous les enregistrements de la première (main gauche) de deux tables, même s’il n’y a aucune valeur correspondante pour les enregistrements dans la deuxième table (à droite).

- `dbRelationRight` La relation est une jointure appropriée. Une jointure externe droite inclut tous les enregistrements de la seconde (droite) de deux tables, même s’il n’y a aucune valeur correspondante pour les enregistrements dans la première table (à gauche).

- `dbRelationUpdateCascade` Les mises à jour s’effectuent en cascade.

- `dbRelationDeleteCascade` Les suppressions s’effectuent en cascade.

*m_pFieldInfos*<br/>
Pointeur vers un tableau de structures [cdaorelationfieldinfo,](../../mfc/reference/cdaorelationfieldinfo-structure.md) . Le tableau contient un objet pour chaque champ de la relation. Le `m_nFields` membre de données donne le nombre d’éléments du tableau.

*m_nFields*<br/>
Nombre d' `CDaoRelationFieldInfo` objets dans la `m_pFieldInfos` donnée membre.

## <a name="remarks"></a>Notes

Les références à Primary et Secondary ci-dessus indiquent comment les informations sont retournées par la fonction membre [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) dans la classe `CDaoDatabase` .

Les objets de relation ne sont pas représentés par une classe MFC. Au lieu de cela, l’objet DAO sous-jacent à un objet MFC de la `CDaoDatabase` classe gère une collection d’objets relation : `CDaoDatabase` fournit des fonctions membres pour accéder à certains éléments d’informations de relation, ou vous pouvez y accéder en même temps avec un `CDaoRelationInfo` objet en appelant la `GetRelationInfo` fonction membre de l’objet de base de données conteneur.

Les informations récupérées par la fonction membre [CDaoDatabase :: GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) sont stockées dans une `CDaoRelationInfo` structure. `CDaoRelationInfo` définit également une `Dump` fonction membre dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoRelationInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Cdaorelationfieldinfo,, structure](../../mfc/reference/cdaorelationfieldinfo-structure.md)
