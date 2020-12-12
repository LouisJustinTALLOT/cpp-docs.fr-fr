---
description: 'En savoir plus sur : structure CDaoQueryDefInfo'
title: CDaoQueryDefInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: 46b9b49d91d3d005d941eb585663c205fe30b2da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271809"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo, structure

La `CDaoQueryDefInfo` structure contient des informations sur un objet querydef défini pour les objets d’accès aux données (DAO).

## <a name="syntax"></a>Syntaxe

```
struct CDaoQueryDefInfo
{
    CString m_strName;               // Primary
    short m_nType;   // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    BOOL m_bUpdatable;               // Secondary
    BOOL m_bReturnsRecords;          // Secondary
    CString m_strSQL;                // All
    CString m_strConnect;            // All
    short m_nODBCTimeout;            // All
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Nomme l’objet querydef de manière unique. Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO. Appelez [CDaoQueryDef :: GetName](../../mfc/reference/cdaoquerydef-class.md#getname) pour récupérer cette propriété directement.

*m_nType*<br/>
Valeur qui indique le type opérationnel d’un objet querydef. Il peut s'agir de l'une des valeurs suivantes :

- `dbQSelect` SELECT : la requête sélectionne les enregistrements.

- `dbQAction` Action : la requête déplace ou modifie des données, mais ne retourne pas d’enregistrements.

- `dbQCrosstab` Crosstab : la requête retourne des données dans un format de feuille de calcul.

- `dbQDelete` Supprimer : la requête supprime un ensemble de lignes spécifiées.

- `dbQUpdate` Mise à jour : la requête modifie un ensemble d’enregistrements.

- `dbQAppend` Append : la requête ajoute de nouveaux enregistrements à la fin d’une table ou d’une requête.

- `dbQMakeTable` Make-Table : la requête crée une nouvelle table à partir d’un jeu d’enregistrements.

- `dbQDDL` Définition des données : la requête affecte la structure des tables ou leurs parties.

- `dbQSQLPassThrough` Pass-through : l’instruction SQL est transmise directement au serveur principal de la base de données, sans traitement intermédiaire.

- `dbQSetOperation` Union : la requête crée un objet Recordset de type instantané contenant les données de tous les enregistrements spécifiés dans deux tables ou plus, avec tous les enregistrements en double supprimés. Pour inclure les doublons, ajoutez le mot clé **All** dans l’instruction SQL de la querydef.

- `dbQSPTBulk` Utilisé avec `dbQSQLPassThrough` pour spécifier une requête qui ne retourne pas d’enregistrements.

> [!NOTE]
> Pour créer une requête SQL directe, vous ne définissez pas la `dbQSQLPassThrough` constante. Cela est défini automatiquement par le moteur de base de données Microsoft Jet lorsque vous créez un objet querydef et définissez la propriété Connect.

Pour plus d’informations, consultez la rubrique « type Property » dans l’aide de DAO.

*m_dateCreated*<br/>
Date et heure de création de l’objet querydef. Pour récupérer directement la date de création de la querydef, appelez la fonction membre [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) de l' `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez les commentaires ci-dessous. Consultez également la rubrique « Propriétés DateCreated, LastUpdated » dans l’aide de DAO.

*m_dateLastUpdated*<br/>
Date et heure de la dernière modification apportée à l’objet querydef. Pour récupérer directement la date de la dernière mise à jour de la table, appelez la fonction membre [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) de l’objet querydef. Pour plus d’informations, consultez les commentaires ci-dessous. Et reportez-vous à la rubrique « DateCreated, LastUpdated Properties » dans l’aide de DAO.

*m_bUpdatable*<br/>
Indique si des modifications peuvent être apportées à un objet querydef. Si cette propriété a la valeur TRUE, l’objet querydef peut être mis à jour ; Sinon, ce n’est pas le cas. Actualisable signifie que la définition de la requête de l’objet querydef peut être modifiée. La propriété pouvant être mise à jour d’un objet querydef a la valeur TRUE si la définition de la requête peut être mise à jour, même si le jeu d’enregistrements résultant ne peut pas être mis à jour. Pour récupérer cette propriété directement, appelez la fonction membre [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) de la querydef. Pour plus d’informations, consultez la rubrique « propriété pouvant être mise à jour » dans l’aide de DAO.

*m_bReturnsRecords*<br/>
Indique si une requête SQL directe à une base de données externe retourne des enregistrements. Si cette propriété a la valeur TRUE, la requête retourne des enregistrements. Pour récupérer directement cette propriété, appelez [CDaoQueryDef :: GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Toutes les requêtes SQL directes vers des bases de données externes ne retournent pas d’enregistrements. Par exemple, une instruction SQL **Update** met à jour les enregistrements sans retourner d’enregistrements, tandis qu’une instruction SQL **Select** ne retourne pas d’enregistrements. Pour plus d’informations, consultez la rubrique « propriété ReturnsRecords » dans l’aide de DAO.

*m_strSQL*<br/>
Instruction SQL qui définit la requête exécutée par un objet querydef. La propriété SQL contient l’instruction SQL qui détermine la façon dont les enregistrements sont sélectionnés, regroupés et triés lorsque vous exécutez la requête. Vous pouvez utiliser la requête pour sélectionner des enregistrements à inclure dans un objet Recordset de type feuille de réponse dynamique ou instantané. Vous pouvez également définir des requêtes en bloc pour modifier des données sans retourner d’enregistrements. Vous pouvez récupérer directement la valeur de cette propriété en appelant la fonction membre [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) de la querydef.

*m_strConnect*<br/>
Fournit des informations sur la source d’une base de données utilisée dans une requête directe. Ces informations prennent la forme d’une chaîne de connexion. Pour plus d’informations sur les chaînes de connexion et pour plus d’informations sur la récupération directe de la valeur de cette propriété, consultez la fonction membre [CDaoDatabase :: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) .

*m_nODBCTimeout*<br/>
Nombre de secondes pendant lesquelles le moteur de base de données Microsoft Jet attend avant qu’une erreur de délai d’attente se produise lors de l’exécution d’une requête sur une base de données ODBC. Lorsque vous utilisez une base de données ODBC, telle que Microsoft SQL Server, il peut y avoir des retards en raison du trafic réseau ou de l’utilisation intensive du serveur ODBC. Au lieu d’attendre indéfiniment, vous pouvez spécifier la durée d’attente du moteur Microsoft Jet avant qu’il génère une erreur. La valeur du délai d’attente par défaut est de 60 secondes. Vous pouvez récupérer directement la valeur de cette propriété en appelant la fonction membre [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) de la querydef. Pour plus d’informations, consultez la rubrique « propriété ODBCTimeout » dans l’aide de DAO.

## <a name="remarks"></a>Notes

Querydef est un objet de la classe [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Les références à Primary, Secondary et All ci-dessus indiquent comment les informations sont retournées par la fonction membre [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) dans la classe `CDaoDatabase` .

Les informations récupérées par la fonction membre [CDaoDatabase :: GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) sont stockées dans une `CDaoQueryDefInfo` structure. Appelez `GetQueryDefInfo` pour l’objet de base de données dans la collection QueryDefs dans laquelle l’objet querydef est stocké. `CDaoQueryDefInfo` définit également une `Dump` fonction membre dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoQueryDefInfo` objet. `CDaoDatabase`La classe fournit également des fonctions membres pour accéder directement à toutes les propriétés retournées dans un `CDaoQueryDefInfo` objet. par conséquent, vous devrez probablement appeler `GetQueryDefInfo` .

Lorsque vous ajoutez un nouvel objet champ ou paramètre à la collection de champs ou de paramètres d’un objet QueryDef, une exception est levée si la base de données sous-jacente ne prend pas en charge le type de données spécifié pour le nouvel objet.

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel l’objet querydef a été créé ou mis à jour pour la dernière fois. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers à l’aide de la commande **net Time** pour éviter les incohérences dans les paramètres de propriété DateCreated et LastUpdated.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef (classe)](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Classe CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
