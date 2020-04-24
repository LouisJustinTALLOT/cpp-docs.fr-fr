---
title: Classe CDaoWorkspace
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: c492c806d64b1cfe0e4f73b3bb880ec7bd0a7e80
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754666"
---
# <a name="cdaoworkspace-class"></a>Classe CDaoWorkspace

Gère une session de base de données nommée et protégée par mot de passe, de la connexion à la déconnexion, pour un seul utilisateur. DAO est soutenu par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète.

## <a name="syntax"></a>Syntaxe

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Construit un objet d’espace de travail. Ensuite, appelez `Create` `Open`ou .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoWorkspace::Append](#append)|Annexe d’un espace de travail nouvellement créé à la collection Workspaces du moteur de base de données.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Commence une nouvelle transaction, qui s’applique à toutes les bases de données ouvertes dans l’espace de travail.|
|[CDaoWorkspace::Fermer](#close)|Ferme l’espace de travail et tous les objets qu’il contient. Les transactions en attente sont annulées.|
|[CDaoWorkspace::CommitTrans](#committrans)|Termine la transaction en cours et enregistre les modifications.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Compacte (ou doublons) une base de données.|
|[CDaoWorkspace::Créer](#create)|Crée un nouvel objet d’espace de travail DAO.|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Retourne le nombre d’objets de base de données DAO dans la collection de bases de données de l’espace de travail.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Renvoie des informations sur une base de données DAO spécifiée définie dans la collection de bases de données de l’espace de travail.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Retourne l’emplacement des paramètres d’initialisation du moteur de base de données Microsoft Jet dans le registre Windows.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Retourne une valeur qui indique si les transactions multiples impliquant la même source de données ODBC sont isolées par le biais de connexions multiples forcées à la source de données.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Retourne le nombre de secondes avant qu’une erreur ne se produise lorsque l’utilisateur tente de se connecter à une base de données ODBC.|
|[CDaoWorkspace::GetName](#getname)|Renvoie le nom défini par l’utilisateur pour l’objet de l’espace de travail.|
|[CDaoWorkspace::GetUserName](#getusername)|Renvoie le nom d’utilisateur spécifié lors de la création de l’espace de travail. C’est le nom du propriétaire de l’espace de travail.|
|[CDaoWorkspace::GetVersion](#getversion)|Retourne une chaîne qui contient la version du moteur de base de données associé à l’espace de travail.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Retourne le nombre d’objets d’espace de travail DAO dans la collection Workspaces du moteur de base de données.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Renvoie des informations sur un espace de travail DAO spécifié défini dans la collection d’espaces de travail du moteur de base de données.|
|[CDaoWorkspace::Idle](#idle)|Permet au moteur de base de données d’effectuer des tâches d’arrière-plan.|
|[CDaoWorkspace::IsOpen](#isopen)|Retourne nonzero si l’espace de travail est ouvert.|
|[CDaoWorkspace::Ouvert](#open)|Ouvre explicitement un objet d’espace de travail associé à l’espace de travail par défaut de DAO.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Tentatives de réparation d’une base de données endommagée.|
|[CDaoWorkspace::Rollback](#rollback)|Termine la transaction en cours et n’enregistre pas les modifications.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Définit le mot de passe que le moteur de base de données utilise lorsqu’un objet d’espace de travail est créé sans mot de passe spécifique.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Définit le nom d’utilisateur que le moteur de base de données utilise lorsqu’un objet d’espace de travail est créé sans nom d’utilisateur spécifique.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Définit l’emplacement des paramètres d’initialisation du moteur de base de données Microsoft Jet dans le registre Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Précise si les transactions multiples impliquant la même source de données ODBC sont isolées en forçant plusieurs connexions à la source de données.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Définit le nombre de secondes avant qu’une erreur ne se produise lorsque l’utilisateur tente de se connecter à une source de données ODBC.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Points à l’objet d’espace de travail DAO sous-jacent.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, vous n’aurez pas besoin de plusieurs espaces de travail, et vous n’aurez pas besoin de créer des objets explicites d’espace de travail ; lorsque vous ouvrez des objets de base de données et d’enregistrements, ils utilisent l’espace de travail par défaut de DAO. Toutefois, si nécessaire, vous pouvez exécuter plusieurs sessions à la fois en créant des objets supplémentaires dans un espace de travail. Chaque objet d’espace de travail peut contenir plusieurs objets de base de données ouverts dans sa propre collection de bases de données. Dans MFC, un espace de travail est avant tout un gestionnaire de transaction, spécifiant un ensemble de bases de données ouvertes toutes dans le même « espace de transaction ».

> [!NOTE]
> Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur la connectivité open Database (ODBC). Tous les noms de classe de base de données DAO ont un préfixe "CDao". En général, les classes MFC basées sur DAO sont plus capables que les classes MFC basées sur ODBC. Les classes basées sur DAO accèdent aux données via le moteur de base de données Microsoft Jet, y compris les pilotes ODBC. Ils prennent également en charge les opérations de langage de définition des données (DDL), telles que la création de bases de données et l’ajout de tables et de champs via les classes, sans avoir à appeler directement DAO.

## <a name="capabilities"></a>Fonctionnalités

La `CDaoWorkspace` classe fournit ce qui suit :

- Accès explicite, si nécessaire, à un espace de travail par défaut, créé en initialisant le moteur de base de données. Habituellement, vous utilisez l’espace de travail par défaut de DAO implicitement en créant des objets de base de données et d’enregistrements.

- Un espace de transaction dans lequel les transactions s’appliquent à toutes les bases de données ouvertes dans l’espace de travail. Vous pouvez créer des espaces de travail supplémentaires pour gérer des espaces de transaction distincts.

- Une interface à de nombreuses propriétés du moteur de base de données Microsoft Jet sous-jacent (voir les fonctions des membres statiques). Ouvrir ou créer un espace de travail, ou appeler une fonction de membre statique avant d’ouvrir ou de créer, initialise le moteur de base de données.

- Accès à la collection Workspaces du moteur de base de données, qui stocke tous les espaces de travail actifs qui lui ont été annexés. Vous pouvez également créer et travailler avec des espaces de travail sans les envoyer à la collection.

## <a name="security"></a>Sécurité

MFC ne met pas en œuvre les collections Utilisateurs et Groupes dans DAO, qui sont utilisés pour le contrôle de sécurité. Si vous avez besoin de ces aspects de DAO, vous devez les programmer vous-même via des appels directs vers les interfaces DAO. Pour plus d’informations, voir [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Usage

Vous pouvez `CDaoWorkspace` utiliser la classe pour :

- Ouvrez explicitement l’espace de travail par défaut.

   Habituellement, votre utilisation de l’espace de travail par défaut est implicite - lorsque vous ouvrez de nouveaux objets [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) ou [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Mais vous devrez peut-être y accéder explicitement — par exemple, pour accéder aux propriétés des moteurs de base de données ou à la collection Workspaces. Voir "Utilisation implicite de l’espace de travail par défaut" ci-dessous.

- Créez de nouveaux espaces de travail. Appelez [l’annexe](#append) si vous souhaitez les ajouter à la collection Workspaces.

- Ouvrez un espace de travail existant dans la collection Workspaces.

La création d’un nouvel espace de travail qui n’existe pas déjà dans la collection Workspaces est décrite sous la fonction [membre Create.](#create) Les objets d’espace de travail ne persistent en aucune façon entre les sessions de moteur datababase. Si votre application relie MFC de façon statique, la fin de l’application uninitialise le moteur de base de données. Si votre application se connecte dynamiquement avec MFC, le moteur de base de données est uninitialisé lorsque le MFC DLL est déchargé.

L’ouverture explicite de l’espace de travail par défaut, ou l’ouverture d’un espace de travail existant dans la collection d’espaces de travail, est décrite sous la fonction membre [Open.](#open)

Terminez une séance d’espace de travail en fermant l’espace de travail avec la fonction [membre Close.](#close) `Close`ferme toutes les bases de données que vous n’avez pas fermées auparavant, en re retourant toute transaction non engagée.

## <a name="transactions"></a>Transactions

DAO gère les transactions au niveau de l’espace de travail; par conséquent, les transactions sur un espace de travail avec plusieurs bases de données ouvertes s’appliquent à toutes les bases de données. Par exemple, si deux bases de données ont des mises à jour non engagées et que vous appelez [CommitTrans,](#committrans)toutes les mises à jour sont validées. Si vous souhaitez limiter les transactions à une seule base de données, vous avez besoin d’un objet d’espace de travail distinct pour cela.

## <a name="implicit-use-of-the-default-workspace"></a>Utilisation implicite de l’espace de travail par défaut

MFC utilise implicitement l’espace de travail par défaut de DAO dans les circonstances suivantes :

- Si vous créez `CDaoDatabase` un nouvel objet mais `CDaoWorkspace` ne le faites pas à travers un objet existant, MFC crée pour vous un objet d’espace de travail temporaire, qui correspond à l’espace de travail par défaut de DAO. Si vous le faites pour plusieurs bases de données, tous les objets de base de données sont associés à l’espace de travail par défaut. Vous pouvez accéder à l’espace `CDaoDatabase` de travail d’une base de données par l’intermédiaire d’un membre des données.

- De même, si `CDaoRecordset` vous créez un objet `CDaoDatabase` sans fournir un pointeur à un objet, MFC crée un objet de base de données temporaire et, par extension, un objet temporaire d’espace de travail. Vous pouvez accéder à la base de données d’un `CDaoRecordset` jeu de données, et indirectement à son espace de travail, par l’intermédiaire d’un membre des données.

## <a name="other-operations"></a>Autres opérations

D’autres opérations de base de données sont également fournies, comme la réparation d’une base de données corrompue ou le compactage d’une base de données.

Pour plus d’informations sur l’appel d’ici et sur la sécurité DAO, voir [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="cdaoworkspaceappend"></a><a name="append"></a>CDaoWorkspace::Append

Appelez cette fonction de membre après avoir appelé [Create](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Notes

`Append`joint un objet d’espace de travail nouvellement créé à la collection Workspaces du moteur de base de données. Les espaces de travail ne persistent pas entre les séances de moteur de base de données; ils ne sont stockés que dans la mémoire, pas sur le disque. Vous n’avez pas à ajouter un espace de travail; si vous ne le faites pas, vous pouvez toujours l’utiliser.

Un espace de travail annexé reste dans la collection Workspaces, dans un état actif et ouvert, jusqu’à ce que vous appeliez sa fonction de membre [Close.](#close)

Pour plus d’informations connexes, consultez le thème « Méthode d’annexe » dans DAO Help.

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a>CDaoWorkspace::BeginTrans

Appelez cette fonction de membre pour lancer une transaction.

```cpp
void BeginTrans();
```

### <a name="remarks"></a>Notes

Après votre `BeginTrans`appel, les mises à jour que vous effectuez à votre structure de données ou de base de données prennent effet lorsque vous commedez la transaction. Étant donné que l’espace de travail définit un espace de transaction unique, la transaction s’applique à toutes les bases de données ouvertes dans l’espace de travail. Il y a deux façons de conclure la transaction :

- Appelez la fonction membre [CommitTrans](#committrans) pour valider la transaction et enregistrer les modifications apportées à la source de données.

- Ou appelez la fonction membre [Rollback](#rollback) pour annuler la transaction.

La fermeture de l’objet de l’espace de travail ou d’un objet de base de données pendant qu’une transaction est en attente annule toutes les transactions en attente.

Si vous avez besoin d’isoler les transactions sur une source de données ODBC à partir de celles d’une autre source de données ODBC, consultez la fonction membre [SetIsolateODBCTrans.](#setisolateodbctrans)

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

Construit un objet `CDaoWorkspace`.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Notes

Après la construction de l’objet C, vous avez deux options :

- Appelez la fonction de membre [Open](#open) de l’objet pour ouvrir l’espace de travail par défaut ou pour ouvrir un objet existant dans la collection Workspaces.

- Ou appelez la fonction membre [Create](#create) de l’objet pour créer un nouvel objet d’espace de travail DAO. Cela démarre explicitement une nouvelle session d’espace `CDaoWorkspace` de travail, à laquelle vous pouvez vous référer via l’objet. Après `Create`avoir appelé , vous pouvez appeler [Append](#append) si vous souhaitez ajouter l’espace de travail à la collection d’espaces de travail du moteur de base de données.

Consultez l’aperçu de la classe pour [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) `CDaoWorkspace` pour plus d’informations sur le moment où vous devez créer explicitement un objet. Habituellement, vous utilisez des espaces de travail créés implicitement lorsque vous ouvrez un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) sans spécifier un espace de travail ou lorsque vous ouvrez un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) sans spécifier un objet de base de données. Les objets MFC DAO créés de cette façon utilisent l’espace de travail par défaut de DAO, qui est créé une fois et réutilisé.

Pour libérer un espace de travail et ses objets contenus, appelez la fonction de membre [Close](#close) de l’objet de l’espace de travail.

## <a name="cdaoworkspaceclose"></a><a name="close"></a>CDaoWorkspace::Fermer

Appelez cette fonction de membre pour fermer l’objet d’espace de travail.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

La fermeture d’un objet d’espace de travail ouvert libère l’objet DAO sous-jacent et, si l’espace de travail est membre de la collection Workspaces, l’enlève de la collection. L’appel `Close` est une bonne pratique de programmation.

> [!CAUTION]
> La fermeture d’un objet d’espace de travail ferme toutes les bases de données ouvertes dans l’espace de travail. Il en résulte que tous les enregistrements s’ouvrent dans les bases de données étant fermés ainsi, et toutes les modifications ou mises à jour en attente sont annulées. Pour plus d’informations, voir la [base de CDaoData::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close), et [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) member functions.

Les objets d’espace de travail ne sont pas permanents; elles n’existent que pendant qu’il y a des références à ces personnes. Cela signifie que lorsque la session du moteur de base de données se termine, l’espace de travail et sa collection de bases de données ne persistent pas. Vous devez les recréer pour la prochaine session en ouvrant à nouveau votre espace de travail et votre base de données.

Pour obtenir des informations connexes, consultez le thème « Méthode de clôture » dans DAO Help.

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a>CDaoWorkspace::CommitTrans

Appelez cette fonction membre pour valider une transaction — enregistrez un groupe de modifications et mises à jour dans une ou plusieurs bases de données dans l’espace de travail.

```cpp
void CommitTrans();
```

### <a name="remarks"></a>Notes

Une transaction consiste en une série de modifications apportées aux données de la base de données ou à sa structure, en commençant par un appel à [BeginTrans](#begintrans). Lorsque vous effectuez la transaction, soit la validez ou la annulez (annuler les modifications) avec [Rollback](#rollback). Par défaut, sans transaction, les mises à jour des enregistrements sont validées immédiatement. L’appel `BeginTrans` entraîne un retard de `CommitTrans`l’engagement des mises à jour jusqu’à ce que vous appeliez .

> [!CAUTION]
> Dans un espace de travail, les transactions sont toujours globales à l’espace de travail et ne sont pas limitées à une seule base de données ou un enregistrement. Si vous effectuez des opérations sur plus d’une `CommitTrans` base de données ou `Rollback` un ensemble d’enregistrements dans le cadre d’une transaction d’espace de travail, engage toutes les mises à jour en attente et restaure toutes les opérations de ces bases de données et enregistrements.

Lorsque vous fermez une base de données ou un espace de travail avec des transactions en attente, les transactions sont toutes annulées.

> [!NOTE]
> Il ne s’agit pas d’un mécanisme d’engagement en deux phases. Si une mise à jour ne s’engage pas, d’autres s’engageront toujours.

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase

Appelez cette fonction de membre pour compacter un Microsoft Jet spécifié (. base de données MDB).

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Paramètres

*lpszSrcName (en)*<br/>
Le nom d’une base de données existante et fermée. Il peut s’agir d’un chemin complet\\et d’un nom de fichier, tels que « C : MYDB. MDB". Si le nom de fichier dispose d’une extension, vous devez le spécifier. Si votre réseau prend en charge la convention de nommage uniforme\\\\\\(UNC), vous pouvez également spécifier un parcours réseau, tel que « MYSERVER\\' MYSHARE\\'MYDIR\\'MYDB. MDB". (Doubles contre-coups de relique sont nécessaires\\dans les cordes du chemin parce que « est le caractère d’évasion de C.)

*lpszDestName*<br/>
Le chemin complet de la base de données compactée que vous créez. Vous pouvez également spécifier un parcours réseau comme avec *lpszSrcName*. Vous ne pouvez pas utiliser *l’argument lpszDestName* pour spécifier le même fichier de base de données que *lpszSrcName*.

*lpszPassword (lpszPassword)*<br/>
Un mot de passe, utilisé lorsque vous souhaitez compacter une base de données protégée par mot de passe. Notez que si vous `CompactDatabase` utilisez la version de ce mot de passe, vous devez fournir tous les paramètres. En outre, parce qu’il s’agit d’un paramètre de connexion, il nécessite un formatage spécial, comme suit: ; PWD *lpszPassword*. Par exemple : ; PWD "Heureux". (Le premier point-virgule est nécessaire.)

*lpszLocale*<br/>
Une expression de chaîne utilisée pour spécifier l’ordre de collecte pour créer *lpszDestName*. Si vous ometez cet argument en `dbLangGeneral` acceptant la valeur par défaut de (voir ci-dessous), le local de la nouvelle base de données est le même que celui de l’ancienne base de données. Les valeurs possibles sont les suivantes :

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

*nOptions*<br/>
Indique une ou plusieurs options pour la base de données cible, *lpszDestName*. Si vous omettez cet argument en acceptant la valeur par défaut, le *lpszDestName* aura le même chiffrement et la même version que *lpszSrcName*. Vous pouvez `dbEncrypt` combiner `dbDecrypt` l’option ou l’une des options de version à l’aide de l’opérateur bitwise-OR. Les valeurs possibles, qui spécifient un format de base de données, et non une version moteur de base de données, sont les suivante :

- `dbEncrypt`Chiffrez la base de données lors du compactage.

- `dbDecrypt`Décryptez la base de données lors du compactage.

- `dbVersion10`Créez une base de données qui utilise la version moteur de base de données Microsoft Jet 1.0 tout en compactant.

- `dbVersion11`Créez une base de données qui utilise la version moteur de base de données Microsoft Jet 1.1 tout en compactant.

- `dbVersion20`Créez une base de données qui utilise la version moteur de base de données Microsoft Jet 2.0 tout en compactant.

- `dbVersion30`Créez une base de données qui utilise la version moteur de base de données Microsoft Jet 3.0 tout en compactant.

Vous pouvez `dbEncrypt` `dbDecrypt` utiliser ou dans l’argument des options pour spécifier s’il faut chiffrer ou déchiffrer la base de données au fur et à mesure qu’elle est compactée. Si vous omettez une constante `dbDecrypt` de `dbEncrypt`chiffrement ou si vous incluez les deux et , *lpszDestName* aura le même cryptage que *lpszSrcName*. Vous pouvez utiliser l’une des constantes de la version dans l’argument des options pour spécifier la version du format de données pour la base de données compactée. Cette constante n’affecte que la version du format de données de *lpszDestName*. Vous ne pouvez spécifier qu’une seule version constante. Si vous omettez une version constante, *lpszDestName* aura la même version que *lpszSrcName*. Vous pouvez compacter *lpszDestName* uniquement à une version qui est la même ou plus tard que celle de *lpszSrcName*.

> [!CAUTION]
> Si une base de données n’est pas cryptée, il est possible, même si vous implémentez la sécurité utilisateur/mot de passe, de lire directement le fichier disque binaire qui constitue la base de données.

### <a name="remarks"></a>Notes

Lorsque vous modifiez des données dans une base de données, le fichier de base de données peut se fragmenter et utiliser plus d’espace disque que nécessaire. Périodiquement, vous devez compacter votre base de données pour défrayer le fichier de base de données. La base de données compactée est généralement plus petite. Vous pouvez également choisir de modifier l’ordre de collecte, le chiffrement ou la version du format de données pendant que vous copiez et compactez la base de données.

> [!CAUTION]
> La `CompactDatabase` fonction membre ne convertira pas correctement une base de données Complète Microsoft Access d’une version à une autre. Seul le format de données est converti. Les objets définis par Microsoft Access, tels que les formulaires et les rapports, ne sont pas convertis. Cependant, les données sont correctement converties.

> [!TIP]
> Vous pouvez `CompactDatabase` également utiliser pour copier un fichier de base de données.

Pour plus d’informations sur les bases de données de compactage, voir le thème "Méthode De base de données compactes" dans DAO Help.

## <a name="cdaoworkspacecreate"></a><a name="create"></a>CDaoWorkspace::Créer

Appelez cette fonction de membre pour créer un nouvel objet `CDaoWorkspace` d’espace de travail DAO et l’associer à l’objet MFC.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Une chaîne avec jusqu’à 14 caractères qui nomme uniquement le nouvel objet d’espace de travail. Vous devez fournir un nom. Pour obtenir des informations connexes, consultez le thème « Propriété du nom » dans DAO Help.

*lpszUserName*<br/>
Le nom d’utilisateur du propriétaire de l’espace de travail. Pour les exigences, consultez le paramètre *lpszDefaultUser* de la fonction membre [SetDefaultUser.](#setdefaultuser) Pour plus d’informations connexes, consultez le thème "UserName Property" dans DAO Help.

*lpszPassword (lpszPassword)*<br/>
Le mot de passe pour le nouvel objet d’espace de travail. Un mot de passe peut être jusqu’à 14 caractères de long et peut contenir n’importe quel personnage sauf ASCII 0 (null). Les mots de passe respectent la casse. Pour obtenir des informations connexes, consultez le thème « Propriété de mot de passe » dans DAO Help.

### <a name="remarks"></a>Notes

Le processus global de création est :

1. Construire un objet [CDaoWorkspace.](#cdaoworkspace)

1. Appelez la fonction `Create` membre de l’objet pour créer l’espace de travail DAO sous-jacent. Vous devez spécifier un nom d’espace de travail.

1. Appelez Optionnellement [Annexe](#append) si vous souhaitez ajouter l’espace de travail à la collection d’espaces de travail du moteur de base de données. Vous pouvez travailler avec l’espace de travail sans l’en dépenser.

Après `Create` l’appel, l’objet de l’espace de travail est en état d’ouverture, prêt à l’emploi. Vous `Open` n’appelez `Create`pas après . Vous n’appelez `Create` pas si l’espace de travail existe déjà dans la collection Workspaces. `Create`initialise le moteur de base de données s’il n’a pas déjà été parasécé pour votre application.

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a>CDaoWorkspace::GetDatabaseCount

Appelez cette fonction membre pour récupérer le nombre d’objets de base de données DAO dans la collection de bases de données de l’espace de travail — le nombre de bases de données ouvertes dans l’espace de travail.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de bases de données ouvertes dans l’espace de travail.

### <a name="remarks"></a>Notes

`GetDatabaseCount`est utile si vous avez besoin de boucler toutes les bases de données définies dans la collection de bases de données de l’espace de travail. Pour obtenir des informations sur une base de données donnée dans la collection, voir [GetDatabaseInfo](#getdatabaseinfo). L’utilisation typique `GetDatabaseCount` est d’appeler pour le nombre de bases de données `GetDatabaseInfo`ouvertes, puis utiliser ce numéro comme un indice de boucle pour les appels répétés à .

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a>CDaoWorkspace::GetDatabaseInfo

Appelez cette fonction de membre pour obtenir divers types d’informations sur une base de données ouverte dans l’espace de travail.

```cpp
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index zéro de l’objet de base de données dans la collection de bases de données de l’espace de travail, pour la recherche par index.

*dbinfo dbinfo*<br/>
Une référence à un objet [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) qui renvoie les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur la base de données à récupérer. Les options disponibles sont énumérées ici ainsi que ce qu’elles causent le retour de la fonction :

- AFX_DAO_PRIMARY_INFO (Par défaut) Nom, Updatable, Transactions

- AFX_DAO_SECONDARY_INFO Informations primaires plus: Version, Collating Order, Query Timeout

- AFX_DAO_ALL_INFO informations primaires et secondaires plus : Connectez-vous

*lpszName (en)*<br/>
Le nom de l’objet de base de données, pour le lookup par nom. Le nom est une chaîne avec jusqu’à 14 caractères qui nomme uniquement le nouvel objet d’espace de travail.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher une base de données par index. L’autre version vous permet de rechercher une base de données par nom.

Pour une description de l’information retournée dans *dbinfo*, voir la structure [CDaoDatabaseInfo.](../../mfc/reference/cdaodatabaseinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous obtenez des informations pour tous les niveaux antérieurs ainsi.

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a>CDaoWorkspace::GetIniPath

Appelez cette fonction de membre pour obtenir l’emplacement des paramètres d’initialisation du moteur de base de données Microsoft Jet dans le registre Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’emplacement du registre.

### <a name="remarks"></a>Notes

Vous pouvez utiliser l’emplacement pour obtenir des informations sur les paramètres du moteur de base de données. L’information retournée est en fait le nom d’un sous-clé de registre.

Pour plus d’informations connexes, consultez les thèmes «IniPath Property» et «Customizing Windows Registry Settings for Data Access» dans DAO Help.

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

Appelez cette fonction de membre pour obtenir la valeur actuelle de la propriété DAO IsolateODBCTrans pour l’espace de travail.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les transactions ODBC sont isolées; sinon 0.

### <a name="remarks"></a>Notes

Dans certaines situations, vous devrez peut-être avoir plusieurs transactions simultanées en attente sur la même base de données ODBC. Pour ce faire, vous devez ouvrir un espace de travail séparé pour chaque transaction. Gardez à l’esprit que même si chaque espace de travail peut avoir sa propre connexion ODBC à la base de données, cela ralentit les performances du système. Étant donné que l’isolement des transactions n’est normalement pas nécessaire, les connexions ODBC à partir de plusieurs objets d’espace de travail ouverts par le même utilisateur sont partagées par défaut.

Certains serveurs ODBC, tels que Microsoft SQL Server, n’autorisent pas les transactions simultanées sur une seule connexion. Si vous avez besoin d’avoir plus d’une transaction à la fois en attente contre une telle base de données, définissez la propriété IsolateODBCTrans à TRUE sur chaque espace de travail dès que vous l’ouvrez. Cela force une connexion ODBC séparée pour chaque espace de travail.

Pour plus d’informations connexes, voir le sujet "IsolateODBCTrans Property" dans DAO Help.

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a>CDaoWorkspace::GetLoginTimeout

Appelez cette fonction de membre pour obtenir la valeur actuelle de la propriété DAO LoginTimeout pour l’espace de travail.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de secondes avant qu’une erreur se produise lorsque vous tentez de vous connecter à une base de données ODBC.

### <a name="remarks"></a>Notes

Cette valeur représente le nombre de secondes avant qu’une erreur ne se produise lorsque vous tentez de vous connecter à une base de données ODBC. Le paramètre LoginTimeout par défaut est de 20 secondes. Lorsque LoginTimeout est réglé à 0, aucun délai d’attente ne se produit et la communication avec la source de données peut cesser de répondre.

Lorsque vous tentez de vous connecter à une base de données ODBC, comme Microsoft SQL Server, la connexion peut échouer en raison d’erreurs de réseau ou parce que le serveur ne s’exécute pas. Plutôt que d’attendre que la valeur par défaut se connecte, vous pouvez spécifier combien de temps le moteur de base de données attend avant de produire une erreur. L’enregistrement au serveur se produit implicitement dans le cadre d’un certain nombre d’événements différents, tels que l’exécution d’une requête sur une base de données serveur externe.

Pour plus d’informations connexes, consultez le thème "LoginTimeout Property" dans DAO Help.

## <a name="cdaoworkspacegetname"></a><a name="getname"></a>CDaoWorkspace::GetName

Appelez cette fonction de membre pour obtenir le nom défini `CDaoWorkspace` par l’utilisateur de l’objet d’espace de travail DAO sous-jacent à l’objet.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom défini par l’utilisateur de l’objet d’espace de travail DAO.

### <a name="remarks"></a>Notes

Le nom est utile pour accéder à l’objet d’espace de travail DAO dans la collection Workspaces du moteur de base de données par son nom.

Pour obtenir des informations connexes, consultez le thème « Propriété du nom » dans DAO Help.

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a>CDaoWorkspace::GetUserName

Appelez cette fonction de membre pour obtenir le nom du propriétaire de l’espace de travail.

```
CString GetUserName();
```

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui représente le propriétaire de l’objet de l’espace de travail.

### <a name="remarks"></a>Notes

Pour obtenir ou définir les autorisations pour le propriétaire de l’espace de travail, appelez DAO directement pour vérifier le réglage de la propriété Permissions; cela détermine les autorisations de cet utilisateur. Pour travailler avec des autorisations, vous avez besoin d’un SYSTEM. Fichier MDA.

Pour plus d’informations sur l’appel DAO directement, voir [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Pour plus d’informations connexes, consultez le thème "UserName Property" dans DAO Help.

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a>CDaoWorkspace::GetVersion

Appelez cette fonction de membre pour déterminer la version du moteur de base de données Microsoft Jet utilisé.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui indique la version du moteur de base de données associé à l’objet.

### <a name="remarks"></a>Notes

La valeur retournée représente le numéro de version sous la forme "major.minor"; par exemple, "3.0". Le numéro de version du produit (par exemple, 3.0) se compose du numéro de version (3), d’une période et du numéro de sortie (0).

Pour obtenir des informations connexes, consultez le thème « Propriété de version » dans DAO Help.

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

Appelez cette fonction de membre pour récupérer le nombre d’objets d’espace de travail DAO dans la collection d’espaces de travail du moteur de base de données.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’espaces de travail ouverts dans la collection Workspaces.

### <a name="remarks"></a>Notes

Ce décompte n’inclut pas les espaces de travail ouverts qui ne sont pas annexés à la collection. `GetWorkspaceCount`est utile si vous avez besoin de boucler tous les espaces de travail définis dans la collection d’espaces de travail. Pour obtenir des informations sur un espace de travail donné dans la collection, voir [GetWorkspaceInfo](#getworkspaceinfo). L’utilisation typique `GetWorkspaceCount` est d’appeler pour le nombre d’espaces de travail `GetWorkspaceInfo`ouverts, puis utiliser ce numéro comme un indice de boucle pour les appels répétés à .

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

Appelez cette fonction de membre pour obtenir divers types d’informations sur un espace de travail ouvert dans la session.

```cpp
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index zéro de l’objet de base de données dans la collection Workspaces, pour la recherche par index.

*wkspcinfo*<br/>
Une référence à un objet [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) qui renvoie les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur l’espace de travail à récupérer. Les options disponibles sont énumérées ici ainsi que ce qu’elles causent le retour de la fonction :

- nom AFX_DAO_PRIMARY_INFO (par défaut)

- AFX_DAO_SECONDARY_INFO informations primaires plus: Nom de l’utilisateur

- AFX_DAO_ALL_INFO informations primaires et secondaires plus: Isolate ODBCTrans

*lpszName (en)*<br/>
Le nom de l’objet de l’espace de travail, pour le lookup par nom. Le nom est une chaîne avec jusqu’à 14 caractères qui nomme uniquement le nouvel objet d’espace de travail.

### <a name="remarks"></a>Notes

Pour une description de l’information retournée dans *wkspcinfo*, voir la structure [CDaoWorkspaceInfo.](../../mfc/reference/cdaoworkspaceinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous obtenez également des informations pour les niveaux antérieurs.

## <a name="cdaoworkspaceidle"></a><a name="idle"></a>CDaoWorkspace::Idle

Appelez `Idle` pour fournir au moteur de base de données la possibilité d’effectuer des tâches d’arrière-plan qui peuvent ne pas être à jour en raison d’un traitement intense des données.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Paramètres

*nAction*<br/>
Une mesure à prendre pendant le traitement au ralenti. Actuellement, la seule `dbFreeLocks`action valide est .

### <a name="remarks"></a>Notes

Cela est souvent vrai dans les environnements multi-usiers multitâche dans lesquels il n’y a pas assez de temps de traitement de fond pour tenir tous les enregistrements dans un courant de registre.

> [!NOTE]
> L’appel `Idle` n’est pas nécessaire avec des bases de données créées avec la version 3.0 du moteur de base de données Microsoft Jet. Utilisez `Idle` uniquement pour les bases de données créées avec des versions antérieures.

Habituellement, les verrous de lecture sont supprimés et les données dans les objets de type dynaset locaux n’est mise à jour que lorsqu’aucune autre action (y compris les mouvements de souris) ne se produit. Si vous appelez `Idle`périodiquement, vous fournissez au moteur de base de données le temps de rattraper les tâches de traitement de fond en libérant des verrous de lecture non éteillés. Spécifier la `dbFreeLocks` constante comme un argument retarde le traitement jusqu’à ce que toutes les serrures de lecture sont libérées.

Cette fonction de membre n’est pas nécessaire dans les environnements d’utilisateur unique à moins que plusieurs instances d’une application ne s’exécutent. La `Idle` fonction membre peut augmenter les performances dans un environnement multi-utilisateurs parce qu’elle force le moteur de base de données à rincer les données au disque, libérant des verrous sur la mémoire. Vous pouvez également publier des verrous de lecture en faisant des opérations une partie d’une transaction.

Pour plus d’informations connexes, consultez le thème « Méthode d’oisiveté » dans DAO Help.

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a>CDaoWorkspace::IsOpen

Appelez cette fonction de `CDaoWorkspace` membre pour déterminer si l’objet est ouvert — c’est-à-dire si l’objet MFC a été para initialisé par un appel à [l’ouverture](#open) ou un appel à [créer](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet de l’espace de travail est ouvert; sinon 0.

### <a name="remarks"></a>Notes

Vous pouvez appeler n’importe laquelle des fonctions membres d’un espace de travail qui est dans un état ouvert.

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a>CDaoWorkspace::m_pDAOWorkspace

Un pointeur vers l’objet d’espace de travail DAO sous-jacent.

### <a name="remarks"></a>Notes

Utilisez ce membre de données si vous avez besoin d’un accès direct à l’objet DAO sous-jacent. Vous pouvez appeler les interfaces de l’objet DAO à travers ce pointeur.

Pour plus d’informations sur l’accès aux objets DAO directement, voir [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaoworkspaceopen"></a><a name="open"></a>CDaoWorkspace::Ouvert

Ouvre explicitement un objet d’espace de travail associé à l’espace de travail par défaut de DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom de l’objet DAO espace de travail à ouvrir - une chaîne avec jusqu’à 14 caractères qui nomme uniquement l’espace de travail. Acceptez la valeur par défaut NULL pour ouvrir explicitement l’espace de travail par défaut. Pour les exigences de nommage, voir le paramètre *lpszName* pour [Créer](#create). Pour obtenir des informations connexes, consultez le thème « Propriété du nom » dans DAO Help.

### <a name="remarks"></a>Notes

Après la `CDaoWorkspace` construction d’un objet, appelez cette fonction de membre pour faire l’un des éléments suivants :

- Ouvrez explicitement l’espace de travail par défaut. Pass NULL pour *lpszName*.

- Ouvrez `CDaoWorkspace` un objet existant, membre de la collection Workspaces, par son nom. Passez un nom valide pour un objet existant dans un espace de travail.

`Open`met l’objet d’espace de travail dans un état ouvert et initialise également le moteur de base de données s’il n’a pas déjà été paralé pour votre application.

Bien `CDaoWorkspace` que de nombreuses fonctions de membre ne puissent être appelées qu’après l’ouverture de l’espace de travail, les `Open`fonctions suivantes des membres, qui fonctionnent sur le moteur de base de données, sont disponibles après la construction de l’objet C, mais avant un appel à :

||||
|-|-|-|
|[Créer](#create)|[GetVersion (getVersion)](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath GetIniPath (en anglais)](#getinipath)|[Idle](#idle)|[SetIniPath SetIniPath](#setinipath)|
|[GetLoginTimeout (en)](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout SetLoginTimeout SetLoginTimeout SetLog](#setlogintimeout)|

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

Appelez cette fonction de membre si vous avez besoin de tenter de réparer une base de données corrompue qui accède au moteur de base de données Microsoft Jet.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom de voie et de fichier pour un fichier de base de données moteur Microsoft Jet existant. Si vous ometez le chemin, seul le répertoire actuel est recherché. Si votre système prend en charge la convention de nommage uniforme\\\\\\(UNC),\\vous\\pouvez également spécifier un chemin réseau, tel que : « MYSERVER 'MYSHARE 'MYDIR\\'MYDB. MDB". (Double backslashes sont nécessaires dans\\la chaîne de chemin parce que " est le caractère d’évasion C.)

### <a name="remarks"></a>Notes

Vous devez fermer la base de données spécifiée par *lpszName* avant de la réparer. Dans un environnement multi-utilisateurs, d’autres utilisateurs ne peuvent pas avoir *lpszName* ouvert pendant que vous le réparez. Si *lpszName n’est* pas fermé ou n’est pas disponible pour une utilisation exclusive, une erreur se produit.

Cette fonction de membre tente de réparer une base de données qui a été marquée comme potentiellement corrompue par une opération d’écriture incomplète. Cela peut se produire si une application utilisant le moteur de base de données Microsoft Jet est fermée de façon inattendue en raison d’une panne de courant ou d’un problème de matériel informatique. Si vous terminez l’opération et appelez la fonction [membre Close](../../mfc/reference/cdaodatabase-class.md#close) ou si vous quittez l’application de manière habituelle, la base de données ne sera pas marquée comme étant peut-être corrompue.

> [!NOTE]
> Après avoir réparé une base de données, il est également une bonne idée de le compacter en utilisant la fonction membre [CompactDatabase](#compactdatabase) pour défragmenter le fichier et récupérer l’espace du disque.

Pour plus d’informations sur la réparation des bases de données, voir le thème "Méthode De base de réparation" dans DAO Aide.

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a>CDaoWorkspace::Rollback

Appelez cette fonction membre pour mettre fin à la transaction actuelle et restaurer toutes les bases de données dans l’espace de travail à leur état avant le début de la transaction.

```cpp
void Rollback();
```

### <a name="remarks"></a>Notes

> [!CAUTION]
> Dans un seul objet d’espace de travail, les transactions sont toujours globales à l’espace de travail et ne se limitent pas à une seule base de données ou un ensemble d’enregistrements. Si vous effectuez des opérations sur plus d’une `Rollback` base de données ou un ensemble d’enregistrements dans le cadre d’une transaction d’espace de travail, restaure toutes les opérations de toutes ces bases de données et enregistrements.

Si vous fermez un objet d’espace de travail sans enregistrer ou faire reculer les transactions en attente, les transactions sont automatiquement annulées. Si vous appelez [CommitTrans](#committrans) ou `Rollback` sans appeler [d’abord BeginTrans](#begintrans), une erreur se produit.

> [!NOTE]
> Lorsque vous commencez une transaction, le moteur de base de données enregistre ses opérations dans un fichier conservé dans l’annuaire spécifié par la variable d’environnement TEMP sur le poste de travail. Si le fichier de journal de transaction épuise le stockage disponible sur votre `CDaoException` disque TEMP, le moteur de base de données entraînera MFC à lancer une erreur (DAO 2004). À ce stade, `CommitTrans`si vous appelez, un nombre indéterminé d’opérations sont engagés, mais les opérations inachevées restantes sont perdues, et l’opération doit être redémarrée. L’appel `Rollback` libère le journal des transactions et annule toutes les opérations de la transaction.

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

Appelez cette fonction de membre pour définir le mot de passe par défaut que le moteur de base de données utilise lorsqu’un objet d’espace de travail est créé sans mot de passe spécifique.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Paramètres

*lpszPassword (lpszPassword)*<br/>
Le mot de passe par défaut. Un mot de passe peut être jusqu’à 14 caractères de long et peut contenir n’importe quel personnage sauf ASCII 0 (null). Les mots de passe respectent la casse.

### <a name="remarks"></a>Notes

Le mot de passe par défaut que vous définissez s’applique aux nouveaux espaces de travail que vous créez après l’appel. Lorsque vous créez des espaces de travail ultérieurs, vous n’avez pas besoin de spécifier un mot de passe dans l’appel [Créer.](#create)

Pour utiliser cette fonction de membre :

1. Construire `CDaoWorkspace` un objet mais `Create`ne pas appeler .

1. Appelez `SetDefaultPassword` et, si vous voulez, [SetDefaultUser](#setdefaultuser).

1. Appelez `Create` pour cet objet d’espace de travail ou ceux qui en ont suivi, sans spécifier un mot de passe.

Par défaut, la propriété DefaultUser est définie à "admin" et la propriété DefaultPassword est réglée à une chaîne vide (").

Pour en savoir plus sur la sécurité, voir le thème "Permissions Property" dans DAO Aide. Pour obtenir des informations connexes, consultez les thèmes « Propriété DefaultPassword » et « Propriété DefaultUser » dans DAO Help.

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser

Appelez cette fonction de membre pour définir le nom d’utilisateur par défaut que le moteur de base de données utilise lorsqu’un objet d’espace de travail est créé sans nom d’utilisateur spécifique.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Paramètres

*lpszDefaultUser*<br/>
Nom de l’utilisateur par défaut. Un nom d’utilisateur peut être de 1 à 20 caractères de long et inclure des caractères alphabétiques, des caractères \[ \] accentués, des nombres, des espaces et des symboles, sauf pour: " (guillemets), / (slash vers l’avant), (backslash), (brackets), : (colon), &#124; (pipe), \< (moins-que le signe), > (plus-que le signe), (plus signe), (signe égal), ; (semi-remorque), , ( virgule), \* (point d’interrogation), (astérisque), espaces de tête, et personnages de contrôle (ASCII 00 à ASCII 31). Pour plus d’informations connexes, consultez le thème "UserName Property" dans DAO Help.

### <a name="remarks"></a>Notes

Le nom d’utilisateur par défaut que vous définissez s’applique aux nouveaux espaces de travail que vous créez après l’appel. Lorsque vous créez des espaces de travail ultérieurs, vous n’avez pas besoin de spécifier un nom d’utilisateur dans l’appel [Créer.](#create)

Pour utiliser cette fonction de membre :

1. Construire `CDaoWorkspace` un objet mais `Create`ne pas appeler .

1. Appelez `SetDefaultUser` et, si vous voulez, [SetDefaultPassword](#setdefaultpassword).

1. Appelez `Create` pour cet objet d’espace de travail ou ceux qui en ont suivi, sans spécifier un nom d’utilisateur.

Par défaut, la propriété DefaultUser est définie à "admin" et la propriété DefaultPassword est réglée à une chaîne vide (").

Pour plus d’informations connexes, consultez les thèmes «DefaultUser Property» et «DefaultPassword Property» dans DAO Help.

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a>CDaoWorkspace::SetIniPath

Appelez cette fonction de membre pour spécifier l’emplacement des paramètres du registre Windows pour le moteur de base de données Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Paramètres

*lpszRegistrySubkey*<br/>
Une chaîne contenant le nom d’un sous-clé de registre Windows pour l’emplacement des paramètres du moteur de base de données Microsoft Jet ou les paramètres nécessaires pour les bases de données ISAM installables.

### <a name="remarks"></a>Notes

Appelez `SetIniPath` uniquement si vous avez besoin de spécifier des paramètres spéciaux. Pour plus d’informations, voir le sujet "IniPath Property" dans DAO Help.

> [!NOTE]
> Appelez `SetIniPath` pendant l’installation de l’application, pas lorsque l’application s’exécute. `SetIniPath`doivent être appelés avant d’ouvrir des espaces de travail, des bases de données ou des enregistrements; autrement, MFC jette une exception.

Vous pouvez utiliser ce mécanisme pour configurer le moteur de base de données avec des paramètres de registre fournis par l’utilisateur. La portée de cet attribut est limitée à votre application et ne peut être modifiée sans redémarrer votre application.

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

Appelez cette fonction membre pour définir la valeur de la propriété DAO IsolateODBCTrans pour l’espace de travail.

```cpp
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Paramètres

*bIsolateODBCTrans (en anglais seulement)*<br/>
Passez VRAI si vous voulez commencer à isoler les transactions ODBC. Passez FALSE si vous voulez arrêter d’isoler les transactions ODBC.

### <a name="remarks"></a>Notes

Dans certaines situations, vous devrez peut-être avoir plusieurs transactions simultanées en attente sur la même base de données ODBC. Pour ce faire, vous devez ouvrir un espace de travail séparé pour chaque transaction. Bien que chaque espace de travail puisse avoir sa propre connexion ODBC à la base de données, cela ralentit les performances du système. Étant donné que l’isolement des transactions n’est normalement pas nécessaire, les connexions ODBC à partir de plusieurs objets d’espace de travail ouverts par le même utilisateur sont partagées par défaut.

Certains serveurs ODBC, tels que Microsoft SQL Server, n’autorisent pas les transactions simultanées sur une seule connexion. Si vous avez besoin d’avoir plus d’une transaction à la fois en attente contre une telle base de données, définissez la propriété IsolateODBCTrans à TRUE sur chaque espace de travail dès que vous l’ouvrez. Cela force une connexion ODBC séparée pour chaque espace de travail.

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a>CDaoWorkspace::SetLoginTimeout

Appelez cette fonction membre pour définir la valeur de la propriété DAO LoginTimeout pour l’espace de travail.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Paramètres

*nSecondes*<br/>
Le nombre de secondes avant qu’une erreur se produise lorsque vous tentez de vous connecter à une base de données ODBC.

### <a name="remarks"></a>Notes

Cette valeur représente le nombre de secondes avant qu’une erreur ne se produise lorsque vous tentez de vous connecter à une base de données ODBC. Le paramètre LoginTimeout par défaut est de 20 secondes. Lorsque LoginTimeout est réglé à 0, aucun délai d’attente ne se produit et la communication avec la source de données peut cesser de répondre.

Lorsque vous tentez de vous connecter à une base de données ODBC, comme Microsoft SQL Server, la connexion peut échouer en raison d’erreurs de réseau ou parce que le serveur ne s’exécute pas. Plutôt que d’attendre que la valeur par défaut se connecte, vous pouvez spécifier combien de temps le moteur de base de données attend avant de produire une erreur. L’enregistrement sur le serveur se produit implicitement dans le cadre d’un certain nombre d’événements différents, tels que l’exécution d’une requête sur une base de données serveur externe. La valeur de délai d’attente est déterminée par le réglage actuel de la propriété LoginTimeout.

Pour plus d’informations connexes, consultez le thème "LoginTimeout Property" dans DAO Help.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)<br/>
[Classe CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[Classe CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Classe CDaoException](../../mfc/reference/cdaoexception-class.md)
