---
title: CDaoDatabase, classe
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
ms.openlocfilehash: debba137878da49921df83da7630003a7d62db2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369019"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase, classe

Représente une connexion à une base de données d’accès à l’aide d’objets d’accès aux données (DAO). DAO est soutenu par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète.

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
|[CDaoDatabase::CanTransact](#cantransact)|Retourne nonzero si la base de données prend en charge les transactions.|
|[CDaoDatabase::CanUpdate](#canupdate)|Retourne nonzero `CDaoDatabase` si l’objet est updatable (non lu uniquement).|
|[CDaoDatabase::Close](#close)|Ferme la connexion de base de données.|
|[CDaoDatabase::Créer](#create)|Crée l’objet de base de `CDaoDatabase` données DAO sous-jacent et initialise l’objet.|
|[CDaoDatabase::CreateRelation](#createrelation)|Définit une nouvelle relation entre les tableaux de la base de données.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Supprime un objet requête enregistré dans la collection RequêteDefs de la base de données.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Supprime une relation existante entre les tables de la base de données.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Supprime la définition d’un tableau dans la base de données. Cela supprime le tableau réel et toutes ses données.|
|[CDaoDatabase::Exécuter](#execute)|Exécute une requête d’action. Demander `Execute` une requête qui renvoie les résultats fait l’exception.|
|[CDaoDatabase::GetConnect](#getconnect)|Retourne la chaîne de `CDaoDatabase` connexion utilisée pour connecter l’objet à une base de données. Utilisé pour ODBC.|
|[CDaoDatabase::GetName](#getname)|Retourne le nom de la base de données actuellement en cours d’utilisation.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Retourne le nombre de requêtes définies pour la base de données.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Renvoie des informations sur une requête spécifiée définie dans la base de données.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Retourne le nombre de secondes après lesquelles les opérations de requête de base de données s’évanouiront. Affecte toutes les opérations ouvertes, d’ajout, de mise à jour et d’autres opérations d’ODBC (seulement) telles que `Execute` les appels.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Retourne le nombre d’enregistrements affectés par la dernière mise à `Execute`jour, modifier ou ajouter l’opération ou par un appel à .|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Retourne le nombre de relations définies entre les tableaux dans la base de données.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Renvoie des informations sur une relation spécifiée définie entre les tableaux de la base de données.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Retourne le nombre de tableaux définis dans la base de données.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Renvoie des informations sur un tableau spécifié dans la base de données.|
|[CDaoDatabase::GetVersion](#getversion)|Retourne la version du moteur de base de données associé à la base de données.|
|[CDaoDatabase::IsOpen](#isopen)|Retourne nonzero `CDaoDatabase` si l’objet est actuellement connecté à une base de données.|
|[CDaoDatabase::Ouvert](#open)|Établit une connexion à une base de données.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Définit le nombre de secondes après lesquelles les opérations de requête de base de données (sur les sources de données ODBC seulement) s’éteil. Affecte toutes les opérations ouvertes, d’ajout de nouvelles, de mise à jour et de suppression.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Un pointeur vers l’objet de base de données DAO sous-jacent.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Un pointeur de l’objet [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) qui contient la base de données et définit son espace de transaction.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur les formats de base de données pris en charge, consultez la fonction membre [GetName.](../../mfc/reference/cdaoworkspace-class.md#getname) Vous pouvez avoir `CDaoDatabase` un ou plusieurs objets actifs à la fois dans un « espace de travail » donné, représenté par un objet [CDaoWorkspace.](../../mfc/reference/cdaoworkspace-class.md) L’espace de travail maintient une collection d’objets de base de données ouverts, appelées la collection databases.

## <a name="usage"></a>Usage

Vous pouvez créer implicitement des objets de base de données, lorsque vous créez des objets de records. Mais vous pouvez également créer des objets de base de données explicitement. Pour utiliser explicitement une `CDaoDatabase`base de données existante avec , faites l’un ou l’autre des éléments suivants :

- Construisez `CDaoDatabase` un objet, en passant un pointeur sur un objet [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) ouvert.

- Ou construisez un `CDaoDatabase` objet sans spécifier l’espace de travail (MFC crée un objet temporaire d’espace de travail).

Pour créer un nouveau Microsoft Jet (. Base de données MDB), construire un `CDaoDatabase` objet et appeler sa fonction de membre [Créer.](#create) N’appelez `Open` `Create` *pas* après .

Pour ouvrir une base `CDaoDatabase` de données existante, construisez un objet et appelez sa fonction de membre [Open.](#open)

L’une ou l’autre de ces techniques joint l’objet de base de données DAO à la collecte des bases de données de l’espace de travail et ouvre une connexion aux données. Lorsque vous construisez ensuite des objets [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)ou [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) pour fonctionner sur la `CDaoDatabase` base de données connectée, passez les constructeurs pour ces objets un pointeur sur votre objet. Lorsque vous avez terminé l’utilisation de la `CDaoDatabase` connexion, appelez la fonction du membre [Close](#close) et détruisez l’objet. `Close`ferme tous les enregistrements que vous n’avez pas fermés auparavant.

## <a name="transactions"></a>Transactions

Le traitement des transactions de base de données est fourni au niveau de l’espace de travail : consultez les fonctions membres [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans) et [ROLLBACK](../../mfc/reference/cdaoworkspace-class.md#rollback) de la classe`CDaoWorkspace`.

## <a name="odbc-connections"></a>Connexions ODBC

La façon recommandée de travailler avec les sources de données ODBC est d’attacher des tables externes à un Microsoft Jet (. base de données MDB).

## <a name="collections"></a>Collections

Chaque base de données conserve ses propres collections d’objets de tabledef, de requête, d’enregistrement et de relation. La `CDaoDatabase` classe fournit aux membres des fonctions de manipulation de ces objets.

> [!NOTE]
> Les objets sont stockés dans DAO, et non dans l’objet de base de données MFC. MFC fournit des cours pour les objets de table, de requête et d’enregistrement, mais pas pour les objets relationnels.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a>CDaoDatabase::CanTransact

Appelez cette fonction de membre pour déterminer si la base de données autorise les transactions.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la base de données prend en charge les transactions; sinon 0.

### <a name="remarks"></a>Notes

Les transactions sont gérées dans l’espace de travail de la base de données.

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a>CDaoDatabase::CanUpdate

Appelez cette fonction de `CDaoDatabase` membre pour déterminer si l’objet permet des mises à jour.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CDaoDatabase` l’objet permet des mises à jour; autrement 0, indiquant soit que vous avez passé TRUE `CDaoDatabase` dans *bReadOnly* lorsque vous avez ouvert l’objet ou que la base de données elle-même est lue uniquement. Voir la fonction de membre [Open.](#open)

### <a name="remarks"></a>Notes

Pour plus d’informations sur la facilité de base de données, consultez le thème "Updatable Property" dans DAO Help.

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase

Construit un objet `CDaoDatabase`.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Paramètres

*pWorkspace (en)*<br/>
Un pointeur `CDaoWorkspace` sur l’objet qui contiendra le nouvel objet de base de données. Si vous acceptez la valeur par défaut `CDaoWorkspace` de NULL, le constructeur crée un objet temporaire qui utilise l’espace de travail DAO par défaut. Vous pouvez obtenir un pointeur vers l’objet de l’espace de travail via le membre [de données m_pWorkspace.](#m_pworkspace)

### <a name="remarks"></a>Notes

Après la construction de l’objet, si vous créez un nouveau Microsoft Jet (. Base de données MDB), appelez la fonction membre [Créer](#create) de l’objet. Si vous êtes, au lieu d’ouvrir une base de données existante, appelez la fonction de membre [Open](#open) de l’objet.

Lorsque vous avez terminé avec l’objet, vous devez `CDaoDatabase` appeler sa fonction de membre [Proche,](#close) puis détruire l’objet.

Vous pourriez trouver pratique d’intégrer l’objet `CDaoDatabase` dans votre classe de documents.

> [!NOTE]
> Un `CDaoDatabase` objet est également créé implicitement si vous ouvrez un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) sans passer un pointeur vers un objet existant. `CDaoDatabase` Cet objet de base de données est fermé lorsque vous fermez l’objet de l’enregistrement.

## <a name="cdaodatabaseclose"></a><a name="close"></a>CDaoDatabase::Close

Appelez cette fonction de membre pour vous déconnecter d’une base de données et fermer tous les enregistrements ouverts, les numéros de dépôt et les requêtes associées à la base de données.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Il est bon de fermer ces objets vous-même avant d’appeler cette fonction de membre. La `CDaoDatabase` fermeture d’un objet le supprime de la collection de bases de données dans l’espace [de travail](../../mfc/reference/cdaoworkspace-class.md)associé. Parce `Close` que ne `CDaoDatabase` détruit pas l’objet, vous pouvez réutiliser l’objet en ouvrant la même base de données ou une base de données différente.

> [!CAUTION]
> Appelez la fonction [membre de mise à jour](../../mfc/reference/cdaorecordset-class.md#update) `Close` (s’il y a des modifications en attente) et la fonction membre sur tous les objets open recordset avant de fermer une base de données. Si vous quittez une fonction qui déclare `CDaoDatabase` [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) ou des objets sur la pile, la base de données est fermée, les modifications nonavées sont perdues, toutes les transactions en attente sont annulées, et toutes les modifications en attente à vos données sont perdues.

> [!CAUTION]
> Si vous essayez de fermer un objet de base de données pendant que les objets de la liste d’enregistrement sont ouverts, ou si vous essayez de fermer un objet d’espace de travail pendant que les objets de base de données appartenant à cet espace de travail spécifique sont ouverts, ces objets de l’enregistrement seront fermés et les mises à jour ou modifications en attente seront annulées. Si vous essayez de fermer un objet d’espace de travail pendant que les objets de base de données qui lui appartiennent sont ouverts, l’opération ferme tous les objets de base de données appartenant à cet objet spécifique d’espace de travail, ce qui peut entraîner la fermeture d’objets de records non fermés. Si vous ne fermez pas votre objet de base de données, MFC signale une défaillance d’affirmation dans les constructions de débogé.

Si l’objet de base de données est défini en dehors de la portée d’une fonction, et que vous quittez la fonction sans la fermer, l’objet de base de données restera ouvert jusqu’à ce qu’il soit explicitement fermé ou que le module dans lequel il est défini est hors de portée.

## <a name="cdaodatabasecreate"></a><a name="create"></a>CDaoDatabase::Créer

Pour créer un nouveau Microsoft Jet (. Base de données MDB), appelez cette `CDaoDatabase` fonction de membre après avoir construit un objet.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Une expression de chaîne qui est le nom du fichier de base de données que vous créez. Il peut être le chemin complet et le\\nom de fichier, tels que "C: 'MYDB. MDB". Vous devez fournir un nom. Si vous ne fournissez pas une extension de nom de fichier, . La BMD est jointe. Si votre réseau prend en charge la convention de nommage uniforme\\\\\\(UNC), vous pouvez également spécifier un parcours réseau, tel que « MYSERVER\\» 'MYSHARE\\'MYDIR\\'MYDB'. Seul Microsoft Jet (. Les fichiers de base de données MDB peuvent être créés à l’aide de cette fonction de membre. (Doubles contre-coups de dos sont nécessaires\\dans les littérals de cordes parce que « est le caractère d’évasion de C.)

*lpszLocale*<br/>
Une expression de chaîne utilisée pour spécifier l’ordre de collecte pour la création de la base de données. La valeur par défaut est `dbLangGeneral`. Les valeurs possibles sont les suivantes :

- `dbLangGeneral`Anglais, Allemand, Français, Portugais, Italien et Espagnol moderne

- `dbLangArabic`Arabe

- `dbLangCyrillic`Russe

- `dbLangCzech`Tchèque

- `dbLangDutch`Néerlandais

- `dbLangGreek`Grec

- `dbLangHebrew`Hébreu

- `dbLangHungarian`Hongrois

- `dbLangIcelandic`Islandais

- `dbLangNordic`Langues nordiques (Microsoft Jet version moteur de base de données 1.0 seulement)

- `dbLangNorwdan`Norvégien et danois

- `dbLangPolish`Polonais

- `dbLangSpanish`Espagnol traditionnel

- `dbLangSwedfin`Suédois et finlandais

- `dbLangTurkish`Turc

*dwOptions*<br/>
Un intégrant qui indique une ou plusieurs options. Les valeurs possibles sont les suivantes :

- `dbEncrypt`Créez une base de données cryptée.

- `dbVersion10`Créez une base de données avec la version 1.0 de la base de données Microsoft Jet.

- `dbVersion11`Créez une base de données avec la version 1.1 de la base de données Microsoft Jet.

- `dbVersion20`Créez une base de données avec la version 2.0 de la base de données Microsoft Jet.

- `dbVersion30`Créez une base de données avec la version 3.0 de la base de données Microsoft Jet.

Si vous ometez la constante de chiffrement, une base de données non chiffrée est créée. Vous ne pouvez spécifier qu’une seule version constante. Si vous ometez une constante de version, une base de données qui utilise la version 3.0 de la base de données Microsoft Jet est créée.

> [!CAUTION]
> Si une base de données n’est pas cryptée, il est possible, même si vous implémentez la sécurité utilisateur/mot de passe, de lire directement le fichier disque binaire qui constitue la base de données.

### <a name="remarks"></a>Notes

`Create`crée le fichier de base de données et l’objet de base de données DAO sous-jacent et initialise l’objet C. L’objet est annexé à la collection de bases de données de l’espace de travail associé. L’objet de base de données est à l’état ouvert; n’appelez `Open*` `Create`pas après .

> [!NOTE]
> Avec `Create`, vous pouvez créer uniquement Microsoft Jet (. bases de données MDB). Vous ne pouvez pas créer de bases de données ISAM ou de bases de données ODBC.

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a>CDaoDatabase::CreateRelation

Appelez cette fonction de membre pour établir une relation entre un ou plusieurs champs dans un tableau primaire dans la base de données et un ou plusieurs champs dans une table étrangère (un autre tableau dans la base de données).

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

*lpszName (en)*<br/>
Le nom unique de l’objet relationnel. Le nom doit commencer par une lettre et peut contenir un maximum de 40 caractères. Il peut inclure des nombres et des personnages de souligner, mais ne peut pas inclure la ponctuation ou des espaces.

*lpszTable (en)*<br/>
Le nom du tableau principal dans la relation. Si le tableau n’existe pas, MFC jette une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Le nom de la table étrangère dans la relation. Si le tableau n’existe pas, MFC `CDaoException`jette une exception de type .

*lAttributes*<br/>
Une valeur à long terme qui contient des informations sur le type de relation. Vous pouvez utiliser cette valeur pour faire respecter l’intégrité référentielle, entre autres choses. Vous pouvez utiliser l’opérateur bitwise-OR ( **&#124;**) pour combiner l’une des valeurs suivantes (tant que la combinaison a du sens):

- `dbRelationUnique`La relation est en tête-à-tête.

- `dbRelationDontEnforce`La relation n’est pas appliquée (pas d’intégrité référentielle).

- `dbRelationInherited`La relation existe dans une base de données non actuelle qui contient les deux tableaux ci-joints.

- `dbRelationUpdateCascade`Les mises à jour seront en cascade (pour en savoir plus sur les cascades, voir Remarques).

- `dbRelationDeleteCascade`Les suppressions vont cascader.

*lpszField (en)*<br/>
Un pointeur à une chaîne non terminée contenant le nom d’un champ dans la table primaire (nommé par *lpszTable*).

*lpszForeignField (en)*<br/>
Un pointeur à une chaîne non terminée contenant le nom d’un champ dans la table étrangère (nommé par *lpszForeignTable*).

*relinfo (en)*<br/>
Une référence à un objet [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) qui contient des informations sur la relation que vous souhaitez créer.

### <a name="remarks"></a>Notes

La relation ne peut pas impliquer une requête ou une table jointe à partir d’une base de données externe.

Utilisez la première version de la fonction lorsque la relation implique un champ dans chacune des deux tables. Utilisez la deuxième version lorsque la relation implique plusieurs champs. Le nombre maximum de champs dans une relation est de 14.

Cette action crée un objet de relation DAO sous-jacent, mais il s’agit d’un `CDaoDatabase`détail de mise en œuvre MFC depuis l’encapsulation MFC des objets relationnels est contenu dans la classe . MFC ne fournit pas de classe pour les relations.

Si vous définissez les attributs de l’objet de relation pour activer les opérations en cascade, le moteur de base de données met à jour ou supprime automatiquement des enregistrements dans une ou plusieurs autres tables lorsque des modifications sont apportées aux tableaux clés primaires connexes.

Supposons, par exemple, d’établir une relation de suppression en cascade entre une table de clients et une table de commandes. Lorsque vous supprimez les enregistrements du tableau des clients, les enregistrements dans le tableau des commandes liés à ce client sont également supprimés. En outre, si vous établissez des relations de suppression en cascade entre le tableau des commandes et d’autres tableaux, les enregistrements de ces tables sont automatiquement supprimés lorsque vous supprimez des enregistrements de la table des clients.

Pour plus d’informations connexes, voir le thème "Méthode de création de la connexion" dans DAO Aide.

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a>CDaoDatabase::DeleteQueryDef

Appelez cette fonction de membre pour supprimer la requête spécifiée — requête enregistrée — de la collection QueryDefs de l’objet. `CDaoDatabase`

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom de la requête enregistrée à supprimer.

### <a name="remarks"></a>Notes

Par la suite, cette requête n’est plus définie dans la base de données.

Pour plus d’informations sur la création d’objets requête, voir classe [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Un objet requête est associé à `CDaoDatabase` un objet `CDaoQueryDef` particulier lorsque vous construisez l’objet, en le passant un pointeur à l’objet de base de données.

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a>CDaoDatabase::DeleteRelation

Appelez cette fonction de membre pour supprimer une relation existante de la collection relations de l’objet de base de données.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom de la relation à supprimer.

### <a name="remarks"></a>Notes

Par la suite, la relation n’existe plus.

Pour obtenir des informations connexes, consultez le thème « Supprimer la méthode » dans DAO Help.

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef

Appelez cette fonction membre pour supprimer le tableau `CDaoDatabase` spécifié et toutes ses données de la collection TableDefs de l’objet.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom du code de dépôt à supprimer.

### <a name="remarks"></a>Notes

Par la suite, ce tableau n’est plus défini dans la base de données.

> [!NOTE]
> Soyez très prudent de ne pas supprimer les tables système.

Pour plus d’informations sur la création d’objets tabledef, voir classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Un objet de table devient `CDaoDatabase` associé à un `CDaoTableDef` objet particulier lorsque vous construisez l’objet, en le passant un pointeur à l’objet de base de données.

Pour obtenir des informations connexes, consultez le thème « Supprimer la méthode » dans DAO Help.

## <a name="cdaodatabaseexecute"></a><a name="execute"></a>CDaoDatabase::Exécuter

Appelez cette fonction de membre pour exécuter une requête d’action ou exécuter une déclaration SQL sur la base de données.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Paramètres

*lpszSQL*<br/>
Pointeur vers une corde non terminée contenant une commande SQL valide à exécuter.

*nOptions*<br/>
Un integer qui spécifie les options relatives à l’intégrité de la requête. Vous pouvez utiliser l’opérateur bitwise-OR ( **&#124;**) pour combiner l’une des constantes suivantes (à condition que la combinaison ait un sens — par exemple, vous ne combineriez `dbInconsistent` pas avec `dbConsistent`):

- `dbDenyWrite`Refuser d’écrire la permission à d’autres utilisateurs.

- `dbInconsistent`(Par défaut) Mises à jour incohérentes.

- `dbConsistent`Mises à jour cohérentes.

- `dbSQLPassThrough`SQL passer. La déclaration SQL doit être transmise à une source de données de l’ODBC pour traitement.

- `dbFailOnError`Annulez les mises à jour en cas d’erreur.

- `dbSeeChanges`Générez une erreur de temps d’exécution si un autre utilisateur modifie les données que vous modifiez.

> [!NOTE]
> Si `dbInconsistent` les `dbConsistent` deux et sont inclus ou si ni l’un ni l’autre n’est inclus, le résultat est la valeur par défaut. Pour une explication de ces constantes, voir le sujet "Execute Method" dans DAO Aide.

### <a name="remarks"></a>Notes

`Execute`ne fonctionne que pour les requêtes d’action ou les requêtes de passage SQL qui ne retournent pas les résultats. Il ne fonctionne pas pour certaines requêtes, qui retournent les enregistrements.

Pour une définition et des informations sur les requêtes d’action, voir les thèmes "Action Query" et "Execute Method" dans DAO Help.

> [!TIP]
> Compte tenu d’une déclaration SQL syntaxiquement correcte et des autorisations appropriées, la `Execute` fonction membre ne manquera pas même si aucune ligne ne peut être modifiée ou supprimée. Par conséquent, `dbFailOnError` utilisez toujours `Execute` l’option lors de l’utilisation de la fonction membre pour exécuter une mise à jour ou supprimer la requête. Cette option amène MFC à jeter une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md) et annule toutes les modifications réussies si l’un des enregistrements concernés sont verrouillés et ne peuvent pas être mis à jour ou supprimés. Notez que vous `GetRecordsAffected` pouvez toujours appeler pour voir combien d’enregistrements ont été affectés.

Appelez la fonction membre [GetRecordsAffected](#getrecordsaffected) de l’objet de base `Execute` de données pour déterminer le nombre d’enregistrements affectés par l’appel le plus récent. Par exemple, `GetRecordsAffected` renvoie des informations sur le nombre d’enregistrements supprimés, mis à jour ou insérés lors de l’exécution d’une requête en action. Le nombre retourné ne reflétera pas les changements dans les tableaux connexes lorsque des mises à jour ou des suppressions en cascade sont en vigueur.

`Execute`ne retourne pas un jeu d’enregistrement. L’utilisation d’une `Execute` requête qui sélectionne les enregistrements `CDaoException`amène MFC à jeter une exception de type . (Il n’y a `ExecuteSQL` `CDatabase::ExecuteSQL`pas de fonction de membre analogue à .)

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a>CDaoDatabase::GetConnect

Appelez cette fonction de membre pour récupérer `CDaoDatabase` la chaîne de connexion utilisée pour connecter l’objet à une base de données ODBC ou ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Valeur de retour

La chaîne de connexion si [Open](#open) a été appelé avec succès sur une source de données ODBC; sinon, une ficelle vide. Pour un Microsoft Jet (. Base de données MDB), la chaîne est toujours `dbSQLPassThrough` vide à moins que vous la définissez pour une utilisation avec l’option utilisée avec la fonction membre [Execute](#execute) ou utilisée pour ouvrir un jeu d’enregistrement.

### <a name="remarks"></a>Notes

La chaîne fournit des informations sur la source d’une base de données ouverte ou d’une base de données utilisée dans une requête de passage. La chaîne de connexion est composée d’un spécificateur de type base de données et de paramètres nuls ou plus séparés par des semi-colons.

> [!NOTE]
> L’utilisation des classes MFC DAO pour se connecter à une source de données via ODBC est moins efficace que la connexion via une table jointe.

> [!NOTE]
> La chaîne de connexion est utilisée pour transmettre des informations supplémentaires à ODBC et à certains pilotes ISAM au besoin. Il n’est pas utilisé pour . bases de données MDB. Pour les tables de base de base de base de microsoft Jet, la chaîne de connexion est une chaîne vide (« ») sauf lorsque vous l’utilisez pour une requête de passage SQL comme décrit sous La valeur de retour ci-dessus.

Consultez la fonction du membre [Open](#open) pour une description de la façon dont la chaîne de connexion est créée. Une fois que la chaîne `Open` de connexion a été définie dans l’appel, vous pouvez plus tard l’utiliser pour vérifier le paramètre afin de déterminer le type, le chemin, l’identifiant utilisateur, le mot de passe ou la source de données ODBC de la base de données.

## <a name="cdaodatabasegetname"></a><a name="getname"></a>CDaoDatabase::GetName

Appelez cette fonction de membre pour récupérer le nom de la base de données actuellement ouverte, qui est le nom d’un fichier de base de données existant ou le nom d’une source de données ODBC enregistrée.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

Le chemin complet et le nom de fichier de la base de données en cas de succès; autrement, un [CString](../../atl-mfc-shared/reference/cstringt-class.md)vide .

### <a name="remarks"></a>Notes

Si votre réseau prend en charge la convention de nommage uniforme\\\\\\(UNC),\\vous\\pouvez également spécifier un chemin réseau, par exemple, « MYSERVER , MYSHARE , MYDIR\\- MYDB. MDB". (Doubles contre-coups de dos sont nécessaires\\dans les littérals de cordes parce que « est le caractère d’évasion de C.)

Vous pouvez, par exemple, afficher ce nom dans un titre. Si une erreur se produit pendant que le nom est récupéré, MFC jette une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
> Pour de meilleures performances lorsque des bases de données externes sont accessibles, nous vous recommandons de joindre des tables de base de données externes à une base de données Microsoft Jet (. MDB) plutôt que de se connecter directement à la source de données.

Le type de base de données est indiqué par le fichier ou l’annuaire que le chemin indique, comme suit :

|Pathname pointe vers.|Type de base de données|
|--------------------------|-------------------|
|. Fichier MDB|Base de données Microsoft Jet (Microsoft Access)|
|Répertoire qui contient . Fichier DBF(s)|base de données dBASE|
|Répertoire qui contient . Fichier XLS|Base de données Microsoft Excel|
|Répertoire qui contient . Fichier PDX(s)|Base de données Paradox|
|Répertoire qui contient des fichiers de base de données textuelles correctement formatés|Base de données sur le format texte|

Pour les bases de données ODBC telles que SQL Server et Oracle, la chaîne de connexion de la base de données identifie un nom source de données (DSN) enregistré par ODBC.

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount

Appelez cette fonction de membre pour récupérer le nombre de requêtes définies dans la collection RequêteDefs de la base de données.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre de requêtes définies dans la base de données.

### <a name="remarks"></a>Notes

`GetQueryDefCount`est utile si vous avez besoin de boucle à travers toutes les requêtes de la collection QueryDefs. Pour obtenir des informations sur une requête donnée dans la collection, voir [GetQueryDefInfo](#getquerydefinfo).

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo

Appelez cette fonction de membre pour obtenir divers types d’informations sur une requête définie dans la base de données.

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
L’index de la requête prédéfinie dans la collection QueryDefs de la base de données, pour la recherche par index.

*requête en question*<br/>
Une référence à un objet [CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md) qui renvoie les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur l’enregistrement à récupérer. Les options disponibles sont énumérées ici ainsi que ce qu’elles font revenir la fonction sur le jeu d’enregistrement :

- AFX_DAO_PRIMARY_INFO (Par défaut) Nom, Type

- AFX_DAO_SECONDARY_INFO’information primaire plus: Date créée, Date de dernière mise à jour, Dossiers de retours, Updatable

- AFX_DAO_ALL_INFO informations primaires et secondaires plus: SQL, Connect, ODBCTimeout

*lpszName (en)*<br/>
Une chaîne contenant le nom d’une requête définie dans la base de données, pour le lookup par nom.

### <a name="remarks"></a>Notes

Deux versions de la fonction sont fournies afin que vous puissiez sélectionner une requête soit par index dans la collection QueryDefs de la base de données, soit par le nom de la requête.

Pour une description de l’information retournée dans *la requête ,* voir la structure [CDaoQueryDefInfo.](../../mfc/reference/cdaoquerydefinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Si vous demandez un niveau d’information, vous obtenez également des niveaux d’information antérieurs.

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout

Appelez cette fonction de membre pour récupérer le nombre actuel de secondes à autoriser avant que les opérations ultérieures sur la base de données connectée ne soient chronométrées.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Valeur de retour

Un peu plus d’intégrant contenant la valeur de temps d’arrêt en quelques secondes.

### <a name="remarks"></a>Notes

Une opération peut s’éteindre en raison de problèmes d’accès au réseau, de temps de traitement excessif des requêtes, et ainsi de suite. Bien que le paramètre soit en vigueur, il affecte tous les ouverts, `CDaoDatabase` ajouter de nouvelles opérations de mise à jour et supprimer les opérations sur tous les enregistrements associés à cet objet. Vous pouvez modifier le calendrier actuel en appelant [SetQueryTimeout](#setquerytimeout). Changer la valeur d’un délai d’attente de requête pour un enregistrement après l’ouverture ne change pas la valeur pour l’enregistrement. Par exemple, les opérations [de déménagement](../../mfc/reference/cdaorecordset-class.md#move) subséquentes n’utilisent pas la nouvelle valeur. La valeur par défaut est initialement définie lorsque le moteur de base de données est initialisé.

La valeur par défaut pour les délais d’attente des requêtes est tirée du registre Windows. S’il n’y a pas de paramètre de registre, la valeur par défaut est de 60 secondes. Toutes les bases de données ne prennent pas en charge la possibilité de définir une valeur de délai d’attente de requête. Si vous définissez une valeur d’arrêt de 0, aucun délai d’attente ne se produit; et la communication avec la base de données peut cesser de répondre. Ce comportement peut être utile pendant le développement. Si l’appel échoue, MFC lance une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

Pour plus d’informations connexes, voir le sujet "QueryTimeout Property" dans DAO Help.

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected

Appelez cette fonction de membre pour déterminer le nombre d’enregistrements affectés par l’appel le plus récent de la fonction de membre [Exécuter.](#execute)

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Valeur de retour

Un long integer contenant le nombre de dossiers touchés.

### <a name="remarks"></a>Notes

La valeur retournée comprend le nombre d’enregistrements supprimés, mis à `Execute`jour ou insérés par une requête d’action exécutée avec . Le nombre retourné ne reflétera pas les changements dans les tableaux connexes lorsque des mises à jour ou des suppressions en cascade sont en vigueur.

Pour obtenir des renseignements connexes, consultez le thème « RecordsAffected Property » dans DAO Help.

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a>CDaoDatabase::GetRelationCount

Appelez cette fonction de membre pour obtenir le nombre de relations définies entre les tableaux dans la base de données.

```
short GetRelationCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de relations définies entre les tableaux de la base de données.

### <a name="remarks"></a>Notes

`GetRelationCount`est utile si vous avez besoin de boucler toutes les relations définies dans la collection relations de la base de données. Pour obtenir des informations sur une relation donnée dans la collection, voir [GetRelationInfo](#getrelationinfo).

Pour illustrer le concept d’une relation, considérez une table fournisseurs et une table produits, qui pourrait avoir une relation unique. Dans cette relation, un fournisseur peut fournir plus d’un produit. D’autres relations sont en tête-à-tête et nombreuses.

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo

Appelez cette fonction de membre pour obtenir des informations sur une relation spécifiée dans la collection relations de la base de données.

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
L’index de l’objet relationnel dans la collection relations de la base de données, pour le suivi par index.

*relinfo (en)*<br/>
Une référence à un objet [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) qui renvoie les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur la relation à récupérer. Les options disponibles sont énumérées ici ainsi que ce qu’elles font revenir la fonction au sujet de la relation :

- AFX_DAO_PRIMARY_INFO (par défaut) Nom, Table, Table étrangère

- AFX_DAO_SECONDARY_INFO Attributs, Informations sur le terrain

L’information sur le terrain est un objet [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) contenant les champs de la table principale impliquée dans la relation.

*lpszName (en)*<br/>
Une chaîne contenant le nom de l’objet relationnel, pour le lookup par son nom.

### <a name="remarks"></a>Notes

Deux versions de cette fonction donnent accès soit par index, soit par nom. Pour une description de l’information retournée en *relinfo*, voir la structure [CDaoRelationInfo.](../../mfc/reference/cdaorelationinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Si vous demandez des informations à un niveau, vous obtenez également des informations à n’importe quel niveau antérieur ainsi.

> [!NOTE]
> Si vous définissez les attributs de l’objet de relation pour activer les opérations en cascade (ou),`dbRelationUpdateCascades` `dbRelationDeleteCascades`le moteur de base de données Microsoft Jet met à jour ou supprime automatiquement des enregistrements dans une ou plusieurs autres tables lorsque des modifications sont apportées aux tableaux clés primaires connexes. Supposons, par exemple, d’établir une relation de suppression en cascade entre une table de clients et une table de commandes. Lorsque vous supprimez les enregistrements du tableau des clients, les enregistrements dans le tableau des commandes liés à ce client sont également supprimés. En outre, si vous établissez des relations de suppression en cascade entre le tableau des commandes et d’autres tableaux, les enregistrements de ces tables sont automatiquement supprimés lorsque vous supprimez des enregistrements de la table des clients.

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a>CDaoDatabase::GetTableDefCount

Appelez cette fonction de membre pour récupérer le nombre de tables définies dans la base de données.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de dépôts définis dans la base de données.

### <a name="remarks"></a>Notes

`GetTableDefCount`est utile si vous avez besoin de boucler tous les numéros de dépôt dans la collection TableDefs de la base de données. Pour obtenir des informations sur un tableau donné dans la collection, voir [GetTableDefInfo](#gettabledefinfo).

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a>CDaoDatabase::GetTableDefInfo

Appelez cette fonction de membre pour obtenir divers types d’informations sur un tableau défini dans la base de données.

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
L’index de l’objet de dépôt dans la collection TableDefs de la base de données, pour le suivi par index.

*tabledefinfo*<br/>
Une référence à un objet [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) qui renvoie les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur la table à récupérer. Les options disponibles sont énumérées ici ainsi que ce qu’elles font revenir la fonction au sujet de la relation :

- AFX_DAO_PRIMARY_INFO (Par défaut) Nom, Updatable, Attributs

- AFX_DAO_SECONDARY_INFO informations primaires plus: Date Créée, Date Dernière mise à jour, Nom de table source, Connect

- AFX_DAO_ALL_INFO informations primaires et secondaires plus : Règle de validation, Texte de validation, Nombre d’enregistrement

*lpszName (en)*<br/>
Le nom de l’objet de dépôt, pour le lookup par son nom.

### <a name="remarks"></a>Notes

Deux versions de la fonction sont fournies afin que vous puissiez sélectionner un tableau soit par index dans la collection TableDefs de la base de données, soit par le nom de la table.

Pour une description de l’information retournée dans *le dépôt de l’information*, voir la structure [CDaoTableDefInfo.](../../mfc/reference/cdaotabledefinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Si vous demandez des informations à un niveau, vous obtenez des informations pour tous les niveaux antérieurs ainsi.

> [!NOTE]
> L’option AFX_DAO_ALL_INFO fournit des informations qui peuvent être lentes à obtenir. Dans ce cas, le comptage des dossiers dans le tableau pourrait prendre beaucoup de temps s’il y a beaucoup de dossiers.

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a>CDaoDatabase::GetVersion

Appelez cette fonction de membre pour déterminer la version du fichier de base de données Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui indique la version du fichier de base de données associé à l’objet.

### <a name="remarks"></a>Notes

La valeur retournée représente le numéro de version sous la forme "major.minor"; par exemple, "3.0". Le numéro de version du produit (par exemple, 3.0) se compose du numéro de version (3), d’une période et du numéro de sortie (0). Les versions à ce jour sont 1.0, 1.1, 2.0, et 3.0.

Pour obtenir des informations connexes, consultez le thème « Propriété de version » dans DAO Help.

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a>CDaoDatabase::IsOpen

Appelez cette fonction de `CDaoDatabase` membre pour déterminer si l’objet est actuellement ouvert sur une base de données.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CDaoDatabase` l’objet est actuellement ouvert; sinon 0.

### <a name="remarks"></a>Notes

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a>CDaoDatabase::m_pDAODatabase

Contient un pointeur vers l’interface OLE `CDaoDatabase` pour l’objet de base de données DAO sous-jacent à l’objet.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous avez besoin d’accéder à l’interface DAO directement.

Pour plus d’informations sur l’appel DAO directement, voir [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a>CDaoDatabase::m_pWorkspace

Contient un pointeur sur l’objet [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) qui contient l’objet de base de données.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous avez besoin d’accéder directement à l’espace de travail — par exemple, pour obtenir des indications sur d’autres objets de base de données dans la collection de bases de données de l’espace de travail.

## <a name="cdaodatabaseopen"></a><a name="open"></a>CDaoDatabase::Ouvert

Vous devez appeler cette fonction de `CDaoDatabase` membre pour initialiser un objet nouvellement construit qui représente une base de données existante.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Une expression de chaîne qui est le nom d’un Microsoft Jet existant (. Fichier de base de données MDB). Si le nom de fichier a une extension, il est nécessaire. Si votre réseau prend en charge la convention de nommage uniforme\\\\\\(UNC), vous pouvez également spécifier un parcours réseau, tel que « MYSERVER\\' MYSHARE\\'MYDIR\\'MYDB. MDB". (Doubles contre-coups de dos sont nécessaires\\dans les littérals de cordes parce que « est le caractère d’évasion de C.)

Certaines considérations s’appliquent lors de *l’utilisation de lpszName*. Si elle:

- Se référant à une base de données qui est déjà ouverte pour un accès exclusif par un autre utilisateur, MFC jette une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md). Pièger cette exception pour faire savoir à votre utilisateur que la base de données n’est pas disponible.

- Est une chaîne vide ("") et *lpszConnect* est "ODBC;", une boîte de dialogue énumérant tous les noms enregistrés source de données ODBC est affiché afin que l’utilisateur peut sélectionner une base de données. Vous devez éviter les connexions directes aux sources de données ODBC; utiliser une table jointe à la place.

- Sinon, ne se réfère pas à une base de données existante ou `CDaoException`valide ODBC nom source de données, MFC jette une exception de type .

> [!NOTE]
> Pour plus de détails sur les codes d’erreur DAO, voir le DAOERR. Fichier H. Pour plus d’informations, consultez le thème « Erreurs d’accès aux données trappables » dans DAO Help.

*bExclusive*<br/>
Une valeur Boolean qui est VRAI si la base de données doit être ouverte pour un accès exclusif (non partagé) et FALSE si la base de données doit être ouverte pour un accès partagé. Si vous ometez cet argument, la base de données est ouverte pour un accès partagé.

*bReadOnly*<br/>
Une valeur Boolean qui est VRAI si la base de données doit être ouverte pour l’accès à la lecture seulement et FALSE si la base de données doit être ouverte pour l’accès à la lecture/écriture. Si vous ometez cet argument, la base de données est ouverte pour l’accès à la lecture/à l’écriture. Tous les documents dépendants héritent de cet attribut.

*lpszConnect*<br/>
Une expression de chaîne utilisée pour ouvrir la base de données. Cette chaîne constitue les arguments de connexion ODBC. Vous devez fournir les arguments exclusifs et lus uniquement pour fournir une chaîne source. Si la base de données est une base de données Microsoft Jet (. MDB), cette chaîne est vide (""). La syntaxe pour la valeur par défaut — **_T**(« » — fournit la portabilité pour Unicode ainsi que les builds ANSI de votre application.

### <a name="remarks"></a>Notes

`Open`associe la base de données à l’objet DAO sous-jacent. Vous ne pouvez pas utiliser l’objet de base de données pour construire des objets d’enregistrement, de code de dépôt ou de requête jusqu’à ce qu’ils soient paralés. `Open`joint l’objet de base de données à la collection de bases de données de l’espace de travail associé.

Utilisez les paramètres comme suit :

- Si vous ouvrez un Microsoft Jet (. MDB) base de données, utilisez le paramètre *lpszName* et passez une chaîne vide pour le paramètre *lpszConnect* ou passez une chaîne de mot de passe du formulaire "; PWD-password" si la base de données est protégée par mot de passe (. Bases de données MDB uniquement).

- Si vous ouvrez une source de données ODBC, passez une chaîne de connexion ODBC valide dans *lpszConnect* et une chaîne vide en *lpszName*.

Pour plus d’informations connexes, voir le thème "OpenDatabase Method" dans DAO Help.

> [!NOTE]
> Pour de meilleures performances lors de l’accès aux bases de données externes, y compris les bases de données ISAM et les sources de données ODBC, il est recommandé de joindre des tables de base de données externes à une base de données du moteur Microsoft Jet (. MDB) plutôt que de se connecter directement à la source de données.

Il est possible pour une tentative de connexion de temps de temps si, par exemple, l’hôte DBMS n’est pas disponible. Si la tentative `Open` de connexion échoue, jette une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md).

Les remarques restantes ne s’appliquent qu’aux bases de données de l’ODBC :

Si la base de données est une base `Open` de données ODBC et que les paramètres de votre appel ne contiennent pas suffisamment d’informations pour effectuer la connexion, le pilote ODBC ouvre une boîte de dialogue pour obtenir les informations nécessaires de l’utilisateur. Lorsque vous `Open`appelez, votre chaîne de connexion, *lpszConnect*, est stocké en privé et est disponible en appelant la fonction membre [GetConnect.](#getconnect)

Si vous le souhaitez, vous pouvez ouvrir `Open` votre propre boîte de dialogue avant d’appeler pour obtenir des informations `Open`de l’utilisateur, comme un mot de passe, puis ajouter ces informations à la chaîne de connexion que vous passez à . Ou vous pouvez enregistrer la chaîne de connexion que vous passez (peut-être dans le `Open` registre `CDaoDatabase` Windows) afin que vous puissiez le réutiliser la prochaine fois que votre application appelle sur un objet.

Vous pouvez également utiliser la chaîne de connexion pour plusieurs `CDaoDatabase` niveaux d’autorisation de connexion (chacun pour un objet différent) ou pour transmettre d’autres informations spécifiques à la base de données.

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout

Appelez cette fonction de membre pour remplacer le nombre de secondes par défaut pour permettre avant les opérations ultérieures sur le temps d’inespérer de la base de données connectée.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Paramètres

*nSecondes*<br/>
Le nombre de secondes à prévoir avant qu’une tentative de requête ne s’évanouie.

### <a name="remarks"></a>Notes

Une opération peut s’éteindre en raison de problèmes d’accès au réseau, de temps de traitement excessif des requêtes, et ainsi de suite. Appelez `SetQueryTimeout` avant d’ouvrir votre jeu d’enregistrement ou avant d’appeler [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Mise à jour](../../mfc/reference/cdaorecordset-class.md#update), ou supprimer [les](../../mfc/reference/cdaorecordset-class.md#delete) fonctions des membres si vous souhaitez modifier la valeur d’un délai d’attente de requête. Le paramètre affecte `AddNew`tous `Update`les `Delete` [ouverts](../../mfc/reference/cdaorecordset-class.md#open)suivants , , `CDaoDatabase` et les appels à tous les enregistrements associés à cet objet. Changer la valeur d’un délai d’attente de requête pour un enregistrement après l’ouverture ne change pas la valeur pour l’enregistrement. Par exemple, les opérations [de déménagement](../../mfc/reference/cdaorecordset-class.md#move) subséquentes n’utilisent pas la nouvelle valeur.

La valeur par défaut pour les délais d’attente des requêtes est de 60 secondes. Toutes les bases de données ne prennent pas en charge la possibilité de définir une valeur de délai d’attente de requête. Si vous définissez une valeur d’arrêt de 0, aucun délai d’attente ne se produit; la communication avec la base de données peut cesser de répondre. Ce comportement peut être utile pendant le développement.

Pour plus d’informations connexes, voir le sujet "QueryTimeout Property" dans DAO Help.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Classe CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[Classe CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Classe CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Classe CDaoException](../../mfc/reference/cdaoexception-class.md)
