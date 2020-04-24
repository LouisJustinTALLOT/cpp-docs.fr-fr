---
title: Classe CDaoQueryDef
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
ms.openlocfilehash: ed298c40daa9485683d0b989e47b97fdce9f6562
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754699"
---
# <a name="cdaoquerydef-class"></a>Classe CDaoQueryDef

Représente une définition de requête, ou « querydef », généralement stockée dans une base de données.

## <a name="syntax"></a>Syntaxe

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Construit un objet `CDaoQueryDef`. Prochain `Open` appel `Create`ou , selon vos besoins.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoQueryDef::Append](#append)|Annexe la requête à la collection RequêteDefs de la base de données sous forme de requête sauvegardée.|
|[CDaoQueryDef::CanUpdate](#canupdate)|Retourne nonzero si la requête peut mettre à jour la base de données.|
|[CDaoQueryDef::Close](#close)|Ferme l’objet de requête. Détruisez l’objet CMD lorsque vous en avez fini avec.|
|[CDaoQueryDef::Créer](#create)|Crée l’objet de requête DAO sous-jacent. Utilisez la requête comme requête temporaire, ou `Append` appelez pour l’enregistrer dans la base de données.|
|[CDaoQueryDef::Execute](#execute)|Exécute la requête définie par l’objet requête.|
|[CDaoQueryDef::GetConnect](#getconnect)|Retourne la chaîne de connexion associée à la requête. La chaîne de connexion identifie la source de données. (Pour les requêtes de passage SQL seulement; sinon une chaîne vide.)|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Retourne la date de création de la requête enregistrée.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Retourne la date à laquelle la requête enregistrée a été mise à jour pour la dernière fois.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Retourne le nombre de champs définis par la requête.|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Renvoie des informations sur un champ spécifié défini dans la requête.|
|[CDaoQueryDef::GetName](#getname)|Retourne le nom de la requête.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Retourne la valeur de délai d’attente utilisée par ODBC (pour une requête ODBC) lorsque la requête est exécutée. Cela détermine combien de temps pour permettre à l’action de la requête de terminer.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Retourne le nombre de paramètres définis pour la requête.|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Renvoie les informations sur un paramètre spécifié à la requête.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Retourne la valeur d’un paramètre spécifié à la requête.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Retourne le nombre d’enregistrements affectés par une requête en action.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Retourne nonzero si la requête définie par la requête renvoie les enregistrements.|
|[CDaoQueryDef::GetSQL](#getsql)|Retourne la chaîne SQL qui spécifie la requête définie par la requête.|
|[CDaoQueryDef::GetType](#gettype)|Retourne le type de requête : supprimer, mettre à jour, ajouter, faire la table, etc.|
|[CDaoQueryDef::IsOpen](#isopen)|Retourne nonzero si la requête est ouverte et peut être exécutée.|
|[CDaoQueryDef::Ouvert](#open)|Ouvre une requête existante stockée dans la collection RequêteDefs de la base de données.|
|[CDaoQueryDef::SetConnect](#setconnect)|Définit la chaîne de connexion pour une requête de passage SQL sur une source de données ODBC.|
|[CDaoQueryDef::SetName](#setname)|Définit le nom de la requête enregistrée, remplaçant le nom utilisé lors de la création de la requête.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Définit la valeur de délai d’attente utilisée par ODBC (pour une requête ODBC) lorsque la requête est exécutée.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Définit la valeur d’un paramètre spécifié à la requête.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Précise si la requête renvoie les enregistrements. La définition de cet attribut à TRUE n’est valable que pour les requêtes de passage SQL.|
|[CDaoQueryDef::SetSQL](#setsql)|Définit la chaîne SQL qui spécifie la requête définie par la requête.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Un pointeur à l’interface OLE pour l’objet de requête DAO sous-jacent.|
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Un pointeur `CDaoDatabase` de l’objet auquel la requête est associée. La requête peut être enregistrée dans la base de données ou non.|

## <a name="remarks"></a>Notes

Une requête est un objet d’accès aux données qui contient la déclaration SQL qui décrit une requête, et ses propriétés, telles que "Date Créé" et "ODBC Timeout." Vous pouvez également créer des objets de requête temporaire sans les enregistrer, mais il est pratique — et beaucoup plus efficace — d’enregistrer des requêtes couramment réutilisées dans une base de données. Un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) conserve une collection, appelée la collection QueryDefs, qui contient ses requêtes enregistrées.

> [!NOTE]
> Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur la connectivité open Database (ODBC). Tous les noms de classe de base de données DAO ont le préfixe "CDao". Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus capables que les classes MFC basées sur ODBC; les classes basées sur le DAO peuvent accéder aux données, y compris par l’intermédiaire des pilotes ODBC, via leur propre moteur de base de données. Les classes basées sur le DAO prennent également en charge les opérations de langage de définition des données (DDL), telles que l’ajout de tables via les classes, sans avoir à appeler directement DAO.

## <a name="usage"></a>Usage

Utilisez des objets de requête pour travailler avec une requête enregistrée existante ou pour créer une nouvelle requête sauvegardée ou une requête temporaire :

1. Dans tous les cas, construisez d’abord un `CDaoQueryDef` objet, fournissant un pointeur à [l’objet CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) auquel appartient la requête.

1. Ensuite, faites ce qui suit, en fonction de ce que vous voulez:

   - Pour utiliser une requête enregistrée existante, appelez la fonction de membre Open de l’objet [de](#open) requête, en fournissant le nom de la requête enregistrée.

   - Pour créer une nouvelle requête enregistrée, appelez la fonction de membre Create de l’objet [de](#create) requête, en fournissant le nom de la requête. Appelez [ensuite Append](#append) pour enregistrer la requête en la versant à la collection RequêteDefs de la base de données. `Create`met la requête dans un état ouvert, `Create` donc après `Open`avoir appelé vous n’appelez pas .

   - Pour créer une requête temporaire, `Create`appelez . Passez une ficelle vide pour le nom de requête. N’appelez pas `Append`.

Lorsque vous avez terminé l’utilisation d’un objet requête, appelez sa fonction de membre [Close](#close) ; puis détruire l’objet de requête.

> [!TIP]
> La façon la plus simple de créer des requêtes enregistrées est de les créer et de les stocker dans votre base de données à l’aide de Microsoft Access. Ensuite, vous pouvez les ouvrir et les utiliser dans votre code MFC.

## <a name="purposes"></a>Fins

Vous pouvez utiliser un objet requête à l’une des fins suivantes :

- Pour créer `CDaoRecordset` un objet

- Appeler la fonction `Execute` membre de l’objet pour exécuter directement une requête d’action ou une requête de passage SQL

Vous pouvez utiliser un objet de requête pour tout type de requête, y compris sélectionner, action, crosstab, supprimer, mettre à jour, ajouter, faire-table, définition de données, sqL pass-through, syndicat, et requêtes en vrac. Le type de requête est déterminé par le contenu de la déclaration SQL que vous fournissez. Pour plus d’informations sur `Execute` les types de requêtes, consultez les fonctions des membres [et getType.](#gettype) Les enregistrements sont couramment utilisés pour les requêtes de retour de rangée, généralement ceux qui utilisent le **SELECT ... DE** mots-clés. `Execute`est le plus couramment utilisé pour les opérations en vrac. Pour plus d’informations, voir [Exécuter](#execute) et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Requêtes et records

Pour utiliser un objet requête pour `CDaoRecordset` créer un objet, vous créez ou ouvrez généralement une requête décrite ci-dessus. Ensuite, construisez un objet recordet, en passant un pointeur à votre objet requête lorsque vous appelez [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). La requête que vous passez doit être en état d’ouverture. Pour plus d’informations, voir classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Vous ne pouvez pas utiliser une requête pour créer un étervère (l’utilisation la plus courante pour une requête) à moins qu’elle ne soit en état d’ouverture. Mettez la requête dans un état ouvert `Open` `Create`en appelant soit ou .

## <a name="external-databases"></a>Bases de données externes

Les objets Querydef sont le moyen privilégié d’utiliser le dialecte SQL natif d’un moteur de base de données externe. Par exemple, vous pouvez créer une requête Transact SQL (comme utilisé sur Microsoft SQL Server) et la stocker dans un objet requête. Lorsque vous devez utiliser une requête SQL qui n’est pas basée sur le moteur de base de données Microsoft Jet, vous devez fournir une chaîne de connexion qui indique la source de données externe. Les requêtes avec les chaînes de connexion valides contournent le moteur de base de données et passent la requête directement au serveur de base de données externe pour le traitement.

> [!TIP]
> La meilleure façon de travailler avec les tables ODBC est de les attacher à un Microsoft Jet (. base de données MDB).

Pour plus d’informations, voir les thèmes "Objet De Requête", "QueryDefs Collection", et "CdbDatabase Object" dans le DAO SDK.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef::Append

Appelez cette fonction de membre après avoir appelé [Create](#create) pour créer un nouvel objet de requête.

```
virtual void Append();
```

### <a name="remarks"></a>Notes

`Append`enregistre la requête dans la base de données en appending l’objet à la collection RequêteDefs de la base de données. Vous pouvez utiliser la requête comme un objet temporaire sans l’appending, mais `Append`si vous voulez qu’il persiste, vous devez appeler .

Si vous tentez d’ajouter un objet de requête temporaire, MFC lance une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate

Appelez cette fonction de membre pour déterminer si vous pouvez modifier la requête — comme changer son nom ou sa chaîne SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si vous êtes autorisé à modifier la requête; sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez modifier la requête si :

- Il n’est pas basé sur une base de données qui est ouverte à la lecture seulement.

- Vous avez des autorisations de mise à jour pour la base de données.

   Cela dépend si vous avez implémenté des fonctionnalités de sécurité. MFC n’apporte pas de soutien à la sécurité; vous devez l’implémenter vous-même en appelant DAO directement ou en utilisant Microsoft Access. Voir le thème "Permissions Property" dans DAO Help.

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

Construit un objet `CDaoQueryDef`.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Paramètres

*base de pData*<br/>
Un pointeur à un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) ouvert.

### <a name="remarks"></a>Notes

L’objet peut représenter un requêtet existant stocké dans la collection RequêteDefs de la base de données, une nouvelle requête à stocker dans la collection, ou une requête temporaire, à ne pas stocker. Votre prochaine étape dépend du type de requête :

- Si l’objet représente un requête en vigueur, appelez la fonction du membre [Open](#open) de l’objet pour l’initialiser.

- Si l’objet représente une nouvelle requête à sauver, appelez la fonction de membre [Créer](#create) de l’objet. Cela ajoute l’objet à la collection RequêteDefs de la base de données. Appelez `CDaoQueryDef` ensuite les fonctions des membres pour définir les attributs de l’objet. Enfin, appelez [l’annexe](#append).

- Si l’objet représente une requête temporaire (à ne pas `Create`être enregistrée dans la base de données), appelez, en passant une chaîne vide pour le nom de la requête. Après `Create`l’appel , initialiser la requête en définissant directement ses attributs. N’appelez pas `Append`.

Pour définir les attributs de la requête, vous pouvez utiliser le [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout), et [SetReturnsRecords fonctions](#setreturnsrecords) membres.

Lorsque vous avez terminé avec l’objet requête, appelez sa fonction de membre [Close.](#close) Si vous avez un pointeur sur la requête, utilisez l’opérateur **de suppression** pour détruire l’objet C.

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef::Close

Appelez cette fonction de membre lorsque vous avez terminé l’utilisation de l’objet requête.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

La fermeture de la requête libère l’objet DAO sous-jacent, mais ne détruit `CDaoQueryDef` pas l’objet de requête DAO enregistré ou l’objet C. Ce n’est pas la même chose que [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), qui supprime le requêtedef de la collection QueryDefs de la base de données dans DAO (si ce n’est une requête temporaire).

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef::Créer

Appelez cette fonction de membre pour créer une nouvelle requête enregistrée ou une nouvelle requête temporaire.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom unique de la requête enregistrée dans la base de données. Pour plus de détails sur la chaîne, voir le sujet "CreateQueryDef Method" dans DAO Help. Si vous acceptez la valeur par défaut, une chaîne vide, une requête temporaire est créée. Une telle requête n’est pas enregistrée dans la collection QueryDefs.

*lpszSQL*<br/>
La chaîne SQL qui définit la requête. Si vous acceptez la valeur par défaut de NULL, vous devez plus tard appeler [SetSQL](#setsql) pour régler la chaîne. Jusque-là, la requête n’est pas définie. Vous pouvez cependant utiliser la requête indéfinie pour ouvrir un dossier; voir Remarques pour plus de détails. La déclaration SQL doit être définie avant de pouvoir annexer la requête à la collection De requêteS.

### <a name="remarks"></a>Notes

Si vous passez un nom dans *lpszName*, vous pouvez alors appeler [Append](#append) pour enregistrer la requête dans la collection RequêteDefs de la base de données. Sinon, l’objet est une requête temporaire et n’est pas enregistré. Dans les deux cas, la requête est en état d’ouverture, et vous pouvez soit l’utiliser pour créer un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) ou appeler la fonction de membre [Execute](#execute) de la requête.

Si vous ne fournissez pas une déclaration SQL en *lpszSQL*, vous ne pouvez pas exécuter la requête avec `Execute` mais vous pouvez l’utiliser pour créer un dossier. Dans ce cas, MFC utilise la déclaration SQL par défaut du recordet.

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef::Execute

Appelez cette fonction de membre pour exécuter la requête définie par l’objet de requête.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Paramètres

*nOptions*<br/>
Un intégrant qui détermine les caractéristiques de la requête. Pour obtenir des informations connexes, consultez le thème « Execute Method » dans DAO Help. Vous pouvez utiliser l’opérateur bitwise-OR ( **&#124;**) pour combiner les constantes suivantes pour cet argument :

- `dbDenyWrite`Refuser d’écrire la permission à d’autres utilisateurs.

- `dbInconsistent`Mises à jour incohérentes.

- `dbConsistent`Mises à jour cohérentes.

- `dbSQLPassThrough`SQL passer. La déclaration SQL doit être transmise à une base de données de l’ODBC pour le traitement.

- `dbFailOnError`Valeur par défaut. Annulez les mises à jour en cas d’erreur et signalez l’erreur à l’utilisateur.

- `dbSeeChanges`Générez une erreur de temps d’exécution si un autre utilisateur modifie les données que vous modifiez.

> [!NOTE]
> Pour une explication des termes «incohérent» et «cohérent», voir le sujet «Execute Method» dans DAO Aide.

### <a name="remarks"></a>Notes

Les objets De requête utilisés pour l’exécution de cette manière ne peuvent représenter qu’un des types de requêtes suivants :

- Requêtes d’action

- Questions de passage SQL

`Execute`ne fonctionne pas pour les requêtes qui renvoient les enregistrements, comme certaines requêtes. `Execute`est couramment utilisé pour les requêtes d’exploitation en vrac, telles que **UPDATE**, **INSERT**, ou **SELECT INTO**, ou pour les opérations de langage de définition de données (DDL).

> [!TIP]
> La meilleure façon de travailler avec les sources de données ODBC est d’attacher des tables à un Microsoft Jet (. base de données MDB). Pour plus d’informations, consultez le thème « Accès aux bases de données externes avec DAO » dans DAO Help.

Appelez la fonction membre [GetRecordsAffected](#getrecordsaffected) de l’objet de requête pour déterminer `Execute` le nombre d’enregistrements affectés par l’appel le plus récent. Par exemple, `GetRecordsAffected` renvoie des informations sur le nombre d’enregistrements supprimés, mis à jour ou insérés lors de l’exécution d’une requête en action. Le nombre retourné ne reflétera pas les changements dans les tableaux connexes lorsque des mises à jour ou des suppressions en cascade sont en vigueur.

Si vous `dbInconsistent` incluez les deux et `dbConsistent` ou si `dbInconsistent`vous n’incluez ni l’un ni l’autre, le résultat est la valeur par défaut, .

`Execute`ne retourne pas un jeu d’enregistrement. L’utilisation d’une `Execute` requête qui sélectionne les enregistrements amène MFC à jeter une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef::GetConnect

Appelez cette fonction de membre pour obtenir la chaîne de connexion associée à la source de données de la requête.

```
CString GetConnect();
```

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant la chaîne de connexion pour la requête.

### <a name="remarks"></a>Notes

Cette fonction n’est utilisée qu’avec les sources de données ODBC et certains pilotes ISAM. Il n’est pas utilisé avec Microsoft Jet (. bases de données MDB) ; dans ce `GetConnect` cas, retourne une chaîne vide. Pour plus d’informations, voir [SetConnect](#setconnect).

> [!TIP]
> La meilleure façon de travailler avec les tables ODBC est de les attacher à un . Base de données de la BMD. Pour plus d’informations, consultez le thème « Accès aux bases de données externes avec DAO » dans DAO Help.

Pour plus d’informations sur les chaînes de connexion, consultez le thème "Connect Property" dans DAO Help.

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated

Appelez cette fonction de membre pour obtenir la date de création de l’objet de requête.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valeur de retour

Un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) contenant la date et l’heure de la création de la requête.

### <a name="remarks"></a>Notes

Pour plus d’informations connexes, voir le sujet "DateCreated, LastUpdated Properties" dans DAO Help.

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

Appelez cette fonction de membre pour obtenir la date à laquelle l’objet de la requête a été mis à jour pour la dernière fois — lorsque l’une de ses propriétés a été modifiée, comme son nom, sa chaîne SQL ou sa chaîne de connexion.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valeur de retour

Un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) contenant la date et l’heure de la requête a été mis à jour pour la dernière fois.

### <a name="remarks"></a>Notes

Pour plus d’informations connexes, voir le sujet "DateCreated, LastUpdated Properties" dans DAO Help.

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

Appelez cette fonction de membre pour récupérer le nombre de champs dans la requête.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de champs définis dans la requête.

### <a name="remarks"></a>Notes

`GetFieldCount`est utile pour boucler à travers tous les champs de la requête. À cette fin, utiliser `GetFieldCount` en conjonction avec [GetFieldInfo](#getfieldinfo).

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo

Appelez cette fonction de membre pour obtenir divers types d’informations sur un champ défini dans la requête.

```cpp
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
L’indice zéro du champ souhaité dans la collection Fields de la requête, pour le lookup par index.

*Fieldinfo*<br/>
Une référence `CDaoFieldInfo` à un objet qui renvoie les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur le champ à récupérer. Les options disponibles sont énumérées ici ainsi que ce qu’elles causent le retour de la fonction :

- AFX_DAO_PRIMARY_INFO (par défaut) Nom, Type, Taille, Attributs

- AFX_DAO_SECONDARY_INFO’information principale plus: Position ordinaire, Requise, Permettre la longueur zéro, Champ Source, Nom étranger, Tableau source, Ordonnance de Collating

- AFX_DAO_ALL_INFO informations primaires et secondaires plus : Valeur par défaut, texte de validation, règle de validation

*lpszName (en)*<br/>
Une chaîne contenant le nom du champ désiré, pour le lookup par son nom. Vous pouvez utiliser un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Pour une description de l’information retournée dans *fieldinfo*, voir la structure [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md) Cette structure a des membres qui correspondent à l’information descriptive sous *dwInfoOptions* ci-dessus. Si vous demandez un niveau d’information, vous obtenez également des niveaux d’information antérieurs.

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef::GetName

Appelez cette fonction de membre pour récupérer le nom de la requête représentée par la requête.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

Nom de la requête.

### <a name="remarks"></a>Notes

Les noms De requête sont des noms uniques définis par l’utilisateur. Pour plus d’informations sur les noms de requête, voir le thème "Nom Propriété" dans DAO Aide.

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

Appelez cette fonction de membre pour récupérer le délai actuel avant une requête à une source de données ODBC fois.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Valeur de retour

Nombre de secondes avant l'expiration d'une requête.

### <a name="remarks"></a>Notes

Pour plus d’informations sur cette limite de temps, voir le sujet "ODBCTimeout Property" dans DAO Help.

> [!TIP]
> La meilleure façon de travailler avec les tables ODBC est de les attacher à un Microsoft Jet (. base de données MDB). Pour plus d’informations, consultez le thème « Accès aux bases de données externes avec DAO » dans DAO Help.

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount

Appelez cette fonction de membre pour récupérer le nombre de paramètres dans la requête enregistrée.

```
short GetParameterCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de paramètres définis dans la requête.

### <a name="remarks"></a>Notes

`GetParameterCount`est utile pour boucler tous les paramètres de la requête. À cette fin, utiliser `GetParameterCount` en conjonction avec [GetParameterInfo](#getparameterinfo).

Pour plus d’informations, consultez les thèmes « Objet Paramètre », « Collection de paramètres » et « Déclaration DE PARAMETERS (SQL) » dans DAO Help.

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo

Appelez cette fonction de membre pour obtenir des informations sur un paramètre défini dans la requête.

```cpp
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
L’indice zéro du paramètre souhaité dans la collection paramètres de la requête, pour la recherche par index.

*paraminfo*<br/>
Une référence à un objet [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) qui renvoie les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur le paramètre à récupérer. L’option disponible est répertoriée ici avec ce qu’elle provoque le retour de la fonction:

- AFX_DAO_PRIMARY_INFO (Par défaut) Nom, Type

*lpszName (en)*<br/>
Une chaîne contenant le nom du paramètre souhaité, pour le lookup par nom. Vous pouvez utiliser un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Pour une description de l’information retournée dans *le paraminfo*, voir la structure [CDaoParameterInfo.](../../mfc/reference/cdaoparameterinfo-structure.md) Cette structure a des membres qui correspondent à l’information descriptive sous *dwInfoOptions* ci-dessus.

Pour plus d’informations, consultez le thème " Déclaration DE PARAMETERS (SQL)" dans DAO Aide.

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

Appelez cette fonction de membre pour récupérer la valeur actuelle du paramètre spécifié stocké dans la collection paramètres de la requête.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom du paramètre dont vous voulez la valeur, pour le lookup par nom.

*nIndex*<br/>
L’indice zéro du paramètre dans la collection paramètres de la requête, pour la recherche par index. Vous pouvez obtenir cette valeur avec des appels à [GetParameterCount](#getparametercount) et [GetParameterInfo](#getparameterinfo).

### <a name="return-value"></a>Valeur de retour

Un objet de classe [COleVariant](../../mfc/reference/colevariant-class.md) qui contient la valeur du paramètre.

### <a name="remarks"></a>Notes

Vous pouvez accéder au paramètre par son nom ou par sa position ordinaire dans la collection.

Pour plus d’informations, consultez le thème " Déclaration DE PARAMETERS (SQL)" dans DAO Aide.

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

Appelez cette fonction de membre pour déterminer combien d’enregistrements ont été affectés par le dernier appel [d’Exécuter](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valeur de retour

Nombre d'enregistrements concernés.

### <a name="remarks"></a>Notes

Le nombre retourné ne reflétera pas les changements dans les tableaux connexes lorsque des mises à jour ou des suppressions en cascade sont en vigueur.

Pour obtenir des informations connexes, consultez le thème « Propriété infectée par les records » dans DAO Help.

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

Appelez cette fonction de membre pour déterminer si la requête est basée sur une requête qui renvoie les dossiers.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la requête est basée sur une requête qui renvoie les enregistrements; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction de membre n’est utilisée que pour les requêtes de passage SQL. Pour plus d’informations sur les requêtes SQL, consultez la fonction du membre [Exécuter.](#execute) Pour plus d’informations sur le travail avec les requêtes de passage SQL, consultez la fonction [membre SetReturnsRecords.](#setreturnsrecords)

Pour plus d’informations connexes, voir le sujet "ReturnsRecords Property" dans DAO Help.

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL

Appelez cette fonction de membre pour récupérer la déclaration SQL qui définit la requête sur laquelle la requête est basée.

```
CString GetSQL();
```

### <a name="return-value"></a>Valeur de retour

La déclaration SQL qui définit la requête sur laquelle la requête est basée.

### <a name="remarks"></a>Notes

Vous allez alors probablement analyser la chaîne pour les mots clés, les noms de table, et ainsi de suite.

Pour plus d’informations, consultez les thèmes "SQL Property", "Comparison of Microsoft Jet Database Engine SQL et ANSI SQL", et "Querying a Database with SQL in Code" dans DAO Help.

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef::GetType

Appelez cette fonction de membre pour déterminer le type de requête de la requête.

```
short GetType();
```

### <a name="return-value"></a>Valeur de retour

Le type de requête défini par la requête. Pour les valeurs, voir Remarques.

### <a name="remarks"></a>Notes

Le type de requête est défini par ce que vous spécifiez dans la chaîne SQL de la requête lorsque vous créez le requêteur ou appelez la fonction de membre [SetSQL](#setsql) d’une requête existante. Le type de requête retourné par cette fonction peut être l’une des valeurs suivantes :

- `dbQSelect`Sélectionnez

- Action `dbQAction`

- `dbQCrosstab`Crosstab (Crosstab)

- `dbQDelete`Supprimer

- `dbQUpdate` Update

- `dbQAppend`Ajouter

- `dbQMakeTable`Table de maquillage

- `dbQDDL`Définition des données

- `dbQSQLPassThrough`Passage à travers

- `dbQSetOperation`Union

- `dbQSPTBulk`Utilisé `dbQSQLPassThrough` pour spécifier une requête qui ne renvoie pas les enregistrements.

> [!NOTE]
> Pour créer une requête de passage SQL, ne `dbSQLPassThrough` définissez pas la constante. Ceci est réglé automatiquement par le moteur de base de données Microsoft Jet lorsque vous créez un objet requête et définissez la chaîne de connexion.

Pour plus d’informations sur les cordes SQL, voir [GetSQL](#getsql). Pour plus d’informations sur les types de requêtes, voir [Exécuter](#execute).

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef::IsOpen

Appelez cette fonction de `CDaoQueryDef` membre pour déterminer si l’objet est actuellement ouvert.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CDaoQueryDef` l’objet est actuellement ouvert; sinon 0.

### <a name="remarks"></a>Notes

Une requête doit être en état ouvert avant de l’utiliser pour appeler [Exécuter](#execute) ou créer un objet [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Mettre une requête dans un appel à l’état ouvert soit [Créer](#create) (pour une nouvelle requête) ou [ouvrir](#open) (pour une requête existante).

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase

Contient un pointeur à l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) associé à l’objet de requête.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous avez besoin d’accéder directement à la base de données — par exemple, pour obtenir des indications sur d’autres objets de requête ou d’enregistrement dans les collections de la base de données.

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef

Contient un pointeur à l’interface OLE pour l’objet de requête DAO sous-jacent.

### <a name="remarks"></a>Notes

Ce pointeur est prévu pour l’exhaustivité et la cohérence avec les autres classes. Cependant, parce que MFC encapsule plutôt pleinement les requêtes DAO, il est peu probable que vous en ayez besoin. Si vous l’utilisez, faites-le prudemment — en particulier, ne modifiez pas la valeur du pointeur à moins que vous ne sachiez ce que vous faites.

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef::Ouvert

Appelez cette fonction de membre pour ouvrir une requête précédemment enregistrée dans la collection QueryDefs de la base de données.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Une chaîne qui contient le nom de la requête sauvegardée pour s’ouvrir. Vous pouvez utiliser un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Une fois que la requête est ouverte, vous pouvez appeler sa fonction de membre [Exécuter](#execute) ou utiliser le code requête pour créer un objet [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md)

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect

Appelez cette fonction de membre pour définir la chaîne de connexion de l’objet de requête.

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Paramètres

*lpszConnect*<br/>
Une chaîne qui contient une chaîne de connexion pour l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) associé.

### <a name="remarks"></a>Notes

La chaîne de connexion est utilisée pour transmettre des informations supplémentaires à ODBC et à certains pilotes ISAM au besoin. Il n’est pas utilisé pour Microsoft Jet (. bases de données MDB).

> [!TIP]
> La meilleure façon de travailler avec les tables ODBC est de les attacher à un . Base de données de la BMD.

Avant d’exécuter une requête qui représente une requête de passage SQL à une source de `SetConnect` données ODBC, définissez la chaîne de connexion et appelez [SetReturnsRecords](#setreturnsrecords) pour spécifier si la requête renvoie les enregistrements.

Pour plus d’informations sur la structure de la chaîne de connexion et des exemples de composants de chaîne de connexion, voir le sujet "Connect Property" dans DAO Help.

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef::SetName

Appelez cette fonction de membre si vous voulez changer le nom d’une requête qui n’est pas temporaire.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Une chaîne qui contient le nouveau nom d’une requête non temporaire dans l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) associé.

### <a name="remarks"></a>Notes

Les noms De requête sont des noms uniques définis par l’utilisateur. Vous pouvez `SetName` appeler avant que l’objet de requête n’est annexé à la collection De RequêteDefs.

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

Appelez cette fonction de membre pour définir le délai avant une requête à une source de données ODBC fois.

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Paramètres

*nODBCTimeout (en anglais seulement)*<br/>
Nombre de secondes avant l'expiration d'une requête.

### <a name="remarks"></a>Notes

Cette fonction de membre vous permet de remplacer le nombre par défaut de secondes avant les opérations ultérieures sur la source de données connectées " temps mort ". Une opération peut s’éteindre en raison de problèmes d’accès au réseau, de temps de traitement excessif des requêtes, et ainsi de suite. Appelez `SetODBCTimeout` avant d’exécuter une requête avec cette requête si vous souhaitez modifier la valeur de temps d’arrêt de requête. (Comme ODBC réutilise les connexions, la valeur de délai d’attente est la même pour tous les clients sur la même connexion.)

La valeur par défaut pour les délais d’attente des requêtes est de 60 secondes.

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

Appelez cette fonction de membre pour définir la valeur d’un paramètre dans la requête au moment de l’exécution.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom du paramètre dont vous souhaitez définir la valeur.

*varValue*<br/>
La valeur à définir; voir Remarques.

*nIndex*<br/>
La position ordinaire du paramètre dans la collection paramètres de la requête. Vous pouvez obtenir cette valeur avec des appels à [GetParameterCount](#getparametercount) et [GetParameterInfo](#getparameterinfo).

### <a name="remarks"></a>Notes

Le paramètre doit déjà avoir été établi dans le cadre de la chaîne SQL de la requête. Vous pouvez accéder au paramètre par son nom ou par sa position ordinaire dans la collection.

Spécifier la `COleVariant` valeur à définir comme objet. Pour plus d’informations sur la `COleVariant` définition de la valeur et le type souhaités dans votre objet, consultez la classe [COleVariant](../../mfc/reference/colevariant-class.md).

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

Appelez cette fonction de membre dans le cadre du processus de mise en place d’une requête de passage SQL à une base de données externe.

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Paramètres

*bReturnsRecords*<br/>
Passez VRAI si la requête sur une base de données externe renvoie des enregistrements; autrement, FALSE.

### <a name="remarks"></a>Notes

Dans un tel cas, vous devez créer la requête `CDaoQueryDef` et définir ses propriétés à l’aide d’autres fonctions membres. Pour une description des bases de données externes, voir [SetConnect](#setconnect).

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL

Appelez cette fonction de membre pour définir la déclaration SQL que la requête exécute.

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Paramètres

*lpszSQL*<br/>
Une chaîne contenant une déclaration SQL complète, adaptée à l’exécution. La syntaxe de cette chaîne dépend de la DBMS que votre requête cible. Pour une discussion sur la syntaxe utilisée dans le moteur de base de données Microsoft Jet, consultez le thème « Construire des déclarations SQL dans le code » dans DAO Help.

### <a name="remarks"></a>Notes

Une utilisation `SetSQL` typique de est la mise en place d’un objet requête pour une utilisation dans une requête DE passage SQL. (Pour la syntaxe des requêtes de passage SQL sur votre DBMS cible, consultez la documentation de votre DBMS.)

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[Classe CDaoException](../../mfc/reference/cdaoexception-class.md)
