---
description: 'En savoir plus sur : structure CDaoTableDefInfo'
title: CDaoTableDefInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDefInfo
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
ms.openlocfilehash: 953a255b35860dcce0ac8d3ef5081951dd15c344
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247967"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo, structure

La `CDaoTableDefInfo` structure contient des informations sur un objet TableDef défini pour les objets d’accès aux données (DAO).

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
Nomme l’objet TableDef de manière unique. Pour récupérer directement la valeur de cette propriété, appelez la fonction membre [GetName](../../mfc/reference/cdaotabledef-class.md#getname) de l’objet TableDef. Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO.

*m_bUpdatable*<br/>
Indique si les modifications peuvent être apportées à la table. La méthode la plus rapide pour déterminer si une table peut être mise à jour consiste à ouvrir un `CDaoTableDef` objet pour la table et à appeler la fonction membre [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) de l’objet. `CanUpdate` retourne toujours une valeur différente de zéro (TRUE) pour un objet TableDef nouvellement créé et 0 (FALSe) pour un objet TableDef attaché. Un nouvel objet TableDef ne peut être ajouté qu’à une base de données pour laquelle l’utilisateur actuel dispose d’une autorisation d’écriture. Si la table contient uniquement des champs pouvant être mis à jour, `CanUpdate` retourne 0. Quand un ou plusieurs champs peuvent être mis à jour, retourne une valeur `CanUpdate` différente de zéro. Vous ne pouvez modifier que les champs pouvant être mis à jour. Pour plus d’informations, consultez la rubrique « propriété pouvant être mise à jour » dans l’aide de DAO.

*m_lAttributes*<br/>
Spécifie les caractéristiques de la table représentée par l’objet TableDef. Pour récupérer les attributs actuels d’un objet TableDef, appelez sa fonction membre [GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes) . La valeur retournée peut être une combinaison de ces constantes longues (à l’aide de l’opérateur de bits or (**&#124;**)) :

- `dbAttachExclusive` Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que la table est une table attachée ouverte pour une utilisation exclusive.

- `dbAttachSavePWD` Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID d’utilisateur et le mot de passe de la table attachée sont enregistrés avec les informations de connexion.

- `dbSystemObject` Indique que la table est une table système fournie par le moteur de base de données Microsoft Jet. (En lecture seule.)

- `dbHiddenObject` Indique que la table est une table cachée fournie par le moteur de base de données Microsoft Jet (pour une utilisation temporaire). (En lecture seule.)

- `dbAttachedTable` Indique que la table est une table attachée à partir d’une base de données non ODBC, telle qu’une base de données Paradox.

- `dbAttachedODBC` Indique que la table est une table attachée à partir d’une base de données ODBC, par exemple Microsoft SQL Server.

*m_dateCreated*<br/>
Date et heure de création de la table. Pour récupérer directement la date à laquelle la table a été créée, appelez la fonction membre [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) de l' `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez les commentaires ci-dessous. Pour obtenir des informations connexes, consultez la rubrique « Propriétés DateCreated, LastUpdated » dans l’aide de DAO.

*m_dateLastUpdated*<br/>
Date et heure de la dernière modification apportée à la conception de la table. Pour récupérer directement la date de la dernière mise à jour de la table, appelez la fonction membre [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) de l' `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez les commentaires ci-dessous. Pour obtenir des informations connexes, consultez la rubrique « Propriétés DateCreated, LastUpdated » dans l’aide de DAO.

*m_strSrcTableName*<br/>
Spécifie le nom d’une table attachée, le cas échéant. Pour récupérer directement le nom de la table source, appelez la fonction membre [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) de l' `CDaoTableDef` objet associé à la table.

*m_strConnect*<br/>
Fournit des informations sur la source d’une base de données ouverte. Vous pouvez vérifier cette propriété en appelant la fonction membre [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) de votre `CDaoTableDef` objet. Pour plus d’informations sur les chaînes de connexion, consultez `GetConnect` .

*m_strValidationRule*<br/>
Valeur qui valide les données dans les champs TableDef à mesure qu’ils sont modifiés ou ajoutés à une table. La validation est prise en charge uniquement pour les bases de données qui utilisent le moteur de base de données Microsoft Jet. Pour récupérer directement la règle de validation, appelez la fonction membre [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) de l' `CDaoTableDef` objet associé à la table. Pour obtenir des informations connexes, consultez la rubrique « propriété ValidationRule » dans l’aide de DAO.

*m_strValidationText*<br/>
Valeur qui spécifie le texte du message que votre application doit afficher si la règle de validation spécifiée par la propriété ValidationRule n’est pas satisfaite. Pour obtenir des informations connexes, consultez la rubrique « propriété MessageSiErreur » dans l’aide de DAO.

*m_lRecordCount*<br/>
Nombre d’enregistrements accessibles dans un objet TableDef. Ce paramètre de propriété est en lecture seule. Pour récupérer directement le nombre d’enregistrements, appelez la fonction membre [GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount) de l' `CDaoTableDef` objet. La documentation de `GetRecordCount` décrit le nombre d’enregistrements. Notez que la récupération de ce nombre peut être une opération longue si la table contient de nombreux enregistrements.

## <a name="remarks"></a>Notes

TableDef est un objet de la classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Les références à Primary, Secondary et All ci-dessus indiquent comment les informations sont retournées par la fonction membre [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) dans la classe `CDaoDatabase` .

Les informations récupérées par la fonction membre [CDaoDatabase :: GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) sont stockées dans une `CDaoTableDefInfo` structure. Appelez la `GetTableDefInfo` fonction membre de l' `CDaoDatabase` objet dans la collection d’objets TableDef dans laquelle l’objet TableDef est stocké. `CDaoTableDefInfo` définit également une `Dump` fonction membre dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoTableDefInfo` objet.

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mise à jour pour la dernière fois. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers afin d’éviter les incohérences dans les paramètres de propriété DateCreated et LastUpdated.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[Classe CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
