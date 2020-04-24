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
ms.openlocfilehash: 6d8bd56c0bfe4f9b35e34d067dd1042ed11066d5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751657"
---
# <a name="database-macros-and-globals"></a>Macros et objet Globals de base de données

Les macros et les produits globaux énumérés ci-dessous s’appliquent aux applications de base de données basées sur L’ODBC. Ils ne sont pas utilisés avec des applications basées sur DAO.

Avant MFC 4.2, `AFX_SQL_ASYNC` les `AFX_SQL_SYNC` macros et ont donné aux opérations asynchrones l’occasion de donner du temps à d’autres processus. À partir du MFC 4.2, la mise en œuvre de ces macros a changé parce que les classes MFC ODBC n’utilisaient que des opérations synchrones. La `AFX_ODBC_CALL` macro était nouvelle pour MFC 4.2.

### <a name="database-macros"></a>Macros de base de données

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Appelle une fonction API ODBC qui revient `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL`appellera à plusieurs reprises la `SQL_STILL_EXECUTING`fonction jusqu’à ce qu’elle ne revienne plus .|
|[AFX_SQL_ASYNC](#afx_sql_async)|Appelle `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Appelle une fonction API ODBC `SQL_STILL_EXECUTING`qui ne revient pas .|

### <a name="database-globals"></a>Globals de base de données

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Ajoute le support de base de données pour un DLL MFC régulier qui est dynamiquement lié à MFC.|
|[AfxGetHENV](#afxgethenv)|Récupère une poignée dans l’environnement ODBC actuellement utilisé par MFC. Vous pouvez utiliser cette poignée dans les appels directs ODBC.|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a>AfxDbInitModule

Pour le support de base de données MFC (ou DAO) d’un DLL MFC régulier qui est dynamiquement lié à MFC, ajoutez un appel à cette fonction dans la fonction de `CWinApp::InitInstance` votre MFC DLL régulière pour initialiser la base de données MFC DLL.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Notes

Assurez-vous que cet appel se produit avant tout appel de classe de base ou tout code supplémentaire qui accède à la base de données MFC DLL. La base de données MFC DLL est une extension MFC DLL; Pour qu’une DLL d’extension MFC `CDynLinkLibrary` soit câblée `CDynLinkLibrary` dans une chaîne, elle doit créer un objet dans le contexte de chaque module qui l’utilisera. `AfxDbInitModule`crée `CDynLinkLibrary` l’objet dans le contexte de votre MFC DLL `CDynLinkLibrary` régulier afin qu’il soit câblé dans la chaîne d’objets de la DLL MFC régulière.

### <a name="requirements"></a>Spécifications

**En-tête:** \<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a>AFX_ODBC_CALL

Utilisez cette macro pour appeler n’importe quelle `SQL_STILL_EXECUTING`fonction API ODBC qui peut revenir .

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Paramètres

*SQLFunc (SQLFunc)*<br/>
Une fonction API ODBC. Pour plus d’informations sur les fonctions ODBC API, voir le SDK Windows.

### <a name="remarks"></a>Notes

`AFX_ODBC_CALL`appelle à plusieurs reprises la `SQL_STILL_EXECUTING`fonction jusqu’à ce qu’il ne revient plus .

Avant d’invoquer `AFX_ODBC_CALL`, vous `nRetCode`devez déclarer une variable, , de type RETCODE.

Notez que les classes MFC ODBC n’utilisent désormais que le traitement synchrone. Afin d’effectuer une opération asynchrone, vous devez appeler `SQLSetConnectOption`la fonction API ODBC . Pour plus d’informations, voir le sujet "Exécution des fonctions asynchrone" dans le SDK Windows.

### <a name="example"></a>Exemple

Cet exemple `AFX_ODBC_CALL` utilise `SQLColumns` pour appeler la fonction ODBC API, qui renvoie une liste des colonnes dans le tableau nommé par `strTableName`. Notez la `nRetCode` déclaration et l’utilisation des membres des données de l’enregistrement pour transmettre les paramètres à la fonction. L’exemple illustre également la vérification `Check`des résultats de `CRecordset`l’appel avec , une fonction membre de la classe . La `prs` variable est un `CRecordset` pointeur d’un objet, déclaré ailleurs.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a>AFX_SQL_ASYNC

La mise en œuvre de cette macro a changé dans MFC 4.2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Paramètres

*Prs*<br/>
Un pointeur `CRecordset` vers `CDatabase` un objet ou un objet. En commençant par MFC 4.2, cette valeur de paramètre est ignorée.

*SQLFunc (SQLFunc)*<br/>
Une fonction API ODBC. Pour plus d’informations sur les fonctions ODBC API, voir le SDK Windows.

### <a name="remarks"></a>Notes

`AFX_SQL_ASYNC`appelle simplement la macro [AFX_ODBC_CALL](#afx_odbc_call) et ignore le paramètre *prs.* Dans les versions de MFC avant `AFX_SQL_ASYNC` 4.2, a été utilisé pour `SQL_STILL_EXECUTING`appeler ODBC fonctions API qui pourraient revenir . Si une fonction API ODBC `AFX_SQL_ASYNC` ne `prs->OnWaitForDataSource`retour `SQL_STILL_EXECUTING`, puis appellerait .

> [!NOTE]
> Les classes MFC ODBC n’utilisent plus que le traitement synchrone. Afin d’effectuer une opération asynchrone, vous devez appeler `SQLSetConnectOption`la fonction API ODBC . Pour plus d’informations, voir le sujet "Exécution des fonctions asynchrone" dans le SDK Windows.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdb.h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a>AFX_SQL_SYNC

La `AFX_SQL_SYNC` macro appelle `SQLFunc`simplement la fonction .

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Paramètres

*SQLFunc (SQLFunc)*<br/>
Une fonction API ODBC. Pour plus d’informations sur ces fonctions, voir le SDK Windows.

### <a name="remarks"></a>Notes

Utilisez cette macro pour appeler ODBC fonctions `SQL_STILL_EXECUTING`API qui ne seront pas de retour .

Avant `AFX_SQL_SYNC`d’appeler , vous `nRetCode`devez déclarer une variable, , de type RETCODE. Vous pouvez vérifier `nRetCode` la valeur de l’appel macro.

Notez que `AFX_SQL_SYNC` la mise en œuvre de modifié dans MFC 4.2. Parce que la vérification de `AFX_SQL_SYNC` l’état du `nRetCode`serveur n’était plus nécessaire, attribue simplement une valeur à . Par exemple, au lieu de faire l’appel

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

vous pouvez simplement faire la mission

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdb.h

## <a name="afxgethenv"></a><a name="afxgethenv"></a>AfxGetHENV AfxGetHENV

Vous pouvez utiliser la poignée retournée dans les appels directs ODBC, mais vous ne devez `CDatabase`pas `CRecordset`fermer la poignée ou supposer que la poignée est toujours valide et disponible après que des objets existants - ou dérivés ont été détruits.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Valeur de retour

La poignée de l’environnement ODBC actuellement utilisé par MFC. Peut `SQL_HENV_NULL` être s’il n’y a pas [d’objets CDatabase](../../mfc/reference/cdatabase-class.md) et pas [d’objets CRecordset](../../mfc/reference/crecordset-class.md) en usage.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdb.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
