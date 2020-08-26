---
title: Macros et objet Globals de base de données
ms.date: 11/04/2016
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
ms.openlocfilehash: 0dc53bce8b43677e7fe0aa1787d1adcc16a560c4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837525"
---
# <a name="database-macros-and-globals"></a>Macros et objet Globals de base de données

Les macros et les champs globaux listés ci-dessous s’appliquent aux applications de base de données ODBC. Elles ne sont pas utilisées avec les applications basées sur DAO.

Avant les MFC 4,2, les macros `AFX_SQL_ASYNC` et ont `AFX_SQL_SYNC` donné aux opérations asynchrones une opportunité de donner du temps à d’autres processus. À partir de MFC 4,2, l’implémentation de ces macros a changé car les classes ODBC MFC utilisaient uniquement des opérations synchrones. La macro `AFX_ODBC_CALL` est nouvelle dans MFC 4,2.

### <a name="database-macros"></a>Macros de base de données

|Nom|Description|
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Appelle une fonction API ODBC qui retourne `SQL_STILL_EXECUTING` . `AFX_ODBC_CALL` appellera la fonction à plusieurs reprises jusqu’à ce qu’elle ne soit plus retournée `SQL_STILL_EXECUTING` .|
|[AFX_SQL_ASYNC](#afx_sql_async)|Appelle `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Appelle une fonction API ODBC qui ne retourne pas `SQL_STILL_EXECUTING` .|

### <a name="database-globals"></a>Bases de données globales

|Nom|Description|
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Ajoute la prise en charge de base de données pour une DLL MFC normale qui est liée de manière dynamique aux MFC.|
|[AfxGetHENV](#afxgethenv)|Récupère un handle vers l’environnement ODBC en cours d’utilisation par MFC. Vous pouvez utiliser ce handle dans des appels ODBC directs.|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a> AfxDbInitModule

Pour la prise en charge des bases de données MFC (ou DAO) à partir d’une DLL MFC normale liée de manière dynamique aux MFC, ajoutez un appel à cette fonction dans la fonction de votre DLL MFC normale `CWinApp::InitInstance` pour initialiser la dll de la base de données MFC.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Notes

Assurez-vous que cet appel se produit avant tout appel de classe de base ou tout code ajouté qui accède à la DLL de base de données MFC. La DLL de la base de données MFC est une DLL d’extension MFC ; pour qu’une DLL d’extension MFC puisse être connectée à une `CDynLinkLibrary` chaîne, elle doit créer un `CDynLinkLibrary` objet dans le contexte de chaque module qui l’utilisera. `AfxDbInitModule` crée l' `CDynLinkLibrary` objet dans le contexte de votre DLL MFC normale afin qu’il soit relié à la `CDynLinkLibrary` chaîne d’objets de la DLL MFC normale.

### <a name="requirements"></a>Configuration requise

**En-tête :**\<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a> AFX_ODBC_CALL

Utilisez cette macro pour appeler une fonction API ODBC qui peut retourner `SQL_STILL_EXECUTING` .

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Paramètres

*SQLFunc*<br/>
Fonction API ODBC. Pour plus d’informations sur les fonctions de l’API ODBC, consultez le SDK Windows.

### <a name="remarks"></a>Notes

`AFX_ODBC_CALL` appelle la fonction à plusieurs reprises jusqu’à ce qu’elle ne soit plus retournée `SQL_STILL_EXECUTING` .

Avant d’appeler `AFX_ODBC_CALL` , vous devez déclarer une variable, `nRetCode` , de type RETCODE.

Notez que les classes ODBC MFC utilisent désormais uniquement le traitement synchrone. Pour effectuer une opération asynchrone, vous devez appeler la fonction API ODBC `SQLSetConnectOption` . Pour plus d’informations, consultez la rubrique « exécution de fonctions de manière asynchrone » dans la SDK Windows.

### <a name="example"></a>Exemple

Cet exemple utilise `AFX_ODBC_CALL` pour appeler la `SQLColumns` fonction API ODBC, qui retourne la liste des colonnes de la table nommée par `strTableName` . Notez la déclaration de `nRetCode` et l’utilisation des membres de données de l’ensemble d’enregistrements pour passer des paramètres à la fonction. L’exemple illustre également la vérification des résultats de l’appel avec `Check` , une fonction membre de classe `CRecordset` . La variable `prs` est un pointeur vers un `CRecordset` objet, déclaré ailleurs.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a> AFX_SQL_ASYNC

L’implémentation de cette macro a changé dans MFC 4,2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Paramètres

*tirage*<br/>
Pointeur vers un `CRecordset` objet ou un `CDatabase` objet. À partir de MFC 4,2, cette valeur de paramètre est ignorée.

*SQLFunc*<br/>
Fonction API ODBC. Pour plus d’informations sur les fonctions de l’API ODBC, consultez le SDK Windows.

### <a name="remarks"></a>Notes

`AFX_SQL_ASYNC` appelle simplement la macro [AFX_ODBC_CALL](#afx_odbc_call) et ignore le paramètre *PRS* . Dans les versions de MFC antérieures à 4,2, `AFX_SQL_ASYNC` a été utilisé pour appeler les fonctions API ODBC qui peuvent retourner `SQL_STILL_EXECUTING` . Si une fonction d’API ODBC a retourné `SQL_STILL_EXECUTING` , `AFX_SQL_ASYNC` appelez `prs->OnWaitForDataSource` .

> [!NOTE]
> Les classes ODBC MFC utilisent désormais uniquement le traitement synchrone. Pour effectuer une opération asynchrone, vous devez appeler la fonction API ODBC `SQLSetConnectOption` . Pour plus d’informations, consultez la rubrique « exécution de fonctions de manière asynchrone » dans la SDK Windows.

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXDB. h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a> AFX_SQL_SYNC

La `AFX_SQL_SYNC` macro appelle simplement la fonction `SQLFunc` .

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Paramètres

*SQLFunc*<br/>
Fonction API ODBC. Pour plus d’informations sur ces fonctions, consultez la SDK Windows.

### <a name="remarks"></a>Notes

Utilisez cette macro pour appeler des fonctions API ODBC qui ne seront pas retournées `SQL_STILL_EXECUTING` .

Avant `AFX_SQL_SYNC` d’appeler, vous devez déclarer une variable, `nRetCode` , de type RETCODE. Vous pouvez vérifier la valeur de `nRetCode` après l’appel de la macro.

Notez que l’implémentation de `AFX_SQL_SYNC` a changé dans MFC 4,2. Étant donné que la vérification de l’état du serveur n’est plus nécessaire, `AFX_SQL_SYNC` assigne simplement une valeur à `nRetCode` . Par exemple, au lieu d’effectuer l’appel

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

vous pouvez simplement effectuer l’affectation

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXDB. h

## <a name="afxgethenv"></a><a name="afxgethenv"></a> AfxGetHENV

Vous pouvez utiliser le handle retourné dans les appels ODBC directs, mais vous ne devez pas fermer le handle ou supposer que le handle est toujours valide et disponible après la `CDatabase` `CRecordset` destruction des objets dérivés de ou existants.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Valeur renvoyée

Handle de l’environnement ODBC en cours d’utilisation par MFC. Peut être `SQL_HENV_NULL` s’il n’y a aucun objet [CDatabase](../../mfc/reference/cdatabase-class.md) et aucun objet [CRecordset](../../mfc/reference/crecordset-class.md) en cours d’utilisation.

### <a name="requirements"></a>Configuration requise

  **En-tête** AFXDB. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
