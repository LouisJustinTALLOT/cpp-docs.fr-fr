---
title: Macros et objet Globals de base de données | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
dev_langs:
- C++
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67a0fd2af9bb8bf3ec11d5a4e2a38c195b18633c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424246"
---
# <a name="database-macros-and-globals"></a>Macros et objet Globals de base de données

Les macros et les variables globales répertoriées ci-dessous s’appliquent aux applications de base de données ODBC. Ils ne sont pas utilisés avec les applications DAO.

Avant de 4.2 de MFC, les macros `AFX_SQL_ASYNC` et `AFX_SQL_SYNC` a donné des opérations asynchrones une opportunité pour céder du temps à d’autres processus. À compter de 4.2 de MFC, l’implémentation de ces macros modifié, car les classes ODBC MFC utilisé uniquement les opérations synchrones. La macro `AFX_ODBC_CALL` n’y a 4.2 de MFC.

### <a name="database-macros"></a>Macros de base de données

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Appelle une fonction API ODBC qui retourne `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL` à plusieurs reprises appelle la fonction jusqu'à ce qu’il n’est plus retourne `SQL_STILL_EXECUTING`.|
|[AFX_SQL_ASYNC](#afx_sql_async)|Appelle `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Appelle une fonction API ODBC qui ne retourne pas `SQL_STILL_EXECUTING`.|

### <a name="database-globals"></a>Objet Globals de base de données

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Ajoute la prise en charge de la base de données pour une DLL MFC normale liée de manière dynamique aux MFC.|
|[AfxGetHENV](#afxgethenv)|Récupère un handle vers l’environnement ODBC en cours d’utilisation par MFC. Vous pouvez utiliser ce handle dans les appels ODBC directs.|


## <a name="afxdbinitmodule"></a> AfxDbInitModule

Pour la base de données MFC (ou DAO) prennent en charge à partir d’une DLL MFC normale liée de manière dynamique aux MFC, ajoutez un appel à cette fonction dans votre MFC DLL régulière `CWinApp::InitInstance` fonction pour initialiser la bibliothèque MFC de base de données de la DLL.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Notes

Assurez-vous que cet appel se produit avant tout appel de la classe de base ou de tout code qui accède à la base de données MFC DLL ajouté. La base de données MFC DLL est une extension MFC DLL ; pour une DLL d’extension MFC puisse être raccordée à un `CDynLinkLibrary` chaîne, il doit créer un `CDynLinkLibrary` objet dans le contexte de chaque module qui l’utiliserez. `AfxDbInitModule` crée le `CDynLinkLibrary` de l’objet dans le contexte de votre MFC DLL régulière afin qu’il obtient câblé dans le `CDynLinkLibrary` chaîne de la DLL MFC normale de l’objet.

### <a name="requirements"></a>Configuration requise

**En-tête :** \<afxdll_.h >

### <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)



##  <a name="afx_odbc_call"></a>  AFX_ODBC_CALL

Utilisez cette macro pour appeler une fonction API ODBC qui peut-être retourner `SQL_STILL_EXECUTING`.

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Paramètres

*SQLFunc*<br/>
Une fonction API ODBC. Pour plus d’informations sur les fonctions API ODBC, consultez le Kit de développement Windows.

### <a name="remarks"></a>Notes

`AFX_ODBC_CALL` appelle à plusieurs reprises la fonction jusqu'à ce qu’il n’est plus retourne `SQL_STILL_EXECUTING`.

Avant d’appeler `AFX_ODBC_CALL`, vous devez déclarer une variable, `nRetCode`, de type et RETCODE contient.

Notez que des classes ODBC MFC maintenant utiliser uniquement le traitement synchrone. Pour effectuer une opération asynchrone, vous devez appeler la fonction API ODBC `SQLSetConnectOption`. Pour plus d’informations, consultez la rubrique « L’exécution de fonctions de façon asynchrone » dans le SDK Windows.


### <a name="example"></a>Exemple

Cet exemple utilise `AFX_ODBC_CALL` pour appeler le `SQLColumns` fonction API ODBC, qui retourne la liste des colonnes dans la table nommée par `strTableName`. Notez la déclaration de `nRetCode` et l’utilisation de membres de données de jeu d’enregistrements pour passer des paramètres à la fonction. L’exemple illustre également la vérification des résultats de l’appel avec `Check`, une fonction membre de classe `CRecordset`. La variable `prs` est un pointeur vers un `CRecordset` objet, déclaré ailleurs.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

##  <a name="afx_sql_async"></a>  AFX_SQL_ASYNC

L’implémentation de cette macro modifiée dans MFC 4.2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Paramètres

*demandes de tirage*<br/>
Un pointeur vers un `CRecordset` objet ou un `CDatabase` objet. Depuis la version 4.2 de MFC, cette valeur de paramètre est ignorée.

*SQLFunc*<br/>
Une fonction API ODBC. Pour plus d’informations sur les fonctions API ODBC, consultez le Kit de développement Windows.

### <a name="remarks"></a>Notes

`AFX_SQL_ASYNC` appelle simplement la macro [AFX_ODBC_CALL](#afx_odbc_call) et ignore le *pr* paramètre. Dans les versions de la bibliothèque MFC antérieures 4.2, `AFX_SQL_ASYNC` a été utilisée pour appeler des fonctions API ODBC qui peuvent retourner `SQL_STILL_EXECUTING`. Si une fonction API ODBC n’a retourné `SQL_STILL_EXECUTING`, puis `AFX_SQL_ASYNC` appellerait `prs->OnWaitForDataSource`.

> [!NOTE]
>  Les classes ODBC MFC utilisent maintenant un traitement synchrone uniquement. Pour effectuer une opération asynchrone, vous devez appeler la fonction API ODBC `SQLSetConnectOption`. Pour plus d’informations, consultez la rubrique « L’exécution de fonctions de façon asynchrone » dans le SDK Windows.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdb.h

##  <a name="afx_sql_sync"></a>  AFX_SQL_SYNC

Le `AFX_SQL_SYNC` macro appelle simplement la fonction `SQLFunc`.

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Paramètres

*SQLFunc*<br/>
Une fonction API ODBC. Pour plus d’informations sur ces fonctions, consultez le Kit de développement Windows.

### <a name="remarks"></a>Notes

Utilisez cette macro pour appeler des fonctions API ODBC qui ne retournent pas `SQL_STILL_EXECUTING`.

Avant d’appeler `AFX_SQL_SYNC`, vous devez déclarer une variable, `nRetCode`, de type et RETCODE contient. Vous pouvez vérifier la valeur de `nRetCode` après l’appel de macro.

Notez que l’implémentation de `AFX_SQL_SYNC` modifié dans MFC 4.2. Étant donné que la vérification de l’état du serveur n’était plus nécessaire, `AFX_SQL_SYNC` simplement affecte une valeur à `nRetCode`. Par exemple, au lieu d’effectuer l’appel

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

Vous pouvez simplement mettre l’attribution

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdb.h

##  <a name="afxgethenv"></a>  AfxGetHENV

Vous pouvez utiliser le handle retourné dans les appels ODBC directs, mais vous ne devez pas fermer le handle ou supposent que le handle est encore valide et disponible après existants `CDatabase`- ou `CRecordset`-objets dérivés ont été détruits.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Valeur de retour

Handle de l’environnement ODBC en cours d’utilisation par MFC. Peut être `SQL_HENV_NULL` s’il existe aucune [CDatabase](../../mfc/reference/cdatabase-class.md) objets et non [CRecordset](../../mfc/reference/crecordset-class.md) objets en cours d’utilisation.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdb.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
