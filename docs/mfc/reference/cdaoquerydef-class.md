---
title: CDaoQueryDef (classe)
ms.date: 11/04/2016
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
ms.openlocfilehash: 08fb2909a4fd2e5bda3dfc63d19224a515c7c699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883887"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef (classe)

Représente une définition de requête, ou « querydef », généralement stockée dans une base de données.

## <a name="syntax"></a>Syntaxe

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CDaoQueryDef :: CDaoQueryDef](#cdaoquerydef)|Construit un objet `CDaoQueryDef`. Appelez ensuite `Open` ou `Create`, en fonction de vos besoins.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CDaoQueryDef :: Append](#append)|Ajoute l’objet querydef à la collection QueryDefs de la base de données en tant que requête enregistrée.|
|[CDaoQueryDef :: CanUpdate](#canupdate)|Retourne une valeur différente de zéro si la requête peut mettre à jour la base de données.|
|[CDaoQueryDef :: Close](#close)|Ferme l’objet querydef. Détruisez C++ l’objet une fois que vous l’avez terminé.|
|[CDaoQueryDef :: Create](#create)|Crée l’objet querydef DAO sous-jacent. Utilisez l’objet querydef comme une requête temporaire ou appelez `Append` pour l’enregistrer dans la base de données.|
|[CDaoQueryDef :: Execute](#execute)|Exécute la requête définie par l’objet querydef.|
|[CDaoQueryDef :: GetConnect](#getconnect)|Retourne la chaîne de connexion associée à l’objet querydef. La chaîne de connexion identifie la source de données. (Pour les requêtes SQL directes uniquement ; sinon, une chaîne vide.)|
|[CDaoQueryDef :: GetDateCreated](#getdatecreated)|Retourne la date à laquelle la requête enregistrée a été créée.|
|[CDaoQueryDef :: GetDateLastUpdated](#getdatelastupdated)|Retourne la date de la dernière mise à jour de la requête enregistrée.|
|[CDaoQueryDef :: GetFieldCount](#getfieldcount)|Retourne le nombre de champs définis par l’objet querydef.|
|[CDaoQueryDef :: GetFieldInfo](#getfieldinfo)|Retourne des informations sur un champ spécifié défini dans la requête.|
|[CDaoQueryDef :: GetName](#getname)|Retourne le nom de l’objet querydef.|
|[CDaoQueryDef :: GetODBCTimeout](#getodbctimeout)|Retourne la valeur du délai d’attente utilisée par ODBC (pour une requête ODBC) lors de l’exécution de la querydef. Cela détermine la durée d’exécution de l’action de la requête.|
|[CDaoQueryDef :: GetParameterCount](#getparametercount)|Retourne le nombre de paramètres définis pour la requête.|
|[CDaoQueryDef :: GetParameterInfo](#getparameterinfo)|Retourne des informations sur un paramètre spécifié de la requête.|
|[CDaoQueryDef :: GetParamValue](#getparamvalue)|Retourne la valeur d’un paramètre spécifié de la requête.|
|[CDaoQueryDef :: GetRecordsAffected](#getrecordsaffected)|Retourne le nombre d’enregistrements affectés par une requête d’action.|
|[CDaoQueryDef :: GetReturnsRecords](#getreturnsrecords)|Retourne une valeur différente de zéro si la requête définie par la querydef retourne des enregistrements.|
|[CDaoQueryDef :: GetSQL](#getsql)|Retourne la chaîne SQL qui spécifie la requête définie par l’objet querydef.|
|[CDaoQueryDef :: GetType](#gettype)|Retourne le type de requête : Delete, Update, Append, Make-table, etc.|
|[CDaoQueryDef :: IsOpen](#isopen)|Retourne une valeur différente de zéro si la querydef est ouverte et peut être exécutée.|
|[CDaoQueryDef :: Open](#open)|Ouvre une querydef existante stockée dans la collection QueryDefs de la base de données.|
|[CDaoQueryDef :: SetConnect](#setconnect)|Définit la chaîne de connexion pour une requête SQL directe sur une source de données ODBC.|
|[CDaoQueryDef :: SetName](#setname)|Définit le nom de la requête enregistrée, en remplaçant le nom utilisé lors de la création de l’objet querydef.|
|[CDaoQueryDef :: SetODBCTimeout](#setodbctimeout)|Définit la valeur du délai d’attente utilisée par ODBC (pour une requête ODBC) lors de l’exécution de la querydef.|
|[CDaoQueryDef :: SetParamValue](#setparamvalue)|Affecte la valeur d’un paramètre spécifié à la requête.|
|[CDaoQueryDef :: SetReturnsRecords](#setreturnsrecords)|Spécifie si l’objet querydef retourne des enregistrements. L’affectation de la valeur TRUE à cet attribut n’est valide que pour les requêtes SQL directes.|
|[CDaoQueryDef :: SetSQL](#setsql)|Définit la chaîne SQL qui spécifie la requête définie par l’objet querydef.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CDaoQueryDef :: m_pDAOQueryDef](#m_pdaoquerydef)|Pointeur vers l’interface OLE pour l’objet querydef DAO sous-jacent.|
|[CDaoQueryDef :: m_pDatabase](#m_pdatabase)|Pointeur vers l’objet `CDaoDatabase` auquel le querydef est associé. L’objet querydef peut être enregistré dans la base de données.|

## <a name="remarks"></a>Notes

Une querydef est un objet d’accès aux données qui contient l’instruction SQL qui décrit une requête, ainsi que ses propriétés, telles que « date de création » et « délai d’expiration ODBC ». Vous pouvez également créer des objets QueryDef temporaires sans les enregistrer, mais cela est pratique, et bien plus efficace, pour enregistrer les requêtes fréquemment réutilisées dans une base de données. Un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) gère une collection, appelée collection QueryDefs, qui contient ses querydefs enregistrés.

> [!NOTE]
>  Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur Open Database Connectivity (ODBC). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus puissantes que les classes MFC basées sur ODBC ; les classes basées sur DAO peuvent accéder aux données, notamment via des pilotes ODBC, via leur propre moteur de base de données. Les classes basées sur DAO prennent également en charge les opérations de langage de définition de données (DDL, Data Definition Language), telles que l’ajout de tables via les classes, sans avoir à appeler DAO directement.

## <a name="usage"></a>Usage

Utilisez des objets QueryDef pour travailler avec une requête enregistrée existante ou pour créer une requête enregistrée ou une requête temporaire :

1. Dans tous les cas, commencez par construire un objet `CDaoQueryDef`, en fournissant un pointeur vers l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) auquel la requête appartient.

1. Procédez ensuite comme suit, en fonction de vos choix :

   - Pour utiliser une requête enregistrée existante, appelez la fonction membre [Open](#open) de l’objet QueryDef, en fournissant le nom de la requête enregistrée.

   - Pour créer une nouvelle requête enregistrée, appelez la fonction membre [Create](#create) de l’objet QueryDef, en fournissant le nom de la requête. Appelez ensuite [Append](#append) pour enregistrer la requête en l’ajoutant à la collection QueryDefs de la base de données. `Create` place l’objet querydef dans un état ouvert. ainsi, après avoir appelé `Create` vous n’appelez pas `Open`.

   - Pour créer un objet querydef temporaire, appelez `Create`. Transmettez une chaîne vide pour le nom de la requête. N’appelez pas `Append`.

Lorsque vous avez fini d’utiliser un objet QueryDef, appelez sa fonction membre [Close](#close) ; Détruisez ensuite l’objet querydef.

> [!TIP]
>  Le moyen le plus simple de créer des requêtes enregistrées consiste à les créer et à les stocker dans votre base de données à l’aide de Microsoft Access. Ensuite, vous pouvez les ouvrir et les utiliser dans votre code MFC.

## <a name="purposes"></a>Opérations

Vous pouvez utiliser un objet querydef pour l’une des raisons suivantes :

- Pour créer un objet `CDaoRecordset`

- Pour appeler la fonction membre `Execute` de l’objet pour exécuter directement une requête d’action ou une requête SQL directe

Vous pouvez utiliser un objet querydef pour tout type de requête, y compris les requêtes SELECT, action, crosstab, Delete, Update, Append, Make-table, de définition de données, SQL direct, Union et Bulk. Le type de la requête est déterminé par le contenu de l’instruction SQL que vous fournissez. Pour plus d’informations sur les types de requêtes, consultez les fonctions membres `Execute` et [GetType](#gettype) . Les jeux d’enregistrements sont couramment utilisés pour les requêtes qui retournent des lignes, généralement celles utilisant l' **option Select... À partir de** Mots clés. `Execute` est le plus souvent utilisé pour les opérations en bloc. Pour plus d’informations, consultez [Execute](#execute) et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Querydefs et recordsets

Pour utiliser un objet querydef afin de créer un objet `CDaoRecordset`, vous créez ou ouvrez généralement un objet querydef comme décrit ci-dessus. Construisez ensuite un objet Recordset, en passant un pointeur vers votre objet querydef quand vous appelez [CDaoRecordset :: Open](../../mfc/reference/cdaorecordset-class.md#open). Le querydef que vous transmettez doit être dans un état ouvert. Pour plus d’informations, consultez la classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Vous ne pouvez pas utiliser un objet querydef pour créer un jeu d’enregistrements (l’utilisation la plus courante pour un objet querydef) à moins qu’il ne soit dans un état ouvert. Mettez l’objet querydef dans un état ouvert en appelant `Open` ou `Create`.

## <a name="external-databases"></a>Bases de données externes

Les objets QueryDef constituent la meilleure façon d’utiliser le dialecte SQL natif d’un moteur de base de données externe. Par exemple, vous pouvez créer une requête Transact SQL (telle qu’elle est utilisée sur Microsoft SQL Server) et la stocker dans un objet querydef. Lorsque vous devez utiliser une requête SQL qui n’est pas basée sur le moteur de base de données Microsoft Jet, vous devez fournir une chaîne de connexion qui pointe vers la source de données externe. Les requêtes avec des chaînes de connexion valides contournent le moteur de base de données et transmettent la requête directement au serveur de base de données externe pour traitement.

> [!TIP]
>  La méthode recommandée pour travailler avec des tables ODBC consiste à les attacher à un Microsoft Jet (. MDB).

Pour obtenir des informations connexes, consultez les rubriques « objet QueryDef », « collection QueryDefs » et « objet CdbDatabase » dans le kit de développement logiciel (SDK) DAO.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

##  <a name="append"></a>CDaoQueryDef :: Append

Appelez cette fonction membre après avoir appelé [Create](#create) pour créer un nouvel objet querydef.

```
virtual void Append();
```

### <a name="remarks"></a>Notes

`Append` enregistre l’objet querydef dans la base de données en l’ajoutant à la collection QueryDefs de la base de données. Vous pouvez utiliser la querydef comme objet temporaire sans l’ajouter, mais si vous voulez qu’elle soit persistante, vous devez appeler `Append`.

Si vous tentez d’ajouter un objet querydef temporaire, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

##  <a name="canupdate"></a>CDaoQueryDef :: CanUpdate

Appelez cette fonction membre pour déterminer si vous pouvez modifier la querydef, telle que la modification de son nom ou de sa chaîne SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si vous êtes autorisé à modifier l’objet querydef. Sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez modifier la querydef si :

- Elle n’est pas basée sur une base de données ouverte en lecture seule.

- Vous disposez des autorisations de mise à jour pour la base de données.

   Cela varie selon que vous avez implémenté des fonctionnalités de sécurité. MFC ne prend pas en charge la sécurité ; vous devez l’implémenter vous-même en appelant DAO directement ou à l’aide de Microsoft Access. Consultez la rubrique « propriété permissions » dans l’aide de DAO.

##  <a name="cdaoquerydef"></a>CDaoQueryDef :: CDaoQueryDef

Construit un objet `CDaoQueryDef`.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Paramètres

*pDatabase*<br/>
Pointeur vers un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) ouvert.

### <a name="remarks"></a>Notes

L’objet peut représenter une querydef existante stockée dans la collection QueryDefs de la base de données, une nouvelle requête à stocker dans la collection, ou une requête temporaire, à ne pas stocker. L’étape suivante dépend du type d’objet querydef :

- Si l’objet représente une querydef existante, appelez la fonction membre [Open](#open) de l’objet pour l’initialiser.

- Si l’objet représente un nouvel objet querydef à enregistrer, appelez la fonction membre [Create](#create) de l’objet. L’objet est ajouté à la collection QueryDefs de la base de données. Appelez ensuite `CDaoQueryDef` fonctions membres pour définir les attributs de l’objet. Enfin, appelez [Append](#append).

- Si l’objet représente un objet querydef temporaire (à ne pas enregistrer dans la base de données), appelez `Create`, en passant une chaîne vide pour le nom de la requête. Après avoir appelé `Create`, initialisez l’objet querydef en définissant directement ses attributs. N’appelez pas `Append`.

Pour définir les attributs de l’objet QueryDef, vous pouvez utiliser les fonctions membres [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)et [SetReturnsRecords](#setreturnsrecords) .

Lorsque vous avez terminé avec l’objet QueryDef, appelez sa fonction membre [Close](#close) . Si vous avez un pointeur vers l’objet QueryDef, utilisez l’opérateur **Delete** pour détruire C++ l’objet.

##  <a name="close"></a>CDaoQueryDef :: Close

Appelez cette fonction membre lorsque vous avez fini d’utiliser l’objet querydef.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

La fermeture de la querydef libère l’objet DAO sous-jacent, mais ne détruit pas l’objet C++ querydef DAO enregistré ou l’objet `CDaoQueryDef`. Ce n’est pas identique à [CDaoDatabase ::D eletequerydef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), qui supprime le querydef de la collection QueryDefs de la base de données dans DAO (s’il ne s’agit pas d’un objet querydef temporaire).

##  <a name="create"></a>CDaoQueryDef :: Create

Appelez cette fonction membre pour créer une requête enregistrée ou une nouvelle requête temporaire.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom unique de la requête enregistrée dans la base de données. Pour plus d’informations sur la chaîne, consultez la rubrique « méthode CreateQueryDef » dans l’aide de DAO. Si vous acceptez la valeur par défaut, une chaîne vide, un objet querydef temporaire est créé. Une telle requête n’est pas enregistrée dans la collection QueryDefs.

*lpszSQL*<br/>
Chaîne SQL qui définit la requête. Si vous acceptez la valeur par défaut NULL, vous devez appeler [SetSQL](#setsql) pour définir la chaîne. Jusqu’à présent, la requête n’est pas définie. Toutefois, vous pouvez utiliser la requête non définie pour ouvrir un Recordset. Pour plus d’informations, consultez la section Notes. L’instruction SQL doit être définie avant que vous puissiez ajouter l’objet querydef à la collection QueryDefs.

### <a name="remarks"></a>Notes

Si vous transmettez un nom dans *lpszName*, vous pouvez ensuite appeler [Append](#append) pour enregistrer l’objet querydef dans la collection QueryDefs de la base de données. Dans le cas contraire, l’objet est un querydef temporaire et n’est pas enregistré. Dans les deux cas, la querydef est dans un état ouvert et vous pouvez l’utiliser pour créer un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) ou appeler la fonction membre [Execute](#execute) de la querydef.

Si vous ne fournissez pas d’instruction SQL dans *lpszSQL*, vous ne pouvez pas exécuter la requête avec `Execute` mais vous pouvez l’utiliser pour créer un jeu d’enregistrements. Dans ce cas, MFC utilise l’instruction SQL par défaut du Recordset.

##  <a name="execute"></a>CDaoQueryDef :: Execute

Appelez cette fonction membre pour exécuter la requête définie par l’objet querydef.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Paramètres

*nOptions*<br/>
Entier qui détermine les caractéristiques de la requête. Pour obtenir des informations connexes, consultez la rubrique « méthode Execute » dans l’aide de DAO. Vous pouvez utiliser l’opérateur or au niveau du **&#124;** bit () pour combiner les constantes suivantes pour cet argument :

- `dbDenyWrite` refuser l’autorisation d’accès en écriture à d’autres utilisateurs.

- `dbInconsistent` des mises à jour incohérentes.

- `dbConsistent` des mises à jour cohérentes.

- `dbSQLPassThrough` SQL directe. Entraîne le passage de l’instruction SQL à une base de données ODBC pour traitement.

- `dbFailOnError` valeur par défaut. Annule les mises à jour si une erreur se produit et signale l’erreur à l’utilisateur.

- `dbSeeChanges` générer une erreur au moment de l’exécution si un autre utilisateur modifie les données que vous modifiez.

> [!NOTE]
>  Pour obtenir une explication des termes « incohérent » et « cohérent », consultez la rubrique « méthode d’exécution » dans l’aide de DAO.

### <a name="remarks"></a>Notes

Les objets QueryDef utilisés pour l’exécution de cette manière peuvent uniquement représenter l’un des types de requêtes suivants :

- Requêtes d’action

- Requêtes SQL directes

`Execute` ne fonctionne pas pour les requêtes qui retournent des enregistrements, telles que des requêtes SELECT. `Execute` est couramment utilisé pour les requêtes d’opérations en bloc, telles que **Update**, **Insert**ou **SELECT INTO**, ou pour les opérations DDL (Data Definition Language).

> [!TIP]
>  La méthode recommandée pour travailler avec des sources de données ODBC consiste à attacher des tables à un Microsoft Jet (. MDB). Pour plus d’informations, consultez la rubrique « accès aux bases de données externes avec DAO » dans l’aide de DAO.

Appelez la fonction membre [GetRecordsAffected](#getrecordsaffected) de l’objet querydef pour déterminer le nombre d’enregistrements affectés par l’appel de `Execute` le plus récent. Par exemple, `GetRecordsAffected` retourne des informations sur le nombre d’enregistrements supprimés, mis à jour ou insérés lors de l’exécution d’une requête d’action. Le nombre retourné ne reflète pas les modifications apportées aux tables associées lorsque des mises à jour ou des suppressions en cascade sont appliquées.

Si vous incluez à la fois `dbInconsistent` et `dbConsistent` ou si vous n’incluez ni l’un ni l’autre, le résultat est le `dbInconsistent`par défaut.

`Execute` ne retourne pas de Recordset. L’utilisation de `Execute` sur une requête qui sélectionne des enregistrements amène les MFC à lever une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

##  <a name="getconnect"></a>CDaoQueryDef :: GetConnect

Appelez cette fonction membre pour récupérer la chaîne de connexion associée à la source de données de la querydef.

```
CString GetConnect();
```

### <a name="return-value"></a>Valeur de retour

[CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant la chaîne de connexion pour l’objet querydef.

### <a name="remarks"></a>Notes

Cette fonction est utilisée uniquement avec les sources de données ODBC et certains pilotes ISAM. Elle n’est pas utilisée avec Microsoft Jet (. MDB); dans ce cas, `GetConnect` retourne une chaîne vide. Pour plus d’informations, consultez [SetConnect](#setconnect).

> [!TIP]
>  La méthode recommandée pour travailler avec des tables ODBC consiste à les attacher à un. Base de données MDB. Pour plus d’informations, consultez la rubrique « accès aux bases de données externes avec DAO » dans l’aide de DAO.

Pour plus d’informations sur les chaînes de connexion, consultez la rubrique « Connect Property » dans l’aide de DAO.

##  <a name="getdatecreated"></a>CDaoQueryDef :: GetDateCreated

Appelez cette fonction membre pour connaître la date à laquelle l’objet querydef a été créé.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valeur de retour

Objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) contenant la date et l’heure de création de l’objet querydef.

### <a name="remarks"></a>Notes

Pour obtenir des informations connexes, consultez la rubrique « Propriétés DateCreated, LastUpdated » dans l’aide de DAO.

##  <a name="getdatelastupdated"></a>CDaoQueryDef :: GetDateLastUpdated

Appelez cette fonction membre pour récupérer la date de la dernière mise à jour de l’objet QueryDef, lorsque l’une de ses propriétés a été modifiée, par exemple son nom, sa chaîne SQL ou sa chaîne de connexion.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valeur de retour

Objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) contenant la date et l’heure de la dernière mise à jour de la querydef.

### <a name="remarks"></a>Notes

Pour obtenir des informations connexes, consultez la rubrique « Propriétés DateCreated, LastUpdated » dans l’aide de DAO.

##  <a name="getfieldcount"></a>CDaoQueryDef :: GetFieldCount

Appelez cette fonction membre pour récupérer le nombre de champs dans la requête.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre de champs définis dans la requête.

### <a name="remarks"></a>Notes

`GetFieldCount` est utile pour boucler dans tous les champs de l’objet querydef. À cet effet, utilisez `GetFieldCount` conjointement avec [GetFieldInfo](#getfieldinfo).

##  <a name="getfieldinfo"></a>CDaoQueryDef :: GetFieldInfo

Appelez cette fonction membre pour obtenir différents genres d’informations sur un champ défini dans l’objet querydef.

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

*nIndex*<br/>
Index de base zéro du champ souhaité dans la collection de champs de la querydef, pour la recherche par index.

*FieldInfo*<br/>
Référence à un objet `CDaoFieldInfo` qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations relatives au champ à récupérer. Les options disponibles sont répertoriées ici, ainsi que ce qu’elles provoquent le retour de la fonction :

- Nom, type, taille, attributs AFX_DAO_PRIMARY_INFO (par défaut)

- AFX_DAO_SECONDARY_INFO informations principales plus : position ordinale, obligatoire, autoriser la longueur nulle, champ source, nom étranger, table source, ordre de classement

- AFX_DAO_ALL_INFO les informations primaires et secondaires plus : valeur par défaut, texte de validation, règle de validation

*lpszName*<br/>
Chaîne contenant le nom du champ souhaité, pour la recherche par nom. Vous pouvez utiliser une [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Pour obtenir une description des informations retournées dans *FieldInfo*, consultez la structure [cdaofieldinfo,](../../mfc/reference/cdaofieldinfo-structure.md) . Cette structure a des membres qui correspondent aux informations descriptives sous *dwInfoOptions* ci-dessus. Si vous demandez un niveau d’information, vous bénéficiez également des niveaux antérieurs d’informations.

##  <a name="getname"></a>CDaoQueryDef :: GetName

Appelez cette fonction membre pour récupérer le nom de la requête représentée par l’objet querydef.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

Nom de la requête.

### <a name="remarks"></a>Notes

Les noms des querydef sont des noms uniques définis par l’utilisateur. Pour plus d’informations sur les noms des QueryDef, consultez la rubrique « propriété de nom » dans l’aide de DAO.

##  <a name="getodbctimeout"></a>CDaoQueryDef :: GetODBCTimeout

Appelez cette fonction membre pour récupérer la limite de temps actuelle avant l’expiration d’une requête à une source de données ODBC.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Valeur de retour

Nombre de secondes avant l'expiration d'une requête.

### <a name="remarks"></a>Notes

Pour plus d’informations sur cette limite de temps, consultez la rubrique « propriété ODBCTimeout » dans l’aide de DAO.

> [!TIP]
>  La méthode recommandée pour travailler avec des tables ODBC consiste à les attacher à un Microsoft Jet (. MDB). Pour plus d’informations, consultez la rubrique « accès aux bases de données externes avec DAO » dans l’aide de DAO.

##  <a name="getparametercount"></a>CDaoQueryDef :: GetParameterCount

Appelez cette fonction membre pour récupérer le nombre de paramètres dans la requête enregistrée.

```
short GetParameterCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre de paramètres définis dans la requête.

### <a name="remarks"></a>Notes

`GetParameterCount` est utile pour boucler dans tous les paramètres de l’objet querydef. À cet effet, utilisez `GetParameterCount` conjointement avec [GetParameterInfo](#getparameterinfo).

Pour obtenir des informations connexes, consultez les rubriques « objet Parameter », « collection Parameters » et « déclaration de paramètres (SQL) » dans l’aide de DAO.

##  <a name="getparameterinfo"></a>CDaoQueryDef :: GetParameterInfo

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

*nIndex*<br/>
Index de base zéro du paramètre souhaité dans la collection de paramètres de la querydef, pour la recherche par index.

*ParamInfo et*<br/>
Référence à un objet [cdaoparameterinfo,](../../mfc/reference/cdaoparameterinfo-structure.md) qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur le paramètre à récupérer. L’option disponible est répertoriée ici, avec la valeur renvoyée par la fonction :

- Nom du AFX_DAO_PRIMARY_INFO (par défaut), tapez

*lpszName*<br/>
Chaîne contenant le nom du paramètre souhaité, pour la recherche par nom. Vous pouvez utiliser une [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Pour obtenir une description des informations retournées dans *ParamInfo et*, consultez la structure [cdaoparameterinfo,](../../mfc/reference/cdaoparameterinfo-structure.md) . Cette structure a des membres qui correspondent aux informations descriptives sous *dwInfoOptions* ci-dessus.

Pour obtenir des informations connexes, consultez la rubrique « Déclaration de paramètres (SQL) » dans l’aide de DAO.

##  <a name="getparamvalue"></a>CDaoQueryDef :: GetParamValue

Appelez cette fonction membre pour récupérer la valeur actuelle du paramètre spécifié stocké dans la collection de paramètres de la querydef.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom du paramètre dont vous souhaitez obtenir la valeur, pour la recherche par nom.

*nIndex*<br/>
Index de base zéro du paramètre dans la collection de paramètres de la querydef, pour la recherche par index. Vous pouvez obtenir cette valeur avec des appels à [GetParameterCount](#getparametercount) et [GetParameterInfo](#getparameterinfo).

### <a name="return-value"></a>Valeur de retour

Objet de la classe [COleVariant](../../mfc/reference/colevariant-class.md) qui contient la valeur du paramètre.

### <a name="remarks"></a>Notes

Vous pouvez accéder au paramètre par son nom ou par sa position ordinale dans la collection.

Pour obtenir des informations connexes, consultez la rubrique « Déclaration de paramètres (SQL) » dans l’aide de DAO.

##  <a name="getrecordsaffected"></a>CDaoQueryDef :: GetRecordsAffected

Appelez cette fonction membre pour déterminer le nombre d’enregistrements affectés par le dernier appel de l' [instruction EXECUTE](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valeur de retour

Nombre d'enregistrements concernés.

### <a name="remarks"></a>Notes

Le nombre retourné ne reflète pas les modifications apportées aux tables associées lorsque des mises à jour ou des suppressions en cascade sont appliquées.

Pour obtenir des informations connexes, consultez la rubrique « propriété RecordsAffected » dans l’aide de DAO.

##  <a name="getreturnsrecords"></a>CDaoQueryDef :: GetReturnsRecords

Appelez cette fonction membre pour déterminer si l’objet querydef est basé sur une requête qui retourne des enregistrements.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet querydef est basé sur une requête qui retourne des enregistrements ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est utilisée uniquement pour les requêtes SQL directes. Pour plus d’informations sur les requêtes SQL, consultez la fonction membre [Execute](#execute) . Pour plus d’informations sur l’utilisation de requêtes SQL directes, consultez la fonction membre [SetReturnsRecords](#setreturnsrecords) .

Pour obtenir des informations connexes, consultez la rubrique « propriété ReturnsRecords » dans l’aide de DAO.

##  <a name="getsql"></a>CDaoQueryDef :: GetSQL

Appelez cette fonction membre pour récupérer l’instruction SQL qui définit la requête sur laquelle la querydef est basée.

```
CString GetSQL();
```

### <a name="return-value"></a>Valeur de retour

Instruction SQL qui définit la requête sur laquelle la querydef est basée.

### <a name="remarks"></a>Notes

Vous allez probablement analyser la chaîne pour les mots clés, les noms de table, etc.

Pour obtenir des informations connexes, consultez les rubriques « propriété SQL », « Comparaison de Microsoft Jet Moteur de base de données SQL et ANSI SQL » et « interrogation d’une base de données avec SQL dans le code » dans l’aide de DAO.

##  <a name="gettype"></a>CDaoQueryDef :: GetType

Appelez cette fonction membre pour déterminer le type de requête de l’objet querydef.

```
short GetType();
```

### <a name="return-value"></a>Valeur de retour

Type de la requête définie par l’objet querydef. Pour obtenir les valeurs, consultez la section Notes.

### <a name="remarks"></a>Notes

Le type de requête est défini par ce que vous spécifiez dans la chaîne SQL de la querydef lorsque vous créez l’objet querydef ou appelez la fonction membre [SetSQL](#setsql) d’une querydef existante. Le type de requête retourné par cette fonction peut être l’une des valeurs suivantes :

- `dbQSelect` sélectionner

- Action `dbQAction`

- Analyse `dbQCrosstab`

- `dbQDelete` supprimer

- `dbQUpdate` Update

- `dbQAppend` ajouter

- `dbQMakeTable` Make-Table

- définition des données de `dbQDDL`

- `dbQSQLPassThrough` directe

- `dbQSetOperation` Union

- `dbQSPTBulk` utilisé avec `dbQSQLPassThrough` pour spécifier une requête qui ne retourne pas d’enregistrements.

> [!NOTE]
>  Pour créer une requête SQL directe, ne définissez pas la constante `dbSQLPassThrough`. Cela est défini automatiquement par le moteur de base de données Microsoft Jet lorsque vous créez un objet querydef et définissez la chaîne de connexion.

Pour plus d’informations sur les chaînes SQL, consultez [GetSQL](#getsql). Pour plus d’informations sur les types de requêtes, consultez [Execute](#execute).

##  <a name="isopen"></a>CDaoQueryDef :: IsOpen

Appelez cette fonction membre pour déterminer si l’objet `CDaoQueryDef` est actuellement ouvert.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet `CDaoQueryDef` est actuellement ouvert ; Sinon, 0.

### <a name="remarks"></a>Notes

Une querydef doit être dans un état ouvert avant que vous ne l’utilisiez pour appeler [Execute](#execute) ou pour créer un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Pour placer un objet querydef dans un appel d’état ouvert, [créez](#create) (pour un nouvel objet querydef) ou [ouvrez](#open) (pour un objet querydef existant).

##  <a name="m_pdatabase"></a>CDaoQueryDef :: m_pDatabase

Contient un pointeur vers l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) associé à l’objet querydef.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous devez accéder directement à la base de données (par exemple, pour obtenir des pointeurs vers d’autres objets QueryDef ou Recordset dans les collections de la base de données).

##  <a name="m_pdaoquerydef"></a>CDaoQueryDef :: m_pDAOQueryDef

Contient un pointeur vers l’interface OLE pour l’objet querydef DAO sous-jacent.

### <a name="remarks"></a>Notes

Ce pointeur est fourni à des fins d’exhaustivité et de cohérence avec les autres classes. Toutefois, dans la mesure où MFC encapsule entièrement les querydefs DAO, il est peu probable que vous en ayez besoin. Si vous l’utilisez, faites-le avec prudence, en particulier, ne modifiez pas la valeur du pointeur, sauf si vous savez ce que vous faites.

##  <a name="open"></a>CDaoQueryDef :: Open

Appelez cette fonction membre pour ouvrir une querydef précédemment enregistrée dans la collection QueryDefs de la base de données.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Chaîne qui contient le nom de l’objet querydef enregistré à ouvrir. Vous pouvez utiliser une [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Une fois la querydef ouverte, vous pouvez appeler sa fonction membre [Execute](#execute) ou utiliser la querydef pour créer un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

##  <a name="setconnect"></a>CDaoQueryDef :: SetConnect

Appelez cette fonction membre pour définir la chaîne de connexion de l’objet querydef.

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Paramètres

*lpszConnect*<br/>
Chaîne qui contient une chaîne de connexion pour l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) associé.

### <a name="remarks"></a>Notes

La chaîne de connexion est utilisée pour transmettre des informations supplémentaires à ODBC et à certains pilotes ISAM en fonction des besoins. Elle n’est pas utilisée pour Microsoft Jet (. MDB).

> [!TIP]
>  La méthode recommandée pour travailler avec des tables ODBC consiste à les attacher à un. Base de données MDB.

Avant d’exécuter une querydef qui représente une requête SQL directe à une source de données ODBC, définissez la chaîne de connexion avec `SetConnect` et appelez [SetReturnsRecords](#setreturnsrecords) pour spécifier si la requête retourne des enregistrements.

Pour plus d’informations sur la structure de la chaîne de connexion et des exemples de composants de chaîne de connexion, consultez la rubrique « Connect Property » dans l’aide de DAO.

##  <a name="setname"></a>CDaoQueryDef :: SetName

Appelez cette fonction membre si vous souhaitez modifier le nom d’une querydef qui n’est pas temporaire.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Chaîne qui contient le nouveau nom d’une requête temporaire dans l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) associé.

### <a name="remarks"></a>Notes

Les noms des querydef sont des noms uniques et définis par l’utilisateur. Vous pouvez appeler `SetName` avant que l’objet querydef soit ajouté à la collection QueryDefs.

##  <a name="setodbctimeout"></a>CDaoQueryDef :: SetODBCTimeout

Appelez cette fonction membre pour définir la limite de temps avant l’expiration d’une requête à une source de données ODBC.

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Paramètres

*nODBCTimeout*<br/>
Nombre de secondes avant l'expiration d'une requête.

### <a name="remarks"></a>Notes

Cette fonction membre vous permet de remplacer le nombre de secondes par défaut avant les opérations suivantes sur la source de données connectée « délai d’expiration ». Une opération peut expirer en raison de problèmes d’accès au réseau, d’un temps de traitement de requêtes excessif, etc. Appelez `SetODBCTimeout` avant d’exécuter une requête avec cette querydef si vous souhaitez modifier la valeur du délai d’expiration de la requête. (Au fur et à mesure que ODBC réutilise les connexions, la valeur du délai d’expiration est la même pour tous les clients sur la même connexion.)

La valeur par défaut du délai d’expiration de la requête est de 60 secondes.

##  <a name="setparamvalue"></a>CDaoQueryDef :: SetParamValue

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

*lpszName*<br/>
Nom du paramètre dont vous souhaitez définir la valeur.

*varValue*<br/>
Valeur à définir ; consultez la section Notes.

*nIndex*<br/>
Position ordinale du paramètre dans la collection de paramètres de la querydef. Vous pouvez obtenir cette valeur avec des appels à [GetParameterCount](#getparametercount) et [GetParameterInfo](#getparameterinfo).

### <a name="remarks"></a>Notes

Le paramètre doit déjà avoir été établi dans le cadre de la chaîne SQL de la querydef. Vous pouvez accéder au paramètre par son nom ou par sa position ordinale dans la collection.

Spécifiez la valeur à définir en tant qu’objet `COleVariant`. Pour plus d’informations sur la définition de la valeur et du type souhaités dans votre objet `COleVariant`, consultez la classe [COleVariant](../../mfc/reference/colevariant-class.md).

##  <a name="setreturnsrecords"></a>CDaoQueryDef :: SetReturnsRecords

Appelez cette fonction membre dans le cadre du processus de configuration d’une requête SQL directe à une base de données externe.

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Paramètres

*bReturnsRecords*<br/>
Passe la valeur TRUE si la requête sur une base de données externe retourne des enregistrements ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Dans ce cas, vous devez créer la querydef et définir ses propriétés à l’aide d’autres fonctions membres `CDaoQueryDef`. Pour obtenir une description des bases de données externes, consultez [SetConnect](#setconnect).

##  <a name="setsql"></a>CDaoQueryDef :: SetSQL

Appelez cette fonction membre pour définir l’instruction SQL exécutée par l’objet querydef.

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Paramètres

*lpszSQL*<br/>
Chaîne contenant une instruction SQL complète, appropriée pour l’exécution. La syntaxe de cette chaîne dépend du SGBD ciblé par votre requête. Pour plus d’informations sur la syntaxe utilisée dans le moteur de base de données Microsoft Jet, consultez la rubrique « Création d’instructions SQL dans le code » dans l’aide de DAO.

### <a name="remarks"></a>Notes

Une utilisation courante de `SetSQL` consiste à configurer un objet querydef en vue de son utilisation dans une requête SQL directe. (Pour la syntaxe des requêtes SQL directes sur votre SGBD cible, consultez la documentation de votre SGBD.)

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset, classe](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException, classe](../../mfc/reference/cdaoexception-class.md)
