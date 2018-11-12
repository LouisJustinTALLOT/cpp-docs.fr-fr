---
title: CDaoRelationInfo, structure
ms.date: 06/25/2018
f1_keywords:
- CDaoRelationInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
ms.openlocfilehash: 1bf60bd3f076dbf682b92898d66cc5f96841c9e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627277"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo, structure

Le `CDaoRelationInfo` structure contient des informations sur une relation définie entre les champs de deux tables dans un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet.

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
Identifiant de manière unique l’objet relation. Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.

*m_strTable*<br/>
Nom de la table primaire dans la relation.

*m_strForeignTable*<br/>
Nom de la table étrangère dans la relation. Une table externe est une table utilisée pour contenir des clés étrangères. En règle générale, vous utilisez une table étrangère pour établir ou appliquer l’intégrité référentielle. La table externe est généralement sur le côté « plusieurs » d’une relation un-à-plusieurs. Exemples de tables externes contiennent des tables contenant des codes pour les États américains, provinces du Canada ou les commandes des clients.

*m_lAttributes*<br/>
Contient des informations sur le type de relation. La valeur de ce membre peut être une des opérations suivantes :

- `dbRelationUnique` Relation est-à-un.

- `dbRelationDontEnforce` Relation n’est pas (aucune intégrité référentielle).

- `dbRelationInherited` Relation existe dans une base de données non courante qui contient les deux tables jointes.

- `dbRelationLeft` La relation est une jointure gauche. Une jointure externe gauche comprend tous les enregistrements de la première (gauche) de deux tables, même si aucune valeur correspondante pour les enregistrements de la seconde table (droite).

- `dbRelationRight` La relation est une jointure droite. Une jointure externe droite inclut tous les enregistrements de la deuxième (droite) de deux tables, même si aucune valeur correspondante pour les enregistrements dans la première table (gauche).

- `dbRelationUpdateCascade` Mises à jour sont mises en cascade.

- `dbRelationDeleteCascade` Suppressions sont mises en cascade.

*m_pFieldInfos*<br/>
Un pointeur vers un tableau de [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) structures. Le tableau contient un objet pour chaque champ dans la relation. Le `m_nFields` membre de données renvoie un nombre des éléments du tableau.

*m_nFields*<br/>
Le nombre de `CDaoRelationFieldInfo` des objets dans le `m_pFieldInfos` membre de données.

## <a name="remarks"></a>Notes

Les références au principal et secondaire ci-dessus indiquent la façon dont les informations sont retournées par la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) fonction membre dans la classe `CDaoDatabase`.

Les objets de relation ne sont pas représentées par une classe MFC. Au lieu de cela, l’objet DAO sous-jacent d’un objet MFC de le `CDaoDatabase` classe maintient une collection d’objets de relation : `CDaoDatabase` fournit des fonctions de membre pour accéder à certains des éléments individuels d’informations sur la relation, ou vous peuvent y accéder à la fois avec un `CDaoRelationInfo` objet en appelant le `GetRelationInfo` fonction membre de l’objet conteneur de la base de données.

Les informations récupérées par le [CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) fonction membre est stockée dans un `CDaoRelationInfo` structure. `CDaoRelationInfo` définit également un `Dump` génère de la fonction membre en mode de débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoRelationInfo` objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="see-also"></a>Voir aussi

[CDaoRelationFieldInfo, structure](../../mfc/reference/cdaorelationfieldinfo-structure.md)
