---
title: Classe de CDaoQueryDef | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3af520de7e92a887f9a49fea7262d7f51b74082
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954632"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef (classe)
Représente une définition de requête, ou « querydef », généralement stockée dans une base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Construit un objet `CDaoQueryDef`. Appelez ensuite `Open` ou `Create`, selon vos besoins.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoQueryDef::Append](#append)|Ajoute l’objet querydef à la collection QueryDefs de la base de données sous la forme d’une requête enregistrée.|  
|[CDaoQueryDef::CanUpdate](#canupdate)|Retourne zéro si la requête peut mettre à jour la base de données.|  
|[CDaoQueryDef::Close](#close)|Ferme l’objet querydef. Détruire l’objet C++ lorsque vous avez terminé avec lui.|  
|[CDaoQueryDef::Create](#create)|Crée l’objet querydef DAO sous-jacent. Utiliser la querydef comme une requête temporaire ou appelez `Append` à enregistrer dans la base de données.|  
|[CDaoQueryDef::Execute](#execute)|Exécute la requête définie par l’objet querydef.|  
|[CDaoQueryDef::GetConnect](#getconnect)|Retourne la chaîne de connexion associée à l’objet querydef. La chaîne de connexion identifie la source de données. (Pour SQL pass-through interroge uniquement ; sinon, une chaîne vide.)|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Retourne la date de que création de la requête enregistrée.|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Retourne la date de que dernière mise à jour de la requête enregistrée.|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Retourne le nombre de champs définis par l’objet querydef.|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Retourne des informations sur un champ spécifié défini dans la requête.|  
|[CDaoQueryDef::GetName](#getname)|Retourne le nom de l’objet querydef.|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Retourne la valeur de délai d’attente utilisée par ODBC (pour une requête ODBC) lors de l’exécution la querydef. Ce paramètre détermine combien de temps à autoriser pour terminer l’action de la requête.|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Retourne le nombre de paramètres définis pour la requête.|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Retourne des informations sur un paramètre spécifique à la requête.|  
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Retourne la valeur d’un paramètre spécifique à la requête.|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Retourne le nombre d’enregistrements affectés par une requête d’action.|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Retourne zéro si la requête définie par l’objet querydef retourne les enregistrements.|  
|[CDaoQueryDef::GetSQL](#getsql)|Retourne la chaîne SQL qui spécifie la requête définie par l’objet querydef.|  
|[CDaoQueryDef::GetType](#gettype)|Retourne le type de requête : supprimer, mettre à jour, ajout, création de table et ainsi de suite.|  
|[CDaoQueryDef::IsOpen](#isopen)|Retourne zéro si la querydef est ouverte et peut être exécutée.|  
|[CDaoQueryDef::Open](#open)|Ouvre un querydef existant stocké dans la collection QueryDefs de la base de données.|  
|[CDaoQueryDef::SetConnect](#setconnect)|Définit la chaîne de connexion pour une requête SQL directe sur une source de données ODBC.|  
|[CDaoQueryDef::SetName](#setname)|Définit le nom de la requête enregistrée, en remplaçant le nom utilisé lors de la création de l’objet querydef.|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Définit la valeur de délai d’attente utilisée par ODBC (pour une requête ODBC) lors de l’exécution la querydef.|  
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Définit la valeur d’un paramètre spécifique à la requête.|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Spécifie si l’objet querydef retourne des enregistrements. Cet attribut **TRUE** est valide uniquement pour les requêtes SQL directes.|  
|[CDaoQueryDef::SetSQL](#setsql)|Définit la chaîne SQL qui spécifie la requête définie par l’objet querydef.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Pointeur vers l’interface OLE pour l’objet querydef DAO sous-jacent.|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Un pointeur vers le `CDaoDatabase` objet auquel est associée l’objet querydef. L’objet querydef peut-être être enregistrée dans la base de données ou non.|  
  
## <a name="remarks"></a>Notes  
 Un objet querydef est un objet d’accès de données qui contient l’instruction SQL qui décrit une requête et ses propriétés, telles que « Date de création de » et « Délai d’attente ODBC ». Vous pouvez également créer des objets querydef temporaire sans les enregistrer, mais il est pratique et beaucoup plus efficace, pour enregistrer fréquemment réutilisé requêtes dans une base de données. A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet maintient une collection, appelée la QueryDefs (collection), qui contient ses querydefs enregistrées.  
  
> [!NOTE]
>  Les classes de base de données DAO sont distincts des classes de base de données MFC basées sur ODBC Open Database Connectivity (). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accès aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus efficaces que les classes MFC basées sur ODBC ; les classes DAO peuvent accéder aux données, y compris par le biais des pilotes ODBC, via leur propre moteur de base de données. Les classes DAO prennent également en charge les opérations de langage de définition de données (DDL), telles que l’ajout de tables via les classes, sans avoir à appeler DAO directement.  
  
## <a name="usage"></a>Utilisation  
 Utilisent des objets querydef soit pour fonctionner avec une requête enregistrée existant ou créer un nouveau enregistré la requête ou requête temporaire :  
  
1.  Dans tous les cas, tout d’abord construire un `CDaoQueryDef` objet, en fournissant un pointeur vers le [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) de l’objet auquel appartient la requête.  
  
2.  Ensuite, procédez comme suit, selon ce que vous souhaitez :  
  
    -   Pour utiliser une requête enregistrée existante, appelez l’objet querydef [ouvrir](#open) fonction membre, en fournissant le nom de la requête enregistrée.  
  
    -   Pour créer une nouvelle requête enregistrée, appelez l’objet querydef [créer](#create) fonction membre, en fournissant le nom de la requête. Appelez ensuite [Append](#append) pour enregistrer la requête en l’ajoutant à la collection QueryDefs de la base de données. `Create` place l’objet querydef dans un état ouvert, c’est le cas après l’appel `Create` vous n’appelez pas `Open`.  
  
    -   Pour créer un objet querydef temporaire, appelez `Create`. Passez une chaîne vide pour le nom de la requête. N’appelez pas `Append`.  
  
 Lorsque vous avez terminé à l’aide d’un objet querydef, appelez sa [fermer](#close) membre fonction ; puis détruisez l’objet querydef.  
  
> [!TIP]
>  Pour créer des requêtes enregistrées, la plus simple consiste à les créer et de les stocker dans votre base de données à l’aide de Microsoft Access. Vous pouvez ensuite ouvrir et les utiliser dans votre code MFC.  
  
## <a name="purposes"></a>À des fins  
 Vous pouvez utiliser un objet querydef pour une des raisons suivantes :  
  
-   Pour créer un `CDaoRecordset` objet  
  
-   Pour appeler l’objet `Execute` fonction membre à exécuter directement une requête action ou une requête SQL directe  
  
 Vous pouvez utiliser un objet querydef pour n’importe quel type de requête, notamment select, action, analyse croisée, suppression, mise à jour, ajouter, de création de table, définition de données, SQL directes, union et les requêtes en bloc. Le type de requête est déterminé par le contenu de l’instruction SQL que vous fournissez. Pour plus d’informations sur les types de requêtes, consultez la `Execute` et [GetType](#gettype) fonctions membres. Jeux d’enregistrements est couramment utilisées pour retourner à la ligne des requêtes, généralement celles utilisant le **sélectionnez... À partir de** mots clés. `Execute` est généralement utilisé pour les opérations en bloc. Pour plus d’informations, consultez [Execute](#execute) et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
## <a name="querydefs-and-recordsets"></a>Querydefs et jeux d’enregistrements  
 Utilisation d’un objet querydef pour créer un `CDaoRecordset` de l’objet, vous créez généralement ou que vous ouvrez un objet querydef comme indiqué ci-dessus. Puis construire un objet recordset, en passant un pointeur vers l’objet querydef lorsque vous appelez [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). L’objet querydef que vous passez doit être dans un état ouvert. Pour plus d’informations, consultez la classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Vous ne pouvez pas utiliser un objet querydef pour créer un jeu d’enregistrements (le plus souvent utilisés pour un objet querydef), sauf si elle est dans un état ouvert. Placez la querydef dans un état ouvert en appelant `Open` ou `Create`.  
  
## <a name="external-databases"></a>Bases de données externes  
 Les objets QueryDef représentent la meilleure façon d’utiliser le dialecte SQL natif d’un moteur de base de données externe. Par exemple, vous pouvez créer une requête Transact SQL (comme dans Microsoft SQL Server) et le stocker dans un objet querydef. Lorsque vous avez besoin d’utiliser une requête SQL ne pas basée sur le moteur de base de données Microsoft Jet, vous devez fournir une chaîne de connexion qui pointe vers la source de données externe. Requêtes avec des chaînes de connexion valides contournent le moteur de base de données et transmettent la requête directement sur le serveur de base de données externe pour le traitement.  
  
> [!TIP]
>  La meilleure façon de travailler avec les tables ODBC consiste à attacher à un Microsoft Jet (. Base de données MDB).  
  
 Pour plus d’informations, consultez les rubriques « Objet QueryDef », « Collection QueryDefs » et « CdbDatabase objet » dans le SDK de DAO.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
##  <a name="append"></a>  CDaoQueryDef::Append  
 Appelez cette fonction membre après avoir appelé [créer](#create) pour créer un nouvel objet querydef.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Notes  
 `Append` enregistre l’objet querydef dans la base de données en ajoutant l’objet à la collection QueryDefs de la base de données. Vous pouvez utiliser la querydef comme objet temporaire sans l’ajouter, mais si vous souhaitez rendre persistantes, vous devez appeler `Append`.  
  
 Si vous essayez d’ajouter un objet querydef temporaire, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate  
 Appelez cette fonction membre pour déterminer si vous pouvez modifier l’objet querydef, telles que la modification de son nom ou une chaîne SQL.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si vous êtes autorisé à modifier la querydef ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez modifier la querydef si :  
  
-   Il n’est pas basé sur une base de données est ouverte en lecture seule.  
  
-   Vous disposez des autorisations de mise à jour pour la base de données.  
  
     Cela dépend si vous avez implémenté des fonctionnalités de sécurité. MFC ne fournit pas de prise en charge pour la sécurité. Vous devez implémenter vous-même par l’appel de DAO directement ou à l’aide de Microsoft Access. Consultez la rubrique « Autorisations Property » dans l’aide de DAO.  
  
##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef  
 Construit un objet `CDaoQueryDef`.  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDatabase*  
 Un pointeur vers open [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 L’objet peut représenter un querydef existant stocké dans la collection QueryDefs de la base de données, une nouvelle requête à stocker dans la collection ou une requête temporaire, ne pas à stocker. L’étape suivante varie selon le type d’objet querydef :  
  
-   Si l’objet représente un objet querydef existant, appelez l’objet [ouvrir](#open) fonction membre pour l’initialiser.  
  
-   Si l’objet représente un nouvel objet querydef doit être enregistré, appelez l’objet [créer](#create) fonction membre. Cela ajoute l’objet à la collection QueryDefs de la base de données. Appelez ensuite `CDaoQueryDef` des fonctions membres pour définir les attributs de l’objet. Enfin, appelez [Append](#append).  
  
-   Si l’objet représente une querydef temporaire (à ne pas être enregistrées dans la base de données), appelez `Create`, en passant une chaîne vide pour le nom de la requête. Après avoir appelé `Create`, initialiser l’objet querydef en directement en définissant ses attributs. N’appelez pas `Append`.  
  
 Pour définir les attributs de l’objet querydef, vous pouvez utiliser la [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)et [SetReturnsRecords ne](#setreturnsrecords) fonctions membres.  
  
 Lorsque vous avez terminé avec l’objet querydef, appelez sa [fermer](#close) fonction membre. Si vous avez un pointeur vers l’objet querydef, utilisez la **supprimer** opérateur pour détruire l’objet C++.  
  
##  <a name="close"></a>  CDaoQueryDef::Close  
 Appelez cette fonction membre lorsque vous avez terminé à l’aide de l’objet querydef.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Notes  
 Fermeture de l’objet querydef libère l’objet DAO sous-jacent, mais ne détruit pas l’objet querydef DAO enregistré ou C++ `CDaoQueryDef` objet. Cela n’est pas le même que [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), ce qui supprime l’objet querydef QueryDefs (collection) de la base de données dans DAO (si ce n’est pas un objet querydef temporaire).  
  
##  <a name="create"></a>  CDaoQueryDef::Create  
 Appelez cette fonction membre pour créer une nouvelle requête enregistrée ou une requête temporaire.  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *Caractère*  
 Le nom unique de la requête enregistrée dans la base de données. Pour plus d’informations sur la chaîne, consultez la rubrique « CreateQueryDef méthode » dans l’aide de DAO. Si vous acceptez la valeur par défaut, une chaîne vide, un objet querydef temporaire est créée. Une telle requête n’est pas enregistrée dans la collection QueryDefs.  
  
 *lpszSQL*  
 La chaîne SQL qui définit la requête. Si vous acceptez la valeur par défaut **NULL**, vous devez appeler ultérieurement [SetSQL](#setsql) pour définir la chaîne. Jusqu'à cette date, la requête n’est pas définie. Vous pouvez, toutefois, utiliser la requête non définie pour ouvrir un jeu d’enregistrements ; Pour plus d’informations, consultez la section Notes. L’instruction SQL doit être définie avant que vous pouvez ajouter à la collection QueryDefs.  
  
### <a name="remarks"></a>Notes  
 Si vous passez un nom dans *le caractère*, vous pouvez ensuite appeler [Append](#append) pour enregistrer l’objet querydef dans la collection QueryDefs de la base de données. Dans le cas contraire, l’objet est un objet querydef temporaire et n’est pas enregistré. Dans les deux cas, l’objet querydef est dans un état ouvert, et vous pouvez soit l’utiliser pour créer un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) de l’objet ou appeler la querydef [Execute](#execute) fonction membre.  
  
 Si vous ne fournissez pas d’une instruction SQL dans *lpszSQL*, vous ne pouvez pas exécuter la requête avec `Execute` mais vous pouvez l’utiliser pour créer un jeu d’enregistrements. Dans ce cas, MFC utilise instruction SQL de valeur par défaut du jeu d’enregistrements.  
  
##  <a name="execute"></a>  CDaoQueryDef::Execute  
 Appelez cette fonction membre pour exécuter la requête définie par l’objet querydef.  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Paramètres  
 *nOptions*  
 Entier qui détermine les caractéristiques de la requête. Pour plus d’informations, consultez la rubrique « Exécuter la méthode » dans l’aide de DAO. Vous pouvez utiliser l’opérateur OR au niveau du bit ( **&#124;**) pour combiner les constantes suivantes pour cet argument :  
  
- **dbDenyWrite** refuser l’autorisation en écriture à d’autres utilisateurs.  
  
- **dbInconsistent** mises à jour incohérentes.  
  
- **dbConsistent** mises à jour cohérentes.  
  
- **dbSQLPassThrough** SQL directes. Provoque l’instruction SQL à passer à une base de données ODBC pour le traitement.  
  
- **dbFailOnError** valeur par défaut. Restaurer les mises à jour si une erreur se produit et signalez l’erreur à l’utilisateur.  
  
- **dbSeeChanges** génère une erreur d’exécution si un autre utilisateur modifie les données que vous modifiez.  
  
> [!NOTE]
>  Pour obtenir une explication des termes du contrat « incohérentes » et « cohérent », consultez la rubrique « Exécuter la méthode » dans l’aide de DAO.  
  
### <a name="remarks"></a>Notes  
 Les objets QueryDef utilisés pour l’exécution de cette manière ne peuvent représenter un des types de requêtes suivants :  
  
-   Requêtes d’action  
  
-   Requêtes SQL directes  
  
 `Execute` ne fonctionne pas pour les requêtes qui retournent des enregistrements, tels que des requêtes select. `Execute` est couramment utilisée pour les requêtes d’opération en bloc, telles que **mise à jour**, **insérer**, ou **SELECT INTO**, ou pour les opérations data definition language (DDL).  
  
> [!TIP]
>  La meilleure façon de travailler avec des sources de données ODBC consiste à joindre des tables à un Microsoft Jet (. Base de données MDB). Pour plus d’informations, consultez la rubrique « L’accès à des bases de données externe avec des DAO » dans l’aide de DAO.  
  
 Appelez le [GetRecordsAffected](#getrecordsaffected) fonction membre de l’objet querydef pour déterminer le nombre d’enregistrements affectés par la plus récente `Execute` appeler. Par exemple, `GetRecordsAffected` renvoie des informations sur le nombre d’enregistrements supprimés, mis à jour ou insérés lors de l’exécution d’une requête d’action. Le nombre retourné ne reflète pas les modifications dans les tables associées lorsque cascade met à jour ou supprime prennent effet.  
  
 Si vous incluez les deux **dbInconsistent** et **dbConsistent** ou si vous incluez aucun, le résultat est la valeur par défaut, **dbInconsistent**.  
  
 `Execute` ne retourne pas d’un jeu d’enregistrements. À l’aide de `Execute` sur une requête qui sélectionne des enregistrements entraîne MFC lever une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect  
 Appelez cette fonction membre pour obtenir la chaîne de connexion liée à la source de données de l’objet querydef.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant la chaîne de connexion pour l’objet querydef.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est utilisée uniquement avec les sources de données ODBC et certains pilotes ISAM. Il n’est pas utilisé avec Microsoft Jet (. Bases de données MDB) ; Dans ce cas, `GetConnect` retourne une chaîne vide. Pour plus d’informations, consultez [SetConnect](#setconnect).  
  
> [!TIP]
>  La meilleure façon de travailler avec les tables ODBC consiste à attacher à un. Base de données MDB. Pour plus d’informations, consultez la rubrique « L’accès à des bases de données externe avec des DAO » dans l’aide de DAO.  
  
 Pour plus d’informations sur les chaînes de connexion, consultez la rubrique « Propriété Connect » dans l’aide de DAO.  
  
##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated  
 Appelez cette fonction membre pour obtenir la date de que création de l’objet querydef.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet contenant la date et l’heure de création de l’objet querydef.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.  
  
##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated  
 Appel de cette fonction membre pour obtenir la date de l’objet querydef a été mises à jour, lorsque une de ses propriétés ont été modifiée, telles que son nom, sa chaîne SQL ou sa chaîne de connexion.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet contenant la date et heure de dernière mise à jour de l’objet querydef.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.  
  
##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount  
 Appelez cette fonction membre pour récupérer le nombre de champs dans la requête.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de champs définis dans la requête.  
  
### <a name="remarks"></a>Notes  
 `GetFieldCount` est utile pour exécuter une boucle dans tous les champs de l’objet querydef. Pour cela, utilisez `GetFieldCount` conjointement avec [GetFieldInfo](#getfieldinfo).  
  
##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo  
 Appelez cette fonction membre pour obtenir les différents types d’informations sur un champ défini dans l’objet querydef.  
  
```  
void GetFieldInfo(
    int nIndex,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetFieldInfo(
    LPCTSTR lpszName,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Index de base zéro du champ souhaité dans la collection de champs de la querydef, pour la recherche par index.  
  
 *FieldInfo*  
 Une référence à un `CDaoFieldInfo` objet qui retourne les informations demandées.  
  
 *dwInfoOptions*  
 Options qui spécifient les informations sur le champ à extraire. Les options disponibles sont répertoriées ici, ainsi que leur cause la fonction retourne :  
  
- `AFX_DAO_PRIMARY_INFO` (Par défaut) Nom, Type, taille, attributs  
  
- `AFX_DAO_SECONDARY_INFO` Informations primaire plues : Position ordinale, requis, autoriser une longueur de zéro, champ Source, nom étrangères, Table Source, ordre de classement  
  
- `AFX_DAO_ALL_INFO` Informations primaires et secondaires plues : règle de Validation de valeur par défaut, le texte de Validation,  
  
 *Caractère*  
 Chaîne contenant le nom du champ souhaité pour la recherche par nom. Vous pouvez utiliser un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Notes  
 Pour obtenir une description des informations retournées dans *fieldinfo*, consultez la [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) structure. Cette structure possède des membres qui correspondent aux informations descriptives sous *dwInfoOptions* ci-dessus. Si vous demandez un niveau d’informations, vous obtenez tous les niveaux préalables d’informations.  
  
##  <a name="getname"></a>  CDaoQueryDef::GetName  
 Appelez cette fonction membre pour récupérer le nom de la requête représentée par l’objet querydef.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nom de la requête.  
  
### <a name="remarks"></a>Notes  
 Les noms de QueryDef sont un nom unique défini par l’utilisateur. Pour plus d’informations sur les noms de querydef, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout  
 Appelez cette fonction membre pour récupérer le délai imparti avant l’expiration d’une requête à une source de données ODBC.  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de secondes avant une requête arrive à expiration.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur cette limite de temps, consultez la rubrique « Propriété ODBCTimeout » dans l’aide de DAO.  
  
> [!TIP]
>  La meilleure façon de travailler avec les tables ODBC consiste à attacher à un Microsoft Jet (. Base de données MDB). Pour plus d’informations, consultez la rubrique « L’accès à des bases de données externe avec des DAO » dans l’aide de DAO.  
  
##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount  
 Appelez cette fonction membre pour récupérer le nombre de paramètres dans la requête enregistrée.  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de paramètres définis dans la requête.  
  
### <a name="remarks"></a>Notes  
 `GetParameterCount` est utile pour exécuter une boucle dans tous les paramètres de l’objet querydef. Pour cela, utilisez `GetParameterCount` conjointement avec [GetParameterInfo](#getparameterinfo).  
  
 Pour plus d’informations, consultez les rubriques « Objet de paramètre », « Collection de paramètres » et « déclaration de paramètres (SQL) » dans l’aide de DAO.  
  
##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo  
 Appelez cette fonction membre pour obtenir des informations sur un paramètre défini dans l’objet querydef.  
  
```  
void GetParameterInfo(
    int nIndex,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetParameterInfo(
    LPCTSTR lpszName,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Index de base zéro du paramètre souhaité dans la collection de paramètres de la querydef, pour la recherche par index.  
  
 *paraminfo et*  
 Une référence à un [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) objet qui retourne les informations demandées.  
  
 *dwInfoOptions*  
 Options qui spécifient les informations sur le paramètre à récupérer. L’option disponible est répertoriée ici, ainsi que la fonction retourne pourquoi il :  
  
- `AFX_DAO_PRIMARY_INFO` (Par défaut) Nom, Type  
  
 *Caractère*  
 Chaîne contenant le nom du paramètre souhaité, pour la recherche par nom. Vous pouvez utiliser un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Notes  
 Pour obtenir une description des informations retournées dans *paraminfo et*, consultez la [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) structure. Cette structure possède des membres qui correspondent aux informations descriptives sous *dwInfoOptions* ci-dessus.  
  
 Pour plus d’informations, consultez la rubrique « déclaration PARAMETERS (SQL) » dans l’aide de DAO.  
  
##  <a name="getparamvalue"></a>  CDaoQueryDef::GetParamValue  
 Appelez cette fonction membre pour extraire la valeur actuelle du paramètre spécifié stocké dans la collection de paramètres de la querydef.  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *Caractère*  
 Le nom du paramètre dont la valeur souhaitée pour la recherche par nom.  
  
 *nIndex*  
 Index de base zéro du paramètre dans la collection de paramètres de la querydef, pour la recherche par index. Vous pouvez obtenir cette valeur avec les appels de [GetParameterCount](#getparametercount) et [GetParameterInfo](#getparameterinfo).  
  
### <a name="return-value"></a>Valeur de retour  
 Un objet de classe [COleVariant](../../mfc/reference/colevariant-class.md) qui contient la valeur du paramètre.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez accéder à la paramètre par nom ou par sa position ordinale dans la collection.  
  
 Pour plus d’informations, consultez la rubrique « déclaration PARAMETERS (SQL) » dans l’aide de DAO.  
  
##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected  
 Appelez cette fonction membre pour déterminer le nombre d’enregistrements qui ont été affecté par le dernier appel de [Execute](#execute).  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’enregistrements concernés.  
  
### <a name="remarks"></a>Notes  
 Le nombre retourné ne reflète pas les modifications dans les tables associées lorsque cascade met à jour ou supprime prennent effet.  
  
 Pour plus d’informations, consultez la rubrique « Propriété RecordsAffected » dans l’aide de DAO.  
  
##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords  
 Appelez cette fonction membre pour déterminer si l’objet querydef est basée sur une requête qui retourne des enregistrements.  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’objet querydef est basée sur une requête qui retourne des enregistrements. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est utilisée uniquement pour les requêtes SQL directes. Pour plus d’informations sur les requêtes SQL, consultez le [Execute](#execute) fonction membre. Pour plus d’informations sur l’utilisation des requêtes SQL directes, consultez la [SetReturnsRecords ne](#setreturnsrecords) fonction membre.  
  
 Pour plus d’informations, consultez la rubrique « Propriété ReturnsRecords » dans l’aide de DAO.  
  
##  <a name="getsql"></a>  CDaoQueryDef::GetSQL  
 Appelez cette fonction membre pour extraire l’instruction SQL qui définit la requête sur laquelle repose la querydef.  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’instruction SQL qui définit la requête sur laquelle repose la querydef.  
  
### <a name="remarks"></a>Notes  
 Vous puis probablement analyse la chaîne de mots clés, les noms de table et ainsi de suite.  
  
 Pour plus d’informations, consultez les rubriques « Propriété SQL », « Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL » et « Interroger une base de données avec SQL dans Code » dans l’aide de DAO.  
  
##  <a name="gettype"></a>  CDaoQueryDef::GetType  
 Appelez cette fonction membre pour déterminer le type de requête de l’objet querydef.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le type de la requête définie par l’objet querydef. Pour les valeurs, consultez la section Notes.  
  
### <a name="remarks"></a>Notes  
 Le type de requête est défini par ce que vous spécifiez dans la chaîne SQL de la querydef lorsque vous créez la querydef ou que vous appelez un objet querydef existant [SetSQL](#setsql) fonction membre. Le type de requête retourné par cette fonction peut être une des valeurs suivantes :  
  
- **dbQSelect** sélectionner  
  
- **dbQAction** Action  
  
- **dbQCrosstab** analyse croisée  
  
- **dbQDelete** supprimer  
  
- **dbQUpdate** mise à jour  
  
- **dbQAppend** Append  
  
- **dbQMakeTable** création de table  
  
- **dbQDDL** définition des données  
  
- **dbQSQLPassThrough** pass-through  
  
- **dbQSetOperation** Union  
  
- **dbQSPTBulk** utilisé avec **dbQSQLPassThrough** pour spécifier une requête qui ne retourne pas d’enregistrements.  
  
> [!NOTE]
>  Pour créer une requête SQL directe, ne définissez pas le **dbSQLPassThrough** constante. Cela est défini d’automatiquement par le moteur de base de données Microsoft Jet lorsque vous créez un objet querydef et que vous définissez la chaîne de connexion.  
  
 Pour plus d’informations sur les chaînes de SQL, consultez [GetSQL](#getsql). Pour plus d’informations sur les types de requêtes, consultez [Execute](#execute).  
  
##  <a name="isopen"></a>  CDaoQueryDef::IsOpen  
 Appelez cette fonction membre pour déterminer si le `CDaoQueryDef` objet est actuellement ouvert.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la `CDaoQueryDef` objet est actuellement ouvert ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un objet querydef doit être dans un état d’ouverture avant de l’utiliser pour appeler [Execute](#execute) ou pour créer un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet. Pour placer un objet querydef dans un appel de l’état ouvert soit [créer](#create) (pour un nouvel objet querydef) ou [ouvrir](#open) (pour un objet querydef existant).  
  
##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase  
 Contient un pointeur vers le [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet associé à l’objet querydef.  
  
### <a name="remarks"></a>Notes  
 Utilisez ce pointeur si vous avez besoin d’accéder directement à la base de données, par exemple, pour obtenir des pointeurs vers d’autres querydef ou d’un jeu d’enregistrements des objets dans des collections de la base de données.  
  
##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef  
 Contient un pointeur vers l’interface OLE pour l’objet querydef DAO sous-jacent.  
  
### <a name="remarks"></a>Notes  
 Ce pointeur est fourni pour l’exhaustivité et la cohérence avec les autres classes. Cependant, MFC encapsule plutôt entièrement querydefs DAO, vous êtes probablement pas besoin. Si vous l’utilisez, faites-le avec précaution, en particulier, ne modifiez pas la valeur du pointeur, sauf si vous savez que vous effectuez.  
  
##  <a name="open"></a>  CDaoQueryDef::Open  
 Appelez cette fonction membre pour ouvrir un objet querydef précédemment enregistrée dans la collection QueryDefs de la base de données.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *Caractère*  
 Chaîne qui contient le nom de la querydef enregistrée à ouvrir. Vous pouvez utiliser un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Notes  
 Une fois la querydef ouverte, vous pouvez appeler son [Execute](#execute) fonction membre ou utilisez la querydef pour créer un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet.  
  
##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect  
 Appelez cette fonction membre pour définir la chaîne de connexion de l’objet querydef.  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszConnect*  
 Chaîne qui contient une chaîne de connexion associé au [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 La chaîne de connexion est utilisée pour passer des informations supplémentaires à ODBC et certains pilotes ISAM si nécessaire. Il n’est pas utilisé pour Microsoft Jet (. Bases de données MDB).  
  
> [!TIP]
>  La meilleure façon de travailler avec les tables ODBC consiste à attacher à un. Base de données MDB.  
  
 Avant l’exécution d’un objet querydef qui représente une requête SQL directe à une source de données ODBC, définissez la chaîne de connexion avec `SetConnect` et appelez [SetReturnsRecords ne](#setreturnsrecords) pour spécifier si la requête renvoie des enregistrements.  
  
 Pour plus d’informations sur la structure et les exemples de composants de chaîne de connexion de la chaîne de connexion, consultez la rubrique « Propriété Connect » dans l’aide de DAO.  
  
##  <a name="setname"></a>  CDaoQueryDef::SetName  
 Appelez cette fonction membre si vous souhaitez modifier le nom d’un objet querydef qui n’est pas temporaire.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Paramètres  
 *Caractère*  
 Chaîne qui contient le nouveau nom pour une requête les dans associé [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet.  
  
### <a name="remarks"></a>Notes  
 Les noms de QueryDef sont des noms uniques, défini par l’utilisateur. Vous pouvez appeler `SetName` avant la querydef objet est ajouté à la collection QueryDefs.  
  
##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout  
 Appelez cette fonction membre pour définir la limite de temps avant l’expiration d’une requête à une source de données ODBC.  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>Paramètres  
 *nODBCTimeout*  
 Le nombre de secondes avant une requête arrive à expiration.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre vous permet de remplacer le nombre par défaut de secondes avant que les opérations suivantes sur la source de données connectée « délai d’expiration ». Une opération peut expirer en raison de problèmes d’accès réseau, le temps de traitement de requête excessive et ainsi de suite. Appelez `SetODBCTimeout` avant d’exécuter une requête avec cette querydef si vous souhaitez modifier la valeur de délai d’attente de requête. (Comme ODBC réutilise les connexions, la valeur de délai d’attente est identique pour tous les clients sur la même connexion.)  
  
 La valeur par défaut pour les délais d’expiration est de 60 secondes.  
  
##  <a name="setparamvalue"></a>  CDaoQueryDef::SetParamValue  
 Appelez cette fonction membre pour définir la valeur d’un paramètre dans l’objet querydef au moment de l’exécution.  
  
```  
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *Caractère*  
 Le nom du paramètre dont vous souhaitez définir la valeur.  
  
 *varValue*  
 La valeur à définir ; consultez la section Notes.  
  
 *nIndex*  
 La position ordinale du paramètre dans la collection de paramètres de la querydef. Vous pouvez obtenir cette valeur avec les appels de [GetParameterCount](#getparametercount) et [GetParameterInfo](#getparameterinfo).  
  
### <a name="remarks"></a>Notes  
 Le paramètre doit déjà avoir été établi dans le cadre de la chaîne SQL de la querydef. Vous pouvez accéder à la paramètre par nom ou par sa position ordinale dans la collection.  
  
 Spécifiez la valeur à définir comme un `COleVariant` objet. Pour plus d’informations sur la définition de la valeur souhaitée et le type dans votre `COleVariant` d’objet, consultez la classe [COleVariant](../../mfc/reference/colevariant-class.md).  
  
##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords  
 Appelez cette fonction membre dans le cadre du processus de configuration d’une requête SQL directe sur une base de données externe.  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>Paramètres  
 *bReturnsRecords*  
 Passer **TRUE** si la requête sur une base de données externe retourne des enregistrements ; sinon, **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Dans ce cas, vous devez créer l’objet querydef et définir ses propriétés à l’aide d’autres `CDaoQueryDef` fonctions membres. Pour obtenir une description des bases de données externes, consultez [SetConnect](#setconnect).  
  
##  <a name="setsql"></a>  CDaoQueryDef::SetSQL  
 Appelez cette fonction membre pour définir l’instruction SQL spécifiée par l’objet querydef.  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszSQL*  
 Chaîne contenant une instruction SQL complète appropriée pour l’exécution. La syntaxe de cette chaîne dépend de SGBD qui votre cible de la requête. Pour une description de la syntaxe utilisée dans le moteur de base de données Microsoft Jet, consultez la rubrique « Construction instructions de Code SQL » dans l’aide de DAO.  
  
### <a name="remarks"></a>Notes  
 En règle générale `SetSQL` est la configuration d’un objet querydef pour une utilisation dans une requête SQL directe. (Pour la syntaxe des requêtes SQL directes sur SGBD cible, consultez la documentation de votre système SGBD.)  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset (classe)](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase (classe)](../../mfc/reference/cdaodatabase-class.md)   
 [Classe d’objet CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException, classe](../../mfc/reference/cdaoexception-class.md)
