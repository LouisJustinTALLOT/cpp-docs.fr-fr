---
title: "TN054 : Appel de DAO directement pendant l’utilisation des Classes DAO MFC | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.dao
dev_langs:
- C++
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: de49cec931878cbfe06939269721b17a37a66202
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054 : appel de DAO directement pendant l'utilisation des classes DAO MFC
> [!NOTE]
>  Les Assistants et l’environnement Visual C++ ne prennent pas en charge les DAO (bien que les classes DAO sont incluses et vous pouvez toujours les utiliser). Microsoft recommande d’utiliser [modèles OLE DB](../data/oledb/ole-db-templates.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour les nouveaux projets. Vous devez uniquement utiliser DAO dans la maintenance des applications existantes.  
  
 Lorsque vous utilisez les classes de base de données DAO MFC, il peut arriver lorsqu’il est nécessaire d’utiliser DAO directement. En règle générale, cela ne sera pas le cas, mais MFC a fourni des mécanismes d’assistance pour faciliter les direct DAO appels simple lors de la combinaison de l’utilisation des classes MFC avec des appels directs de DAO. Apporter directement DAO appels aux méthodes d’un objet DAO de MFC gérés doivent nécessitent uniquement quelques lignes de code. Si vous devez créer et utiliser des objets DAO sont *pas* géré par MFC, vous devez faire un peu plus de travail en appelant réellement **version** sur l’objet. Cette note technique explique où vous voudriez appeler DAO directement, ce que les programmes d’assistance MFC peuvent faire pour vous aider à et comment utiliser les interfaces OLE DAO. Enfin, cette note fournit quelques exemples de fonctions montrant comment appeler DAO directement pour les fonctionnalités de sécurité DAO.  
  
## <a name="when-to-make-direct-dao-calls"></a>Quand effectuer des appels DAO directement  
 Les situations les plus courantes pour DAO appels directs se produisent lorsque les collections doivent être actualisés, ou lorsque vous implémentez des fonctionnalités non encapsulées par MFC. La fonction la plus importante ne pas exposée par MFC est la sécurité. Si vous souhaitez implémenter des fonctionnalités de sécurité, vous devrez utiliser directement des objets DAO ou les utilisateurs et groupes. Outre la sécurité, il existe seulement quelques autres DAO fonctionnalités non prises en charge par MFC. Notamment les fonctionnalités de réplication le clonage et la base de données de jeu d’enregistrements, ainsi que quelques ajouts à liaison tardive vers DAO.  
  
## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Une vue d’ensemble de l’implémentation DAO de MFC  
 Habillage de MFC facilite DAO à l’aide de DAO plus facile à gérer de nombreux détails pour ne pas avoir à vous soucier les petites choses. Cela inclut l’initialisation d’OLE, la création et la gestion des objets DAO (en particulier les objets de collection), erreur de vérifier et en fournissant une interface fortement typée, le plus simple (sans **VARIANT** ou `BSTR` arguments). Vous pouvez effectuer des appels directs de DAO et tirer parti de ces fonctionnalités. Tout votre code doit faire est d’appel **version** pour tous les objets créés par DAO direct appelle et *pas* modifiez pas les pointeurs d’interface MFC dépendent en interne. Par exemple, ne modifiez pas le **m_pDAORecordset** membre ouvert `CDaoRecordset` de l’objet, sauf si vous comprenez *tous les* les ramifications internes. Toutefois, vous pouvez utiliser la **m_pDAORecordset** interface pour appeler DAO directement pour obtenir la collection de champs. Dans ce cas le **m_pDAORecordset** membre n’est pas modifié. Vous devez simplement appeler **version** sur l’objet de collection de champs lorsque vous avez terminé avec l’objet.  
  
## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Description de programmes d’assistance pour rendre DAO appelle plus facile  
 Les programmes d’assistance fournies pour que l’appel de DAO plus facile même d’assistance sont le qui est utilisée en interne dans les classes de base de données DAO de MFC. Ces programmes d’assistance utilisées pour rechercher les codes de retour lors d’un appel direct de DAO, la journalisation de la sortie du débogage, la vérification des erreurs attendues et lever des exceptions appropriées si nécessaire. Il existe deux fonctions d’assistance sous-jacent et quatre macros qui correspondent à un de ces deux programmes d’assistance. La meilleure explication serait simplement lire le code. Consultez **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM**, et **DAO_TRACE** dans AFXDAO. H pour voir les macros, consultez **AfxDaoCheck** et **AfxDaoTrace** dans DAOCORE. CPP.  
  
## <a name="using-the-dao-ole-interfaces"></a>À l’aide des Interfaces OLE DAO  
 Les interfaces OLE pour chaque objet dans la hiérarchie d’objets DAO sont définies dans le fichier d’en-tête DBDAOINT. H, qui se trouve dans le répertoire \Program Files\Microsoft 2003\VC7\include de Visual Studio .NET. Ces interfaces fournissent des méthodes qui vous permettent de manipuler l’ensemble de la hiérarchie DAO.  
  
 Pour la plupart des méthodes dans les interfaces DAO, vous devez manipuler un `BSTR` objet (une chaîne préfixée par sa longueur utilisée dans OLE automation). Le `BSTR` objet généralement est encapsulé dans la **VARIANT** type de données. La classe MFC `COleVariant` elle-même hérite de la **VARIANT** type de données. Selon que vous générez votre projet pour ANSI ou Unicode, les interfaces DAO retournera ANSI ou Unicode `BSTR`s. Deux macros, **V_BSTR** et **V_BSTRT**, sont utiles pour s’assurer que l’interface DAO Obtient le `BSTR` du type attendu.  
  
 **V_BSTR** extrait la **bstrVal** membre d’un `COleVariant`. Cette macro est généralement utilisée lorsque vous devez passer le contenu d’un `COleVariant` à une méthode d’une interface DAO. Le fragment de code suivant montre les déclarations et l’utilisation réelle pour les deux méthodes de l’interface DAO DAOUser qui tirent parti de la **V_BSTR** macro :  
  
```  
COleVariant varOldName;  
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

 
// Code to assign pUser to a valid value omitted  
DAOUser *pUser = NULL;  
 
// These method declarations were taken from DBDAOINT.H  
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;  
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;  
 
DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));

DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```  
  
 Notez que la `VT_BSTRT` argument spécifié dans le `COleVariant` constructeur ci-dessus permet de s’assurer qu’il y aura un ANSI `BSTR` dans les `COleVariant` si vous générez une version ANSI de votre application et Unicode `BSTR` pour une version Unicode de votre application. C’est ce qu’attend DAO.  
  
 La macro **V_BSTRT**, extrait ANSI ou Unicode **bstrVal** membre `COleVariant` selon le type de build (ANSI ou Unicode). Le code suivant montre comment extraire le `BSTR` valeur un `COleVariant` dans un `CString`:  
  
```  
COleVariant varName(_T("MyName"), VT_BSTRT);

CString str = V_BSTRT(&varName);
```  
  
 Le **V_BSTRT** (macro), ainsi que d’autres techniques pour ouvrir d’autres types qui sont stockés dans `COleVariant`, est illustré dans l’exemple DAOVIEW. Plus précisément, cette traduction est effectuée dans le **CCrack::strVARIANT** (méthode). Cette méthode, si possible, convertit la valeur d’un `COleVariant` dans une instance de `CString`.  
  
## <a name="simple-example-of-a-direct-call-to-dao"></a>Exemple simple d’un appel Direct de DAO  
 Certaines situations peuvent lorsqu’il est nécessaire d’actualiser les objets de collection DAO sous-jacente. Normalement, cela ne doit pas être nécessaire, mais il est une procédure simple s’il est nécessaire. Un exemple de lorsqu’une collection devra peut-être être actualisé est lors du fonctionnement dans un environnement multi-utilisateur avec plusieurs utilisateurs de la création de nouveaux tabledefs. Dans ce cas, votre collection tabledefs peut devenir obsolète. Pour actualiser la collection, vous devez simplement appeler le **Actualiser** méthode de l’objet de collection particulière et de la vérification des erreurs :  
  
```  
DAO_CHECK(pMyDaoDatabase->  
    m_pDAOTableDefs->Refresh());
```  
  
 Notez que toutes les interfaces d’objet de collection DAO sont actuellement les détails d’implémentation non documentées des classes de base de données DAO de MFC.  
  
## <a name="using-dao-directly-for-dao-security-features"></a>À l’aide de DAO directement pour les fonctionnalités de sécurité DAO  
 Les classes de base de données DAO MFC n’imbriquez pas les fonctionnalités de sécurité DAO. Vous devez appeler les méthodes des interfaces DAO à utiliser certaines fonctionnalités de sécurité DAO. La fonction suivante définit la base de données système, puis modifie le mot de passe. Cette fonction appelle trois autres fonctions, qui sont définies par la suite.  
  
```  
void ChangeUserPassword()  
{ *// Specify path to the Microsoft Access *// system database  
    CString strSystemDB = 
    _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

 *// Set system database before MFC initilizes DAO *// NOTE: An MFC module uses only one instance *// of a DAO database engine object. If you have *// called a DAO object in your application prior *// to calling the function below,
    you must call *// AfxDaoTerm to destroy the existing database *// engine object. Otherwise,
    the database engine *// object already in use will be reused,
    and setting *// a system datbase will have no effect. *// *// If you have used a DAO object prior to calling *// this function it is important that DAO be *// terminated with AfxDaoTerm since an MFC *// module only gets one copy of the database engine *// and that engine will be reused if it hasn't been *// terminated. In other words,
    if you do not call *// AfxDaoTerm and there is currently a database *// initialized,
    setting the system database will *// have no affect.  
 
    SetSystemDB(strSystemDB);

 *// User name and password manually added *// by using Microsoft Access  
    CString strUserName = _T("NewUser");

    CString strOldPassword = _T("Password");

    CString strNewPassword = _T("NewPassword");

 *// Set default user so that MFC will be able *// to log in by default using the user name and *// password from the system database  
    SetDefaultUser(strUserName,
    strOldPassword);

 *// Change the password. You should be able to *// call this function from anywhere in your *// MFC application  
    ChangePassword(strUserName,
    strOldPassword,   
    strNewPassword);

 
 .  
 .  
 .  
 
}  
```  
  
 Les quatre exemples montrent comment :  
  
-   Définir la base de données DAO système (. Fichier MDW).  
  
-   Définir l’utilisateur par défaut et le mot de passe.  
  
-   Modifier le mot de passe d’un utilisateur.  
  
-   Modifier le mot de passe d’un. Fichier MDB.  
  
### <a name="setting-the-system-database"></a>Définition de la base de données système  
 Voici un exemple de fonction pour définir la base de données système qui sera utilisé par une application. Cette fonction doit être appelée avant que tous les autres appels DAO sont effectuées.  
  
```  
// Set the system database that the   
// DAO database engine will use  
 
void SetSystemDB(CString& strSystemMDB)  
{  
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

 *// Initialize DAO for MFC  
    AfxDaoInit();
DAODBEngine* pDBEngine = AfxDaoGetEngine();

 
    ASSERT(pDBEngine != NULL);

 *// Call put_SystemDB method to set the *// system database for DAO engine  
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));

} 
```  
  
### <a name="setting-the-default-user-and-password"></a>Définition de l’utilisateur par défaut et le mot de passe  
 Pour définir l’utilisateur par défaut et le mot de passe pour une base de données système, utilisez la fonction suivante :  
  
```  
void SetDefaultUser(CString& strUserName,
    CString& strPassword)  
{  
    COleVariant varUserName(strUserName,
    VT_BSTRT);

    COleVariant varPassword(strPassword,
    VT_BSTRT);

 
    DAODBEngine* pDBEngine = AfxDaoGetEngine();
ASSERT(pDBEngine != NULL);

 *// Set default user:  
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

 *// Set default password:  
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));

} 
```  
  
### <a name="changing-a-users-password"></a>Modification de mot de passe d’un utilisateur  
 Pour modifier le mot de passe d’un utilisateur, utilisez la fonction suivante :  
  
```  
void ChangePassword(CString &strUserName,   
    CString &strOldPassword,   
    CString &strNewPassword)  
{ *// Create (open) a workspace  
    CDaoWorkspace wsp;  
    CString strWspName = _T("Temp Workspace");

 
    wsp.Create(strWspName, strUserName,  
    strOldPassword);

 wsp.Append();

 *// Determine how many objects there are *// in the Users collection  
    short nUserCount;  
    short nCurrentUser;  
    DAOUser *pUser = NULL;  
    DAOUsers *pUsers = NULL;  
 *// Side-effect is implicit OLE AddRef() *// on DAOUser object:  
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

 *// Side-effect is implicit OLE AddRef() *// on DAOUsers object  
    DAO_CHECK(pUsers->getcount(&nUserCount));

 *// Traverse through the list of users *// and change password for the userid *// used to create/open the workspace  
    for(nCurrentUser = 0; nCurrentUser <nUserCount;  
    nCurrentUser++) 
 {  
    COleVariant varIndex(nCurrentUser, VT_I2);

    COleVariant varName;  
 *// Retrieve information for user nCurrentUser  
    DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

 *// Retrieve name for user nCurrentUser  
    DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

 
    CString strTemp = V_BSTRT(&varName);

 *// If there is a match, change the password  
    if(strTemp == strUserName)  
 {  
    COleVariant varOldPwd(strOldPassword,   
    VT_BSTRT);

 COleVariant  varNewPwd(strNewPassword,   
    VT_BSTRT);

 
    DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd), 
    V_BSTR(&varNewPwd)));

 
    TRACE("\t Password is changed\n");

 }  
 }  
 *// Clean up: decrement the usage count *// on the OLE objects  
    pUser->Release();
pUsers->Release();

 
    wsp.Close();

} 
```  
  
### <a name="changing-the-password-of-an-mdb-file"></a>Modification de mot de passe d’un. Fichier MDB  
 Pour modifier le mot de passe d’un. MDB, utilisez la fonction suivante :  
  
```  
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)  
{  
    CDaoDatabase db;  
    CString strConnect(_T(";pwd="));

 *// the database must be opened as exclusive *// to set a password  
    db.Open(pDB,
    TRUE,
    FALSE,   
    strConnect + pszOldPassword);

 
    COleVariant NewPassword(pszNewPassword,
    VT_BSTRT),  
    OldPassword(pszOldPassword,
    VT_BSTRT);

 
    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword), 
    V_BSTR(&NewPassword)));

 
    db.Close();

} 
```  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

