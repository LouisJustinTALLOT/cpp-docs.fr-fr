---
title: CDaoQueryDefInfo, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDefInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0b3e5834aa8b338448c2024603783cedb6f6cae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367228"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo, structure
Le `CDaoQueryDefInfo` structure contient des informations sur un objet querydef défini pour les objets d’accès aux données (DAO).  
  
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
 `m_strName`  
 Identifiant de manière unique l’objet querydef. Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO. Appelez [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) pour récupérer cette propriété directement.  
  
 `m_nType`  
 Une valeur qui indique le type opérationnel d’un objet querydef. Il peut avoir l’une des valeurs suivantes :  
  
- **dbQSelect** sélectionnez : la requête sélectionne des enregistrements.  
  
- **dbQAction** Action : la requête se déplace ou modifie des données, mais ne retourne pas d’enregistrements.  
  
- **dbQCrosstab** analyse croisée : la requête retourne des données dans un format de feuille de calcul.  
  
- **dbQDelete** supprimer : la requête supprime un ensemble de lignes spécifiés.  
  
- **dbQUpdate** mise à jour, la requête devient un jeu d’enregistrements.  
  
- **dbQAppend** Ajout, la requête ajoute de nouveaux enregistrements à la fin d’une table ou une requête.  
  
- **dbQMakeTable** création de table, la requête crée une nouvelle table à partir d’un jeu d’enregistrements.  
  
- **dbQDDL** définition des données, la requête a une incidence sur la structure de tables ou de leurs parties.  
  
- **dbQSQLPassThrough** pass-through, l’instruction SQL est transmise directement au serveur principal de base de données, sans traitement intermédiaire.  
  
- **dbQSetOperation** Union, la requête crée un objet de jeu d’enregistrements de type instantané contenant les données à partir de tous les enregistrements spécifiés dans deux ou plusieurs tables avec des doublons supprimés. Pour inclure les doublons, ajoutez le mot clé **tous les** dans l’instruction SQL querydef.  
  
- **dbQSPTBulk** utilisé avec **dbQSQLPassThrough** pour spécifier une requête qui ne retourne pas d’enregistrements.  
  
> [!NOTE]
>  Pour créer une requête SQL directe, vous ne définissez pas le **dbQSQLPassThrough** constante. Cela est défini d’automatiquement par le moteur de base de données Microsoft Jet lorsque vous créez un objet querydef et que vous définissez la propriété de connexion.  
  
 Pour plus d’informations, consultez la rubrique « Propriété de Type » dans l’aide de DAO.  
  
 `m_dateCreated`  
 Date et heure de que création de l’objet querydef. Pour récupérer directement la date de création de l’objet querydef, appelez le [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) fonction membre de la `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez les commentaires ci-dessous. Consultez également la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.  
  
 `m_dateLastUpdated`  
 La date et l’heure de la dernière modification apportée à l’objet querydef. Pour récupérer directement la date de dernière mise à jour de la table, appelez le [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) fonction membre de l’objet querydef. Pour plus d’informations, consultez les commentaires ci-dessous. Et consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.  
  
 `m_bUpdatable`  
 Indique si les modifications peuvent être apportées à un objet querydef. Si cette propriété est **TRUE**, querydef est modifiable ; sinon, il n’est pas. Updatable signifie que la définition de la requête de l’objet querydef peut être modifiée. A la valeur de la propriété d’être mise à jour d’un objet querydef **TRUE** si la définition de requête peut être mis à jour, même si le jeu d’enregistrements résultant n’est pas modifiable. Pour récupérer cette propriété directement, appelez la querydef [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété actualisable » dans l’aide de DAO.  
  
 *m_bReturnsRecords*  
 Indique si une requête SQL directe sur une base de données externe renvoie des enregistrements. Si cette propriété est **TRUE**, la requête retourne les enregistrements. Pour extraire directement cette propriété, appelez [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Pas toutes les requêtes SQL directes aux bases de données externes renvoient des enregistrements. Par exemple, SQL **mise à jour** instruction met à jour les enregistrements sans en renvoyer lors SQL **sélectionnez** instruction retourne des enregistrements. Pour plus d’informations, consultez la rubrique « Propriété ReturnsRecords » dans l’aide de DAO.  
  
 *m_strSQL*  
 L’instruction SQL qui définit la requête exécutée par un objet querydef. La propriété SQL contient l’instruction SQL qui détermine la façon dont les enregistrements sont sélectionnés, groupés et triés lorsque vous exécutez la requête. Vous pouvez utiliser la requête pour sélectionner des enregistrements à inclure dans un objet de jeu d’enregistrements de type feuille de réponse dynamique ou instantané. Vous pouvez également définir des requêtes pour modifier des données sans retourner les enregistrements en bloc. Vous pouvez récupérer la valeur de cette propriété directement en appelant la querydef [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) fonction membre.  
  
 `m_strConnect`  
 Fournit des informations sur la source d’une base de données utilisé dans une requête directe. Ces informations prennent la forme d’une chaîne de connexion. Pour plus d’informations sur les chaînes de connexion et pour plus d’informations sur la récupération de la valeur de cette propriété directement, consultez le [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) fonction membre.  
  
 *m_nODBCTimeout*  
 Le nombre de secondes pendant lesquelles que le moteur de base de données Microsoft Jet patiente avant une erreur de délai d’attente se produit lorsqu’une requête est exécutée sur une base de données ODBC. Lorsque vous utilisez une base de données ODBC, telles que Microsoft SQL Server, des retards peuvent être en raison de réseau du trafic ou une utilisation intensive du serveur ODBC. Au lieu d’attendre indéfiniment, vous pouvez spécifier la durée pendant laquelle le moteur Microsoft Jet doit attendre une erreur produit. La valeur de délai d’attente par défaut est 60 secondes. Vous pouvez récupérer la valeur de cette propriété directement en appelant la querydef [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété ODBCTimeout » dans l’aide de DAO.  
  
## <a name="remarks"></a>Notes  
 L’objet querydef est un objet de classe [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Les références au principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la [fonction membre GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) fonction membre dans la classe `CDaoDatabase`.  
  
 Les informations extraites par le [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) fonction membre est stockée dans un `CDaoQueryDefInfo` structure. Appelez `GetQueryDefInfo` pour l’objet de base de données dans dont QueryDefs (collection) est stocké l’objet querydef. `CDaoQueryDefInfo` définit également un `Dump` builds de la fonction membre en mode débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoQueryDefInfo` objet. Classe `CDaoDatabase` fournit également des fonctions de membre pour accéder directement à toutes les propriétés retournées dans un `CDaoQueryDefInfo` objet, vous devrez probablement rarement appeler `GetQueryDefInfo`.  
  
 Lorsque vous ajoutez un champ ou un objet de paramètre à la collection de champs ou des paramètres d’un objet querydef, une exception est levée si la base de données sous-jacente ne prend pas en charge le type de données spécifié pour le nouvel objet.  
  
 Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la querydef a été créée ou mises à jour. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichier en utilisant le **net temps** commande afin d’éviter des incohérences dans les paramètres de propriété DateCreated et LastUpdated.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef (classe)](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)
