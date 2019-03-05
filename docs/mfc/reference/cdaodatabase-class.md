---
title: CDaoDatabase, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: d1e9db1ddebe05d42cbb8c4ba242938d6d86cc81
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272895"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase, classe

Représente une connexion à une base de données, par l'intermédiaire de laquelle vous pouvez utiliser les données.

## <a name="syntax"></a>Syntaxe

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Construit un objet `CDaoDatabase`. Appelez `Open` pour connecter l’objet à une base de données.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Retourne une valeur différente de zéro si la base de données prend en charge les transactions.|
|[CDaoDatabase::CanUpdate](#canupdate)|Retourne la valeur différente de zéro si le `CDaoDatabase` objet est modifiable (pas en lecture seule).|
|[CDaoDatabase::Close](#close)|Ferme la connexion de base de données.|
|[CDaoDatabase::Create](#create)|Crée l’objet de base de données DAO sous-jacent et initialise le `CDaoDatabase` objet.|
|[CDaoDatabase::CreateRelation](#createrelation)|Définit une relation entre les tables dans la base de données.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Supprime un objet querydef enregistré dans la collection QueryDefs de la base de données.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Supprime une relation existante entre les tables dans la base de données.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Supprime la définition d’une table dans la base de données. Cette opération supprime la table réelle et toutes ses données.|
|[CDaoDatabase::Execute](#execute)|Exécute une requête d’action. Appel `Execute` pour une requête qui retourne des résultats lève une exception.|
|[CDaoDatabase::GetConnect](#getconnect)|Retourne la chaîne de connexion permet de connecter le `CDaoDatabase` objet à une base de données. Utilisé pour ODBC.|
|[CDaoDatabase::GetName](#getname)|Retourne le nom de la base de données actuellement en cours d’utilisation.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Retourne le nombre de requêtes définies pour la base de données.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Retourne des informations sur une requête spécifiée définie dans la base de données.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Retourne le nombre de secondes après la base de données des opérations de requête va expirer. Affecte toutes les ouvrir, ajouter un nouveau, mettre à jour et modifier les opérations et autres opérations sur les sources de données ODBC (uniquement) telles que `Execute` appels.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Retourne le nombre d’enregistrements affecté par la dernière mise à jour, modifier ou ajouter une opération ou par un appel à `Execute`.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Retourne le nombre de relations définies entre les tables dans la base de données.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Retourne des informations sur une relation spécifiée définie entre des tables dans la base de données.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Retourne le nombre de tables définies dans la base de données.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Retourne des informations sur une table spécifiée dans la base de données.|
|[CDaoDatabase::GetVersion](#getversion)|Retourne la version du moteur de base de données associé à la base de données.|
|[CDaoDatabase::IsOpen](#isopen)|Retourne la valeur différente de zéro si le `CDaoDatabase` objet est actuellement connecté à une base de données.|
|[CDaoDatabase::Open](#open)|Établit une connexion à une base de données.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Définit le nombre de secondes après la base de données des opérations (sur les sources de données ODBC uniquement) de requête va expirer. Affecte toutes les ouvre, ajouter un nouveau, mettre à jour et les opérations de suppression.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Pointeur vers l’objet de base de données DAO sous-jacent.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Un pointeur vers le [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objet qui contient la base de données et définit son espace de transaction.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les formats de base de données pris en charge, consultez le [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) fonction membre. Vous pouvez avoir une ou plusieurs `CDaoDatabase` objets actifs à la fois dans un « espace de travail donné, « représenté par un [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objet. L’espace de travail gère une collection d’objets de base de données ouverte, appelée la collection de bases de données.

> [!NOTE]
>  Les classes de base de données DAO de MFC sont distinctes des classes de base de données MFC basées sur ODBC. Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Classe `CDaoDatabase` fournit une interface similaire à celle de la classe ODBC [CDatabase](../../mfc/reference/cdatabase-class.md). La principale différence est que `CDatabase` accède au SGBD via la connectivité ODBC (Open Database) et un pilote ODBC pour ce système SGBD. `CDaoDatabase` accède aux données via un objet DAO (Data Access) basé sur le moteur de base de données Microsoft Jet. En général, les classes MFC basées sur DAO sont plus efficaces que les classes MFC basées sur ODBC ; les classes DAO peuvent accéder aux données, y compris via des pilotes ODBC, via leur propre moteur de base de données. Les classes DAO prennent également en charge les opérations de langage de définition de données (DDL), telles que l’ajout de tables via les classes, sans devoir appeler DAO directement.

## <a name="usage"></a>Utilisation

Vous pouvez créer des objets de base de données implicitement, lorsque vous créez des objets de jeu d’enregistrements. Mais vous pouvez également créer explicitement les objets de base de données. Pour utiliser la base de données existante explicitement `CDaoDatabase`, effectuez une des opérations suivantes :

- Construire un `CDaoDatabase` objet, en passant un pointeur vers une ouverture [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objet.

- Ou que vous construisez un `CDaoDatabase` objet sans spécifier l’espace de travail (MFC crée un objet de l’espace de travail temporaire).

Pour créer un nouveau Microsoft Jet (. Base de données MDB), construire un `CDaoDatabase` objet et appelez sa [créer](#create) fonction membre. Faire *pas* appeler `Open` après `Create`.

Pour ouvrir une base de données existante, vous devez construire un `CDaoDatabase` objet et appelez sa [ouvrir](#open) fonction membre.

Une de ces techniques ajoute l’objet de base de données DAO à la collection de bases de données de l’espace de travail et ouvre une connexion aux données. Lorsque vous construisez puis [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), ou [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) passer des objets pour l’exploitation de la base de données connectée, les constructeurs pour ces objets un pointeur vers votre `CDaoDatabase` objet. Lorsque vous avez terminé à l’aide de la connexion, appelez le [fermer](#close) membre de fonction et de détruire le `CDaoDatabase` objet. `Close` ferme les jeux d’enregistrements que vous n’avez pas fermé précédemment.

## <a name="transactions"></a>Transactions

Traitement des transactions de base de données est fourni au niveau de l’espace de travail, consultez le [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans), et [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) fonctions membres de classe `CDaoWorkspace` .

## <a name="odbc-connections"></a>Connexions ODBC

La méthode recommandée pour travailler avec des sources de données ODBC consiste à joindre des tables externes à un Microsoft Jet (. Base de données MDB).

## <a name="collections"></a>Collections

Chaque base de données gère ses propres collections de tabledef, querydef, jeu d’enregistrements et les objets de relation. Classe `CDaoDatabase` fournit les fonctions membres permettant de manipuler ces objets.

> [!NOTE]
>  Les objets sont stockés dans DAO, pas dans l’objet de base de données MFC. MFC fournit des classes pour objets tabledef, querydef et jeu d’enregistrements, mais pas pour les objets de relation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao.h

##  <a name="cantransact"></a>  CDaoDatabase::CanTransact

Appelez cette fonction membre pour déterminer si la base de données autorise les transactions.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la base de données prend en charge les transactions ; sinon 0.

### <a name="remarks"></a>Notes

Les transactions sont gérées dans l’espace de travail de la base de données.

##  <a name="canupdate"></a>  CDaoDatabase::CanUpdate

Appelez cette fonction membre pour déterminer si le `CDaoDatabase` objet permet des mises à jour.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le `CDaoDatabase` objet permet des mises à jour ; sinon, 0, qui indique soit que vous avez passé TRUE *bReadOnly* lorsque vous avez ouvert le `CDaoDatabase` objet ou que la base de données est en lecture seule. Consultez le [Open](#open) fonction membre.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les mises à jour de la base de données, consultez la rubrique « Propriété actualisable » dans l’aide de DAO.

##  <a name="cdaodatabase"></a>  CDaoDatabase::CDaoDatabase

Construit un objet `CDaoDatabase`.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Paramètres

*pWorkspace*<br/>
Un pointeur vers le `CDaoWorkspace` objet qui contient le nouvel objet de base de données. Si vous acceptez la valeur NULL comme valeur par défaut, le constructeur crée une table temporaire `CDaoWorkspace` objet qui utilise l’espace de travail DAO par défaut. Vous pouvez obtenir un pointeur vers l’objet de l’espace de travail via le [m_pWorkspace](#m_pworkspace) membre de données.

### <a name="remarks"></a>Notes

Après la construction de l’objet, si vous créez un nouveau Microsoft Jet (. MDB) de base de données, appelez l’objet [créer](#create) fonction membre. Si vous êtes, au lieu de cela, l’ouverture d’une base de données existante, appeler l’objet [Open](#open) fonction membre.

Lorsque vous avez terminé avec l’objet, vous devez appeler sa [fermer](#close) membre de fonction, puis détruisez le `CDaoDatabase` objet.

Il peut s’avérer pratique pour incorporer le `CDaoDatabase` objet dans votre classe de document.

> [!NOTE]
>  Un `CDaoDatabase` objet est également créé implicitement si vous ouvrez un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet sans en passant un pointeur vers un existant `CDaoDatabase` objet. Cet objet de base de données est fermé lorsque vous fermez l’objet recordset.

##  <a name="close"></a>  CDaoDatabase::Close

Appelez cette fonction membre pour vous déconnecter à partir d’une base de données et fermez tous les recordsets ouverts, tabledefs et querydefs associés à la base de données.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Il est conseillé de fermer ces objets vous-même avant d’appeler cette fonction membre. Fermeture d’un `CDaoDatabase` objet supprime de la collection de bases de données dans le texte associé [espace de travail](../../mfc/reference/cdaoworkspace-class.md). Étant donné que `Close` ne détruit pas les `CDaoDatabase` de l’objet, vous pouvez réutiliser l’objet en ouvrant la même base de données ou une autre base de données.

> [!CAUTION]
>  Appelez le [mise à jour](../../mfc/reference/cdaorecordset-class.md#update) fonction membre (absence de modifications en attente) et le `Close` fonction membre sur tous les objets de jeu d’enregistrements ouverts avant de fermer une base de données. Si vous quittez une fonction qui déclare [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) ou `CDaoDatabase` objets sur la pile, la base de données est fermée, les modifications non enregistrées sont perdues, toutes les transactions en attente sont annulées, et toutes les modifications en attente à vos données sont perdues.

> [!CAUTION]
>  Si vous essayez de fermer un objet de base de données des objets recordset sont ouverts, ou si vous tentez de fermer un objet de l’espace de travail des objets de base de données appartenant à cet espace de travail spécifique sont ouverts, ces objets de jeu d’enregistrements va être fermées et que les mises à jour en attente ou les modifications seront restaurée. Si vous essayez de fermer un objet de l’espace de travail des objets de base de données appartenant à ce dernier sont ouverts, l’opération ferme tous les objets de base de données appartenant à cet objet d’espace de travail spécifique, ce qui peut aboutir dans les objets de jeu d’enregistrements non fermés en cours de fermeture. Si vous ne fermez pas votre objet de base de données, MFC signale un échec d’assertion dans les versions debug.

Si l’objet de base de données est défini en dehors de l’étendue d’une fonction, et que vous quittez la fonction sans le fermer, l’objet de base de données reste ouverte jusqu'à ce qu’explicitement fermée ou le module dans lequel elle est définie est hors de portée.

##  <a name="create"></a>  CDaoDatabase::Create

Pour créer un nouveau Microsoft Jet (. MDB) de base de données, appelez cette fonction membre après avoir construit un `CDaoDatabase` objet.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Une expression de chaîne qui est le nom du fichier de base de données que vous créez. Il peut être le chemin d’accès complet et le nom de fichier, tel que « C:\\\MYDB. MDB ». Vous devez fournir un nom. Si vous ne fournissez pas une extension de nom de fichier. MDB est ajouté. Si votre réseau prend en charge la convention d’affectation de noms uniforme (UNC), vous pouvez également spécifier un chemin d’accès réseau, tels que «\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB ». Uniquement Microsoft Jet (. Fichiers de base de données MDB) peuvent être créés à l’aide de cette fonction membre. (Barres obliques inverses doubles sont requis dans les littéraux de chaîne, car «\\» est le caractère d’échappement de C++.)

*lpszLocale*<br/>
Une expression de chaîne utilisée pour spécifier l’ordre de classement pour la création de la base de données. La valeur par défaut est `dbLangGeneral`. Les valeurs possibles sont :

- `dbLangGeneral` Anglais, allemand, Français, portugais, italien et modernes espagnol

- `dbLangArabic` Arabe

- `dbLangCyrillic` Russe

- `dbLangCzech` Tchèque

- `dbLangDutch` Néerlandais

- `dbLangGreek` Grec

- `dbLangHebrew` Hébreu

- `dbLangHungarian` Hongrois

- `dbLangIcelandic` Islandais

- `dbLangNordic` Langues nordiques (moteur Microsoft Jet database version 1.0 uniquement)

- `dbLangNorwdan` Norvégien et danois

- `dbLangPolish` Polonais

- `dbLangSpanish` Espagnol traditionnel

- `dbLangSwedfin` Suédois et finnois

- `dbLangTurkish` Turc

*dwOptions*<br/>
Entier qui indique une ou plusieurs options. Les valeurs possibles sont :

- `dbEncrypt` Créer une base de données chiffrée.

- `dbVersion10` Créer une base de données avec la version de base de données Microsoft Jet 1.0.

- `dbVersion11` Créer une base de données avec la version de base de données Microsoft Jet 1.1.

- `dbVersion20` Créer une base de données avec la version de base de données Microsoft Jet 2.0.

- `dbVersion30` Créer une base de données avec la version de base de données Microsoft Jet 3.0.

Si vous omettez la constante de chiffrement, une base de données non chiffré est créé. Vous pouvez spécifier qu’une seule constante de version. Si vous l’omettez, une base de données qui utilise la version de base de données Microsoft Jet 3.0 est créé.

> [!CAUTION]
>  Si une base de données n’est pas chiffré, il est possible, même si vous implémentez la sécurité d’utilisateur/mot de passe, pour lire directement le fichier binaire sur disque qui constitue la base de données.

### <a name="remarks"></a>Notes

`Create` crée le fichier de base de données et de l’objet de base de données DAO sous-jacent et initialise l’objet C++. L’objet est ajouté à la collection de bases de données de l’espace de travail associé. L’objet de base de données est dans un état ouvert ; n’appelez pas `Open*` après `Create`.

> [!NOTE]
>  Avec `Create`, vous pouvez créer uniquement Microsoft Jet (. Bases de données MDB). Impossible de créer les bases de données ISAM ou bases de données ODBC.

##  <a name="createrelation"></a>  CDaoDatabase::CreateRelation

Appelez cette fonction membre pour établir une relation entre un ou plusieurs champs dans une table dans la base de données primaire et un ou plusieurs champs dans une table externe (une autre table dans la base de données).

```
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
Le nom unique de l’objet relation. Le nom doit commencer par une lettre et peut contenir un maximum de 40 caractères. Il peut inclure des nombres et caractères de trait de soulignement mais ne peut pas inclure de signes de ponctuation ou d’espaces.

*lpszTable*<br/>
Le nom de la table primaire dans la relation. Si la table n’existe pas, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Le nom de la table étrangère dans la relation. Si la table n’existe pas, MFC lève une exception de type `CDaoException`.

*lAttributes*<br/>
Valeur longue qui contient des informations sur le type de relation. Vous pouvez utiliser cette valeur pour appliquer l’intégrité référentielle, entre autres choses. Vous pouvez utiliser l’opérateur OR au niveau du bit ( **&#124;**) pour combiner les valeurs suivantes (à condition que la combinaison sens) :

- `dbRelationUnique` Relation est-à-un.

- `dbRelationDontEnforce` Relation n’est pas (aucune intégrité référentielle).

- `dbRelationInherited` Relation existe dans une base de données non courante qui contient les deux tables jointes.

- `dbRelationUpdateCascade` Mises à jour en cascade (pour plus d’informations sur les cascades, consultez la section Notes).

- `dbRelationDeleteCascade` Suppressions sont mises en cascade.

*lpszField*<br/>
Un pointeur vers une chaîne se terminant par null qui contient le nom d’un champ dans la table primaire (nommé par *lpszTable*).

*lpszForeignField*<br/>
Un pointeur vers une chaîne se terminant par null qui contient le nom d’un champ dans la table étrangère (nommé par *lpszForeignTable*).

*relinfo*<br/>
Une référence à un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objet qui contient des informations sur la relation que vous souhaitez créer.

### <a name="remarks"></a>Notes

La relation ne peut pas impliquer une requête ou une table jointe à partir d’une base de données externe.

Utilisez la première version de la fonction lorsque la relation implique un champ dans chacune des deux tables. Utilisez la deuxième version lors de la relation implique plusieurs champs. Le nombre maximal de champs dans une relation est 14.

Cette action crée un objet de relation DAO sous-jacent, mais c’est un détail d’implémentation MFC dans la mesure où l’encapsulation de MFC objets relation est contenue dans la classe `CDaoDatabase`. MFC ne fournit pas une classe de relations.

Si vous définissez la relation des attributs de l’objet pour activer les opérations en cascade, le moteur de base de données met à jour automatiquement ou supprime des enregistrements dans une ou plusieurs tables lorsque des modifications sont apportées aux tables connexes de clé primaires.

Par exemple, supposons que vous établissez une relation de suppression en cascade entre une table Customers et une table de commandes. Lorsque vous supprimez des enregistrements à partir de la table Customers, enregistrements dans la table de commandes associées à ce client sont également supprimés. En outre, si vous établissez des relations de suppression en cascade entre la table Orders et d’autres tables, les enregistrements à partir de ces tables sont automatiquement supprimés lorsque vous supprimez des enregistrements à partir de la table Customers.

Pour plus d’informations, consultez la rubrique « Méthode CreateRelation » dans l’aide de DAO.

##  <a name="deletequerydef"></a>  CDaoDatabase::DeleteQueryDef

Appelez cette fonction membre pour supprimer l’objet querydef spécifié, la requête enregistrée, à partir de la `CDaoDatabase` QueryDefs (collection) de l’objet.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Le nom de la requête enregistrée à supprimer.

### <a name="remarks"></a>Notes

Par la suite, cette requête n’est plus définie dans la base de données.

Pour plus d’informations sur la création d’objets querydef, consultez la classe [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Un objet querydef est associé à un particulier `CDaoDatabase` de l’objet lorsque vous construisez le `CDaoQueryDef` objet, en passant un pointeur vers l’objet de base de données.

##  <a name="deleterelation"></a>  CDaoDatabase::DeleteRelation

Appelez cette fonction membre pour supprimer une relation existante à partir de la collection de Relations de l’objet de base de données.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Le nom de la relation à supprimer.

### <a name="remarks"></a>Notes

Par la suite, la relation n’est plus existe.

Pour plus d’informations, consultez la rubrique « Supprimer la méthode » dans l’aide de DAO.

##  <a name="deletetabledef"></a>  CDaoDatabase::DeleteTableDef

Appelez cette fonction membre pour supprimer la table spécifiée et toutes ses données à partir de la `CDaoDatabase` TableDefs (collection) de l’objet.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Le nom de l’objet à supprimer.

### <a name="remarks"></a>Notes

Par la suite, cette table n’est plus définie dans la base de données.

> [!NOTE]
>  Être très attention à ne pas supprimer les tables système.

Pour plus d’informations sur la création d’objets tabledef, consultez la classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Un objet tabledef est associé à un particulier `CDaoDatabase` de l’objet lorsque vous construisez le `CDaoTableDef` objet, en passant un pointeur vers l’objet de base de données.

Pour plus d’informations, consultez la rubrique « Supprimer la méthode » dans l’aide de DAO.

##  <a name="execute"></a>  CDaoDatabase::Execute

Appelez cette fonction membre pour exécuter une requête d’action ou d’exécuter une instruction SQL sur la base de données.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Paramètres

*lpszSQL*<br/>
Pointeur vers une chaîne se terminant par null qui contient une commande SQL valide à exécuter.

*nOptions*<br/>
Entier qui spécifie les options relatives à l’intégrité de la requête. Vous pouvez utiliser l’opérateur OR au niveau du bit ( **&#124;**) pour combiner une des constantes suivantes (fournie par la combinaison de sens, par exemple, vous ne combinez pas `dbInconsistent` avec `dbConsistent`) :

- `dbDenyWrite` Refuser l’autorisation d’écriture à d’autres utilisateurs.

- `dbInconsistent` (Valeur par défaut) Mises à jour incohérentes.

- `dbConsistent` Mises à jour cohérentes.

- `dbSQLPassThrough` Directe SQL. Provoque l’instruction SQL à passer à une source de données ODBC pour traitement.

- `dbFailOnError` Annuler les mises à jour si une erreur se produit.

- `dbSeeChanges` Générer une erreur d’exécution si un autre utilisateur modifie les données que vous modifiez.

> [!NOTE]
>  Si les deux `dbInconsistent` et `dbConsistent` sont inclus ou si aucun n’est inclus, le résultat est la valeur par défaut. Pour obtenir une explication de ces constantes, consultez la rubrique « Méthode Execute » dans l’aide de DAO.

### <a name="remarks"></a>Notes

`Execute` fonctionne uniquement pour les requêtes d’action ou des requêtes SQL directes qui ne retournent pas de résultats. Il ne fonctionne pas pour les requêtes select qui retournent des enregistrements.

Pour une définition et les informations sur les requêtes d’action, consultez les rubriques « Requête Action » et « Exécuter la méthode » dans l’aide de DAO.

> [!TIP]
>  Étant donné une instruction SQL syntaxiquement correcte et les autorisations appropriées, le `Execute` fonction membre n’échouera pas même si ce n’est pas une ligne unique peut être modifiée ou supprimée. Par conséquent, utilisez toujours le `dbFailOnError` option lorsque vous utilisez le `Execute` fonction membre pour exécuter une mise à jour ou supprimer des requêtes. Cette option provoque MFC lever une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md) et restaure toutes les modifications réussites si les enregistrements affectés sont verrouillés et ne peut pas être mis à jour ou supprimés. Notez que vous pouvez toujours appeler `GetRecordsAffected` pour voir combien d’enregistrements ont été affectés.

Appelez le [GetRecordsAffected](#getrecordsaffected) fonction membre de l’objet de base de données pour déterminer le nombre d’enregistrements affectés par la plus récente `Execute` appeler. Par exemple, `GetRecordsAffected` renvoie des informations sur le nombre d’enregistrements supprimés, mis à jour ou inséré lors de l’exécution d’une requête d’action. Le nombre retourné ne reflète pas les modifications dans les tables associées lorsque cascade met à jour ou supprime prennent effet.

`Execute` ne retourne pas d’un jeu d’enregistrements. À l’aide de `Execute` sur une requête qui sélectionne des enregistrements provoque MFC lever une exception de type `CDaoException`. (Il existe aucune `ExecuteSQL` fonction membre analogue à `CDatabase::ExecuteSQL`.)

##  <a name="getconnect"></a>  CDaoDatabase::GetConnect

Appelez cette fonction membre pour récupérer la chaîne de connexion permet de connecter le `CDaoDatabase` objet à une base de données ODBC ou ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Valeur de retour

La chaîne de connexion si [Open](#open) a été appelée avec succès sur une source de données ODBC ; sinon, une chaîne vide. Pour un Microsoft Jet (. Base de données MDB), la chaîne est toujours vide sauf si vous la définissez pour une utilisation avec le `dbSQLPassThrough` option utilisée avec le [Execute](#execute) fonction membre ou utilisé lors de l’ouverture d’un jeu d’enregistrements.

### <a name="remarks"></a>Notes

La chaîne fournit des informations sur la source d’une base de données ouverte ou d’une base de données utilisé dans une requête directe. La chaîne de connexion est composée d’un spécificateur de type de base de données et de zéro ou plusieurs paramètres séparés par des points-virgules.

> [!NOTE]
>  À l’aide des classes DAO de MFC pour se connecter à une source de données via ODBC est moins efficace que la connexion via une table attachée.

> [!NOTE]
>  La chaîne de connexion est utilisée pour passer des informations supplémentaires à ODBC et certains pilotes ISAM si nécessaire. Il n’est pas utilisé pour. Bases de données MDB. Pour les tables de base de base de données Microsoft Jet, la chaîne de connexion est une chaîne vide (" »), sauf lorsque vous l’utiliser pour une requête SQL directe comme décrit sous retournent la valeur ci-dessus.

Consultez le [Open](#open) fonction membre pour une description de la création de la chaîne de connexion. Une fois que la chaîne de connexion a été définie dans le `Open` appel, vous pouvez ultérieurement utiliser pour vérifier le paramètre pour déterminer le type, le chemin d’accès, la source de données utilisateur ID, le mot de passe ou ODBC de la base de données.

##  <a name="getname"></a>  CDaoDatabase::GetName

Appelez cette fonction membre pour récupérer le nom de la base de données actuellement ouvert, ce qui est le nom d’un fichier de base de données existant, ou le nom d’une source de données ODBC inscrit.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

Le chemin d’accès complet et le nom de la base de données en cas de réussite ; Sinon, vide [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Si votre réseau prend en charge la convention d’affectation de noms uniforme (UNC), vous pouvez également spécifier un chemin d’accès réseau, par exemple, «\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ». (Barres obliques inverses doubles sont requis dans les littéraux de chaîne, car «\\» est le caractère d’échappement de C++.)

Peut, par exemple, voulez-vous afficher ce nom dans un titre. Si une erreur se produit alors que le nom est récupéré, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
>  Pour de meilleures performances lors de l’accès des bases de données externes, nous recommandons de lier les tables de base de données externe à une base de données Microsoft Jet (. MDB) au lieu de se connecter directement à la source de données.

Le type de base de données est indiqué par le fichier ou le répertoire que le chemin d’accès pointe, comme suit :

|Points de chemin d’accès à...|Type de base de données|
|--------------------------|-------------------|
|. Fichier MDB|Base de données Microsoft Jet (Microsoft Access)|
|Répertoire qui contient. Fichiers DBF|base de données dBASE|
|Répertoire qui contient. Fichier XLS|Base de données Microsoft Excel|
|Répertoire qui contient. PDX fichier (s)|Base de données Paradox|
|Répertoire qui contient les fichiers de base de données de texte correctement mis en forme|Base de données de format de texte|

Pour les bases de données ODBC comme SQL Server et Oracle, chaîne de connexion de la base de données identifie un nom de source de données (DSN) qui est inscrit par ODBC.

##  <a name="getquerydefcount"></a>  CDaoDatabase::GetQueryDefCount

Appelez cette fonction membre pour récupérer le nombre de requêtes définies dans la collection QueryDefs de la base de données.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de requêtes définies dans la base de données.

### <a name="remarks"></a>Notes

`GetQueryDefCount` est utile si vous avez besoin itérer sur tous les querydefs dans la collection QueryDefs. Pour obtenir des informations sur une requête donnée dans la collection, consultez [fonction membre GetQueryDefInfo](#getquerydefinfo).

##  <a name="getquerydefinfo"></a>  CDaoDatabase::GetQueryDefInfo

Appelez cette fonction membre pour obtenir les différents types d’informations sur une requête définie dans la base de données.

```
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
Index de la requête prédéfinie dans QueryDefs (collection) de la base de données, pour la recherche par index.

*querydefinfo*<br/>
Une référence à un [objet CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) objet qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur le jeu d’enregistrements à récupérer. Les options disponibles sont répertoriées ici, ainsi que leur cause la fonction retourne le jeu d’enregistrements :

- Nom AFX_DAO_PRIMARY_INFO (valeur par défaut), Type

- Informations de AFX_DAO_SECONDARY_INFO primaire plus (+) : Date de création, Date de dernière mise à jour, renvoie les enregistrements, être mise à jour

- AFX_DAO_ALL_INFO primaire et secondaire informations plus (+) : SQL, vous connecter, ODBCTimeout

*lpszName*<br/>
Chaîne contenant le nom d’une requête définie dans la base de données pour la recherche par nom.

### <a name="remarks"></a>Notes

Deux versions de la fonction sont fournies afin de pouvoir sélectionner une requête par index dans la collection QueryDefs de la base de données ou par le nom de la requête.

Pour obtenir une description des informations retournées dans *querydefinfo*, consultez le [objet CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) structure. Cette structure a des membres qui correspondent aux éléments d’informations répertoriées ci-dessus dans la description de *dwInfoOptions*. Si vous demandez un niveau d’informations, vous obtenez tous les niveaux d’informations ainsi préalables.

##  <a name="getquerytimeout"></a>  CDaoDatabase::GetQueryTimeout

Appelez cette fonction membre pour récupérer le nombre actuel de secondes autorisé avant que les opérations suivantes sur la base de données connectée a été dépassées.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Valeur de retour

Entier court qui contient la valeur de délai d’expiration en secondes.

### <a name="remarks"></a>Notes

Une opération peut expirer en raison de problèmes d’accès réseau, le temps de traitement de requête excessif et ainsi de suite. Alors que le paramètre est en vigueur, il affecte tous ouverts ajouter un nouveau, mettre à jour et supprimer des opérations sur les jeux d’enregistrements associé à cet `CDaoDatabase` objet. Vous pouvez modifier le paramètre de délai d’attente actuel en appelant [SetQueryTimeout](#setquerytimeout). Modification de la valeur de délai d’expiration de requête pour un jeu d’enregistrements après l’ouverture ne change pas la valeur pour le jeu d’enregistrements. Par exemple, suivante [déplacer](../../mfc/reference/cdaorecordset-class.md#move) opérations n’utilisent pas la nouvelle valeur. La valeur par défaut est initialement définie lorsque le moteur de base de données est initialisé.

La valeur par défaut des délais d’expiration de la requête est effectuée à partir du Registre Windows. S’il n’existe aucun paramètre de Registre, la valeur par défaut est de 60 secondes. Pas toutes les bases de données prend en charge la possibilité de définir une valeur de délai d’expiration de requête. Si vous définissez une valeur de délai d’expiration de requête de 0, aucun délai d’expiration se produit ; et la communication avec la base de données peut cesser de répondre. Ce comportement peut être utile lors du développement. Si l’appel échoue, MFC lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

Pour plus d’informations, consultez la rubrique « Propriété QueryTimeout » dans l’aide de DAO.

##  <a name="getrecordsaffected"></a>  CDaoDatabase::GetRecordsAffected

Appelez cette fonction membre pour déterminer le nombre d’enregistrements affectés par l’appel le plus récent de la [Execute](#execute) fonction membre.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valeur de retour

Entier long contenant le nombre d’enregistrements concernés.

### <a name="remarks"></a>Notes

La valeur retournée inclut le nombre d’enregistrements supprimés, mis à jour ou inséré par une requête d’action exécuter avec `Execute`. Le nombre retourné ne reflète pas les modifications dans les tables associées lorsque cascade met à jour ou supprime prennent effet.

Pour plus d’informations, consultez la rubrique « Propriété RecordsAffected » dans l’aide de DAO.

##  <a name="getrelationcount"></a>  CDaoDatabase::GetRelationCount

Appelez cette fonction membre pour obtenir le nombre de relations définies entre les tables dans la base de données.

```
short GetRelationCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de relations définies entre les tables dans la base de données.

### <a name="remarks"></a>Notes

`GetRelationCount` est utile si vous devez effectuer une boucle sur toutes les relations définies dans la collection de Relations de la base de données. Pour obtenir des informations sur une relation donnée dans la collection, consultez [GetRelationInfo](#getrelationinfo).

Pour illustrer le concept d’une relation, considérez une table fournisseurs et une table de produits, ce qui peut avoir une relation un-à-plusieurs. Dans cette relation, un seul fournisseur peut fournir plusieurs produits. Autres relations sont-à-un et plusieurs-à-plusieurs.

##  <a name="getrelationinfo"></a>  CDaoDatabase::GetRelationInfo

Appelez cette fonction membre pour obtenir des informations sur une relation spécifiée dans la collection de Relations de la base de données.

```
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
L’index de l’objet de relation dans la collection de Relations de la base de données, pour la recherche par index.

*relinfo*<br/>
Une référence à un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objet qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur la relation à récupérer. Les options disponibles sont répertoriées ici, ainsi que leur cause la fonction retourner sur la relation :

- Table étrangère du nom, Table, AFX_DAO_PRIMARY_INFO (valeur par défaut)

- Attributs AFX_DAO_SECONDARY_INFO, informations de champ

Les informations de champ est un [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) objet contenant les champs à partir de la table primaire impliquée dans la relation.

*lpszName*<br/>
Chaîne contenant le nom de l’objet de relation pour la recherche par nom.

### <a name="remarks"></a>Notes

Deux versions de cette fonction fournissent l’accès par index ou par nom. Pour obtenir une description des informations retournées dans *relinfo*, consultez le [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) structure. Cette structure a des membres qui correspondent aux éléments d’informations répertoriées ci-dessus dans la description de *dwInfoOptions*. Si vous demandez des informations à un niveau, vous obtenez également des informations à n’importe quel préalable des niveaux.

> [!NOTE]
>  Si vous définissez la relation des attributs de l’objet pour activer les opérations en cascade (`dbRelationUpdateCascades` ou `dbRelationDeleteCascades`), le moteur de base de données Microsoft Jet automatiquement des mises à jour ou supprime des enregistrements dans une ou plusieurs autres tables lorsque des modifications sont apportées à relation clé primaire tables. Par exemple, supposons que vous établissez une relation de suppression en cascade entre une table Customers et une table de commandes. Lorsque vous supprimez des enregistrements à partir de la table Customers, enregistrements dans la table de commandes associées à ce client sont également supprimés. En outre, si vous établissez des relations de suppression en cascade entre la table Orders et d’autres tables, les enregistrements à partir de ces tables sont automatiquement supprimés lorsque vous supprimez des enregistrements à partir de la table Customers.

##  <a name="gettabledefcount"></a>  CDaoDatabase::GetTableDefCount

Appelez cette fonction membre pour récupérer le nombre de tables définies dans la base de données.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de tabledefs définis dans la base de données.

### <a name="remarks"></a>Notes

`GetTableDefCount` est utile si vous avez besoin itérer sur tous les tabledefs dans TableDefs (collection) de la base de données. Pour obtenir des informations sur une table donnée dans la collection, consultez [GetTableDefInfo](#gettabledefinfo).

##  <a name="gettabledefinfo"></a>  CDaoDatabase::GetTableDefInfo

Appelez cette fonction membre pour obtenir les différents types d’informations sur une table définie dans la base de données.

```
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
L’index de l’objet tabledef dans TableDefs (collection) de la base de données, pour la recherche par index.

*tabledefinfo*<br/>
Une référence à un [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) objet qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur la table à récupérer. Les options disponibles sont répertoriées ici, ainsi que leur cause la fonction retourner sur la relation :

- Attributs de nom AFX_DAO_PRIMARY_INFO (valeur par défaut), être mise à jour,

- Informations de AFX_DAO_SECONDARY_INFO primaire plus (+) : Date de création, Date de dernière mise à jour, nom de la Table Source, se connecter

- AFX_DAO_ALL_INFO primaire et secondaire informations plus (+) : Nombre d’enregistrements de règle, le texte de Validation, de validation

*lpszName*<br/>
Le nom de l’objet tabledef, pour la recherche par nom.

### <a name="remarks"></a>Notes

Deux versions de la fonction sont fournies afin de pouvoir sélectionner une table par index dans la collection TableDefs de la base de données ou par le nom de la table.

Pour obtenir une description des informations retournées dans *tabledefinfo*, consultez le [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) structure. Cette structure a des membres qui correspondent aux éléments d’informations répertoriées ci-dessus dans la description de *dwInfoOptions*. Si vous demandez des informations à un niveau, vous obtenez des informations sur n’importe quel préalable des niveaux.

> [!NOTE]
>  L’option AFX_DAO_ALL_INFO fournit des informations qui peuvent être lentes à obtenir. Dans ce cas, les enregistrements dans la table d’inventaire peut être beaucoup de temps s’il existe de nombreux enregistrements.

##  <a name="getversion"></a>  CDaoDatabase::GetVersion

Appelez cette fonction membre pour déterminer la version du fichier de base de données Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui indique la version du fichier de base de données associé à l’objet.

### <a name="remarks"></a>Notes

La valeur retournée représente le numéro de version sous la forme « major.minor » ; par exemple, « 3.0 ». Le numéro de version du produit (par exemple, version 3.0) comprend le numéro de version (3), une période et le numéro de version (0). Les versions à la date sont 1.0, 1.1, 2.0 et 3.0.

Pour plus d’informations, consultez la rubrique « Propriété de Version » dans l’aide de DAO.

##  <a name="isopen"></a>  CDaoDatabase::IsOpen

Appelez cette fonction membre pour déterminer si le `CDaoDatabase` objet est actuellement ouvert sur une base de données.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le `CDaoDatabase` objet est actuellement ouvert ; sinon, 0.

### <a name="remarks"></a>Notes

##  <a name="m_pdaodatabase"></a>  CDaoDatabase::m_pDAODatabase

Contient un pointeur vers l’interface OLE pour l’objet de base de données DAO sous-jacent le `CDaoDatabase` objet.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous avez besoin d’accéder à l’interface DAO directement.

Pour plus d’informations sur l’appel de DAO directement, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="m_pworkspace"></a>  CDaoDatabase::m_pWorkspace

Contient un pointeur vers le [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objet qui contient l’objet de base de données.

### <a name="remarks"></a>Notes

Utiliser ce pointeur si vous avez besoin d’accéder directement à l’espace de travail, par exemple, pour obtenir des pointeurs à d’autres objets de base de données dans la collection de bases de données de l’espace de travail.

##  <a name="open"></a>  CDaoDatabase::Open

Vous devez appeler cette fonction membre pour initialiser un nouvellement construit `CDaoDatabase` objet qui représente une base de données existante.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Une expression de chaîne qui est le nom d’un existant Microsoft Jet (. Fichier de base de données MDB). Si le nom de fichier a une extension, il est nécessaire. Si votre réseau prend en charge la convention d’affectation de noms uniforme (UNC), vous pouvez également spécifier un chemin d’accès réseau, tels que «\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ». (Barres obliques inverses doubles sont requis dans les littéraux de chaîne, car «\\» est le caractère d’échappement de C++.)

Certaines considérations s’appliquent lorsque vous utilisez *le caractère*. Si elle :

- Fait référence à une base de données est déjà ouverte pour un accès exclusif par un autre utilisateur, MFC les lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md). Intercepter cette exception pour informer vos utilisateurs que la base de données n’est pas disponible.

- Est une chaîne vide (" ») et *lpszConnect* est « ODBC ; », une boîte de dialogue répertoriant les inscrits tous les noms de source de données ODBC s’affiche afin que l’utilisateur peut sélectionner une base de données. Vous devez éviter les connexions directes à des sources de données ODBC ; Utilisez une table attachée à la place.

- Dans le cas contraire, ne fait pas référence à une base de données existante ou une valide nom de la source de données ODBC, MFC les lève une exception de type `CDaoException`.

> [!NOTE]
>  Pour plus d’informations sur les codes d’erreur DAO, consultez la DAOERR. Fichier de H. Pour plus d’informations, consultez la rubrique « Erreurs d’accès données récupérables » dans l’aide de DAO.

*bExclusive*<br/>
Valeur booléenne qui a la valeur TRUE si la base de données doit être ouvert pour un accès exclusif (non partagé) et FALSE si la base de données doit être ouvert pour un accès partagé. Si vous omettez cet argument, la base de données est ouvert pour un accès partagé.

*bReadOnly*<br/>
Valeur booléenne qui a la valeur TRUE si la base de données doit être ouvert pour l’accès en lecture seule et FALSE si la base de données doit être ouvert pour un accès en lecture/écriture. Si vous omettez cet argument, la base de données est ouvert pour un accès en lecture/écriture. Tous les jeux d’enregistrements dépendants hérite de cet attribut.

*lpszConnect*<br/>
Une expression de chaîne utilisée pour l’ouverture de la base de données. Cette chaîne constitue ODBC connecter des arguments. Vous devez fournir les arguments exclusifs et en lecture seule pour fournir une chaîne source. Si la base de données est une base de données Microsoft Jet (. (MDB), cette chaîne est vide ( » »). La syntaxe de la valeur par défaut : **_T**(« »), fournit la portabilité pour Unicode comme ANSI pour les builds de votre application.

### <a name="remarks"></a>Notes

`Open` associe la base de données à l’objet DAO sous-jacent. Vous ne pouvez pas utiliser l’objet de base de données pour construire le jeu d’enregistrements, tabledef ou objets querydef jusqu'à ce qu’il est initialisé. `Open` Ajoute l’objet de base de données à la collection de bases de données de l’espace de travail associé.

Utilisez les paramètres comme suit :

- Si vous ouvrez un Microsoft Jet (. Base de données MDB), utilisez le *le caractère* paramètre et passe une chaîne vide pour le *lpszConnect* paramètre ou passer une chaîne de mot de passe du formulaire « ; PWD = mot de passe » si la base de données est protégée par mot de passe (. MDB bases de données uniquement).

- Si vous ouvrez une source de données ODBC, passez une chaîne de connexion ODBC valide dans *lpszConnect* et une chaîne vide dans *le caractère*.

Pour plus d’informations, consultez la rubrique « Méthode OpenDatabase » dans l’aide de DAO.

> [!NOTE]
>  Pour de meilleures performances lorsqu’ils accèdent à des bases de données externes, y compris les bases de données ISAM et sources de données ODBC, il est recommandé de lier les tables de base de données externe à une base de données de moteur Microsoft Jet (. MDB) au lieu de se connecter directement à la source de données.

Il est possible qu’une tentative de connexion expire si, par exemple, l’hôte de SGBD n’est pas disponible. Si la tentative de connexion échoue, `Open` lève une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

La section Notes restante s’appliquent uniquement aux bases de données ODBC :

Si la base de données est une base de données ODBC et les paramètres dans votre `Open` appel ne contiennent pas suffisamment d’informations pour établir la connexion, le pilote ODBC ouvre une boîte de dialogue pour obtenir les informations nécessaires à partir de l’utilisateur. Lorsque vous appelez `Open`, votre chaîne de connexion, *lpszConnect*, est stocké en privé et est disponible en appelant le [GetConnect](#getconnect) fonction membre.

Si vous le souhaitez, vous pouvez ouvrir votre propre boîte de dialogue avant d’appeler `Open` pour obtenir des informations à partir de l’utilisateur, comme un mot de passe, puis ajoutez ces informations à la chaîne de connexion que vous passez à `Open`. Ou vous souhaiterez peut-être enregistrer la chaîne de connexion que vous passez (peut-être dans le Registre Windows), vous pouvez le réutiliser la prochaine fois que votre application appelle `Open` sur un `CDaoDatabase` objet.

Vous pouvez également utiliser la chaîne de connexion pour plusieurs niveaux d’autorisation de connexion (chacun correspondant à un autre `CDaoDatabase` objet) ou pour transmettre d’autres informations spécifiques à la base de données.

##  <a name="setquerytimeout"></a>  CDaoDatabase::SetQueryTimeout

Appelez cette fonction membre pour remplacer le nombre de secondes avant les opérations suivantes sur le délai d’attente de base de données connectée par défaut.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Paramètres

*nSeconds*<br/>
Le nombre de secondes avant une tentative de requête arrive à expiration.

### <a name="remarks"></a>Notes

Une opération peut expirer en raison de problèmes d’accès réseau, le temps de traitement de requête excessif et ainsi de suite. Appelez `SetQueryTimeout` avant l’ouverture du recordset ou avant d’appeler le jeu d’enregistrements [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [mise à jour](../../mfc/reference/cdaorecordset-class.md#update), ou [supprimer](../../mfc/reference/cdaorecordset-class.md#delete) si vous souhaitez modifier la requête de fonctions membres valeur de délai d’attente. Le paramètre affecte tous les [Open](../../mfc/reference/cdaorecordset-class.md#open), `AddNew`, `Update`, et `Delete` appels à tous les recordsets associés à cet `CDaoDatabase` objet. Modification de la valeur de délai d’expiration de requête pour un jeu d’enregistrements après l’ouverture ne change pas la valeur pour le jeu d’enregistrements. Par exemple, suivante [déplacer](../../mfc/reference/cdaorecordset-class.md#move) opérations n’utilisent pas la nouvelle valeur.

La valeur par défaut des délais d’expiration de la requête est de 60 secondes. Pas toutes les bases de données prend en charge la possibilité de définir une valeur de délai d’expiration de requête. Si vous définissez une valeur de délai d’expiration de requête de 0, aucun délai d’expiration se produit ; la communication avec la base de données peut cesser de répondre. Ce comportement peut être utile lors du développement.

Pour plus d’informations, consultez la rubrique « Propriété QueryTimeout » dans l’aide de DAO.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace, classe](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset, classe](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef, classe](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException, classe](../../mfc/reference/cdaoexception-class.md)
