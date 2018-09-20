---
title: CDaoTableDefInfo, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0563cf930d9722adf175a2b82c1e7788ea3d066a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415822"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo, structure

Le `CDaoTableDefInfo` structure contient des informations sur un objet tabledef défini pour les objets d’accès aux données (DAO).

## <a name="syntax"></a>Syntaxe

```
struct CDaoTableDefInfo
{
    CString m_strName;               // Primary
    BOOL m_bUpdatable;               // Primary
    long m_lAttributes;              // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    CString m_strSrcTableName;       // Secondary
    CString m_strConnect;            // Secondary
    CString m_strValidationRule;     // All
    CString m_strValidationText;     // All
    long m_lRecordCount;             // All
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Identifiant de manière unique l’objet tabledef. Pour récupérer la valeur de cette propriété directement, appelez l’objet tabledef [GetName](../../mfc/reference/cdaotabledef-class.md#getname) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.

*m_bUpdatable*<br/>
Indique si les modifications peuvent être apportées à la table. La méthode rapide pour déterminer si une table est modifiable consiste à ouvrir un `CDaoTableDef` de l’objet pour la table et appeler l’objet [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) fonction membre. `CanUpdate` Retourne toujours différente de zéro (TRUE) pour un objet tabledef nouvellement créé et 0 (FALSE) pour un objet tabledef attaché. Un nouvel objet tabledef peut être ajouté uniquement à une base de données pour lequel l’utilisateur actuel a l’autorisation d’écriture. Si la table contient uniquement des champs assimilables, `CanUpdate` retourne 0. Lorsqu’un ou plusieurs champs sont modifiables, `CanUpdate` retourne différente de zéro. Vous pouvez modifier que les champs modifiables. Pour plus d’informations, consultez la rubrique « Propriété actualisable » dans l’aide de DAO.

*m_lAttributes*<br/>
Spécifie les caractéristiques de la table représentée par l’objet tabledef. Pour récupérer les attributs actuels d’un objet, appelez sa [GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes) fonction membre. La valeur retournée peut être une combinaison de ces constantes longues (à l’aide de l’opération de bits OR (**&#124;**) opérateur) :

- `dbAttachExclusive` Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique la table est une table attachée ouverte pour une utilisation exclusive.

- `dbAttachSavePWD` Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID utilisateur et le mot de passe pour la table jointe sont enregistrées avec les informations de connexion.

- `dbSystemObject` Indique la table est une table système fournie par le moteur de base de données Microsoft Jet. (En lecture seule.)

- `dbHiddenObject` Indique la table est une table masquée fournie par le moteur de base de données Microsoft Jet (pour une utilisation temporaire). (En lecture seule.)

- `dbAttachedTable` Indique la table est une table jointe à partir d’une base de données non-ODBC, comme une base de données Paradox.

- `dbAttachedODBC` Indique la table est une table jointe à partir d’une base de données ODBC, telles que Microsoft SQL Server.

*m_dateCreated*<br/>
Date et heure de que création de la table. Pour récupérer directement la date de la table a été créée, appelez le [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) fonction membre de la `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez les commentaires ci-dessous. Pour plus d’informations, consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.

*m_dateLastUpdated*<br/>
La date et l’heure de la dernière modification apportée à la conception de la table. Pour récupérer directement la date de dernière mise à jour de la table, appelez le [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) fonction membre de la `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez les commentaires ci-dessous. Pour plus d’informations, consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.

*m_strSrcTableName*<br/>
Spécifie le nom d’une table jointe, le cas échéant. Pour extraire directement le nom de la table source, appelez le [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) fonction membre de la `CDaoTableDef` objet associé à la table.

*m_strConnect*<br/>
Fournit des informations sur la source d’une base de données ouverte. Vous pouvez vérifier cette propriété en appelant le [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) fonction membre de votre `CDaoTableDef` objet. Pour plus d’informations sur les chaînes de connexion, consultez `GetConnect`.

*m_strValidationRule*<br/>
Une valeur qui valide les données dans les champs tabledef car ils sont modifiées ou ajoutées à une table. La validation est pris en charge uniquement pour les bases de données qui utilisent le moteur de base de données Microsoft Jet. Pour récupérer directement la règle de validation, appelez le [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) fonction membre de la `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO.

*m_strValidationText*<br/>
Une valeur qui spécifie le texte du message que votre application doit s’afficher si la règle de validation spécifiée par la propriété ValidationRule n’est pas satisfaite. Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO.

*m_lRecordCount*<br/>
Le nombre d’enregistrements auquel accédé dans un objet tabledef. Cette propriété est en lecture seule. Pour extraire directement le nombre d’enregistrements, appelez le [GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount) fonction membre de la `CDaoTableDef` objet. La documentation de `GetRecordCount` décrit le nombre d’enregistrements supplémentaires. Notez que la récupération de ce nombre peut être une opération longue si la table contient de nombreux enregistrements.

## <a name="remarks"></a>Notes

Cet objet est un objet de classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Les références à principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) fonction membre dans la classe `CDaoDatabase`.

Les informations récupérées par le [CDaoDatabase::GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) fonction membre est stockée dans un `CDaoTableDefInfo` structure. Appelez le `GetTableDefInfo` fonction membre de la `CDaoDatabase` objet dans dont TableDefs (collection) est stocké l’objet tabledef. `CDaoTableDefInfo` définit également un `Dump` génère de la fonction membre en mode de débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoTableDefInfo` objet.

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mises à jour. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers afin d’éviter des incohérences dans le DateCreated et les paramètres de propriété LastUpdated.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)
