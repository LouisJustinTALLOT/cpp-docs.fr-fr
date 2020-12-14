---
description: 'En savoir plus sur : classe CDaoDatabase'
title: Classe CDaoDatabase
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: 2044f24c2485071e0fa8930956e8ea15753047ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250970"
---
# <a name="cdaodatabase-class"></a>Classe CDaoDatabase

Représente une connexion à une base de données Access à l’aide d’objets d’accès aux données (DAO). DAO est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.

## <a name="syntax"></a>Syntaxe

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDaoDatabase :: CDaoDatabase](#cdaodatabase)|Construit un objet `CDaoDatabase`. Appelez `Open` pour connecter l’objet à une base de données.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoDatabase :: CanTransact](#cantransact)|Retourne une valeur différente de zéro si la base de données prend en charge les transactions.|
|[CDaoDatabase :: CanUpdate](#canupdate)|Retourne une valeur différente de zéro si l' `CDaoDatabase` objet peut être mis à jour (pas en lecture seule).|
|[CDaoDatabase :: Close](#close)|Ferme la connexion à la base de données.|
|[CDaoDatabase :: Create](#create)|Crée l’objet de base de données DAO sous-jacent et initialise l' `CDaoDatabase` objet.|
|[CDaoDatabase :: CreateRelation](#createrelation)|Définit une nouvelle relation entre les tables de la base de données.|
|[CDaoDatabase ::D eleteQueryDef](#deletequerydef)|Supprime un objet querydef enregistré dans la collection QueryDefs de la base de données.|
|[CDaoDatabase ::D eleteRelation](#deleterelation)|Supprime une relation existante entre les tables de la base de données.|
|[CDaoDatabase ::D eleteTableDef](#deletetabledef)|Supprime la définition d’une table dans la base de données. Cela supprime la table réelle et toutes ses données.|
|[CDaoDatabase :: Execute](#execute)|Exécute une requête d’action. `Execute`L’appel de pour une requête qui retourne des résultats lève une exception.|
|[CDaoDatabase :: GetConnect](#getconnect)|Retourne la chaîne de connexion utilisée pour connecter l' `CDaoDatabase` objet à une base de données. Utilisé pour ODBC.|
|[CDaoDatabase::GetName](#getname)|Retourne le nom de la base de données en cours d’utilisation.|
|[CDaoDatabase :: GetQueryDefCount](#getquerydefcount)|Retourne le nombre de requêtes définies pour la base de données.|
|[CDaoDatabase :: GetQueryDefInfo](#getquerydefinfo)|Retourne des informations sur une requête spécifiée définie dans la base de données.|
|[CDaoDatabase :: GetQueryTimeout](#getquerytimeout)|Retourne le nombre de secondes après lesquelles les opérations de requête de base de données expirent. Affecte toutes les opérations d’ouverture, d’ajout, de mise à jour et de modification suivantes, ainsi que d’autres opérations sur les sources de données ODBC (uniquement) telles que les `Execute` appels.|
|[CDaoDatabase :: GetRecordsAffected](#getrecordsaffected)|Retourne le nombre d’enregistrements affectés par la dernière opération Update, Edit ou Add ou par un appel à `Execute` .|
|[CDaoDatabase :: GetRelationCount](#getrelationcount)|Retourne le nombre de relations définies entre les tables de la base de données.|
|[CDaoDatabase :: GetRelationInfo](#getrelationinfo)|Retourne des informations sur une relation spécifiée entre des tables dans la base de données.|
|[CDaoDatabase :: GetTableDefCount](#gettabledefcount)|Retourne le nombre de tables définies dans la base de données.|
|[CDaoDatabase :: GetTableDefInfo](#gettabledefinfo)|Retourne des informations sur une table spécifiée dans la base de données.|
|[CDaoDatabase :: GetVersion](#getversion)|Retourne la version du moteur de base de données associée à la base de données.|
|[CDaoDatabase :: IsOpen](#isopen)|Retourne une valeur différente de zéro si l' `CDaoDatabase` objet est actuellement connecté à une base de données.|
|[CDaoDatabase :: Open](#open)|Établit une connexion à une base de données.|
|[CDaoDatabase :: SetQueryTimeout](#setquerytimeout)|Définit le nombre de secondes au terme desquelles les opérations de requête de base de données (sur les sources de données ODBC uniquement) expirent. Affecte toutes les opérations d’ajout, de mise à jour et de suppression suivantes.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoDatabase :: m_pDAODatabase](#m_pdaodatabase)|Pointeur vers l’objet de base de données DAO sous-jacent.|
|[CDaoDatabase :: m_pWorkspace](#m_pworkspace)|Pointeur vers l’objet [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) qui contient la base de données et définit son espace de transaction.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les formats de base de données pris en charge, consultez la fonction membre [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) . Vous pouvez avoir un ou plusieurs `CDaoDatabase` objets actifs à la fois dans un « espace de travail » donné, représenté par un objet [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) . L’espace de travail gère une collection d’objets de base de données ouverts, appelée collection de bases de données.

## <a name="usage"></a>Utilisation

Vous pouvez créer des objets de base de données implicitement lorsque vous créez des objets Recordset. Toutefois, vous pouvez également créer des objets de base de données de manière explicite. Pour utiliser une base de données existante explicitement avec `CDaoDatabase` , effectuez l’une des opérations suivantes :

- Construit un `CDaoDatabase` objet, en passant un pointeur vers un objet [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) ouvert.

- Ou construisez un `CDaoDatabase` objet sans spécifier l’espace de travail (MFC crée un objet espace de travail temporaire).

Pour créer un nouveau Microsoft Jet (. MDB), construisez un `CDaoDatabase` objet et appelez sa fonction membre [Create](#create) . N'  appelez pas `Open` after `Create` .

Pour ouvrir une base de données existante, construisez un `CDaoDatabase` objet et appelez sa fonction membre [Open](#open) .

L’une de ces techniques ajoute l’objet de base de données DAO à la collection de bases de données de l’espace de travail et ouvre une connexion aux données. Lorsque vous construisez ensuite des objets [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)ou [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) pour fonctionner sur la base de données connectée, transmettez les constructeurs de ces objets à un pointeur vers votre `CDaoDatabase` objet. Lorsque vous avez terminé d’utiliser la connexion, appelez la fonction membre [Close](#close) et détruisez l' `CDaoDatabase` objet. `Close` ferme tous les jeux d’enregistrements que vous n’avez pas fermés précédemment.

## <a name="transactions"></a>Transactions

Le traitement des transactions de base de données est fourni au niveau de l’espace de travail : consultez les fonctions membres [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans) et [ROLLBACK](../../mfc/reference/cdaoworkspace-class.md#rollback) de la classe`CDaoWorkspace`.

## <a name="odbc-connections"></a>Connexions ODBC

La méthode recommandée pour utiliser des sources de données ODBC consiste à attacher des tables externes à un Microsoft Jet (. MDB).

## <a name="collections"></a>Collections

Chaque base de données gère ses propres collections d’objets TableDef, QueryDef, Recordset et relation. La classe `CDaoDatabase` fournit des fonctions membres pour manipuler ces objets.

> [!NOTE]
> Les objets sont stockés dans DAO, et non dans l’objet de base de données MFC. MFC fournit des classes pour les objets TableDef, QueryDef et Recordset, mais pas pour les objets relation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a> CDaoDatabase :: CanTransact

Appelez cette fonction membre pour déterminer si la base de données autorise les transactions.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la base de données prend en charge les transactions ; Sinon, 0.

### <a name="remarks"></a>Notes

Les transactions sont gérées dans l’espace de travail de la base de données.

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a> CDaoDatabase :: CanUpdate

Appelez cette fonction membre pour déterminer si l' `CDaoDatabase` objet autorise les mises à jour.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l' `CDaoDatabase` objet autorise les mises à jour ; sinon, 0, ce qui indique que vous avez passé la valeur true dans *bReadOnly* lorsque vous avez ouvert l' `CDaoDatabase` objet ou que la base de données elle-même est en lecture seule. Consultez la fonction membre [Open](#open) .

### <a name="remarks"></a>Notes

Pour plus d’informations sur la mise à jour de la base de données, consultez la rubrique « propriété pouvant être mise à jour » dans l’aide de DAO.

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a> CDaoDatabase :: CDaoDatabase

Construit un objet `CDaoDatabase`.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Paramètres

*pWorkspace*<br/>
Pointeur vers l' `CDaoWorkspace` objet qui contiendra le nouvel objet de base de données. Si vous acceptez la valeur par défaut NULL, le constructeur crée un `CDaoWorkspace` objet temporaire qui utilise l’espace de travail DAO par défaut. Vous pouvez obtenir un pointeur vers l’objet de l’espace de travail via le membre de données [m_pWorkspace](#m_pworkspace) .

### <a name="remarks"></a>Notes

Après avoir construit l’objet, si vous créez un nouveau Microsoft Jet (. MDB), appelez la fonction membre [Create](#create) de l’objet. Si vous ouvrez une base de données existante, appelez la fonction membre [Open](#open) de l’objet.

Lorsque vous avez terminé avec l’objet, vous devez appeler sa fonction membre [Close](#close) , puis détruire l' `CDaoDatabase` objet.

Il peut s’avérer pratique d’incorporer l' `CDaoDatabase` objet dans votre classe de document.

> [!NOTE]
> Un `CDaoDatabase` objet est également créé implicitement si vous ouvrez un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) sans passer un pointeur à un `CDaoDatabase` objet existant. Cet objet de base de données est fermé lorsque vous fermez l’objet Recordset.

## <a name="cdaodatabaseclose"></a><a name="close"></a> CDaoDatabase :: Close

Appelez cette fonction membre pour vous déconnecter d’une base de données et fermer tous les jeux d’enregistrements, les TableDefs et les querydefs ouverts associés à la base de données.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Il est conseillé de fermer ces objets vous-même avant d’appeler cette fonction membre. La fermeture d’un `CDaoDatabase` objet le supprime de la collection de bases de données dans l' [espace de travail](../../mfc/reference/cdaoworkspace-class.md)associé. Étant donné que `Close` ne détruit pas l' `CDaoDatabase` objet, vous pouvez réutiliser l’objet en ouvrant la même base de données ou une autre base de données.

> [!CAUTION]
> Appelez la fonction membre [Update](../../mfc/reference/cdaorecordset-class.md#update) (s’il existe des modifications en attente) et la `Close` fonction membre sur tous les objets Recordset ouverts avant de fermer une base de données. Si vous quittez une fonction qui déclare [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) ou `CDaoDatabase` des objets sur la pile, la base de données est fermée, toutes les modifications non enregistrées sont perdues, toutes les transactions en attente sont annulées et toutes les modifications en attente apportées à vos données sont perdues.

> [!CAUTION]
> Si vous essayez de fermer un objet de base de données alors que des objets Recordset sont ouverts, ou si vous tentez de fermer un objet Workspace alors que des objets de base de données appartenant à cet espace de travail spécifique sont ouverts, ces objets Recordset seront fermés et toutes les mises à jour ou modifications en attente seront annulées. Si vous essayez de fermer un objet d’espace de travail alors que des objets de base de données qui lui appartiennent sont ouverts, l’opération ferme tous les objets de base de données appartenant à cet objet d’espace de travail spécifique, ce qui peut entraîner la fermeture d’objets Recordset non fermés. Si vous ne fermez pas votre objet de base de données, MFC signale un échec d’assertion dans les versions Debug.

Si l’objet de base de données est défini en dehors de la portée d’une fonction et que vous quittez la fonction sans la fermer, l’objet de base de données restera ouvert jusqu’à ce que le module dans lequel il est défini soit hors de portée.

## <a name="cdaodatabasecreate"></a><a name="create"></a> CDaoDatabase :: Create

Pour créer un nouveau Microsoft Jet (. MDB), appelez cette fonction membre après avoir construit un `CDaoDatabase` objet.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Expression de chaîne qui représente le nom du fichier de base de données que vous créez. Il peut s’agir du chemin d’accès complet et du nom de fichier, par exemple «C : \\ \MYDB. MDB». Vous devez fournir un nom. Si vous ne fournissez pas d’extension de nom de fichier,. MDB est ajouté. Si votre réseau prend en charge le format UNC (Uniform Naming Convention), vous pouvez également spécifier un chemin d’accès réseau, tel que « \\ \\ \\ \monserveur \\ \MYSHARE \\ \MYDIR \\ \MYDB ». Uniquement Microsoft Jet (. MDB) les fichiers de base de données peuvent être créés à l’aide de cette fonction membre. (Les doubles barres obliques inverses sont nécessaires dans les littéraux de chaîne, car « \\ » est le caractère d’échappement C++.)

*lpszLocale*<br/>
Expression de chaîne utilisée pour spécifier l’ordre de classement pour la création de la base de données. La valeur par défaut est `dbLangGeneral`. Les valeurs possibles sont les suivantes :

- `dbLangGeneral` Anglais, allemand, français, portugais, italien et espagnol moderne

- `dbLangArabic` Arabe

- `dbLangCyrillic` Russe

- `dbLangCzech` Tchèque

- `dbLangDutch` Néerlandais

- `dbLangGreek` Grec

- `dbLangHebrew` Hébreu

- `dbLangHungarian` Hongrois

- `dbLangIcelandic` Islandais

- `dbLangNordic` Langues nordiques (moteur de base de données Microsoft Jet version 1,0 uniquement)

- `dbLangNorwdan` Norvégien et danois

- `dbLangPolish` Polonais

- `dbLangSpanish` Espagnol traditionnel

- `dbLangSwedfin` Suédois et finnois

- `dbLangTurkish` Turc

*dwOptions*<br/>
Entier qui indique une ou plusieurs options. Les valeurs possibles sont les suivantes :

- `dbEncrypt` Créer une base de données chiffrée.

- `dbVersion10` Créer une base de données avec la version 1,0 de la base de données Microsoft Jet.

- `dbVersion11` Créer une base de données avec la version 1,1 de la base de données Microsoft Jet.

- `dbVersion20` Créer une base de données avec la version 2,0 de la base de données Microsoft Jet.

- `dbVersion30` Créer une base de données avec la version 3,0 de la base de données Microsoft Jet.

Si vous omettez la constante de chiffrement, une base de données non chiffrée est créée. Vous ne pouvez spécifier qu’une seule constante de version. Si vous omettez une constante de version, une base de données qui utilise la version 3,0 de la base de données Microsoft Jet est créée.

> [!CAUTION]
> Si une base de données n’est pas chiffrée, il est possible, même si vous implémentez la sécurité utilisateur/mot de passe, de lire directement le fichier de disque binaire qui constitue la base de données.

### <a name="remarks"></a>Notes

`Create` crée le fichier de base de données et l’objet de base de données DAO sous-jacent, puis initialise l’objet C++. L’objet est ajouté à la collection de bases de données de l’espace de travail associé. L’état de l’objet de base de données est ouvert ; n’appelez pas `Open*` after `Create` .

> [!NOTE]
> Avec `Create` , vous pouvez créer uniquement Microsoft Jet (. MDB). Vous ne pouvez pas créer de bases de données ISAM ou ODBC.

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a> CDaoDatabase :: CreateRelation

Appelez cette fonction membre pour établir une relation entre un ou plusieurs champs d’une table primaire de la base de données et un ou plusieurs champs d’une table étrangère (une autre table de la base de données).

```cpp
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom unique de l’objet relation. Le nom doit commencer par une lettre et peut contenir jusqu’à 40 caractères. Elle peut inclure des nombres et des traits de soulignement, mais ne peut pas inclure de signes de ponctuation ou d’espace.

*lpszTable*<br/>
Nom de la table primaire dans la relation. Si la table n’existe pas, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Nom de la table étrangère dans la relation. Si la table n’existe pas, MFC lève une exception de type `CDaoException` .

*lAttributes*<br/>
Valeur de type long qui contient des informations sur le type de relation. Vous pouvez utiliser cette valeur pour appliquer l’intégrité référentielle, entre autres choses. Vous pouvez utiliser l’opérateur or au niveau du bit ( **&#124;**) pour combiner les valeurs suivantes (tant que la combinaison est logique) :

- `dbRelationUnique` La relation est un-à-un.

- `dbRelationDontEnforce` La relation n’est pas appliquée (aucune intégrité référentielle).

- `dbRelationInherited` La relation existe dans une base de données non active qui contient les deux tables attachées.

- `dbRelationUpdateCascade` Les mises à jour sont en cascade (pour plus d’informations sur les cascades, consultez la section Notes).

- `dbRelationDeleteCascade` Les suppressions s’effectuent en cascade.

*lpszField*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom d’un champ dans la table primaire (nommé par *lpszTable*).

*lpszForeignField*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom d’un champ dans la table étrangère (nommé par *lpszForeignTable*).

*relinfo*<br/>
Référence à un objet [cdaorelationinfo,](../../mfc/reference/cdaorelationinfo-structure.md) qui contient des informations sur la relation que vous souhaitez créer.

### <a name="remarks"></a>Notes

La relation ne peut pas impliquer une requête ou une table attachée à partir d’une base de données externe.

Utilisez la première version de la fonction lorsque la relation implique un champ dans chacune des deux tables. Utilisez la deuxième version lorsque la relation implique plusieurs champs. Le nombre maximal de champs dans une relation est 14.

Cette action crée un objet de relation DAO sous-jacent, mais il s’agit d’un détail d’implémentation MFC puisque l’encapsulation des objets de relation de MFC est contenue dans la classe `CDaoDatabase` . MFC ne fournit pas de classe pour les relations.

Si vous définissez les attributs de l’objet relation pour activer les opérations en cascade, le moteur de base de données met à jour ou supprime automatiquement les enregistrements dans une ou plusieurs autres tables lorsque des modifications sont apportées aux tables de clés primaires associées.

Supposons, par exemple, que vous établissez une relation de suppression en cascade entre une table Customers et une table Orders. Lorsque vous supprimez des enregistrements de la table Customers, les enregistrements de la table Orders associés à ce client sont également supprimés. En outre, si vous établissez des relations de suppression en cascade entre la table Orders et d’autres tables, les enregistrements de ces tables sont automatiquement supprimés lorsque vous supprimez des enregistrements de la table Customers.

Pour obtenir des informations connexes, consultez la rubrique « CreateRelation, méthode » dans l’aide de DAO.

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a> CDaoDatabase ::D eleteQueryDef

Appelez cette fonction membre pour supprimer la querydef (requête enregistrée) spécifiée à partir de la `CDaoDatabase` collection QueryDefs de l’objet.

```cpp
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom de la requête enregistrée à supprimer.

### <a name="remarks"></a>Notes

Ensuite, cette requête n’est plus définie dans la base de données.

Pour plus d’informations sur la création d’objets QueryDef, consultez la classe [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Un objet querydef est associé à un `CDaoDatabase` objet particulier lorsque vous construisez l' `CDaoQueryDef` objet, en lui passant un pointeur vers l’objet de base de données.

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a> CDaoDatabase ::D eleteRelation

Appelez cette fonction membre pour supprimer une relation existante de la collection de relations de l’objet de base de données.

```cpp
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom de la relation à supprimer.

### <a name="remarks"></a>Notes

Par la suite, la relation n’existe plus.

Pour obtenir des informations connexes, consultez la rubrique « méthode Delete » dans l’aide de DAO.

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a> CDaoDatabase ::D eleteTableDef

Appelez cette fonction membre pour supprimer la table spécifiée et toutes ses données de la `CDaoDatabase` collection TableDefs de l’objet.

```cpp
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom de l’objet TableDef à supprimer.

### <a name="remarks"></a>Notes

Ensuite, cette table n’est plus définie dans la base de données.

> [!NOTE]
> Veillez à ne pas supprimer les tables système.

Pour plus d’informations sur la création d’objets TableDef, consultez la classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Un objet TableDef est associé à un `CDaoDatabase` objet particulier lorsque vous construisez l' `CDaoTableDef` objet, en lui transmettant un pointeur vers l’objet de base de données.

Pour obtenir des informations connexes, consultez la rubrique « méthode Delete » dans l’aide de DAO.

## <a name="cdaodatabaseexecute"></a><a name="execute"></a> CDaoDatabase :: Execute

Appelez cette fonction membre pour exécuter une requête d’action ou exécuter une instruction SQL sur la base de données.

```cpp
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Paramètres

*lpszSQL*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient une commande SQL valide à exécuter.

*nOptions*<br/>
Entier qui spécifie les options relatives à l’intégrité de la requête. Vous pouvez utiliser l’opérateur or au niveau du bit ( **&#124;**) pour combiner les constantes suivantes (à condition que la combinaison soit logique, par exemple, vous ne pouvez pas combiner `dbInconsistent` avec `dbConsistent` ) :

- `dbDenyWrite` Refuser l’autorisation d’accès en écriture à d’autres utilisateurs.

- `dbInconsistent` Valeurs Mises à jour incohérentes.

- `dbConsistent` Mises à jour cohérentes.

- `dbSQLPassThrough` SQL directe. Entraîne le passage de l’instruction SQL à une source de données ODBC pour traitement.

- `dbFailOnError` Restaure les mises à jour si une erreur se produit.

- `dbSeeChanges` Générez une erreur au moment de l’exécution si un autre utilisateur modifie les données que vous modifiez.

> [!NOTE]
> Si `dbInconsistent` et `dbConsistent` sont inclus, ou si aucun n’est inclus, le résultat est la valeur par défaut. Pour obtenir une explication de ces constantes, consultez la rubrique « méthode Execute » dans l’aide de DAO.

### <a name="remarks"></a>Notes

`Execute` fonctionne uniquement pour les requêtes d’action ou les requêtes SQL directes qui ne retournent pas de résultats. Il ne fonctionne pas pour les requêtes SELECT qui retournent des enregistrements.

Pour obtenir une définition et des informations sur les requêtes d’action, consultez les rubriques « requête d’action » et « méthode d’exécution » dans l’aide de DAO.

> [!TIP]
> Étant donné une instruction SQL correcte syntaxiquement et les autorisations appropriées, la `Execute` fonction membre n’échouera pas, même si une seule ligne ne peut pas être modifiée ou supprimée. Par conséquent, utilisez toujours l' `dbFailOnError` option lors de l’utilisation `Execute` de la fonction membre pour exécuter une requête Update ou DELETE. Cette option force MFC à lever une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md) et restaure toutes les modifications réussies si l’un des enregistrements affectés est verrouillé et ne peut pas être mis à jour ou supprimé. Notez que vous pouvez toujours appeler `GetRecordsAffected` pour voir le nombre d’enregistrements affectés.

Appelez la fonction membre [GetRecordsAffected](#getrecordsaffected) de l’objet de base de données pour déterminer le nombre d’enregistrements affectés par l’appel le plus récent `Execute` . Par exemple, `GetRecordsAffected` retourne des informations sur le nombre d’enregistrements supprimés, mis à jour ou insérés lors de l’exécution d’une requête d’action. Le nombre retourné ne reflète pas les modifications apportées aux tables associées lorsque des mises à jour ou des suppressions en cascade sont appliquées.

`Execute` ne retourne pas un Recordset. L’utilisation `Execute` de sur une requête qui sélectionne des enregistrements amène les MFC à lever une exception de type `CDaoException` . (Il n’y a aucune `ExecuteSQL` fonction membre analogue à `CDatabase::ExecuteSQL` .)

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a> CDaoDatabase :: GetConnect

Appelez cette fonction membre pour récupérer la chaîne de connexion utilisée pour connecter l' `CDaoDatabase` objet à une base de données ODBC ou ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Valeur renvoyée

La chaîne de connexion si l' [ouverture](#open) a été appelée avec succès sur une source de données ODBC ; Sinon, une chaîne vide. Pour un Microsoft Jet (. MDB), la chaîne est toujours vide, sauf si vous la définissez pour une utilisation avec l' `dbSQLPassThrough` option utilisée avec la fonction membre [Execute](#execute) ou utilisée lors de l’ouverture d’un Recordset.

### <a name="remarks"></a>Notes

La chaîne fournit des informations sur la source d’une base de données ouverte ou d’une base de données utilisée dans une requête directe. La chaîne de connexion est composée d’un spécificateur de type de base de données et de zéro, un ou plusieurs paramètres séparés par des points-virgules.

> [!NOTE]
> L’utilisation des classes DAO MFC pour se connecter à une source de données via ODBC est moins efficace que la connexion via une table attachée.

> [!NOTE]
> La chaîne de connexion est utilisée pour transmettre des informations supplémentaires à ODBC et à certains pilotes ISAM en fonction des besoins. Elle n’est pas utilisée pour. Bases de données MDB. Pour les tables de base de base de données Microsoft Jet, la chaîne de connexion est une chaîne vide (""), sauf lorsque vous l’utilisez pour une requête SQL directe, comme décrit dans valeur de retour ci-dessus.

Consultez la fonction membre [Open](#open) pour obtenir une description de la façon dont la chaîne de connexion est créée. Une fois que la chaîne de connexion a été définie dans l' `Open` appel, vous pouvez l’utiliser ultérieurement pour vérifier le paramètre afin de déterminer le type, le chemin d’accès, l’ID utilisateur, le mot de passe ou la source de données ODBC de la base de données.

## <a name="cdaodatabasegetname"></a><a name="getname"></a> CDaoDatabase :: GetName

Appelez cette fonction membre pour récupérer le nom de la base de données actuellement ouverte, qui est le nom d’un fichier de base de données existant ou le nom d’une source de données ODBC inscrite.

```
CString GetName();
```

### <a name="return-value"></a>Valeur renvoyée

Le chemin d’accès complet et le nom de fichier de la base de données en cas de réussite ; Sinon, une [CString](../../atl-mfc-shared/reference/cstringt-class.md)vide.

### <a name="remarks"></a>Notes

Si votre réseau prend en charge l’UNC (Uniform Naming Convention), vous pouvez également spécifier un chemin d’accès réseau, par exemple, « \\ \\ \\ \monserveur \\ \MYSHARE \\ \MYDIR \\ \MYDB. MDB». (Les doubles barres obliques inverses sont nécessaires dans les littéraux de chaîne, car « \\ » est le caractère d’échappement C++.)

Vous pouvez, par exemple, souhaiter afficher ce nom dans un en-tête. Si une erreur se produit pendant que le nom est récupéré, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
> Pour de meilleures performances lors de l’accès aux bases de données externes, nous vous recommandons d’attacher des tables de base de données externes à une base de données Microsoft Jet (. MDB) au lieu de se connecter directement à la source de données.

Le type de base de données est indiqué par le fichier ou le répertoire vers lequel pointe le chemin d’accès, comme suit :

|Le chemin d’accès pointe vers..|Type de base de données|
|--------------------------|-------------------|
|. Fichier MDB|Base de données Microsoft Jet (Microsoft Access)|
|Répertoire qui contient. Fichier (s) DBF|base de données dBASE|
|Répertoire qui contient. Fichier XLS|Base de données Microsoft Excel|
|Répertoire qui contient. Fichier (s) PDX|Base de données Paradox|
|Répertoire qui contient les fichiers de base de données texte mis en forme de manière appropriée|Base de données au format texte|

Pour les bases de données ODBC telles que SQL Server et Oracle, la chaîne de connexion de la base de données identifie un nom de source de données (DSN) inscrit par ODBC.

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a> CDaoDatabase :: GetQueryDefCount

Appelez cette fonction membre pour récupérer le nombre de requêtes définies dans la collection QueryDefs de la base de données.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de requêtes définies dans la base de données.

### <a name="remarks"></a>Notes

`GetQueryDefCount` est utile si vous devez exécuter en boucle tous les querydefs de la collection QueryDefs. Pour obtenir des informations sur une requête donnée dans la collection, consultez [GetQueryDefInfo](#getquerydefinfo).

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a> CDaoDatabase :: GetQueryDefInfo

Appelez cette fonction membre pour obtenir différents genres d’informations sur une requête définie dans la base de données.

```cpp
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la requête prédéfinie dans la collection QueryDefs de la base de données, pour la recherche par index.

*querydefinfo*<br/>
Référence à un objet [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations relatives au jeu d’enregistrements à récupérer. Les options disponibles sont répertoriées ici, ainsi que les raisons pour lesquelles la fonction retourne à propos du Recordset :

- Nom du AFX_DAO_PRIMARY_INFO (par défaut), tapez

- AFX_DAO_SECONDARY_INFO informations principales plus : date de création, date de la dernière mise à jour, enregistrements de retour, pouvant être mis à jour

- AFX_DAO_ALL_INFO des informations primaires et secondaires plus : SQL, Connect, ODBCTimeout

*lpszName*<br/>
Chaîne contenant le nom d’une requête définie dans la base de données, pour la recherche par nom.

### <a name="remarks"></a>Notes

Deux versions de la fonction sont fournies pour vous permettre de sélectionner une requête soit par index dans la collection QueryDefs de la base de données, soit par le nom de la requête.

Pour obtenir une description des informations retournées dans *querydefinfo*, consultez la structure [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) . Cette structure a des membres qui correspondent aux éléments d’informations énumérés ci-dessus dans la description de *dwInfoOptions*. Si vous demandez un niveau d’information, vous bénéficiez également des niveaux antérieurs d’informations.

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a> CDaoDatabase :: GetQueryTimeout

Appelez cette fonction membre pour récupérer le nombre de secondes en vigueur avant que les opérations suivantes sur la base de données connectée aient dépassé le délai d’attente.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Valeur renvoyée

Entier Short contenant la valeur du délai d’attente en secondes.

### <a name="remarks"></a>Notes

Une opération peut expirer en raison de problèmes d’accès au réseau, d’un temps de traitement de requêtes excessif, etc. Si le paramètre est activé, il affecte toutes les opérations Open, Add New, Update et Delete sur tous les jeux d’enregistrements associés à cet `CDaoDatabase` objet. Vous pouvez modifier le paramètre de délai d’attente actuel en appelant [SetQueryTimeout](#setquerytimeout). La modification de la valeur du délai d’expiration de la requête pour un jeu d’enregistrements après l’ouverture ne modifie pas la valeur de l’ensemble d’enregistrements. Par exemple, les opérations de [déplacement](../../mfc/reference/cdaorecordset-class.md#move) suivantes n’utilisent pas la nouvelle valeur. La valeur par défaut est initialement définie lorsque le moteur de base de données est initialisé.

La valeur par défaut pour les délais d’attente de requête provient du Registre Windows. S’il n’existe aucun paramètre de Registre, la valeur par défaut est de 60 secondes. Toutes les bases de données ne prennent pas en charge la possibilité de définir une valeur de délai d’attente de requête. Si vous définissez une valeur de délai d’attente de requête de 0, aucun délai d’attente n’est atteint. et la communication avec la base de données peut cesser de répondre. Ce comportement peut être utile lors du développement. Si l’appel échoue, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

Pour obtenir des informations connexes, consultez la rubrique « propriété QueryTimeout » dans l’aide de DAO.

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a> CDaoDatabase :: GetRecordsAffected

Appelez cette fonction membre pour déterminer le nombre d’enregistrements affectés par l’appel le plus récent de la fonction membre [Execute](#execute) .

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valeur renvoyée

Entier long contenant le nombre d’enregistrements affectés.

### <a name="remarks"></a>Notes

La valeur retournée comprend le nombre d’enregistrements supprimés, mis à jour ou insérés par une requête d’action exécutée avec `Execute` . Le nombre retourné ne reflète pas les modifications apportées aux tables associées lorsque des mises à jour ou des suppressions en cascade sont appliquées.

Pour obtenir des informations connexes, consultez la rubrique « propriété RecordsAffected » dans l’aide de DAO.

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a> CDaoDatabase :: GetRelationCount

Appelez cette fonction membre pour obtenir le nombre de relations définies entre les tables de la base de données.

```
short GetRelationCount();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de relations définies entre les tables de la base de données.

### <a name="remarks"></a>Notes

`GetRelationCount` est utile si vous devez exécuter en boucle toutes les relations définies dans la collection de relations de la base de données. Pour obtenir des informations sur une relation donnée dans la collection, consultez [GetRelationInfo](#getrelationinfo).

Pour illustrer le concept de relation, considérez une table Suppliers et une table Products, qui peuvent avoir une relation un-à-plusieurs. Dans cette relation, un fournisseur peut fournir plusieurs produits. Les autres relations sont un-à-un et plusieurs-à-plusieurs.

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a> CDaoDatabase :: GetRelationInfo

Appelez cette fonction membre pour obtenir des informations sur une relation spécifiée dans la collection de relations de la base de données.

```cpp
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’objet relation dans la collection de relations de la base de données, pour la recherche par index.

*relinfo*<br/>
Référence à un objet [cdaorelationinfo,](../../mfc/reference/cdaorelationinfo-structure.md) qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations relatives à la relation à récupérer. Les options disponibles sont répertoriées ici, ainsi que les raisons pour lesquelles la fonction retourne à propos de la relation :

- Nom du AFX_DAO_PRIMARY_INFO (par défaut), table, table étrangère

- Attributs de AFX_DAO_SECONDARY_INFO, informations sur les champs

Les informations de champ sont un objet [cdaorelationfieldinfo,](../../mfc/reference/cdaorelationfieldinfo-structure.md) qui contient les champs de la table primaire impliquée dans la relation.

*lpszName*<br/>
Chaîne contenant le nom de l’objet relation, pour la recherche par nom.

### <a name="remarks"></a>Notes

Deux versions de cette fonction fournissent l’accès par index ou par nom. Pour obtenir une description des informations retournées dans *relinfo*, consultez la structure [cdaorelationinfo,](../../mfc/reference/cdaorelationinfo-structure.md) . Cette structure a des membres qui correspondent aux éléments d’informations énumérés ci-dessus dans la description de *dwInfoOptions*. Si vous demandez des informations à un niveau, vous pouvez également obtenir des informations à tous les niveaux antérieurs.

> [!NOTE]
> Si vous définissez les attributs de l’objet relation pour activer les opérations en cascade ( `dbRelationUpdateCascades` ou `dbRelationDeleteCascades` ), le moteur de base de données Microsoft Jet met à jour ou supprime automatiquement les enregistrements dans une ou plusieurs autres tables lorsque des modifications sont apportées aux tables de clés primaires associées. Supposons, par exemple, que vous établissez une relation de suppression en cascade entre une table Customers et une table Orders. Lorsque vous supprimez des enregistrements de la table Customers, les enregistrements de la table Orders associés à ce client sont également supprimés. En outre, si vous établissez des relations de suppression en cascade entre la table Orders et d’autres tables, les enregistrements de ces tables sont automatiquement supprimés lorsque vous supprimez des enregistrements de la table Customers.

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a> CDaoDatabase :: GetTableDefCount

Appelez cette fonction membre pour récupérer le nombre de tables définies dans la base de données.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’objets TableDefs définis dans la base de données.

### <a name="remarks"></a>Notes

`GetTableDefCount` est utile si vous devez effectuer une boucle sur tous les TableDefs de la collection TableDefs de la base de données. Pour obtenir des informations sur une table donnée dans la collection, consultez [GetTableDefInfo](#gettabledefinfo).

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a> CDaoDatabase :: GetTableDefInfo

Appelez cette fonction membre pour obtenir différents genres d’informations sur une table définie dans la base de données.

```cpp
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’objet TableDef dans la collection TableDefs de la base de données, pour la recherche par index.

*tabledefinfo*<br/>
Référence à un objet [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations relatives à la table à récupérer. Les options disponibles sont répertoriées ici, ainsi que les raisons pour lesquelles la fonction retourne à propos de la relation :

- Nom de AFX_DAO_PRIMARY_INFO (par défaut), pouvant être mis à jour, attributs

- AFX_DAO_SECONDARY_INFO informations principales plus : date de création, date de dernière mise à jour, nom de la table source, se connecter

- AFX_DAO_ALL_INFO les informations principales et secondaires plus : règle de validation, texte de validation, nombre d’enregistrements

*lpszName*<br/>
Nom de l’objet TableDef, pour la recherche par nom.

### <a name="remarks"></a>Notes

Deux versions de la fonction sont fournies pour vous permettre de sélectionner une table soit par index dans la collection TableDefs de la base de données, soit par le nom de la table.

Pour obtenir une description des informations retournées dans *tabledefinfo*, consultez la structure [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) . Cette structure a des membres qui correspondent aux éléments d’informations énumérés ci-dessus dans la description de *dwInfoOptions*. Si vous demandez des informations à un niveau, vous recevez également des informations sur les niveaux précédents.

> [!NOTE]
> L’option AFX_DAO_ALL_INFO fournit des informations qui peuvent être lentes à obtenir. Dans ce cas, le fait de compter les enregistrements dans la table peut prendre beaucoup de temps s’il y a de nombreux enregistrements.

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a> CDaoDatabase :: GetVersion

Appelez cette fonction membre pour déterminer la version du fichier de base de données Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Valeur renvoyée

[CString](../../atl-mfc-shared/reference/cstringt-class.md) qui indique la version du fichier de base de données associé à l’objet.

### <a name="remarks"></a>Notes

La valeur retournée représente le numéro de version sous la forme « major. minor »; par exemple, « 3,0 ». Le numéro de version du produit (par exemple, 3,0) se compose du numéro de version (3), d’un point et du numéro de version (0). Les versions à ce jour sont 1,0, 1,1, 2,0 et 3,0.

Pour obtenir des informations connexes, consultez la rubrique « Version Property » dans l’aide de DAO.

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a> CDaoDatabase :: IsOpen

Appelez cette fonction membre pour déterminer si l' `CDaoDatabase` objet est actuellement ouvert dans une base de données.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l' `CDaoDatabase` objet est actuellement ouvert ; sinon, 0.

### <a name="remarks"></a>Notes

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a> CDaoDatabase :: m_pDAODatabase

Contient un pointeur vers l’interface OLE pour l’objet de base de données DAO sous-jacent à l' `CDaoDatabase` objet.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous devez accéder directement à l’interface DAO.

Pour plus d’informations sur l’appel direct de DAO, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a> CDaoDatabase :: m_pWorkspace

Contient un pointeur vers l’objet [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) qui contient l’objet de base de données.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous devez accéder directement à l’espace de travail (par exemple, pour obtenir des pointeurs vers d’autres objets de base de données dans la collection de bases de données de l’espace de travail).

## <a name="cdaodatabaseopen"></a><a name="open"></a> CDaoDatabase :: Open

Vous devez appeler cette fonction membre pour initialiser un objet nouvellement construit `CDaoDatabase` qui représente une base de données existante.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Expression de chaîne qui est le nom d’un Microsoft Jet existant (. MDB). Si le nom de fichier a une extension, il est requis. Si votre réseau prend en charge le format UNC (Uniform Naming Convention), vous pouvez également spécifier un chemin d’accès réseau, tel que « \\ \\ \\ \monserveur \\ \MYSHARE \\ \MYDIR \\ \MYDB. MDB». (Les doubles barres obliques inverses sont nécessaires dans les littéraux de chaîne, car « \\ » est le caractère d’échappement C++.)

Certaines considérations s’appliquent lors de l’utilisation de *lpszName*. Si :

- Fait référence à une base de données déjà ouverte pour un accès exclusif par un autre utilisateur, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md). Interceptez cette exception pour signaler à votre utilisateur que la base de données n’est pas disponible.

- Est une chaîne vide ("") et *lpszConnect* est "ODBC ;", une boîte de dialogue qui répertorie tous les noms de sources de données ODBC inscrits s’affiche pour permettre à l’utilisateur de sélectionner une base de données. Vous devez éviter les connexions directes à des sources de données ODBC. Utilisez plutôt une table attachée.

- Sinon, ne fait pas référence à une base de données existante ou à un nom de source de données ODBC valide, MFC lève une exception de type `CDaoException` .

> [!NOTE]
> Pour plus d’informations sur les codes d’erreur DAO, consultez DAOERR. Fichier H. Pour obtenir des informations connexes, consultez la rubrique « Erreurs d’accès aux données récupérables » dans l’aide de DAO.

*bExclusive*<br/>
Valeur booléenne qui est TRUE si la base de données doit être ouverte pour un accès exclusif (non partagé) et FALSe si la base de données doit être ouverte pour un accès partagé. Si vous omettez cet argument, la base de données est ouverte pour un accès partagé.

*bReadOnly*<br/>
Valeur booléenne qui est TRUE si la base de données doit être ouverte pour un accès en lecture seule et FALSe si la base de données doit être ouverte pour un accès en lecture/écriture. Si vous omettez cet argument, la base de données est ouverte pour un accès en lecture/écriture. Tous les jeux d’enregistrements dépendants héritent de cet attribut.

*lpszConnect*<br/>
Expression de chaîne utilisée pour ouvrir la base de données. Cette chaîne constitue les arguments ODBC Connect. Vous devez fournir les arguments exclusifs et en lecture seule pour fournir une chaîne source. Si la base de données est une base de données Microsoft Jet (. MDB), cette chaîne est vide (""). La syntaxe de la valeur par défaut, **_T**(«»), assure la portabilité pour Unicode ainsi que les versions ANSI de votre application.

### <a name="remarks"></a>Notes

`Open` associe la base de données à l’objet DAO sous-jacent. Vous ne pouvez pas utiliser l’objet de base de données pour construire des objets Recordset, TableDef ou querydef tant qu’il n’a pas été initialisé. `Open` Ajoute l’objet de base de données à la collection de bases de données de l’espace de travail associé.

Utilisez les paramètres comme suit :

- Si vous ouvrez un Microsoft Jet (. MDB), utilisez le paramètre *lpszName* et transmettez une chaîne vide pour le paramètre *lpszConnect* ou transmettez une chaîne de mot de passe sous la forme "; PWD = Password» si la base de données est protégée par mot de passe (. Bases de données MDB uniquement).

- Si vous ouvrez une source de données ODBC, transmettez une chaîne de connexion ODBC valide dans *lpszConnect* et une chaîne vide dans *lpszName*.

Pour obtenir des informations connexes, consultez la rubrique « méthode OpenDatabase » dans l’aide de DAO.

> [!NOTE]
> Pour obtenir de meilleures performances lors de l’accès à des bases de données externes, notamment des bases de données ISAM et des sources de données ODBC, il est recommandé de joindre des tables de base de données externes à une base de données du moteur Microsoft Jet (. MDB) au lieu de se connecter directement à la source de données.

Une tentative de connexion peut expirer si, par exemple, l’hôte SGBD n’est pas disponible. Si la tentative de connexion échoue, `Open` lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

Les notes restantes s’appliquent uniquement aux bases de données ODBC :

Si la base de données est une base de données ODBC et que les paramètres de votre `Open` appel ne contiennent pas suffisamment d’informations pour établir la connexion, le pilote ODBC ouvre une boîte de dialogue qui vous permet d’obtenir les informations nécessaires auprès de l’utilisateur. Lorsque vous appelez `Open` , votre chaîne de connexion, *lpszConnect*, est stockée en privé et est disponible en appelant la fonction membre [GetConnect](#getconnect) .

Si vous le souhaitez, vous pouvez ouvrir votre propre boîte de dialogue avant `Open` d’appeler pour obtenir des informations de l’utilisateur, par exemple un mot de passe, puis ajouter ces informations à la chaîne de connexion que vous transmettez à `Open` . Vous pouvez également enregistrer la chaîne de connexion que vous transmettez (peut-être dans le Registre Windows) afin de pouvoir la réutiliser la prochaine fois que votre application appelle `Open` sur un `CDaoDatabase` objet.

Vous pouvez également utiliser la chaîne de connexion pour plusieurs niveaux d’autorisation de connexion (chacun pour un `CDaoDatabase` objet différent) ou pour transmettre d’autres informations spécifiques à la base de données.

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a> CDaoDatabase :: SetQueryTimeout

Appelez cette fonction membre pour remplacer le nombre de secondes par défaut à autoriser avant les opérations suivantes sur le délai d’expiration de la base de données connectée.

```cpp
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Paramètres

*nSeconds*<br/>
Nombre de secondes à autoriser avant l’expiration d’une tentative de requête.

### <a name="remarks"></a>Notes

Une opération peut expirer en raison de problèmes d’accès au réseau, d’un temps de traitement de requêtes excessif, etc. Appelez `SetQueryTimeout` avant d’ouvrir le jeu d’enregistrements ou avant d’appeler les fonctions membres [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)ou [Delete](../../mfc/reference/cdaorecordset-class.md#delete) du Recordset si vous souhaitez modifier la valeur du délai d’expiration de la requête. Le paramètre affecte tous les appels,, et [ouverts](../../mfc/reference/cdaorecordset-class.md#open)suivants `AddNew` `Update` `Delete` à tous les jeux d’enregistrements associés à cet `CDaoDatabase` objet. La modification de la valeur du délai d’expiration de la requête pour un jeu d’enregistrements après l’ouverture ne modifie pas la valeur de l’ensemble d’enregistrements. Par exemple, les opérations de [déplacement](../../mfc/reference/cdaorecordset-class.md#move) suivantes n’utilisent pas la nouvelle valeur.

La valeur par défaut du délai d’expiration de la requête est de 60 secondes. Toutes les bases de données ne prennent pas en charge la possibilité de définir une valeur de délai d’attente de requête. Si vous définissez une valeur de délai d’attente de requête de 0, aucun délai d’attente n’est atteint. la communication avec la base de données peut cesser de répondre. Ce comportement peut être utile lors du développement.

Pour obtenir des informations connexes, consultez la rubrique « propriété QueryTimeout » dans l’aide de DAO.

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace (classe)](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset (classe)](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef (classe)](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException (classe)](../../mfc/reference/cdaoexception-class.md)
