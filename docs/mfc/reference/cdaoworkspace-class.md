---
title: Classe de CDaoWorkspace | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b249f8069ba12772d21d170b67236a5f013290ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace (classe)
Gère une session de base de données nommée et protégée par mot de passe, de la connexion à la déconnexion, pour un seul utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoWorkspace : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Construit un objet de l’espace de travail. Ensuite, appelez **créer** ou **ouvrir**.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoWorkspace::Append](#append)|Ajoute un espace de travail nouvellement créé à la collection d’espaces de travail du moteur de base de données.|  
|[CDaoWorkspace::BeginTrans](#begintrans)|Commence une nouvelle transaction, qui s’applique à toutes les bases de données ouvertes dans l’espace de travail.|  
|[CDaoWorkspace::Close](#close)|Ferme l’espace de travail et tous les objets qu’il contient. Transactions en attente sont annulées.|  
|[CDaoWorkspace::CommitTrans](#committrans)|Termine la transaction actuelle et enregistre les modifications.|  
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Compacte (ou les doublons) une base de données.|  
|[CDaoWorkspace::Create](#create)|Crée un nouvel objet d’espace de travail DAO.|  
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Retourne le nombre d’objets de base de données DAO dans la collection de bases de données de l’espace de travail.|  
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Retourne des informations sur une base de données DAO spécifié défini dans la collection de bases de données de l’espace de travail.|  
|[CDaoWorkspace::GetIniPath](#getinipath)|Retourne des paramètres de l’initialisation du moteur de l’emplacement de la base de données Microsoft Jet dans le Registre Windows.|  
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Retourne une valeur qui indique si plusieurs transactions qui impliquent la même source de données ODBC sont isolées via plusieurs connexions à la source de données.|  
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Retourne le nombre de secondes avant qu’une erreur se produit lorsque l’utilisateur tente de se connecter à une base de données ODBC.|  
|[CDaoWorkspace::GetName](#getname)|Retourne le nom défini par l’utilisateur pour l’objet de l’espace de travail.|  
|[CDaoWorkspace::GetUserName](#getusername)|Retourne que le nom d’utilisateur spécifié lorsque l’espace de travail a été créé. Ceci est le nom du propriétaire de l’espace de travail.|  
|[CDaoWorkspace::GetVersion](#getversion)|Retourne une chaîne qui contient la version du moteur de base de données associé à l’espace de travail.|  
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Retourne le nombre d’objets d’espace de travail DAO dans la collection d’espaces de travail du moteur de base de données.|  
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Retourne des informations sur un espace de travail DAO spécifié défini dans la collection d’espaces de travail du moteur de base de données.|  
|[CDaoWorkspace::Idle](#idle)|Permet au moteur de base de données effectuer des tâches en arrière-plan.|  
|[CDaoWorkspace::IsOpen](#isopen)|Retourne zéro si l’espace de travail s’ouvre.|  
|[CDaoWorkspace::Open](#open)|Explicitement ouvre un objet de l’espace de travail associé avec un espace de travail par défaut de DAO.|  
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Tente de réparer une base de données endommagée.|  
|[CDaoWorkspace::Rollback](#rollback)|Termine la transaction actuelle et ne pas enregistrer les modifications.|  
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Définit le mot de passe par le moteur de base de données lorsqu’un objet de l’espace de travail est créé sans mot de passe spécifique.|  
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Définit le nom d’utilisateur par le moteur de base de données lorsqu’un objet de l’espace de travail est créé sans un nom d’utilisateur spécifique.|  
|[CDaoWorkspace::SetIniPath](#setinipath)|Définit des paramètres de l’initialisation du moteur de l’emplacement de la base de données Microsoft Jet dans le Registre Windows.|  
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Spécifie si plusieurs transactions qui impliquent la même source de données ODBC sont isolées en forçant plusieurs connexions à la source de données.|  
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Définit le nombre de secondes avant qu’une erreur se produit lorsque l’utilisateur tente de se connecter à une source de données ODBC.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Pointe vers l’objet d’espace de travail DAO sous-jacent.|  
  
## <a name="remarks"></a>Notes  
 Dans la plupart des cas, vous n’aurez pas plusieurs espaces de travail, et vous ne devez pas créer des objets de l’espace de travail explicites ; Lorsque vous ouvrez des objets de base de données et le jeu d’enregistrements, ils utilisent d’espace de travail par défaut de DAO. Toutefois, si nécessaire, vous pouvez exécuter plusieurs sessions à la fois en créant des objets de l’espace de travail supplémentaires. Chaque objet de l’espace de travail peut contenir plusieurs objets de base de données ouverte dans sa propre collection de bases de données. Dans les MFC, un espace de travail est principalement un gestionnaire de transactions, en spécifiant un ensemble de bases de données ouvertes dans le même « espace de transaction ».  
  
> [!NOTE]
>  Les classes de base de données DAO sont distincts des classes de base de données MFC basées sur ODBC Open Database Connectivity (). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». En général, les classes MFC basées sur DAO sont plus efficaces que les classes MFC basées sur ODBC. Les classes DAO accéder aux données via le moteur de base de données Microsoft Jet, y compris des pilotes ODBC. Ils prennent également en charge des opérations de langage de définition de données (DDL), telles que la création de bases de données et ajouter des tables et des champs via les classes, sans avoir à appeler DAO directement.  
  
## <a name="capabilities"></a>Fonctionnalités  
 Classe `CDaoWorkspace` fournit les éléments suivants :  
  
-   Accès explicite, si nécessaire, à un espace de travail par défaut, créé par l’initialisation du moteur de base de données. En général vous utilisez espace de travail par défaut de DAO d’implicitement en créant des objets de base de données et le jeu d’enregistrements.  
  
-   Un espace de transaction dans laquelle les transactions s’appliquent à toutes les bases de données s’ouvre dans l’espace de travail. Vous pouvez créer des espaces de travail supplémentaires pour gérer les espaces de transaction distincte.  
  
-   Une interface de nombreuses propriétés du moteur de base de données Microsoft Jet sous-jacente (voir les fonctions membres statiques). Ouverture ou de création d’un espace de travail ou d’appel d’une fonction membre statique avant d’ouvrir ou créer, initialise le moteur de base de données.  
  
-   Accès à la collection d’espaces de travail du moteur de base de données, qui stocke tous les espaces de travail actifs qui ont été ajoutées. Vous pouvez également créer et utiliser des espaces de travail sans en les ajoutant à la collection.  
  
## <a name="security"></a>Sécurité  
 MFC n’implémente pas les regroupements d’utilisateurs et groupes dans DAO, qui sont utilisés pour contrôler la sécurité. Si vous avez besoin de ces aspects de DAO, vous devez programmer vous-même via des appels directs aux interfaces DAO. Pour plus d’informations, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## <a name="usage"></a>Utilisation  
 Vous pouvez utiliser la classe `CDaoWorkspace` pour :  
  
-   Ouvrir explicitement l’espace de travail par défaut.  
  
     Généralement, l’utilisation de l’espace de travail par défaut est implicite, lorsque vous ouvrez un nouveau [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objets. Mais vous devrez peut-être accéder de manière explicite, par exemple, pour les propriétés du moteur de base de données access ou de la collection d’espaces de travail. Consultez « Utilisation implicite de l’espace de travail par défaut » ci-dessous.  
  
-   Créer de nouveaux espaces de travail. Appelez [Append](#append) si vous souhaitez les ajouter à la collection d’espaces de travail.  
  
-   Ouvrir un espace de travail existant dans la collection d’espaces de travail.  
  
 Création d’un espace de travail qui n’existe pas déjà dans les espaces de travail de collection est décrite sous la [créer](#create) fonction membre. Objets de l’espace de travail ne sont pas conservent en aucune façon entre les sessions de moteur de base de données TSO. Si votre application est liée statiquement MFC, fin de l’application n’initialise pas le moteur de base de données. Si votre application est lié dynamiquement à MFC, le moteur de base de données n’est pas initialisé lors de la DLL MFC est déchargée.  
  
 Explicitement ouverture de l’espace de travail par défaut ou l’ouverture d’un espace de travail existant dans la collection d’espaces de travail, est décrite sous la [ouvrir](#open) fonction membre.  
  
 Terminer une session de l’espace de travail par la fermeture de l’espace de travail avec le [fermer](#close) fonction membre. **Fermer** ferme toutes les bases de données que vous n'avez pas fermé précédemment, restaurant les transactions non validées.  
  
## <a name="transactions"></a>Transactions  
 DAO gère des transactions au niveau de l’espace de travail ; Par conséquent, les transactions sur un espace de travail avec plusieurs bases de données ouvertes s’appliquent à toutes les bases de données. Par exemple, si deux bases de données ont des mises à jour non validées et que vous appelez [CommitTrans](#committrans), toutes les mises à jour sont validées. Si vous souhaitez limiter les transactions pour une base de données, vous avez besoin d’un objet de l’espace de travail distinct pour elle.  
  
## <a name="implicit-use-of-the-default-workspace"></a>Utilisation implicite de l’espace de travail par défaut  
 MFC utilise un espace de travail de DAO par défaut implicitement dans les circonstances suivantes :  
  
-   Si vous créez un nouveau `CDaoDatabase` de l’objet, mais ne le faites pas via un existant `CDaoWorkspace` objet MFC crée un objet de l’espace de travail temporaire, qui correspond à l’espace de travail par défaut de DAO. Si vous le faites pour plusieurs bases de données, tous les objets de base de données sont associés à l’espace de travail par défaut. Vous pouvez accéder à espace de travail de base de données via un `CDaoDatabase` membre de données.  
  
-   De même, si vous créez un `CDaoRecordset` objet sans fournir un pointeur vers un `CDaoDatabase` de l’objet, MFC crée un objet de base de données temporaire et, par extension, un objet de l’espace de travail temporaire. Vous pouvez accéder à base de données d’un jeu d’enregistrements et indirectement son espace de travail, via un `CDaoRecordset` membre de données.  
  
## <a name="other-operations"></a>Autres opérations  
 Autres opérations de base de données sont également fournies, telles que la réparation d’une base de données endommagée ou le compactage d’une base de données.  
  
 Pour plus d’informations sur l’appel de DAO directement et sur la sécurité DAO, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdao.h  
  
##  <a name="append"></a>  CDaoWorkspace::Append  
 Appelez cette fonction membre après avoir appelé [créer](#create).  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Notes  
 **Ajouter** ajoute un objet de l’espace de travail nouvellement créé à la collection d’espaces de travail du moteur de base de données. Espaces de travail ne sont pas conservés entre les sessions du moteur de base de données ; elles sont stockées uniquement dans la mémoire, pas sur le disque. Vous n’avez pas à ajouter un espace de travail ; Si vous ne le faites pas, vous pouvez toujours l’utiliser.  
  
 Un espace de travail ajouté reste dans la collection d’espaces de travail, active, un état ouvert, jusqu'à ce que vous appeliez son [fermer](#close) fonction membre.  
  
 Pour plus d’informations, consultez la rubrique « Ajout de la méthode » dans l’aide de DAO.  
  
##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans  
 Appelez cette fonction membre pour initier une transaction.  
  
```  
void BeginTrans();
```  
  
### <a name="remarks"></a>Notes  
 Après avoir appelé **BeginTrans**, que vous apportez à votre structure de données ou de la base de données prendre effet lorsque vous validez la transaction. L’espace de travail définit un espace de transaction unique, la transaction s’applique à toutes les bases de données ouvertes dans l’espace de travail. Il existe deux façons de terminer la transaction :  
  
-   Appelez le [CommitTrans](#committrans) fonction membre à valider la transaction et enregistrer les modifications apportées à la source de données.  
  
-   Ou appelez le [restauration](#rollback) fonction membre d’annuler la transaction.  
  
 La fermeture de l’objet de l’espace de travail ou un objet de base de données pendant qu’une transaction est en attente annule toutes les transactions en attente.  
  
 Si vous avez besoin isoler les transactions sur une source de données ODBC à partir de ceux qui sont sur une autre source de données ODBC, consultez le [SetIsolateODBCTrans](#setisolateodbctrans) fonction membre.  
  
##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace  
 Construit un objet `CDaoWorkspace`.  
  
```  
CDaoWorkspace();
```  
  
### <a name="remarks"></a>Notes  
 Après avoir construit l’objet C++, vous avez deux options :  
  
-   Appelez l’objet [ouvrir](#open) fonction membre pour ouvrir l’espace de travail par défaut ou d’ouvrir un objet existant dans la collection d’espaces de travail.  
  
-   Ou d’appeler l’objet [créer](#create) fonction membre pour créer un nouvel objet d’espace de travail DAO. Cela démarre explicitement une nouvelle session d’espace de travail, vous pouvez faire référence à via le `CDaoWorkspace` objet. Après avoir appelé **créer**, vous pouvez appeler [Append](#append) si vous souhaitez ajouter l’espace de travail à la collection d’espaces de travail du moteur de base de données.  
  
 Consultez la vue d’ensemble de la classe pour [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) pour plus d’informations sur lorsque vous devez créer explicitement un `CDaoWorkspace` objet. En règle générale, vous utilisez des espaces de travail créés implicitement lorsque vous ouvrez un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet sans spécifier un espace de travail ou lorsque vous ouvrez un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet sans spécifier un objet de base de données. Objets DAO de MFC créées de cette manière utilisent par défaut espace de travail DAO, qui est créé qu’une seule fois et réutilisée.  
  
 Pour libérer un espace de travail et les objets qu’elle contient, appelez l’objet de l’espace de travail [fermer](#close) fonction membre.  
  
##  <a name="close"></a>  CDaoWorkspace::Close  
 Appelez cette fonction membre pour fermer l’objet de l’espace de travail.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Notes  
 Fermeture d’un objet de l’espace de travail ouvert libère l’objet DAO sous-jacent et, si l’espace de travail est un membre de la collection d’espaces de travail, il le supprime de la collection. Appel de **fermer** est bonne pratique de programmation.  
  
> [!CAUTION]
>  Fermeture d’un objet de l’espace de travail ferme toutes les bases de données ouvertes dans l’espace de travail. Ainsi, tous les jeux d’enregistrements ouverts dans les bases de données qui est également fermé et toutes les modifications en attente ou les mises à jour sont annulées. Pour plus d’informations, consultez la [CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close), et [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) fonctions membres.  
  
 Objets de l’espace de travail ne sont pas permanents ; ils n’existent que lorsqu’il existent des références à ceux-ci. Cela signifie que lorsque la session du moteur de base de données se termine, l’espace de travail et de sa collection de bases de données ne sont pas conservent. Vous devez recréer les pour la session suivante en l’ouvrant à nouveau de votre espace de travail et les bases de données.  
  
 Pour plus d’informations, consultez la rubrique « Close (méthode) » dans l’aide de DAO.  
  
##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans  
 Appelez cette fonction membre pour valider une transaction, l’enregistrement d’un groupe de modifications et mises à jour une ou plusieurs bases de données dans l’espace de travail.  
  
```  
void CommitTrans();
```  
  
### <a name="remarks"></a>Notes  
 Une transaction est composée d’une série de modifications apportées aux données de la base de données ou sa structure, en commençant par un appel à [BeginTrans](#begintrans). Lorsque vous terminez la transaction, soit valide ou restaure (annuler les modifications) avec [restauration](#rollback). Par défaut, sans transactions, les mises à jour des enregistrements sont immédiatement validées. Appel de **BeginTrans** provoque l’engagement de mises à jour peut être différé jusqu'à ce que vous appeliez **CommitTrans**.  
  
> [!CAUTION]
>  Dans un espace de travail, les transactions sont toujours globales dans l’espace de travail et ne sont pas limitées à qu’une seule base de données ou un recordset. Si vous effectuez des opérations sur plus d’une base de données ou un recordset dans une transaction de l’espace de travail, **CommitTrans** validations tout en attente de mises à jour, et **restauration** restaure toutes les opérations sur ces bases de données et jeux d’enregistrements.  
  
 Lorsque vous fermez une base de données ou d’un espace de travail avec des transactions en attente, les transactions sont toutes annulées.  
  
> [!NOTE]
>  Ce n’est pas un mécanisme de validation en deux phases. Si une mise à jour ne parvient pas à valider, d’autres encore valide.  
  
##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase  
 Appelez cette fonction membre pour compacter un spécifié Microsoft Jet (. Base de données MDB).  
  
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
 `lpszSrcName`  
 Le nom d’un objet, fermé la base de données. Il peut être un chemin d’accès complet et le nom de fichier, tel que « C:\\\MYDB. MDB ». Si le nom de fichier a une extension, vous devez la spécifier. Si votre réseau prend en charge la convention d’affectation de noms uniforme (UNC), vous pouvez également spécifier un chemin d’accès réseau, tels que «\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ». (Deux barres obliques inverses sont nécessaires dans les chaînes de chemin d’accès, car «\\» est le caractère d’échappement de C++.)  
  
 `lpszDestName`  
 Le chemin d’accès complet de la base de données compactée que vous créez. Vous pouvez également spécifier un chemin d’accès réseau en tant qu’avec `lpszSrcName`. Vous ne pouvez pas utiliser le `lpszDestName` pour spécifier le même fichier de base de données en tant qu’argument `lpszSrcName`.  
  
 `lpszPassword`  
 Un mot de passe, lorsque vous souhaitez compacter une base de données protégé par mot de passe. Notez que si vous utilisez la version de `CompactDatabase` qui accepte un mot de passe, vous devez fournir tous les paramètres. En outre, comme il s’agit d’un paramètre de connexion, il requiert mise en forme spéciale, comme suit : ; PWD = `lpszPassword`. Par exemple : ; PWD = « Bonne ». (Le point-virgule de début est obligatoire.)  
  
 `lpszLocale`  
 Permet de spécifier l’ordre de classement pour la création d’une expression de chaîne `lpszDestName`. Si vous omettez cet argument en acceptant la valeur par défaut **dbLangGeneral** (voir ci-dessous), les paramètres régionaux de la base de données sont identique à celle de l’ancienne base de données. Les valeurs possibles sont :  
  
- **dbLangGeneral** anglais, allemand, Français, portugais, italien et Espagnol moderne  
  
- **dbLangArabic** arabe  
  
- **dbLangCyrillic** russe  
  
- **dbLangCzech** tchèque  
  
- **dbLangDutch** néerlandais  
  
- **dbLangGreek** grec  
  
- **dbLangHebrew** hébreu  
  
- **dbLangHungarian** hongrois  
  
- **dbLangIcelandic** islandais  
  
- **dbLangNordic** langues scandinaves (moteur Microsoft Jet de base de données version 1.0 uniquement)  
  
- **dbLangNorwdan** norvégien et danois  
  
- **dbLangPolish** polonais  
  
- **dbLangSpanish** espagnol  
  
- **dbLangSwedfin** suédois et finnois  
  
- **dbLangTurkish** turc  
  
 `nOptions`  
 Indique une ou plusieurs options pour la base de données cible, `lpszDestName`. Si vous omettez cet argument en acceptant la valeur par défaut, le `lpszDestName` aura le même chiffrement et la même version que `lpszSrcName`. Vous pouvez combiner la **dbEncrypt** ou **dbDecrypt** option avec une des options de version à l’aide de l’opérateur OR au niveau du bit. Les valeurs possibles, qui spécifient un format de base de données, pas une version du moteur de base de données, sont :  
  
- **dbEncrypt** chiffrer la base de données pendant le compactage.  
  
- **dbDecrypt** déchiffrer la base de données pendant le compactage.  
  
- **dbVersion10** créer une base de données qui utilise la version de moteur de base de données Microsoft Jet 1.0 pendant le compactage.  
  
- **dbVersion11** créer une base de données qui utilise la version de moteur de base de données Microsoft Jet 1.1 pendant le compactage.  
  
- **dbVersion20** créer une base de données qui utilise la version de moteur de base de données Microsoft Jet 2.0 pendant le compactage.  
  
- **dbVersion30** créer une base de données qui utilise la version de moteur de base de données Microsoft Jet 3.0 pendant le compactage.  
  
 Vous pouvez utiliser **dbEncrypt** ou **dbDecrypt** dans l’argument options pour spécifier s’il faut chiffrer ou déchiffrer la base de données car elle est compressée. Si vous omettez la constante de chiffrement ou si vous incluez les deux **dbDecrypt** et **dbEncrypt**, `lpszDestName` aura le même chiffrement que `lpszSrcName`. Vous pouvez utiliser une des constantes de version dans l’argument options pour spécifier la version du format de données pour la base de données compressée. Cette constante affecte uniquement la version du format de données de `lpszDestName`. Vous pouvez spécifier qu’une seule constante de version. Si vous l’omettez, `lpszDestName` aura la même version que `lpszSrcName`. Vous pouvez compresser `lpszDestName` uniquement vers une version identique ou ultérieure à celle de `lpszSrcName`.  
  
> [!CAUTION]
>  Si une base de données n’est pas chiffré, il est possible, même si vous implémentez la sécurité de l’utilisateur/mot de passe, pour directement lire le fichier binaire sur disque qui constitue la base de données.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous modifiez des données dans une base de données, le fichier de base de données peut se fragmenter et utiliser plus d’espace disque que nécessaire. Régulièrement, vous devez compacter votre base de données pour défragmenter le fichier de base de données. La base de données compactée est généralement plus petite. Vous pouvez également choisir de modifier l’ordre de classement, le chiffrement ou la version du format de données pendant que vous copiez et compactez la base de données.  
  
> [!CAUTION]
>  Le `CompactDatabase` fonction membre ne convertira pas le correctement une base de données Microsoft Access à partir d’une version à l’autre. Seul le format de données est converti. Objets définis par l’accès Microsoft, tels que les formulaires et les États, ne sont pas convertis. Toutefois, les données sont correctement converties.  
  
> [!TIP]
>  Vous pouvez également utiliser `CompactDatabase` pour copier un fichier de base de données.  
  
 Pour plus d’informations sur le compactage des bases de données, consultez la rubrique « CompactDatabase méthode » dans l’aide de DAO.  
  
##  <a name="create"></a>  CDaoWorkspace::Create  
 Appelez cette fonction membre pour créer un nouvel objet d’espace de travail DAO et l’associer à la bibliothèque MFC `CDaoWorkspace` objet.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszUserName,  
    LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszName`  
 Une chaîne en utilisant jusqu'à 14 caractères qui identifie de façon unique le nouvel objet de l’espace de travail. Vous devez fournir un nom. Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
 *lpszUserName*  
 Le nom d’utilisateur du propriétaire de l’espace de travail. Pour la configuration requise, consultez le `lpszDefaultUser` paramètre à la [SetDefaultUser](#setdefaultuser) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété de nom d’utilisateur » dans l’aide de DAO.  
  
 `lpszPassword`  
 Le mot de passe pour le nouvel objet de l’espace de travail. Un mot de passe peut comporter jusqu'à 14 caractères et peut contenir n’importe quel caractère sauf ASCII 0 (null). Les mots de passe respectent la casse. Pour plus d’informations, consultez la rubrique « Propriété de mot de passe » dans l’aide de DAO.  
  
### <a name="remarks"></a>Notes  
 Le processus de création générale est la suivante :  
  
1.  Construire un [CDaoWorkspace](#cdaoworkspace) objet.  
  
2.  Appelez l’objet **créer** fonction membre pour créer l’espace de travail DAO sous-jacent. Vous devez spécifier un nom d’espace de travail.  
  
3.  Vous pouvez également appeler [Append](#append) si vous souhaitez ajouter l’espace de travail à la collection d’espaces de travail du moteur de base de données. Vous pouvez travailler avec l’espace de travail sans l’ajouter.  
  
 Après le **créer** appel, l’objet de l’espace de travail est dans un état ouvert, prêt à être utilisé. Vous n’appelez pas **ouvrir** après **créer**. Vous n’appelez pas **créer** si l’espace de travail existe déjà dans la collection d’espaces de travail. **Créer** initialise le moteur de base de données s’il n’a pas déjà été initialisé pour votre application.  
  
##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount  
 Appelez cette fonction membre pour récupérer le nombre d’objets de base de données DAO dans la collection de bases de données de l’espace de travail, le nombre de bases de données ouvertes dans l’espace de travail.  
  
```  
short GetDatabaseCount();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de bases de données ouvertes dans l’espace de travail.  
  
### <a name="remarks"></a>Notes  
 `GetDatabaseCount` est utile si vous devez effectuer une boucle sur toutes les bases de données définies dans la collection de bases de données de l’espace de travail. Pour obtenir plus d’informations sur une base de données dans la collection, consultez [GetDatabaseInfo](#getdatabaseinfo). Utilisation typique consiste à appeler `GetDatabaseCount` pour le nombre de bases de données ouvertes, puis utiliser ce nombre comme un index de boucle pour les appels répétés à `GetDatabaseInfo`.  
  
##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo  
 Appelez cette fonction membre pour obtenir les différents types d’informations sur une base de données est ouverte dans l’espace de travail.  
  
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
 `nIndex`  
 Index de base zéro de l’objet de base de données dans la collection de bases de données de l’espace de travail, pour la recherche par index.  
  
 `dbinfo`  
 Une référence à un [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) objet qui retourne les informations demandées.  
  
 `dwInfoOptions`  
 Options qui spécifient les informations sur la base de données à récupérer. Les options disponibles sont répertoriées ici, ainsi que leur cause la fonction retourne :  
  
- `AFX_DAO_PRIMARY_INFO` (Par défaut) Nom mis à jour, Transactions  
  
- `AFX_DAO_SECONDARY_INFO` Informations primaire plues : délai de requête de Version, l’ordre de classement,  
  
- `AFX_DAO_ALL_INFO` Informations primaires et secondaires plues : se connecter  
  
 `lpszName`  
 Le nom de l’objet de base de données, pour la recherche par nom. Le nom est une chaîne qui identifie de façon unique le nouvel objet de l’espace de travail en utilisant jusqu'à 14 caractères.  
  
### <a name="remarks"></a>Notes  
 Une version de la fonction vous permet de rechercher une base de données par index. L’autre version vous permet de rechercher une base de données par nom.  
  
 Pour obtenir une description des informations retournées dans `dbinfo`, consultez la [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) structure. Cette structure possède des membres qui correspondent aux éléments d’informations répertoriés ci-dessus dans la description de `dwInfoOptions`. Lorsque vous demandez des informations à un niveau, vous obtenez des informations pour les niveaux de préalables.  
  
##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath  
 Appelez cette fonction membre pour obtenir des paramètres de l’initialisation du moteur dans le Registre Windows de l’emplacement de la base de données Microsoft Jet.  
  
```  
static CString PASCAL GetIniPath();
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’emplacement de Registre.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser l’emplacement pour obtenir des informations sur les paramètres pour le moteur de base de données. Les informations retournées sont en fait le nom d’une sous-clé de Registre.  
  
 Pour plus d’informations, consultez les rubriques « Propriété IniPath » et « Personnalisation de Windows Registre paramètres pour accès aux données » dans l’aide de DAO.  
  
##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans  
 Appelez cette fonction membre pour obtenir la valeur actuelle de la propriété DAO IsolateODBCTrans pour l’espace de travail.  
  
```  
BOOL GetIsolateODBCTrans();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les transactions ODBC sont isolées ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Dans certaines situations, vous devrez peut-être avoir plusieurs transactions simultanées en cours sur la même base de données ODBC. Pour ce faire, vous devez ouvrir un espace de travail distinct pour chaque transaction. Gardez à l’esprit que bien que chaque espace de travail peut avoir sa propre connexion ODBC à la base de données, cela ralentit les performances du système. Étant donné que l’isolation des transactions est généralement pas nécessaire, les connexions ODBC à partir de plusieurs objets d’espace de travail ouverts par le même utilisateur sont partagées par défaut.  
  
 Certains serveurs ODBC, telles que Microsoft SQL Server, n’autorisent pas les transactions simultanées sur une seule connexion. Si vous avez besoin d’avoir plusieurs transactions en cours sur une base de données, définissez la propriété IsolateODBCTrans **TRUE** sur chaque espace de travail dès que vous l’ouvrez. Cette opération force une connexion ODBC séparée pour chaque espace de travail.  
  
 Pour plus d’informations, consultez la rubrique « Propriété IsolateODBCTrans » dans l’aide de DAO.  
  
##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout  
 Appelez cette fonction membre pour obtenir la valeur actuelle de la propriété DAO LoginTimeout pour l’espace de travail.  
  
```  
static short PASCAL GetLoginTimeout();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de secondes avant qu’une erreur se produit lorsque vous essayez de vous connecter à une base de données ODBC.  
  
### <a name="remarks"></a>Notes  
 Cette valeur représente le nombre de secondes avant qu’une erreur se produit lorsque vous essayez de vous connecter à une base de données ODBC. La valeur par défaut LoginTimeout est 20 secondes. Lorsque LoginTimeout est définie sur 0, aucun délai d’expiration se produit et la communication avec la source de données peut cesser de répondre.  
  
 Lorsque vous tentez de vous connecter à une base de données ODBC, telles que Microsoft SQL Server, la connexion peut échouer en raison d’erreurs réseau ou parce que le serveur n’est pas en cours d’exécution. Au lieu d’attendre la valeur par défaut 20 secondes pour se connecter, vous pouvez spécifier la durée pendant laquelle le moteur de base de données doit attendre une erreur produit. La connexion au serveur se produit implicitement dans le cadre d’un nombre d’événements, telles que l’exécution d’une requête sur une base de données du serveur externe.  
  
 Pour plus d’informations, consultez la rubrique « Propriété LoginTimeout » dans l’aide de DAO.  
  
##  <a name="getname"></a>  CDaoWorkspace::GetName  
 Appelez cette fonction membre pour obtenir le nom défini par l’utilisateur de l’espace de travail actif DAO objet sous-jacent le `CDaoWorkspace` objet.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom défini par l’utilisateur de l’objet d’espace de travail DAO.  
  
### <a name="remarks"></a>Notes  
 Le nom est utile pour accéder à l’objet d’espace de travail DAO dans la collection d’espaces de travail du moteur de base de données par nom.  
  
 Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
##  <a name="getusername"></a>  CDaoWorkspace::GetUserName  
 Appelez cette fonction membre pour obtenir le nom du propriétaire de l’espace de travail.  
  
```  
CString GetUserName();
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui représente le propriétaire de l’objet de l’espace de travail.  
  
### <a name="remarks"></a>Notes  
 Pour obtenir ou définir les autorisations pour le propriétaire de l’espace de travail, appeler DAO directement pour vérifier le paramètre de propriété autorisations ; Ce paramètre détermine les autorisations dont dispose cet utilisateur. Pour travailler avec des autorisations, vous avez besoin d’un système. Fichier de l’Assistant Débogage MANAGÉ.  
  
 Pour plus d’informations sur l’appel de DAO directement, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Pour plus d’informations, consultez la rubrique « Propriété de nom d’utilisateur » dans l’aide de DAO.  
  
##  <a name="getversion"></a>  CDaoWorkspace::GetVersion  
 Appelez cette fonction membre pour déterminer la version du moteur de base de données Microsoft Jet en cours d’utilisation.  
  
```  
static CString PASCAL GetVersion();
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui indique la version du moteur de base de données associé à l’objet.  
  
### <a name="remarks"></a>Notes  
 La valeur renvoyée représente le numéro de version sous la forme « major.minor » ; par exemple, « 3.0 ». Le numéro de version du produit (par exemple, version 3.0) comprend le numéro de version (3), un point et le numéro de version (0).  
  
 Pour plus d’informations, consultez la rubrique « Propriété de Version » dans l’aide de DAO.  
  
##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount  
 Appelez cette fonction membre pour récupérer le nombre d’objets d’espace de travail DAO dans la collection d’espaces de travail du moteur de base de données.  
  
```  
short GetWorkspaceCount();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nombre d’espaces de travail ouverts dans la collection d’espaces de travail.  
  
### <a name="remarks"></a>Notes  
 Ce nombre n’inclut pas les espaces de travail ouverts ne pas ajoutés à la collection. `GetWorkspaceCount` est utile si vous devez effectuer une boucle sur tous les espaces de travail définis dans la collection d’espaces de travail. Pour obtenir plus d’informations sur un espace de travail donné dans la collection, consultez [GetWorkspaceInfo](#getworkspaceinfo). Utilisation typique consiste à appeler `GetWorkspaceCount` pour le nombre d’espaces de travail ouverts, puis utiliser ce nombre comme un index de boucle pour les appels répétés à `GetWorkspaceInfo`.  
  
##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo  
 Appelez cette fonction membre pour obtenir les différents types d’informations sur un espace de travail est ouvert dans la session.  
  
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
 `nIndex`  
 Index de base zéro de l’objet de base de données dans la collection d’espaces de travail, pour la recherche par index.  
  
 `wkspcinfo`  
 Une référence à un [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) objet qui retourne les informations demandées.  
  
 `dwInfoOptions`  
 Options qui spécifient les informations sur l’espace de travail à récupérer. Les options disponibles sont répertoriées ici, ainsi que leur cause la fonction retourne :  
  
- `AFX_DAO_PRIMARY_INFO` (Par défaut) Nom  
  
- `AFX_DAO_SECONDARY_INFO` Informations primaire plues : nom d’utilisateur  
  
- `AFX_DAO_ALL_INFO` Informations primaires et secondaires plues : isoler un ODBCTrans  
  
 `lpszName`  
 Le nom de l’objet de l’espace de travail, pour la recherche par nom. Le nom est une chaîne qui identifie de façon unique le nouvel objet de l’espace de travail en utilisant jusqu'à 14 caractères.  
  
### <a name="remarks"></a>Notes  
 Pour obtenir une description des informations retournées dans `wkspcinfo`, consultez la [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) structure. Cette structure possède des membres qui correspondent aux éléments d’informations répertoriés ci-dessus dans la description de `dwInfoOptions`. Lorsque vous demandez des informations à un niveau, vous obtenez des informations pour ainsi des niveaux précédents.  
  
##  <a name="idle"></a>  CDaoWorkspace::Idle  
 Appelez **inactif** pour fournir le moteur de base de données avec la possibilité d’effectuer des tâches en arrière-plan qui ne peuvent pas être à jour en raison de l’intensité du traitement des données.  
  
```  
static void PASCAL Idle(int nAction = dbFreeLocks);
```  
  
### <a name="parameters"></a>Paramètres  
 `nAction`  
 Action à exécuter pendant le traitement inactif. Actuellement la seule action valide est **dbFreeLocks**.  
  
### <a name="remarks"></a>Notes  
 Cela est souvent le cas dans les environnements multitâche multi-utilisateur dans lequel il n’est pas suffisamment le temps de traitement en arrière-plan pour conserver tous les enregistrements dans un jeu d’enregistrements actuel.  
  
> [!NOTE]
>  Appel de **inactif** n’est pas nécessaire avec les bases de données créées avec la version 3.0 du moteur de base de données Microsoft Jet. Utilisez **inactif** uniquement pour les bases de données créées avec les versions antérieures.  
  
 En règle générale, verrous en lecture sont supprimés et les données dans des objets de jeu d’enregistrements de type local est mis à jour uniquement quand aucune autre action (y compris les mouvements de souris) ne se produisent. Si vous appelez régulièrement **inactif**, vous fournissez le moteur de base de données avec le temps de découvrir les tâches de traitement en libérant un arrière-plan inutiles des verrous de lecture. En spécifiant le **dbFreeLocks** constante en tant qu’argument diffère le traitement jusqu'à ce que tous les verrous de lecture sont libérés.  
  
 Cette fonction membre n’est pas nécessaire dans les environnements à utilisateur unique, sauf si plusieurs instances d’une application en cours d’exécution. Le **inactif** fonction membre peut améliorer les performances dans un environnement multi-utilisateur, car elle force le moteur de base de données à vider les données sur le disque, la libération des verrous de la mémoire. Vous pouvez également libérer des verrous en lecture en intégrant les opérations d’une transaction.  
  
 Pour plus d’informations, consultez la rubrique « Des temps d’inactivité de la méthode » dans l’aide de DAO.  
  
##  <a name="isopen"></a>  CDaoWorkspace::IsOpen  
 Appelez cette fonction membre pour déterminer si le `CDaoWorkspace` objet est ouvert, autrement dit, si l’objet MFC a été initialisé par un appel à [ouvrir](#open) ou un appel à [créer](#create).  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’objet de l’espace de travail est ouvert ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez appeler les du membre de fonctions d’un espace de travail est dans un état ouvert.  
  
##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace  
 Pointeur vers l’objet d’espace de travail DAO sous-jacent.  
  
### <a name="remarks"></a>Notes  
 Utilisez ce membre de données si vous avez besoin un accès direct à l’objet DAO sous-jacent. Vous pouvez appeler des interfaces de l’objet DAO via ce pointeur.  
  
 Pour plus d’informations sur l’accès à des objets DAO directement, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
##  <a name="open"></a>  CDaoWorkspace::Open  
 Explicitement ouvre un objet de l’espace de travail associé avec un espace de travail par défaut de DAO.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszName`  
 Le nom de l’objet d’espace de travail DAO pour ouvrir, une chaîne qui identifie de façon unique l’espace de travail en utilisant jusqu'à 14 caractères. Acceptez la valeur par défaut **NULL** à ouvrir explicitement l’espace de travail par défaut. Pour nommer la configuration requise, consultez le `lpszName` paramètre [créer](#create). Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
### <a name="remarks"></a>Notes  
 Après avoir construit un `CDaoWorkspace` d’objet, appelez cette fonction membre pour effectuer l’une des opérations suivantes :  
  
-   Ouvrir explicitement l’espace de travail par défaut. Passer **NULL** pour `lpszName`.  
  
-   Ouvrir un existant `CDaoWorkspace` objet, un membre de la collection d’espaces de travail, par nom. Passez un nom valide pour un objet d’espace de travail existant.  
  
 **Ouvrez** place l’objet de l’espace de travail en état ouvert et initialise également le moteur de base de données s’il n’a pas déjà été initialisé pour votre application.  
  
 Bien que plusieurs `CDaoWorkspace` membre fonctions peuvent être appelées uniquement après l’ouverture de l’espace de travail, les fonctions membres suivantes, qui fonctionnent sur le moteur de base de données, sont disponibles après la construction de l’objet C++, mais avant un appel à **ouvert** :  
  
||||  
|-|-|-|  
|[Créer](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|  
|[GetIniPath](#getinipath)|[Des temps d’inactivité](#idle)|[SetIniPath](#setinipath)|  
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|  
  
##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase  
 Appelez cette fonction membre, si vous avez besoin tenter de réparer une base de données endommagée qui accède au moteur de base de données Microsoft Jet.  
  
```  
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszName`  
 Le chemin d’accès et le nom de fichier pour un fichier de base de données de moteur Microsoft Jet existant. Si vous omettez le chemin d’accès, uniquement le répertoire actif est recherché. Si votre système prend en charge la convention d’affectation de noms uniforme (UNC), vous pouvez également spécifier un chemin d’accès réseau, tels que : «\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ». (Deux barres obliques inverses sont nécessaires dans la chaîne de chemin d’accès, car «\\» est le caractère d’échappement de C++.)  
  
### <a name="remarks"></a>Notes  
 Vous devez fermer la base de données spécifiée par `lpszName` avant de la réparer. Dans un environnement multi-utilisateur, les autres utilisateurs ne peuvent pas avoir `lpszName` ouvertes pendant que vous réparez il. Si `lpszName` n’est pas fermée ou n’est pas disponible pour une utilisation exclusive, une erreur se produit.  
  
 Cette fonction membre tente de réparer une base de données qui a été marqué comme peut-être endommagé par une opération d’écriture incomplète. Cela peut se produire si une application en utilisant le moteur de base de données Microsoft Jet fermeture inattendue en raison d’un problème de matériel ordinateur ou de panne d’alimentation. Si vous terminez l’opération et l’appel de la [fermer](../../mfc/reference/cdaodatabase-class.md#close) fonction membre ou si vous quittez l’application de façon habituelle, la base de données n’est pas marqué comme peut-être endommagé.  
  
> [!NOTE]
>  Après avoir réparé une base de données, il est également judicieux de compact à l’aide de la [CompactDatabase](#compactdatabase) fonction membre pour défragmenter le fichier et à récupérer l’espace disque.  
  
 Pour plus d’informations sur la réparation des bases de données, consultez la rubrique « RepairDatabase méthode » dans l’aide de DAO.  
  
##  <a name="rollback"></a>  CDaoWorkspace::Rollback  
 Appelez cette fonction membre pour terminer la transaction en cours et rétablir toutes les bases de données dans l’espace de travail avant de la transaction a commencé.  
  
```  
void Rollback();
```  
  
### <a name="remarks"></a>Notes  
  
> [!CAUTION]
>  Au sein d’un objet de l’espace de travail, les transactions sont toujours globales dans l’espace de travail et ne sont pas limitées à qu’une seule base de données ou un recordset. Si vous effectuez des opérations sur plus d’une base de données ou un recordset dans une transaction de l’espace de travail, **restauration** restaure toutes les opérations sur toutes les bases de données et les jeux d’enregistrements.  
  
 Si vous fermez un objet de l’espace de travail sans enregistrement ou annulation des transactions en attente, les transactions sont automatiquement annulées. Si vous appelez [CommitTrans](#committrans) ou **restauration** sans appeler d’abord [BeginTrans](#begintrans), une erreur se produit.  
  
> [!NOTE]
>  Lorsque vous commencez une transaction, le moteur de base de données enregistre ses opérations dans un fichier conservé dans le répertoire spécifié par la variable d’environnement TEMP sur la station de travail. Si le fichier journal des transactions épuise le stockage disponible sur le lecteur TEMP, le moteur de base de données entraîne des MFC lever un `CDaoException` (erreur DAO 2004). À ce stade, si vous appelez **CommitTrans**, un nombre indéterminé d’opérations est validé, mais les opérations non terminées restantes sont perdues, et l’opération doit être redémarré. Appel de **restauration** libère le journal des transactions et annule toutes les opérations dans la transaction.  
  
##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword  
 Appelez cette fonction membre pour définir le mot de passe par défaut par le moteur de base de données lorsqu’un objet de l’espace de travail est créé sans mot de passe spécifique.  
  
```  
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszPassword`  
 Le mot de passe par défaut. Un mot de passe peut comporter jusqu'à 14 caractères et peut contenir n’importe quel caractère sauf ASCII 0 (null). Les mots de passe respectent la casse.  
  
### <a name="remarks"></a>Notes  
 Le mot de passe par défaut que vous définissez s’applique aux nouveaux espaces de travail créés après l’appel. Lorsque vous créez des espaces de travail suivants, il est inutile de spécifier un mot de passe dans le [créer](#create) appeler.  
  
 Pour utiliser cette fonction membre :  
  
1.  Construire un `CDaoWorkspace` de l’objet, mais n’appelez pas **créer**.  
  
2.  Appelez `SetDefaultPassword` et, si vous le souhaitez, [SetDefaultUser](#setdefaultuser).  
  
3.  Appelez **créer** pour cet objet de l’espace de travail ou les conditions suivantes, sans spécifier un mot de passe.  
  
 Par défaut, la propriété DefaultUser est définie à « admin » et la propriété DefaultPassword est définie sur une chaîne vide (« »).  
  
 Pour plus d’informations sur la sécurité, consultez la rubrique « Autorisations Property » dans l’aide de DAO. Pour plus d’informations, consultez les rubriques « Propriété DefaultPassword » et « DefaultUser Property » dans l’aide de DAO.  
  
##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser  
 Appelez cette fonction membre pour définir le nom d’utilisateur par défaut par le moteur de base de données lorsqu’un objet de l’espace de travail est créé sans un nom d’utilisateur spécifique.  
  
```  
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszDefaultUser`  
 Le nom d’utilisateur par défaut. Un nom d’utilisateur peut comporter 1 à 20 caractères et inclure des caractères alphabétiques, les caractères accentués, nombres, des espaces et les symboles à l’exception de : » (entre guillemets), / (barre oblique), \ (barre oblique inverse), \[ \] (crochets), : (deux-points), &#124; () canal de communication), \< (moins-signe), > (supérieur-signe), signe plus (+), = (signe égal), (point-virgule), (virgule), (interrogation) * (astérisque), des espaces et des caractères de contrôle (ASCII 00 ASCII 31). Pour plus d’informations, consultez la rubrique « Propriété de nom d’utilisateur » dans l’aide de DAO.  
  
### <a name="remarks"></a>Notes  
 Le nom d’utilisateur par défaut que vous définissez s’applique aux nouveaux espaces de travail créés après l’appel. Lorsque vous créez des espaces de travail suivants, il est inutile de spécifier un nom d’utilisateur dans le [créer](#create) appeler.  
  
 Pour utiliser cette fonction membre :  
  
1.  Construire un `CDaoWorkspace` de l’objet, mais n’appelez pas **créer**.  
  
2.  Appelez `SetDefaultUser` et, si vous le souhaitez, [SetDefaultPassword](#setdefaultpassword).  
  
3.  Appelez **créer** pour cet objet de l’espace de travail ou les conditions suivantes, sans spécifier un nom d’utilisateur.  
  
 Par défaut, la propriété DefaultUser est définie à « admin » et la propriété DefaultPassword est définie sur une chaîne vide (« »).  
  
 Pour plus d’informations, consultez les rubriques « Propriété DefaultUser » et « DefaultPassword Property » dans l’aide de DAO.  
  
##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath  
 Appelez cette fonction membre pour spécifier l’emplacement des paramètres du Registre Windows pour le moteur de base de données Microsoft Jet.  
  
```  
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszRegistrySubkey*  
 Chaîne contenant le nom d’une sous-clé de Registre Windows pour l’emplacement des paramètres du moteur de base de données Microsoft Jet ou les paramètres requis pour les bases de données ISAM.  
  
### <a name="remarks"></a>Notes  
 Appelez `SetIniPath` uniquement si vous devez spécifier des paramètres spéciaux. Pour plus d’informations, consultez la rubrique « Propriété IniPath » dans l’aide de DAO.  
  
> [!NOTE]
>  Appelez `SetIniPath` pendant l’installation de l’application, pas lorsque l’application s’exécute. `SetIniPath` doit être appelé avant d’ouvrir les espaces de travail, les bases de données ou les jeux d’enregistrements ; dans le cas contraire, MFC lève une exception.  
  
 Vous pouvez utiliser ce mécanisme pour configurer le moteur de base de données avec les paramètres de Registre fournis par l’utilisateur. L’étendue de cet attribut est limitée à votre application et ne peut pas être modifié sans avoir à redémarrer votre application.  
  
##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans  
 Appelez cette fonction membre pour définir la valeur de la propriété DAO IsolateODBCTrans pour l’espace de travail.  
  
```  
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```  
  
### <a name="parameters"></a>Paramètres  
 *bIsolateODBCTrans*  
 Passer **TRUE** si vous souhaitez commencer l’isolement des transactions ODBC. Passer **FALSE** si vous souhaitez arrêter l’isolement des transactions ODBC.  
  
### <a name="remarks"></a>Notes  
 Dans certaines situations, vous devrez peut-être avoir plusieurs transactions simultanées en cours sur la même base de données ODBC. Pour ce faire, vous devez ouvrir un espace de travail distinct pour chaque transaction. Bien que chaque espace de travail peut avoir sa propre connexion ODBC à la base de données, cela ralentit les performances du système. Étant donné que l’isolation des transactions est généralement pas nécessaire, les connexions ODBC à partir de plusieurs objets d’espace de travail ouverts par le même utilisateur sont partagées par défaut.  
  
 Certains serveurs ODBC, telles que Microsoft SQL Server, n’autorisent pas les transactions simultanées sur une seule connexion. Si vous avez besoin d’avoir plusieurs transactions en cours sur une base de données, définissez la propriété IsolateODBCTrans **TRUE** sur chaque espace de travail dès que vous l’ouvrez. Cette opération force une connexion ODBC séparée pour chaque espace de travail.  
  
##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout  
 Appelez cette fonction membre pour définir la valeur de la propriété DAO LoginTimeout pour l’espace de travail.  
  
```  
static void PASCAL SetLoginTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>Paramètres  
 `nSeconds`  
 Le nombre de secondes avant qu’une erreur se produit lorsque vous essayez de vous connecter à une base de données ODBC.  
  
### <a name="remarks"></a>Notes  
 Cette valeur représente le nombre de secondes avant qu’une erreur se produit lorsque vous essayez de vous connecter à une base de données ODBC. La valeur par défaut LoginTimeout est 20 secondes. Lorsque LoginTimeout est définie sur 0, aucun délai d’expiration se produit et la communication avec la source de données peut cesser de répondre.  
  
 Lorsque vous tentez de vous connecter à une base de données ODBC, telles que Microsoft SQL Server, la connexion peut échouer en raison d’erreurs réseau ou parce que le serveur n’est pas en cours d’exécution. Au lieu d’attendre la valeur par défaut 20 secondes pour se connecter, vous pouvez spécifier la durée pendant laquelle le moteur de base de données doit attendre une erreur produit. Ouverture de session le serveur se produit implicitement dans le cadre d’un nombre d’événements, telles que l’exécution d’une requête sur une base de données du serveur externe. La valeur de délai d’expiration est déterminée par le paramètre actuel de la propriété LoginTimeout.  
  
 Pour plus d’informations, consultez la rubrique « Propriété LoginTimeout » dans l’aide de DAO.  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase (classe)](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset (classe)](../../mfc/reference/cdaorecordset-class.md)   
 [Classe d’objet CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef (classe)](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoException, classe](../../mfc/reference/cdaoexception-class.md)
