---
title: CDaoQueryDefInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: e2f0325237a30989637821464c63a4d8b8000b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368933"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo, structure

La `CDaoQueryDefInfo` structure contient des informations sur un objet de requête défini pour les objets d’accès aux données (DAO).

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
Nomme uniquement l’objet de requête. Pour plus d’informations, consultez le thème "Nom Propriété" dans DAO Aide. Appelez [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) pour récupérer cette propriété directement.

*m_nType*<br/>
Une valeur qui indique le type opérationnel d’un objet requête. Il peut s'agir de l'une des valeurs suivantes :

- `dbQSelect`Sélectionnez — la requête sélectionne les enregistrements.

- `dbQAction`Action — la requête déplace ou modifie les données, mais ne renvoie pas les enregistrements.

- `dbQCrosstab`Crosstab — la requête renvoie les données dans un format de tableur.

- `dbQDelete`Supprimer — la requête supprime un ensemble de lignes spécifiées.

- `dbQUpdate`Mise à jour — la requête modifie un ensemble d’enregistrements.

- `dbQAppend`Annexe — la requête ajoute de nouveaux enregistrements à la fin d’une table ou d’une requête.

- `dbQMakeTable`Make-table — la requête crée une nouvelle table à partir d’un jeu d’enregistrements.

- `dbQDDL`Définition des données — la requête affecte la structure des tableaux ou de leurs pièces.

- `dbQSQLPassThrough`Passage — la déclaration SQL est transmise directement à la rétroendice de la base de données, sans traitement intermédiaire.

- `dbQSetOperation`Union — la requête crée un objet de type enregistrement de type instantané contenant des données de tous les enregistrements spécifiés dans deux tableaux ou plus avec des enregistrements en double supprimés. Pour inclure les doublons, ajoutez le mot clé **ALL** dans la déclaration SQL de la requête.

- `dbQSPTBulk`Utilisé `dbQSQLPassThrough` pour spécifier une requête qui ne renvoie pas les enregistrements.

> [!NOTE]
> Pour créer une requête SQL pass-through, `dbQSQLPassThrough` vous ne définissez pas la constante. Ceci est défini automatiquement par le moteur de base de données Microsoft Jet lorsque vous créez un objet requête et définissez la propriété Connect.

Pour plus d’informations, consultez le thème "Type Property" dans DAO Help.

*m_dateCreated*<br/>
La date et l’heure de la requête a été créée. Pour récupérer directement la date de création de la requête, appelez la `CDaoTableDef` fonction membre [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) de l’objet associé à la table. Voir commentaires ci-dessous pour plus d’informations. Voir également le thème "DateCreated, LastUpdated Properties" dans DAO Help.

*m_dateLastUpdated*<br/>
La date et l’heure du changement le plus récent apportés à la requête. Pour récupérer directement la date à laquelle la table a été mise à jour pour la dernière fois, appelez la fonction membre [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) de la requête. Voir commentaires ci-dessous pour plus d’informations. Et voir le sujet "DateCreated, LastUpdated Properties" dans DAO Help.

*m_bUpdatable*<br/>
Indique si des modifications peuvent être apportées à un objet de requête. Si cette propriété est VRAI, la requête est updatable; sinon, ce n’est pas le cas. Updatable signifie que la définition de requête de l’objet de requête de la requête peut être modifiée. La propriété Updatable d’un objet de requête est définie à TRUE si la définition de requête peut être mise à jour, même si le jeu d’enregistrement résultant n’est pas updatable. Pour récupérer cette propriété directement, appelez la fonction de membre [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) de la requête. Pour plus d’informations, voir le thème "Updatable Property" dans DAO Help.

*m_bReturnsRecords*<br/>
Indique si une requête de passage SQL à une base de données externe renvoie les enregistrements. Si cette propriété est VRAI, la requête renvoie les enregistrements. Pour récupérer directement cette propriété, appelez [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Toutes les requêtes de passage SQL aux bases de données externes ne retournent pas les enregistrements. Par exemple, une instruction **SQL UPDATE** met à jour les enregistrements sans retourner les enregistrements, tandis qu’une déclaration **SQL SELECT** renvoie les enregistrements. Pour plus d’informations, voir le sujet "ReturnsRecords Property" dans DAO Help.

*m_strSQL*<br/>
La déclaration SQL qui définit la requête exécutée par un objet requête. La propriété SQL contient la déclaration SQL qui détermine comment les dossiers sont sélectionnés, regroupés et commandés lorsque vous exécutez la requête. Vous pouvez utiliser la requête pour sélectionner des enregistrements à inclure dans un objet de type album de type dynaset ou instantané. Vous pouvez également définir des requêtes en vrac pour modifier les données sans retourner les enregistrements. Vous pouvez récupérer la valeur de cette propriété directement en appelant la fonction membre [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) de la requête.

*m_strConnect*<br/>
Fournit des informations sur la source d’une base de données utilisée dans une requête de passage. Cette information prend la forme d’une chaîne de connexion. Pour plus d’informations sur les chaînes de connexion, et pour plus d’informations sur la récupération de la valeur de cette propriété directement, voir la [base CDaoData::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) fonction membre.

*m_nODBCTimeout*<br/>
Le nombre de secondes que le moteur de base de données Microsoft Jet attend avant qu’une erreur de délai d’attente se produise lorsqu’une requête est exécutée sur une base de données ODBC. Lorsque vous utilisez une base de données ODBC, comme Microsoft SQL Server, il peut y avoir des retards en raison du trafic réseau ou de l’utilisation intensive du serveur ODBC. Plutôt que d’attendre indéfiniment, vous pouvez spécifier combien de temps le moteur Microsoft Jet attend avant de produire une erreur. La valeur de délai d’attente par défaut est de 60 secondes. Vous pouvez récupérer la valeur de cette propriété directement en appelant la fonction membre [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) de la requête. Pour plus d’informations, voir le thème "ODBCTimeout Property" dans DAO Help.

## <a name="remarks"></a>Notes

La requête est un objet de classe [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Les références à Primaire, Secondaire, et Tous ci-dessus indiquent comment l’information `CDaoDatabase`est retournée par la fonction [membre GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) en classe .

Informations récupérées par la [base de CDaoData::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) fonction membre est stocké dans une `CDaoQueryDefInfo` structure. Appelez `GetQueryDefInfo` l’objet de base de données dans lequel la collection De RequêteDefs l’objet de requête est stocké. `CDaoQueryDefInfo`définit également `Dump` une fonction de membre dans les constructions de débogé. Vous pouvez `Dump` utiliser pour vider le contenu d’un `CDaoQueryDefInfo` objet. La `CDaoDatabase` classe fournit également des fonctions de membre `CDaoQueryDefInfo` pour accéder directement à toutes `GetQueryDefInfo`les propriétés retournées dans un objet, ainsi vous devrez probablement rarement appeler.

Lorsque vous appendiciez un nouveau champ ou un nouvel objet paramètre à la collecte fields ou paramètres d’un objet requête, une exception est projetée si la base de données sous-jacente ne prend pas en charge le type de données spécifié pour le nouvel objet.

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la requête a été créée ou mise à jour pour la dernière fois. Dans un environnement multiusage, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers en utilisant la commande **de temps net** pour éviter les écarts dans les paramètres de propriété DateCreated et LastUpdated.

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Classe CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)
