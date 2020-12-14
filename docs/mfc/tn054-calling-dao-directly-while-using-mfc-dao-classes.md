---
description: 'En savoir plus sur : TN054 : appel de DAO directement pendant l’utilisation des classes DAO MFC'
title: "TN054 : appel de DAO directement pendant l'utilisation des classes DAO MFC"
ms.date: 09/17/2019
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
ms.openlocfilehash: e374f283639fde095d63f2626246c97d5606466e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214960"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054 : appel de DAO directement pendant l'utilisation des classes DAO MFC

> [!NOTE]
> DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète. L’environnement et les assistants de Visual C++ ne prennent pas en charge DAO (bien que les classes DAO soient incluses et vous puissiez toujours les utiliser). Microsoft vous recommande d’utiliser les [modèles OLE DB](../data/oledb/ole-db-templates.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour les nouveaux projets. Vous ne devez utiliser que DAO pour gérer les applications existantes.

Lorsque vous utilisez les classes de base de données DAO MFC, il peut y avoir des situations où il est nécessaire d’utiliser directement DAO. En règle générale, ce n’est pas le cas, mais MFC a fourni des mécanismes d’assistance pour faciliter la création d’appels DAO directs lors de la combinaison de l’utilisation des classes MFC avec les appels DAO directs. L’exécution d’appels DAO directs aux méthodes d’un objet DAO managé par MFC ne doit nécessiter que quelques lignes de code. Si vous avez besoin de créer et d’utiliser des objets DAO qui ne sont *pas* gérés par MFC, vous devez effectuer un peu plus de travail en appelant réellement `Release` sur l’objet. Cette note technique explique quand vous pouvez appeler DAO directement, ce que les aide MFC peuvent faire pour vous aider et comment utiliser les interfaces OLE DAO. Enfin, cette note fournit des exemples de fonctions qui montrent comment appeler DAO directement pour les fonctionnalités de sécurité de DAO.

## <a name="when-to-make-direct-dao-calls"></a>Quand effectuer des appels DAO directs

Les situations les plus courantes pour effectuer des appels DAO directs se produisent lorsque des collections doivent être actualisées ou lorsque vous implémentez des fonctionnalités qui ne sont pas encapsulées par MFC. La fonctionnalité la plus significative qui n’est pas exposée par MFC est la sécurité. Si vous souhaitez implémenter des fonctionnalités de sécurité, vous devez utiliser directement les objets de l’utilisateur et des groupes (s) de DAO. Outre la sécurité, il n’existe que quelques autres fonctionnalités DAO non prises en charge par MFC. Celles-ci incluent le clonage de Recordset et les fonctionnalités de réplication de base de données, ainsi que quelques ajouts tardifs à DAO.

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>Brève vue d’ensemble de l’implémentation de DAO et de MFC

L’encapsulation de DAO dans MFC facilite l’utilisation de DAO en gérant un grand nombre des détails. vous n’avez donc pas à vous soucier des petits éléments. Cela comprend l’initialisation d’OLE, la création et la gestion des objets DAO (en particulier les objets de collection), la vérification des erreurs et la fourniture d’une interface fortement typée, plus simple (sans **variante** ou `BSTR` argument). Vous pouvez effectuer des appels DAO directs tout en tirant parti de ces fonctionnalités. Tout votre code doit faire appel `Release` à des objets créés par des appels DAO directs et *ne pas* modifier les pointeurs d’interface sur lesquels MFC peut s’appuyer en interne. Par exemple, ne modifiez pas le membre *m_pDAORecordset* d’un `CDaoRecordset` objet ouvert, sauf si vous comprenez *toutes* les ramifications internes. Toutefois, vous pouvez utiliser l’interface *m_pDAORecordset* pour appeler DAO directement pour récupérer la collection de champs. Dans ce cas, le membre de *m_pDAORecordset* n’est pas modifié. Vous devez simplement appeler `Release` sur l’objet de collection Fields lorsque vous avez terminé avec l’objet.

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>Description des applications auxiliaires pour faciliter les appels à DAO

Les applications d’assistance fournies pour faciliter l’appel de DAO sont les mêmes que celles utilisées en interne dans les classes de base de données DAO MFC. Ces applications auxiliaires permettent de vérifier les codes de retour lors de l’exécution d’un appel DAO direct, de la journalisation de la sortie de débogage, de la vérification des erreurs attendues et de la levée des exceptions appropriées si nécessaire. Deux fonctions d’assistance sous-jacentes et quatre macros sont mappées à l’une de ces deux applications auxiliaires. La meilleure explication est de simplement lire le code. Consultez **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM** et **DAO_TRACE** dans AFXDAO. H pour voir les macros et voir **AfxDaoCheck** et **AfxDaoTrace** dans DAOCORE. Cotisations.

## <a name="using-the-dao-ole-interfaces"></a>Utilisation des interfaces DAO OLE

Les interfaces OLE pour chaque objet de la hiérarchie d’objets DAO sont définies dans le fichier d’en-tête DBDAOINT. H, qui se trouve dans le répertoire \Program Files\Microsoft Visual Studio .NET 2003 \ VC7\include. Ces interfaces fournissent des méthodes qui vous permettent de manipuler l’ensemble de la hiérarchie des objets DAO.

Pour la plupart des méthodes des interfaces DAO, vous devrez manipuler un `BSTR` objet (une chaîne préfixée par sa longueur utilisée dans OLE Automation). L' `BSTR` objet est généralement encapsulé dans le type de données **Variant** . La classe MFC `COleVariant` elle-même hérite du type de données **Variant** . Selon que vous générez votre projet pour ANSI ou Unicode, les interfaces DAO retournent ANSI ou Unicode `BSTR` s. Deux macros, V_BSTR et V_BSTRT, sont utiles pour garantir que l’interface DAO obtient le `BSTR` du type attendu.

V_BSTR extraira le membre *bstrVal* d’un `COleVariant` . Cette macro est généralement utilisée lorsque vous devez passer le contenu d’un `COleVariant` à une méthode d’une interface DAO. Le fragment de code suivant montre à la fois les déclarations et l’utilisation réelle de deux méthodes de l’interface DAO DAOUser qui tirent parti de la macro V_BSTR :

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted DAOUser *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;
DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));
DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

Notez que l' `VT_BSTRT` argument spécifié dans le `COleVariant` constructeur ci-dessus garantit qu’il y aura un ANSI `BSTR` dans `COleVariant` si vous générez une version ANSI de votre application et une `BSTR` version Unicode pour une version Unicode de votre application. C’est ce que DAO attend.

L’autre macro, V_BSTRT, extrait un membre *BSTRVAL* ANSI ou Unicode de `COleVariant` selon le type de build (ANSI ou Unicode). Le code suivant montre comment extraire la `BSTR` valeur d’un `COleVariant` dans un `CString` :

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

La macro V_BSTRT, ainsi que d’autres techniques permettant d’ouvrir d’autres types stockés dans `COleVariant` , sont illustrées dans l’exemple DAOVIEW. Plus précisément, cette traduction est effectuée dans la `CCrack::strVARIANT` méthode. Cette méthode, dans la mesure du possible, convertit la valeur d’un `COleVariant` en instance de `CString` .

## <a name="simple-example-of-a-direct-call-to-dao"></a>Exemple simple d’un appel direct à DAO

Des situations peuvent survenir lorsqu’il est nécessaire d’actualiser les objets de la collection DAO sous-jacente. Normalement, cela ne devrait pas être nécessaire, mais il s’agit d’une procédure simple si nécessaire. Un exemple d’actualisation d’une collection est l’utilisation d’un environnement multi-utilisateur avec plusieurs utilisateurs qui créent de nouveaux TableDefs. Dans ce cas, votre collection TableDefs peut devenir obsolète. Pour actualiser la collection, il vous suffit d’appeler la `Refresh` méthode de l’objet de collection particulier et de rechercher les erreurs :

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

Notez que actuellement toutes les interfaces d’objet de collection DAO sont des détails d’implémentation non documentés des classes de base de données DAO MFC.

## <a name="using-dao-directly-for-dao-security-features"></a>Utilisation directe de DAO pour les fonctionnalités de sécurité DAO

Les classes de base de données DAO MFC n’encapsulent pas les fonctionnalités de sécurité de DAO. Vous devez appeler des méthodes d’interfaces DAO pour utiliser certaines fonctionnalités de sécurité de DAO. La fonction suivante définit la base de données système, puis modifie le mot de passe de l’utilisateur. Cette fonction appelle trois autres fonctions, qui sont définies par la suite.

```cpp
void ChangeUserPassword()
{
    // Specify path to the Microsoft Access *// system database
    CString strSystemDB =
        _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

    // Set system database before MFC initilizes DAO
    // NOTE: An MFC module uses only one instance
    // of a DAO database engine object. If you have
    // called a DAO object in your application prior
    // to calling the function below, you must call
    // AfxDaoTerm to destroy the existing database
    // engine object. Otherwise, the database engine
    // object already in use will be reused, and setting
    // a system datbase will have no effect.
    //
    // If you have used a DAO object prior to calling
    // this function it is important that DAO be
    // terminated with AfxDaoTerm since an MFC
    // module only gets one copy of the database engine
    // and that engine will be reused if it hasn't been
    // terminated. In other words, if you do not call
    // AfxDaoTerm and there is currently a database
    // initialized, setting the system database will
    // have no effect.
    SetSystemDB(strSystemDB);

    // User name and password manually added
    // by using Microsoft Access
    CString strUserName = _T("NewUser");
    CString strOldPassword = _T("Password");
    CString strNewPassword = _T("NewPassword");

    // Set default user so that MFC will be able
    // to log in by default using the user name and
    // password from the system database
    SetDefaultUser(strUserName, strOldPassword);

    // Change the password. You should be able to
    // call this function from anywhere in your
    // MFC application
    ChangePassword(strUserName, strOldPassword, strNewPassword);

    // ...
}
```

Les quatre exemples suivants montrent comment :

- Définissez la base de données DAO système (. Fichier MDW).

- Définissez l’utilisateur et le mot de passe par défaut.

- Modifier le mot de passe d’un utilisateur.

- Modifiez le mot de passe d’un. Fichier MDB.

### <a name="setting-the-system-database"></a>Définition de la base de données système

Vous trouverez ci-dessous un exemple de fonction permettant de définir la base de données système qui sera utilisée par une application. Cette fonction doit être appelée avant tout autre appel DAO.

```cpp
// Set the system database that the
// DAO database engine will use

void SetSystemDB(CString& strSystemMDB)
{
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

    // Initialize DAO for MFC
    AfxDaoInit();
    DAODBEngine* pDBEngine = AfxDaoGetEngine();

    ASSERT(pDBEngine != NULL);

    // Call put_SystemDB method to set the *// system database for DAO engine
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));
}
```

### <a name="setting-the-default-user-and-password"></a>Définition de l’utilisateur et du mot de passe par défaut

Pour définir l’utilisateur et le mot de passe par défaut d’une base de données système, utilisez la fonction suivante :

```cpp
void SetDefaultUser(CString& strUserName,
    CString& strPassword)
{
    COleVariant varUserName(strUserName, VT_BSTRT);
    COleVariant varPassword(strPassword, VT_BSTRT);

    DAODBEngine* pDBEngine = AfxDaoGetEngine();
    ASSERT(pDBEngine != NULL);

    // Set default user:
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

    // Set default password:
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));
}
```

### <a name="changing-a-users-password"></a>Modification du mot de passe d’un utilisateur

Pour modifier le mot de passe d’un utilisateur, utilisez la fonction suivante :

```cpp
void ChangePassword(CString &strUserName,
    CString &strOldPassword,
    CString &strNewPassword)
{
    // Create (open) a workspace
    CDaoWorkspace wsp;
    CString strWspName = _T("Temp Workspace");

    wsp.Create(strWspName, strUserName, strOldPassword);
    wsp.Append();

    // Determine how many objects there are *// in the Users collection
    short nUserCount;
    short nCurrentUser;
    DAOUser *pUser = NULL;
    DAOUsers *pUsers = NULL;

    // Side-effect is implicit OLE AddRef()
    // on DAOUser object:
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

    // Side-effect is implicit OLE AddRef()
    // on DAOUsers object
    DAO_CHECK(pUsers->getcount(&nUserCount));

    // Traverse through the list of users
    // and change password for the userid
    // used to create/open the workspace
    for(nCurrentUser = 0; nCurrentUser <nUserCount; nCurrentUser++)
    {
        COleVariant varIndex(nCurrentUser, VT_I2);
        COleVariant varName;

        // Retrieve information for user nCurrentUser
        DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

        // Retrieve name for user nCurrentUser
        DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

        CString strTemp = V_BSTRT(&varName);

        // If there is a match, change the password
        if (strTemp == strUserName)
        {
            COleVariant varOldPwd(strOldPassword, VT_BSTRT);
            COleVariant varNewPwd(strNewPassword, VT_BSTRT);

            DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd),
                V_BSTR(&varNewPwd)));

            TRACE("\t Password is changed\n");
        }
    }
    // Clean up: decrement the usage count
    // on the OLE objects
    pUser->Release();
    pUsers->Release();
    wsp.Close();
}
```

### <a name="changing-the-password-of-an-mdb-file"></a>Modification du mot de passe d’un. Fichier MDB

Pour modifier le mot de passe d’un. Fichier MDB, utilisez la fonction suivante :

```cpp
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)
{
    CDaoDatabase db;
    CString strConnect(_T(";pwd="));

    // the database must be opened as exclusive
    // to set a password
    db.Open(pDB, TRUE, FALSE, strConnect + pszOldPassword);

    COleVariant NewPassword(pszNewPassword, VT_BSTRT),
                OldPassword(pszOldPassword, VT_BSTRT);

    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword),
        V_BSTR(&NewPassword)));

    db.Close();
}
```

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
