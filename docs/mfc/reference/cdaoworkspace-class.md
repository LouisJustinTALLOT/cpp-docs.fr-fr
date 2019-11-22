---
title: CDaoWorkspace (classe)
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
ms.openlocfilehash: c1d235035cee9342c8c54c7aaa4e05a96d5a37e3
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303468"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace (classe)

Gère une session de base de données nommée et protégée par mot de passe, de la connexion à la déconnexion, pour un seul utilisateur. DAO est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.

## <a name="syntax"></a>Syntaxe

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDaoWorkspace :: CDaoWorkspace](#cdaoworkspace)|Construit un objet Workspace. Ensuite, appelez `Create` ou `Open`.|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoWorkspace :: Append](#append)|Ajoute un espace de travail nouvellement créé à la collection d’espaces de travail du moteur de base de données.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Commence une nouvelle transaction, qui s’applique à toutes les bases de données ouvertes dans l’espace de travail.|
|[CDaoWorkspace::Close](#close)|Ferme l’espace de travail et tous les objets qu’il contient. Les transactions en attente sont annulées.|
|[CDaoWorkspace::CommitTrans](#committrans)|Termine la transaction en cours et enregistre les modifications.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Compacte (ou duplique) une base de données.|
|[CDaoWorkspace::Create](#create)|Crée un nouvel objet d’espace de travail DAO.|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Retourne le nombre d’objets de base de données DAO dans la collection de bases de données de l’espace de travail.|
|[CDaoWorkspace :: GetDatabaseInfo](#getdatabaseinfo)|Retourne des informations sur une base de données DAO spécifiée définie dans la collection de bases de données de l’espace de travail.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Retourne l’emplacement des paramètres d’initialisation du moteur de base de données Microsoft Jet dans le Registre Windows.|
|[CDaoWorkspace :: GetIsolateODBCTrans](#getisolateodbctrans)|Retourne une valeur qui indique si plusieurs transactions qui impliquent la même source de données ODBC sont isolées par le biais de connexions multiples forcées à la source de données.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Retourne le nombre de secondes avant qu’une erreur ne se produise lorsque l’utilisateur tente de se connecter à une base de données ODBC.|
|[CDaoWorkspace :: GetName](#getname)|Retourne le nom défini par l’utilisateur pour l’objet Workspace.|
|[CDaoWorkspace::GetUserName](#getusername)|Retourne le nom d’utilisateur spécifié lors de la création de l’espace de travail. Il s’agit du nom du propriétaire de l’espace de travail.|
|[CDaoWorkspace::GetVersion](#getversion)|Retourne une chaîne qui contient la version du moteur de base de données associé à l’espace de travail.|
|[CDaoWorkspace :: GetWorkspaceCount](#getworkspacecount)|Retourne le nombre d’objets d’espace de travail DAO dans la collection d’espaces de travail du moteur de base de données.|
|[CDaoWorkspace :: GetWorkspaceInfo](#getworkspaceinfo)|Retourne des informations sur un espace de travail DAO spécifié défini dans la collection d’espaces de travail du moteur de base de données.|
|[CDaoWorkspace :: Idle](#idle)|Permet au moteur de base de données d’effectuer des tâches en arrière-plan.|
|[CDaoWorkspace::IsOpen](#isopen)|Retourne une valeur différente de zéro si l’espace de travail est ouvert.|
|[CDaoWorkspace :: Open](#open)|Ouvre explicitement un objet d’espace de travail associé à l’espace de travail par défaut de DAO.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Tente de réparer une base de données endommagée.|
|[CDaoWorkspace::Rollback](#rollback)|Met fin à la transaction en cours et n’enregistre pas les modifications.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Définit le mot de passe que le moteur de base de données utilise lorsqu’un objet d’espace de travail est créé sans un mot de passe spécifique.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Définit le nom d’utilisateur que le moteur de base de données utilise lorsqu’un objet d’espace de travail est créé sans nom d’utilisateur spécifique.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Définit l’emplacement des paramètres d’initialisation du moteur de base de données Microsoft Jet dans le Registre Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Spécifie si plusieurs transactions qui impliquent la même source de données ODBC sont isolées en forçant plusieurs connexions à la source de données.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Définit le nombre de secondes avant qu’une erreur ne se produise lorsque l’utilisateur tente de se connecter à une source de données ODBC.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Pointe vers l’objet de l’espace de travail DAO sous-jacent.|

## <a name="remarks"></a>Notes

Dans la plupart des cas, vous n’aurez pas besoin de plusieurs espaces de travail, et vous n’aurez pas besoin de créer des objets d’espace de travail explicites. Lorsque vous ouvrez la base de données et les objets Recordset, ils utilisent l’espace de travail par défaut de DAO. Toutefois, si nécessaire, vous pouvez exécuter plusieurs sessions à la fois en créant des objets d’espace de travail supplémentaires. Chaque objet d’espace de travail peut contenir plusieurs objets de base de données ouverts dans sa propre collection de bases de données. Dans MFC, un espace de travail est principalement un gestionnaire de transactions, en spécifiant un ensemble de bases de données ouvertes dans le même « espace de transaction ».

> [!NOTE]
>  Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur Open Database Connectivity (ODBC). Tous les noms de classe de base de données DAO ont un préfixe « CDao ». En général, les classes MFC basées sur DAO sont plus puissantes que les classes MFC basées sur ODBC. Les classes basées sur DAO accèdent aux données via le moteur de base de données Microsoft Jet, y compris les pilotes ODBC. Ils prennent également en charge les opérations DDL (Data Definition Language), telles que la création de bases de données et l’ajout de tables et de champs par le biais des classes, sans devoir appeler DAO directement.

## <a name="capabilities"></a>Fonctionnalités

La `CDaoWorkspace` de la classe fournit les éléments suivants :

- Accès explicite, si nécessaire, à un espace de travail par défaut, créé en initialisant le moteur de base de données. En général, vous utilisez implicitement l’espace de travail par défaut de DAO en créant des objets de base de données et d’objet Recordset.

- Espace de transaction dans lequel les transactions s’appliquent à toutes les bases de données ouvertes dans l’espace de travail. Vous pouvez créer des espaces de travail supplémentaires pour gérer des espaces de transaction distincts.

- Interface à de nombreuses propriétés du moteur de base de données Microsoft Jet sous-jacent (consultez les fonctions membres statiques). L’ouverture ou la création d’un espace de travail, ou l’appel d’une fonction membre statique avant d’ouvrir ou de créer, initialise le moteur de base de données.

- Accès à la collection d’espaces de travail du moteur de base de données, qui stocke tous les espaces de travail actifs qui y ont été ajoutés. Vous pouvez également créer et utiliser des espaces de travail sans les ajouter à la collection.

## <a name="security"></a>Sécurité

MFC n’implémente pas les collections Users et groups dans DAO, qui sont utilisées pour le contrôle de sécurité. Si vous avez besoin de ces aspects de DAO, vous devez les programmer par le biais d’appels directs à des interfaces DAO. Pour plus d’informations, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Utilisation

Vous pouvez utiliser la classe `CDaoWorkspace` pour :

- Ouvrir explicitement l’espace de travail par défaut.

   En général, l’utilisation de l’espace de travail par défaut est implicite lorsque vous ouvrez de nouveaux objets [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Toutefois, vous devrez peut-être y accéder explicitement (par exemple, pour accéder aux propriétés du moteur de base de données ou à la collection d’espaces de travail). Consultez la section « utilisation implicite de l’espace de travail par défaut » ci-dessous.

- Créer des espaces de travail. Appelez [Append](#append) si vous souhaitez les ajouter à la collection d’espaces de travail.

- Ouvrez un espace de travail existant dans la collection d’espaces de travail.

La création d’un espace de travail qui n’existe pas encore dans la collection d’espaces de travail est décrite sous la fonction [créer](#create) un membre. Les objets d’espace de travail ne sont pas persistants entre les sessions du moteur base. Si votre application lie les MFC statiquement, la fin de l’application n’initialise pas le moteur de base de données. Si votre application est liée de manière dynamique à MFC, le moteur de base de données n’est pas initialisé lorsque la DLL MFC est déchargée.

L’ouverture explicite de l’espace de travail par défaut ou l’ouverture d’un espace de travail existant dans la collection d’espaces de travail est décrite sous la fonction membre [Open](#open) .

Terminer une session d’espace de travail en fermant l’espace de travail avec la fonction membre [Close](#close) . `Close` ferme toutes les bases de données que vous n’avez pas fermées précédemment, en annulant toutes les transactions non validées.

## <a name="transactions"></a>Transactions

DAO gère les transactions au niveau de l’espace de travail. par conséquent, les transactions sur un espace de travail avec plusieurs bases de données ouvertes s’appliquent à toutes les bases de données. Par exemple, si deux bases de données comportent des mises à jour non validées et que vous appelez [CommitTrans](#committrans), toutes les mises à jour sont validées. Si vous souhaitez limiter les transactions à une base de données unique, vous devez disposer d’un objet d’espace de travail distinct.

## <a name="implicit-use-of-the-default-workspace"></a>Utilisation implicite de l’espace de travail par défaut

MFC utilise implicitement l’espace de travail par défaut de DAO dans les circonstances suivantes :

- Si vous créez un objet `CDaoDatabase` mais que vous ne le faites pas par l’intermédiaire d’un objet `CDaoWorkspace` existant, MFC crée un objet espace de travail temporaire pour vous, qui correspond à l’espace de travail par défaut de DAO. Si vous le faites pour plusieurs bases de données, tous les objets de base de données sont associés à l’espace de travail par défaut. Vous pouvez accéder à l’espace de travail d’une base de données par le biais d’un membre de données `CDaoDatabase`.

- De même, si vous créez un objet `CDaoRecordset` sans fournir de pointeur vers un objet `CDaoDatabase`, MFC crée un objet de base de données temporaire et, par extension, un objet espace de travail temporaire. Vous pouvez accéder à la base de données d’un jeu d’enregistrements, et indirectement à son espace de travail, par le biais d’un membre de données `CDaoRecordset`.

## <a name="other-operations"></a>Autres opérations

D’autres opérations de base de données sont également fournies, telles que la réparation d’une base de données endommagée ou le compactage d’une base de données.

Pour plus d’informations sur l’appel de DAO directement et sur la sécurité DAO, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Conditions requises

**En-tête :** afxdao. h

##  <a name="append"></a>CDaoWorkspace :: Append

Appelez cette fonction membre après avoir appelé [Create](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Notes

`Append` ajoute un nouvel objet d’espace de travail à la collection d’espaces de travail du moteur de base de données. Les espaces de travail ne sont pas conservés entre les sessions du moteur de base de données. ils sont stockés uniquement en mémoire, pas sur le disque. Vous n’avez pas besoin d’ajouter un espace de travail. Si vous ne le faites pas, vous pouvez toujours l’utiliser.

Un espace de travail ajouté reste dans la collection d’espaces de travail, dans un état actif et ouvert, jusqu’à ce que vous appeliez sa fonction membre [Close](#close) .

Pour obtenir des informations connexes, consultez la rubrique « méthode Append » dans l’aide de DAO.

##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans

Appelez cette fonction membre pour initier une transaction.

```
void BeginTrans();
```

### <a name="remarks"></a>Notes

Une fois que vous avez appelé `BeginTrans`, les mises à jour que vous apportez à vos données ou à votre structure de base de données prennent effet lorsque vous validez la transaction. Étant donné que l’espace de travail définit un seul espace de transaction, la transaction s’applique à toutes les bases de données ouvertes dans l’espace de travail. Il existe deux façons de terminer la transaction :

- Appelez la fonction membre [CommitTrans](#committrans) pour valider la transaction et enregistrer les modifications apportées à la source de données.

- Ou appelez la fonction membre [Rollback](#rollback) pour annuler la transaction.

La fermeture de l’objet de l’espace de travail ou d’un objet de base de données pendant qu’une transaction est en attente restaure toutes les transactions en attente.

Si vous devez isoler des transactions sur une source de données ODBC de celles qui se trouvent sur une autre source de données ODBC, consultez la fonction membre [SetIsolateODBCTrans](#setisolateodbctrans) .

##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace

Construit un objet `CDaoWorkspace`.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Notes

Après avoir construit l' C++ objet, vous avez deux options :

- Appelez la fonction membre [Open](#open) de l’objet pour ouvrir l’espace de travail par défaut ou pour ouvrir un objet existant dans la collection d’espaces de travail.

- Ou appelez la fonction membre [Create](#create) de l’objet pour créer un nouvel objet d’espace de travail DAO. Cette action démarre explicitement une nouvelle session d’espace de travail, à laquelle vous pouvez vous référer via l’objet `CDaoWorkspace`. Après avoir appelé `Create`, vous pouvez appeler [Append](#append) si vous souhaitez ajouter l’espace de travail à la collection Workspaces du moteur de base de données.

Consultez la vue d’ensemble de la classe pour [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) pour plus d’informations sur le moment où vous devez créer explicitement un objet `CDaoWorkspace`. En règle générale, vous utilisez des espaces de travail créés implicitement lorsque vous ouvrez un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) sans spécifier un espace de travail ou lorsque vous ouvrez un objet [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) sans spécifier d’objet de base de données. Les objets DAO MFC créés de cette façon utilisent l’espace de travail par défaut de DAO, qui est créé une fois et réutilisé.

Pour libérer un espace de travail et ses objets contenus, appelez la fonction membre [Close](#close) de l’objet Workspace.

##  <a name="close"></a>  CDaoWorkspace::Close

Appelez cette fonction membre pour fermer l’objet de l’espace de travail.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

La fermeture d’un objet d’espace de travail ouvert libère l’objet DAO sous-jacent et, si l’espace de travail est membre de la collection Workspaces, le supprime de la collection. L’appel de `Close` est une bonne pratique de programmation.

> [!CAUTION]
>  La fermeture d’un objet Workspace ferme toutes les bases de données ouvertes dans l’espace de travail. Tous les jeux d’enregistrements ouverts dans les bases de données sont également fermés, et toutes les modifications ou mises à jour en attente sont annulées. Pour obtenir des informations connexes, consultez les fonctions membres [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#close):: Close, [CDaoRecordset :: Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef :: Close](../../mfc/reference/cdaotabledef-class.md#close)et [CDaoQueryDef :: Close](../../mfc/reference/cdaoquerydef-class.md#close) .

Les objets d’espace de travail ne sont pas permanents. ils existent uniquement lorsque des références à ces derniers existent. Cela signifie que lorsque la session du moteur de base de données se termine, l’espace de travail et sa collection de bases de données ne sont pas conservés. Vous devez les recréer pour la session suivante en ouvrant à nouveau votre espace de travail et votre ou vos bases de données.

Pour obtenir des informations connexes, consultez la rubrique « méthode Close » dans l’aide de DAO.

##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans

Appelez cette fonction membre pour valider une transaction : enregistrez un groupe de modifications et de mises à jour dans une ou plusieurs bases de données de l’espace de travail.

```
void CommitTrans();
```

### <a name="remarks"></a>Notes

Une transaction se compose d’une série de modifications apportées aux données de la base de données ou à sa structure, en commençant par un appel à [BeginTrans](#begintrans). Une fois la transaction terminée, validez-la ou restaurez-la (annulez les modifications) avec la [restauration](#rollback). Par défaut, sans transactions, les mises à jour des enregistrements sont validées immédiatement. L’appel de `BeginTrans` entraîne le report de l’engagement des mises à jour jusqu’à ce que vous appeliez `CommitTrans`.

> [!CAUTION]
>  Dans un espace de travail, les transactions sont toujours globales dans l’espace de travail et ne sont pas limitées à une seule base de données ou un seul Recordset. Si vous effectuez des opérations sur plusieurs bases de données ou jeux d’enregistrements au sein d’une transaction d’espace de travail, `CommitTrans` valide toutes les mises à jour en attente et `Rollback` restaure toutes les opérations sur ces bases de données et jeux d’enregistrements.

Lorsque vous fermez une base de données ou un espace de travail avec des transactions en attente, toutes les transactions sont restaurées.

> [!NOTE]
>  Il ne s’agit pas d’un mécanisme de validation en deux phases. Si une mise à jour ne peut pas être validée, d’autres seront validées.

##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase

Appelez cette fonction membre pour compacter un Microsoft Jet (. MDB).

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

*lpszSrcName*<br/>
Nom d’une base de données existante et fermée. Il peut s’agir d’un chemin d’accès complet et d’un nom de fichier, par exemple «C :\\\MYDB. MDB». Si le nom de fichier a une extension, vous devez le spécifier. Si votre réseau prend en charge le format UNC (Uniform Naming Convention), vous pouvez également spécifier un chemin d’accès réseau, par exemple «\\\\\\\MONSERVEUR\\\MYSHARE\\\MYDIR\\\MYDB. MDB». (Les doubles barres obliques inverses sont nécessaires dans les chaînes de chemin d' C++ accès car «\\» est le caractère d’échappement.)

*lpszDestName*<br/>
Chemin d’accès complet de la base de données compactée que vous créez. Vous pouvez également spécifier un chemin d’accès réseau comme avec *lpszSrcName*. Vous ne pouvez pas utiliser l’argument *lpszDestName* pour spécifier le même fichier de base de données que *lpszSrcName*.

*lpszPassword*<br/>
Un mot de passe, utilisé lorsque vous souhaitez compacter une base de données protégée par mot de passe. Notez que si vous utilisez la version de `CompactDatabase` qui prend un mot de passe, vous devez fournir tous les paramètres. En outre, comme il s’agit d’un paramètre de connexion, il requiert une mise en forme spéciale, comme suit :; PWD = *lpszPassword*. Par exemple :; PWD = « heureux ». (Le point-virgule de début est requis.)

*lpszLocale*<br/>
Expression de chaîne utilisée pour spécifier l’ordre de classement pour la création de *lpszDestName*. Si vous omettez cet argument en acceptant la valeur par défaut de `dbLangGeneral` (voir ci-dessous), les paramètres régionaux de la nouvelle base de données sont les mêmes que ceux de l’ancienne base de données. Les valeurs possibles sont :

- `dbLangGeneral` l’anglais, l’allemand, le français, le portugais, l’italien et l’espagnol moderne

- `dbLangArabic` arabe

- `dbLangCyrillic` russe

- `dbLangCzech` tchèque

- `dbLangDutch` néerlandais

- `dbLangGreek` grec

- `dbLangHebrew` Hébreu

- `dbLangHungarian` hongrois

- `dbLangIcelandic` islandais

- `dbLangNordic` langues nordiques (moteur de base de données Microsoft Jet version 1,0 uniquement)

- `dbLangNorwdan` norvégien et danois

- `dbLangPolish` polonais

- `dbLangSpanish` espagnol traditionnel

- `dbLangSwedfin` suédois et finnois

- `dbLangTurkish` turc

*nOptions*<br/>
Indique une ou plusieurs options pour la base de données cible, *lpszDestName*. Si vous omettez cet argument en acceptant la valeur par défaut, le *lpszDestName* aura le même chiffrement et la même version que *lpszSrcName*. Vous pouvez combiner l’option `dbEncrypt` ou `dbDecrypt` avec l’une des options de version à l’aide de l’opérateur or au niveau du bit. Les valeurs possibles, qui spécifient un format de base de données, et non une version du moteur de base de données, sont les suivantes :

- `dbEncrypt` chiffrer la base de données lors du compactage.

- `dbDecrypt` déchiffrer la base de données lors du compactage.

- `dbVersion10` créer une base de données qui utilise le moteur de base de données Microsoft Jet version 1,0 lors du compactage.

- `dbVersion11` créer une base de données qui utilise le moteur de base de données Microsoft Jet version 1,1 lors du compactage.

- `dbVersion20` créer une base de données qui utilise le moteur de base de données Microsoft Jet version 2,0 lors du compactage.

- `dbVersion30` créer une base de données qui utilise le moteur de base de données Microsoft Jet version 3,0 lors du compactage.

Vous pouvez utiliser `dbEncrypt` ou `dbDecrypt` dans l’argument options pour spécifier s’il faut chiffrer ou déchiffrer la base de données lorsqu’elle est compactée. Si vous omettez une constante de chiffrement ou si vous incluez à la fois `dbDecrypt` et `dbEncrypt`, *lpszDestName* aura le même chiffrement que *lpszSrcName*. Vous pouvez utiliser l’une des constantes de version dans l’argument options pour spécifier la version du format de données pour la base de données compactée. Cette constante affecte uniquement la version du format de données de *lpszDestName*. Vous ne pouvez spécifier qu’une seule constante de version. Si vous omettez une constante de version, *lpszDestName* aura la même version que *lpszSrcName*. Vous pouvez compacter *lpszDestName* uniquement vers une version identique ou ultérieure à celle de *lpszSrcName*.

> [!CAUTION]
>  Si une base de données n’est pas chiffrée, il est possible, même si vous implémentez la sécurité utilisateur/mot de passe, de lire directement le fichier de disque binaire qui constitue la base de données.

### <a name="remarks"></a>Notes

Lorsque vous modifiez des données dans une base de données, le fichier de base de données peut être fragmenté et utiliser plus d’espace disque que nécessaire. Régulièrement, vous devez compacter votre base de données pour défragmenter le fichier de base de données. La base de données compactée est généralement plus petite. Vous pouvez également choisir de modifier l’ordre de classement, le chiffrement ou la version du format de données pendant que vous copiez et compactez la base de données.

> [!CAUTION]
>  La fonction membre `CompactDatabase` ne convertit pas correctement une base de données Microsoft Access complète d’une version à une autre. Seul le format de données est converti. Les objets définis par Microsoft Access, tels que les formulaires et les rapports, ne sont pas convertis. Toutefois, les données sont correctement converties.

> [!TIP]
>  Vous pouvez également utiliser `CompactDatabase` pour copier un fichier de base de données.

Pour plus d’informations sur le compactage des bases de données, consultez la rubrique « méthode CompactDatabase » dans l’aide de DAO.

##  <a name="create"></a>  CDaoWorkspace::Create

Appelez cette fonction membre pour créer un nouvel objet d’espace de travail DAO et l’associer à l’objet MFC `CDaoWorkspace`.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Chaîne comportant jusqu’à 14 caractères qui nomme le nouvel objet Workspace de manière unique. Vous devez fournir un nom. Pour obtenir des informations connexes, consultez la rubrique « propriété Name » dans l’aide de DAO.

*lpszUserName*<br/>
Nom d’utilisateur du propriétaire de l’espace de travail. Pour connaître la configuration requise, consultez le paramètre *lpszDefaultUser* de la fonction membre [SetDefaultUser](#setdefaultuser) . Pour obtenir des informations connexes, consultez la rubrique « propriété UserName » dans l’aide de DAO.

*lpszPassword*<br/>
Mot de passe du nouvel objet Workspace. Un mot de passe peut comporter jusqu’à 14 caractères et peut contenir n’importe quel caractère, à l’exception de ASCII 0 (null). Les mots de passe respectent la casse. Pour obtenir des informations connexes, consultez la rubrique « propriété de mot de passe » dans l’aide de DAO.

### <a name="remarks"></a>Notes

Le processus de création global est le suivant :

1. Construisez un objet [CDaoWorkspace](#cdaoworkspace) .

1. Appelez la fonction membre `Create` de l’objet pour créer l’espace de travail DAO sous-jacent. Vous devez spécifier un nom d’espace de travail.

1. Appelez éventuellement [Append](#append) si vous souhaitez ajouter l’espace de travail à la collection Workspaces du moteur de base de données. Vous pouvez utiliser l’espace de travail sans l’ajouter.

Après l’appel de `Create`, l’objet de l’espace de travail est dans un état ouvert, prêt à être utilisé. Vous n’appelez pas `Open` après `Create`. Vous n’appelez pas `Create` si l’espace de travail existe déjà dans la collection d’espaces de travail. `Create` Initialise le moteur de base de données s’il n’a pas déjà été initialisé pour votre application.

##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount

Appelez cette fonction membre pour récupérer le nombre d’objets de base de données DAO dans la collection de bases de données de l’espace de travail (le nombre de bases de données ouvertes dans l’espace de travail).

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre de bases de données ouvertes dans l’espace de travail.

### <a name="remarks"></a>Notes

`GetDatabaseCount` est utile si vous devez exécuter en boucle toutes les bases de données définies dans la collection de bases de données de l’espace de travail. Pour obtenir des informations sur une base de données donnée dans la collection, consultez [GetDatabaseInfo](#getdatabaseinfo). L’utilisation courante consiste à appeler `GetDatabaseCount` pour le nombre de bases de données ouvertes, puis à utiliser ce nombre comme index de boucle pour les appels répétés à `GetDatabaseInfo`.

##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo

Appelez cette fonction membre pour obtenir différents genres d’informations sur une base de données ouverte dans l’espace de travail.

```
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
Index de base zéro de l’objet de base de données dans la collection de bases de données de l’espace de travail, pour la recherche par index.

*dbinfo*<br/>
Référence à un objet [cdaodatabaseinfo,](../../mfc/reference/cdaodatabaseinfo-structure.md) qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations relatives à la base de données à récupérer. Les options disponibles sont répertoriées ici, ainsi que ce qu’elles provoquent le retour de la fonction :

- Nom du AFX_DAO_PRIMARY_INFO (par défaut), pouvant être mis à jour, transactions

- AFX_DAO_SECONDARY_INFO informations principales plus : version, ordre de classement, délai d’expiration de la requête

- AFX_DAO_ALL_INFO les informations primaires et secondaires plus : Connect

*lpszName*<br/>
Nom de l’objet de base de données, pour la recherche par nom. Le nom est une chaîne comportant jusqu’à 14 caractères qui nomme le nouvel objet Workspace de manière unique.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher une base de données par index. L’autre version vous permet de rechercher une base de données par nom.

Pour obtenir une description des informations retournées dans *dbinfo*, consultez la structure [cdaodatabaseinfo,](../../mfc/reference/cdaodatabaseinfo-structure.md) . Cette structure a des membres qui correspondent aux éléments d’informations énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous recevez également des informations sur les niveaux précédents.

##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath

Appelez cette fonction membre pour obtenir l’emplacement des paramètres d’initialisation du moteur de base de données Microsoft Jet dans le Registre Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Valeur de retour

[CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’emplacement du Registre.

### <a name="remarks"></a>Notes

Vous pouvez utiliser l’emplacement pour obtenir des informations sur les paramètres du moteur de base de données. Les informations retournées sont en fait le nom d’une sous-clé de registre.

Pour obtenir des informations connexes, consultez les rubriques « propriété IniPath » et « personnalisation des paramètres du Registre Windows pour l’accès aux données » dans l’aide de DAO.

##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans

Appelez cette fonction membre pour obtenir la valeur actuelle de la propriété DAO IsolateODBCTrans pour l’espace de travail.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les transactions ODBC sont isolées ; Sinon, 0.

### <a name="remarks"></a>Notes

Dans certains cas, il se peut que vous deviez avoir plusieurs transactions simultanées en attente sur la même base de données ODBC. Pour ce faire, vous devez ouvrir un espace de travail distinct pour chaque transaction. Gardez à l’esprit que même si chaque espace de travail peut avoir sa propre connexion ODBC à la base de données, Cela ralentit les performances du système. Étant donné que l’isolation des transactions n’est généralement pas nécessaire, les connexions ODBC de plusieurs objets d’espace de travail ouverts par le même utilisateur sont partagées par défaut.

Certains serveurs ODBC, tels que Microsoft SQL Server, n’autorisent pas les transactions simultanées sur une seule connexion. Si vous devez avoir plusieurs transactions à la fois en attente sur une telle base de données, affectez la valeur TRUE à la propriété IsolateODBCTrans sur chaque espace de travail dès que vous l’ouvrez. Cela force une connexion ODBC distincte pour chaque espace de travail.

Pour obtenir des informations connexes, consultez la rubrique « propriété IsolateODBCTrans » dans l’aide de DAO.

##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout

Appelez cette fonction membre pour obtenir la valeur actuelle de la propriété DAO LoginTimeout pour l’espace de travail.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Valeur de retour

Nombre de secondes avant qu’une erreur ne se produise lorsque vous tentez de vous connecter à une base de données ODBC.

### <a name="remarks"></a>Notes

Cette valeur représente le nombre de secondes avant qu’une erreur se produise lorsque vous tentez de vous connecter à une base de données ODBC. Le paramètre LoginTimeout par défaut est de 20 secondes. Lorsque LoginTimeout a la valeur 0, aucun délai d’attente n’est atteint et la communication avec la source de données peut cesser de répondre.

Lorsque vous tentez de vous connecter à une base de données ODBC, par exemple Microsoft SQL Server, la connexion peut échouer en raison d’erreurs réseau ou du fait que le serveur n’est pas en cours d’exécution. Au lieu d’attendre que les 20 secondes par défaut se connectent, vous pouvez spécifier la durée pendant laquelle le moteur de base de données attend avant de générer une erreur. La connexion au serveur se produit implicitement dans le cadre d’un certain nombre d’événements différents, tels que l’exécution d’une requête sur une base de données de serveur externe.

Pour obtenir des informations connexes, consultez la rubrique « propriété LoginTimeout » dans l’aide de DAO.

##  <a name="getname"></a>  CDaoWorkspace::GetName

Appelez cette fonction membre pour récupérer le nom défini par l’utilisateur de l’objet espace de travail DAO sous-jacent de l’objet `CDaoWorkspace`.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

[CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom défini par l’utilisateur de l’objet de l’espace de travail DAO.

### <a name="remarks"></a>Notes

Le nom est utile pour accéder à l’objet espace de travail DAO dans la collection Workspaces du moteur de base de données par nom.

Pour obtenir des informations connexes, consultez la rubrique « propriété Name » dans l’aide de DAO.

##  <a name="getusername"></a>  CDaoWorkspace::GetUserName

Appelez cette fonction membre pour obtenir le nom du propriétaire de l’espace de travail.

```
CString GetUserName();
```

### <a name="return-value"></a>Valeur de retour

[CString](../../atl-mfc-shared/reference/cstringt-class.md) qui représente le propriétaire de l’objet Workspace.

### <a name="remarks"></a>Notes

Pour obtenir ou définir les autorisations pour le propriétaire de l’espace de travail, appelez DAO directement pour vérifier le paramètre de propriété Permissions. cela détermine les autorisations dont dispose l’utilisateur. Pour utiliser des autorisations, vous avez besoin d’un système. Fichier MDA.

Pour plus d’informations sur l’appel direct de DAO, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Pour obtenir des informations connexes, consultez la rubrique « propriété UserName » dans l’aide de DAO.

##  <a name="getversion"></a>  CDaoWorkspace::GetVersion

Appelez cette fonction membre pour déterminer la version du moteur de base de données Microsoft Jet en cours d’utilisation.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Valeur de retour

[CString](../../atl-mfc-shared/reference/cstringt-class.md) qui indique la version du moteur de base de données associée à l’objet.

### <a name="remarks"></a>Notes

La valeur retournée représente le numéro de version sous la forme « major. minor »; par exemple, « 3,0 ». Le numéro de version du produit (par exemple, 3,0) se compose du numéro de version (3), d’un point et du numéro de version (0).

Pour obtenir des informations connexes, consultez la rubrique « Version Property » dans l’aide de DAO.

##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount

Appelez cette fonction membre pour récupérer le nombre d’objets d’espace de travail DAO dans la collection d’espaces de travail du moteur de base de données.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’espaces de travail ouverts dans la collection d’espaces de travail.

### <a name="remarks"></a>Notes

Ce nombre n’inclut pas les espaces de travail ouverts qui ne sont pas ajoutés à la collection. `GetWorkspaceCount` est utile si vous devez parcourir tous les espaces de travail définis dans la collection d’espaces de travail. Pour obtenir des informations sur un espace de travail donné dans la collection, consultez [GetWorkspaceInfo](#getworkspaceinfo). L’utilisation courante consiste à appeler `GetWorkspaceCount` pour le nombre d’espaces de travail ouverts, puis à utiliser ce nombre comme index de boucle pour les appels répétés à `GetWorkspaceInfo`.

##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo

Appelez cette fonction membre pour obtenir différents genres d’informations sur un espace de travail ouvert dans la session.

```
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
Index de base zéro de l’objet de base de données dans la collection d’espaces de travail, pour la recherche par index.

*wkspcinfo*<br/>
Référence à un objet [cdaoworkspaceinfo,](../../mfc/reference/cdaoworkspaceinfo-structure.md) qui retourne les informations demandées.

*dwInfoOptions*<br/>
Options qui spécifient les informations relatives à l’espace de travail à récupérer. Les options disponibles sont répertoriées ici, ainsi que ce qu’elles provoquent le retour de la fonction :

- Nom de l’AFX_DAO_PRIMARY_INFO (par défaut)

- AFX_DAO_SECONDARY_INFO informations principales plus : nom d’utilisateur

- AFX_DAO_ALL_INFO les informations primaires et secondaires plus : isoler ODBCTrans

*lpszName*<br/>
Nom de l’objet de l’espace de travail, pour la recherche par nom. Le nom est une chaîne comportant jusqu’à 14 caractères qui nomme le nouvel objet Workspace de manière unique.

### <a name="remarks"></a>Notes

Pour obtenir une description des informations retournées dans *wkspcinfo*, consultez la structure [cdaoworkspaceinfo,](../../mfc/reference/cdaoworkspaceinfo-structure.md) . Cette structure a des membres qui correspondent aux éléments d’informations énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous recevez également des informations pour les niveaux précédents.

##  <a name="idle"></a>  CDaoWorkspace::Idle

Appelez `Idle` pour permettre au moteur de base de données d’effectuer des tâches en arrière-plan qui peuvent ne pas être à jour en raison d’un traitement intensif des données.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Paramètres

*nAction*<br/>
Action à effectuer pendant le traitement inactif. Actuellement, la seule action valide est `dbFreeLocks`.

### <a name="remarks"></a>Notes

Cela est souvent le cas dans les environnements multitâches et multi-utilisateurs dans lesquels il n’y a pas assez de temps de traitement en arrière-plan pour conserver tous les enregistrements d’un jeu d’enregistrements à jour.

> [!NOTE]
>  L’appel de `Idle` n’est pas nécessaire avec les bases de données créées avec la version 3,0 du moteur de base de données Microsoft Jet. Utilisez `Idle` uniquement pour les bases de données créées avec des versions antérieures.

En règle générale, les verrous de lecture sont supprimés et les données des objets Recordset de type feuille de réponse locale sont uniquement mises à jour quand aucune autre action (y compris les mouvements de la souris) ne se produit. Si vous appelez régulièrement `Idle`, vous fournissez au moteur de base de données le temps de rattraper les tâches de traitement en arrière-plan en libérant les verrous de lecture inutiles. La spécification de la constante `dbFreeLocks` comme argument retarde le traitement jusqu’à ce que tous les verrous de lecture soient libérés.

Cette fonction membre n’est pas nécessaire dans les environnements à utilisateur unique, sauf si plusieurs instances d’une application sont en cours d’exécution. La fonction membre `Idle` peut augmenter les performances dans un environnement multi-utilisateur, car elle force le moteur de base de données à vider les données sur le disque et à libérer des verrous sur la mémoire. Vous pouvez également libérer des verrous en lecture en faisant partie des opérations d’une transaction.

Pour obtenir des informations connexes, consultez la rubrique « méthode inactive » dans l’aide de DAO.

##  <a name="isopen"></a>  CDaoWorkspace::IsOpen

Appelez cette fonction membre pour déterminer si l’objet `CDaoWorkspace` est ouvert (c’est-à-dire, si l’objet MFC a été initialisé par un appel à [Open](#open) ou un appel à [Create](#create)).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet de l’espace de travail est ouvert ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez appeler n’importe quelle fonction membre d’un espace de travail qui est dans un état ouvert.

##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace

Pointeur vers l’objet de l’espace de travail DAO sous-jacent.

### <a name="remarks"></a>Notes

Utilisez ce membre de données si vous avez besoin d’un accès direct à l’objet DAO sous-jacent. Vous pouvez appeler les interfaces de l’objet DAO via ce pointeur.

Pour plus d’informations sur l’accès direct aux objets DAO, consultez la [note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="open"></a>CDaoWorkspace :: Open

Ouvre explicitement un objet d’espace de travail associé à l’espace de travail par défaut de DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom de l’objet de l’espace de travail DAO à ouvrir (chaîne comportant jusqu’à 14 caractères) qui nomme l’espace de travail de façon unique. Acceptez la valeur par défaut NULL pour ouvrir explicitement l’espace de travail par défaut. Pour connaître les conditions requises pour l’affectation de noms, consultez le paramètre *lpszName* pour [Create](#create). Pour obtenir des informations connexes, consultez la rubrique « propriété Name » dans l’aide de DAO.

### <a name="remarks"></a>Notes

Après avoir construit un objet `CDaoWorkspace`, appelez cette fonction membre pour effectuer l’une des opérations suivantes :

- Ouvrir explicitement l’espace de travail par défaut. Passe la valeur NULL pour *lpszName*.

- Ouvrez un objet `CDaoWorkspace` existant, membre de la collection Workspaces, par nom. Transmettez un nom valide pour un objet d’espace de travail existant.

`Open` met l’objet de l’espace de travail dans un état ouvert et initialise également le moteur de base de données s’il n’a pas déjà été initialisé pour votre application.

Bien que de nombreuses fonctions membres de `CDaoWorkspace` ne puissent être appelées qu’après l’ouverture de l’espace de travail, les fonctions membres suivantes, qui opèrent sur le moteur C++ de base de données, sont disponibles après la construction de l’objet, mais avant un appel à `Open`:

||||
|-|-|-|
|[Créer](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Idle](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase

Appelez cette fonction membre si vous devez tenter de réparer une base de données endommagée qui accède au moteur de base de données Microsoft Jet.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Chemin d’accès et nom de fichier d’un fichier de base de données du moteur Microsoft Jet existant. Si vous omettez le chemin d’accès, seul le répertoire actif est recherché. Si votre système prend en charge le format UNC (Uniform Naming Convention), vous pouvez également spécifier un chemin d’accès réseau, par exemple : «\\\\\\\MONSERVEUR\\\MYSHARE\\\MYDIR\\\MYDB. MDB». (Les doubles barres obliques inverses sont nécessaires dans la chaîne du chemin d' C++ accès car «\\» est le caractère d’échappement.)

### <a name="remarks"></a>Notes

Vous devez fermer la base de données spécifiée par *lpszName* avant de la réparer. Dans un environnement multi-utilisateur, les autres utilisateurs ne peuvent pas avoir des *lpszName* ouverts pendant la réparation. Si *lpszName* n’est pas fermé ou n’est pas disponible pour une utilisation exclusive, une erreur se produit.

Cette fonction membre tente de réparer une base de données marquée comme potentiellement endommagée par une opération d’écriture incomplète. Cela peut se produire si une application utilisant le moteur de base de données Microsoft Jet est fermée de manière inattendue en raison d’une panne de courant ou d’un problème matériel informatique. Si vous terminez l’opération et appelez la fonction membre [Close](../../mfc/reference/cdaodatabase-class.md#close) ou si vous quittez l’application normalement, la base de données n’est pas marquée comme potentiellement endommagée.

> [!NOTE]
>  Après la réparation d’une base de données, il est également judicieux de la compacter à l’aide de la fonction membre [CompactDatabase](#compactdatabase) pour défragmenter le fichier et récupérer de l’espace disque.

Pour plus d’informations sur la réparation des bases de données, consultez la rubrique « méthode RepairDatabase » dans l’aide de DAO.

##  <a name="rollback"></a>  CDaoWorkspace::Rollback

Appelez cette fonction membre pour mettre fin à la transaction en cours et restaurer toutes les bases de données de l’espace de travail dans leur condition avant le début de la transaction.

```
void Rollback();
```

### <a name="remarks"></a>Notes

> [!CAUTION]
>  Dans un objet d’espace de travail, les transactions sont toujours globales dans l’espace de travail et ne sont pas limitées à une seule base de données ou un seul Recordset. Si vous effectuez des opérations sur plusieurs bases de données ou jeux d’enregistrements au sein d’une transaction d’espace de travail, `Rollback` restaure toutes les opérations sur toutes ces bases de données et jeux d’enregistrements.

Si vous fermez un objet Workspace sans enregistrer ou restaurer de transactions en attente, les transactions sont automatiquement restaurées. Si vous appelez [CommitTrans](#committrans) ou `Rollback` sans appeler au préalable [BeginTrans](#begintrans), une erreur se produit.

> [!NOTE]
>  Lorsque vous commencez une transaction, le moteur de base de données enregistre ses opérations dans un fichier conservé dans le répertoire spécifié par la variable d’environnement TEMP sur la station de travail. Si le fichier journal de transactions épuise le stockage disponible sur votre lecteur TEMP, le moteur de base de données fait en sorte que MFC lève une `CDaoException` (erreur DAO 2004). À ce stade, si vous appelez `CommitTrans`, un nombre indéterminé d’opérations sont validées, mais les opérations non terminées restantes sont perdues et l’opération doit être redémarrée. L’appel de `Rollback` libère le journal des transactions et restaure toutes les opérations dans la transaction.

##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword

Appelez cette fonction membre pour définir le mot de passe par défaut que le moteur de base de données utilise lorsqu’un objet d’espace de travail est créé sans un mot de passe spécifique.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Paramètres

*lpszPassword*<br/>
Mot de passe par défaut. Un mot de passe peut comporter jusqu’à 14 caractères et peut contenir n’importe quel caractère, à l’exception de ASCII 0 (null). Les mots de passe respectent la casse.

### <a name="remarks"></a>Notes

Le mot de passe par défaut que vous définissez s’applique aux nouveaux espaces de travail que vous créez après l’appel. Lorsque vous créez des espaces de travail suivants, vous n’avez pas besoin de spécifier un mot de passe dans l’appel de [création](#create) .

Pour utiliser cette fonction membre :

1. Construisez un objet `CDaoWorkspace` mais n’appelez pas `Create`.

1. Appelez `SetDefaultPassword` et, si vous le souhaitez, [SetDefaultUser](#setdefaultuser).

1. Appelez `Create` pour cet objet Workspace ou ceux qui suivent, sans spécifier de mot de passe.

Par défaut, la propriété DefaultUser est définie sur « admin » et la propriété DefaultPassword est définie sur une chaîne vide ("").

Pour plus d’informations sur la sécurité, consultez la rubrique « propriété des autorisations » dans l’aide de DAO. Pour obtenir des informations connexes, consultez les rubriques « DefaultPassword Property » et « DefaultUser Property » dans l’aide de DAO.

##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser

Appelez cette fonction membre pour définir le nom d’utilisateur par défaut que le moteur de base de données utilise lorsqu’un objet d’espace de travail est créé sans nom d’utilisateur spécifique.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Paramètres

*lpszDefaultUser*<br/>
Nom d’utilisateur par défaut. Un nom d’utilisateur peut avoir une longueur de 1 à 20 caractères et inclure des caractères alphabétiques, des caractères accentués, des chiffres, des espaces et des symboles à l’exception de : » (entre guillemets), / (barre oblique), \ (barre oblique inverse), \[ \] (crochets), : (deux-points), &#124; () barre verticale), \< (moins-signe supérieur), > (supérieur-signe supérieur), signe plus (+), = (signe égal), (point-virgule), (virgule), (point d’interrogation), \* astérisque , des espaces et les caractères de contrôle (ASCII 00 et ASCII 31). Pour obtenir des informations connexes, consultez la rubrique « propriété UserName » dans l’aide de DAO.

### <a name="remarks"></a>Notes

Le nom d’utilisateur par défaut que vous définissez s’applique aux nouveaux espaces de travail que vous créez après l’appel. Lorsque vous créez des espaces de travail suivants, vous n’avez pas besoin de spécifier un nom d’utilisateur dans l’appel de [création](#create) .

Pour utiliser cette fonction membre :

1. Construisez un objet `CDaoWorkspace` mais n’appelez pas `Create`.

1. Appelez `SetDefaultUser` et, si vous le souhaitez, [SetDefaultPassword](#setdefaultpassword).

1. Appelez `Create` pour cet objet Workspace ou ceux qui suivent, sans spécifier de nom d’utilisateur.

Par défaut, la propriété DefaultUser est définie sur « admin » et la propriété DefaultPassword est définie sur une chaîne vide ("").

Pour obtenir des informations connexes, consultez les rubriques « DefaultUser Property » et « DefaultPassword Property » dans l’aide de DAO.

##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath

Appelez cette fonction membre pour spécifier l’emplacement des paramètres du Registre Windows pour le moteur de base de données Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Paramètres

*lpszRegistrySubkey*<br/>
Chaîne contenant le nom d’une sous-clé de Registre Windows pour l’emplacement des paramètres ou paramètres du moteur de base de données Microsoft Jet requis pour les bases de données ISAM installables.

### <a name="remarks"></a>Notes

Appelez `SetIniPath` uniquement si vous devez spécifier des paramètres spéciaux. Pour plus d’informations, consultez la rubrique « propriété IniPath » dans l’aide de DAO.

> [!NOTE]
>  Appelez `SetIniPath` lors de l’installation de l’application, et non lors de l’exécution de l’application. `SetIniPath` doit être appelé avant d’ouvrir des espaces de travail, des bases de données ou des jeux d’enregistrements ; dans le cas contraire, MFC lève une exception.

Vous pouvez utiliser ce mécanisme pour configurer le moteur de base de données avec les paramètres de Registre fournis par l’utilisateur. L’étendue de cet attribut est limitée à votre application et ne peut pas être modifiée sans redémarrer votre application.

##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans

Appelez cette fonction membre pour définir la valeur de la propriété DAO IsolateODBCTrans pour l’espace de travail.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Paramètres

*bIsolateODBCTrans*<br/>
Si vous souhaitez commencer à isoler les transactions ODBC, transmettez TRUE. Transmettez la valeur FALSe si vous souhaitez arrêter l’isolement des transactions ODBC.

### <a name="remarks"></a>Notes

Dans certains cas, il se peut que vous deviez avoir plusieurs transactions simultanées en attente sur la même base de données ODBC. Pour ce faire, vous devez ouvrir un espace de travail distinct pour chaque transaction. Bien que chaque espace de travail puisse avoir sa propre connexion ODBC à la base de données, Cela ralentit les performances du système. Étant donné que l’isolation des transactions n’est généralement pas nécessaire, les connexions ODBC de plusieurs objets d’espace de travail ouverts par le même utilisateur sont partagées par défaut.

Certains serveurs ODBC, tels que Microsoft SQL Server, n’autorisent pas les transactions simultanées sur une seule connexion. Si vous devez avoir plusieurs transactions à la fois en attente sur une telle base de données, affectez la valeur TRUE à la propriété IsolateODBCTrans sur chaque espace de travail dès que vous l’ouvrez. Cela force une connexion ODBC distincte pour chaque espace de travail.

##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout

Appelez cette fonction membre pour définir la valeur de la propriété DAO LoginTimeout de l’espace de travail.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Paramètres

*nSeconds*<br/>
Nombre de secondes avant qu’une erreur ne se produise lorsque vous tentez de vous connecter à une base de données ODBC.

### <a name="remarks"></a>Notes

Cette valeur représente le nombre de secondes avant qu’une erreur se produise lorsque vous tentez de vous connecter à une base de données ODBC. Le paramètre LoginTimeout par défaut est de 20 secondes. Lorsque LoginTimeout a la valeur 0, aucun délai d’attente n’est atteint et la communication avec la source de données peut cesser de répondre.

Lorsque vous tentez de vous connecter à une base de données ODBC, par exemple Microsoft SQL Server, la connexion peut échouer en raison d’erreurs réseau ou du fait que le serveur n’est pas en cours d’exécution. Au lieu d’attendre que les 20 secondes par défaut se connectent, vous pouvez spécifier la durée pendant laquelle le moteur de base de données attend avant de générer une erreur. La connexion au serveur se produit implicitement dans le cadre d’un certain nombre d’événements différents, tels que l’exécution d’une requête sur une base de données de serveur externe. La valeur du délai d’attente est déterminée par le paramètre actuel de la propriété LoginTimeout.

Pour obtenir des informations connexes, consultez la rubrique « propriété LoginTimeout » dans l’aide de DAO.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset, classe](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef, classe](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef, classe](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException, classe](../../mfc/reference/cdaoexception-class.md)
