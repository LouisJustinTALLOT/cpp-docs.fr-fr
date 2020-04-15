---
title: 'TN042 : Recommandations du développeur concernant le pilote ODBC'
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 67f7a86a247b60be66dabb0a89f04d39ce76222b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372136"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042 : Recommandations du développeur concernant le pilote ODBC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les lignes directrices pour les auteurs de pilotes ODBC. Il décrit les exigences générales et les hypothèses de la fonctionnalité ODBC que les classes de base de données MFC font, et divers détails sémantiques attendus. La fonctionnalité requise du `CRecordset` conducteur pour prendre en charge les trois modes Open **(forwardOnly**, **snapshot** et **dynaset**) sont décrites.

## <a name="odbcs-cursor-library"></a>Bibliothèque cursor de l’ODBC

Les classes de base de données MFC présentent des fonctionnalités à l’utilisateur qui, dans de nombreux cas, surpasse les fonctionnalités fournies par la plupart des pilotes ODBC de niveau 1. Heureusement, la bibliothèque Cursor d’ODBC se superposera entre les classes de base de données et le pilote, et fournira automatiquement une grande partie de cette fonctionnalité supplémentaire.

Par exemple, la plupart des conducteurs de 1,0 ne prennent pas en charge le défilement vers l’arrière. La bibliothèque Cursor peut détecter cela, et cache les lignes du conducteur et `SQLExtendedFetch`les présenter comme demandé sur FETCH_PREV appels .

Un autre exemple important de dépendance à la bibliothèque de curseurs est les mises à jour positionnées. La plupart des pilotes 1.0 n’ont pas non plus de mises à jour positionnées, mais la bibliothèque de curseurs générera des énoncés de mise à jour qui identifient une ligne cible sur la source de données en fonction de ses valeurs de données mises en cache actuelles, ou une valeur de timestamp mise en cache.

La bibliothèque de classe n’utilise jamais plusieurs rames. Par conséquent, `SQLSetPos` les quelques déclarations sont toujours appliquées à la rangée 1 de la rangée.

## <a name="cdatabases"></a>Bases CData

Chacun `CDatabase` alloue un seul **HDBC**. (Si `CDatabase`la `ExecuteSQL` fonction est utilisée, un **HSTMT** est temporairement attribué.) Donc, `CDatabase`si plusieurs 's sont nécessaires, plusieurs **HDBC**s par **HENV** doit être pris en charge.

Les classes de base de données nécessitent la bibliothèque de curseurs. Cela se reflète `SQLSetConnections` dans un appel **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.

`SQLDriverConnect`, **SQL_DRIVER_COMPLETE** est utilisé `CDatabase::Open` pour établir la connexion à la source de données.

Le conducteur `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >= doit prendre en `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >= charge **SQL_OAC_LEVEL1**, **SQL_OSC_MINIMUM**.

Pour que les transactions soient `CDatabase` prises en charge `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` pour les registres et ses registres dépendants, et **SQL_CURSOR_ROLLBACK_BEHAVIOR** doivent avoir **SQL_CR_PRESERVE**. Dans le cas contraire, les tentatives d’effectuer le contrôle des transactions seront ignorées.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY`doit être soutenu. S’il renvoie « Y », aucune opération de mise à jour ne sera effectuée sur la source de données.

Si `CDatabase` le est ouvert ReadOnly, une tentative de définir `SQLSetConnectOption SQL_ACCESS_MODE`la source de données lue seulement sera faite avec , **SQL_MODE_READ_ONLY**.

Si les identifiants nécessitent une citation, ces informations `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` doivent être retournées du conducteur avec un appel.

À des fins `SQLGetInfo SQL_DBMS_VER` de débogage, et **SQL_DBMS_NAME** sont récupérés auprès du conducteur.

`SQLSetStmtOption SQL_QUERY_TIMEOUT`et **SQL_ASYNC_ENABLE** peut être appelé `CDatabase`sur un **«HDBC**.

`SQLError`peut être appelé avec tout ou tous les arguments NULL.

Bien `SQLAllocEnv`sûr, `SQLAllocConnect` `SQLDisconnect` , `SQLFreeConnect` , et doit être soutenu.

## <a name="executesql"></a>ExecuteSQL

En plus d’allouer et de libérer `ExecuteSQL` `SQLExecDirect`un `SQLFetch` `SQLNumResultCol` **HSTMT**temporaire , appels , , , et `SQLMoreResults`. `SQLCancel`peut être appelé sur le **HSTMT**.

## <a name="getdatabasename"></a>GetDatabaseName (en)

`SQLGetInfo SQL_DATABASE_NAME`sera appelé.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans, Rollback

`SQLSetConnectOption SQL_AUTOCOMMIT`et `SQLTransact SQL_COMMIT`, **SQL_ROLLBACK** et **SQL_AUTOCOMMIT** seront appelés si des demandes de transaction sont faites.

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`, `SQLPrepare` `SQLExecute` ( `Open` (Pour et `Requery`), `SQLExecDirect` `SQLFreeStmt` (pour les opérations de mise à jour), doit être pris en charge. `SQLNumResultCols`et `SQLDescribeCol` sera appelé sur les résultats fixés à divers moments.

`SQLSetParam`est largement utilisé pour la liaison des données de paramètres et **DATA_AT_EXEC** fonctionnalité.

`SQLBindCol`est largement utilisé pour enregistrer les emplacements de stockage de données de la colonne de sortie avec ODBC.

Deux `SQLGetData` appels sont utilisés pour récupérer **SQL_LONG_VARCHAR** et **SQL_LONG_VARBINARY** données. Le premier appel tente de trouver la longueur `SQLGetData` totale de la valeur de la colonne en appelant avec cbMaxValue de 0, mais avec un pcbValue valide. Si pcbValue détient **SQL_NO_TOTAL**, une exception est lancée. Dans le cas contraire, un **HGLOBAL** est attribué, et un autre `SQLGetData` appel fait pour récupérer l’ensemble du résultat.

## <a name="updating"></a>Mise à jour

Si un verrouillage pessimiste `SQLGetInfo SQL_LOCK_TYPES` est demandé, sera interrogé. Si **SQL_LCK_EXCLUSIVE n’est** pas pris en charge, une exception sera lancée.

Les tentatives `CRecordset` de mise à jour**d’un instantané** ou **dynaset**) feront en sorte qu’un deuxième **HSTMT** sera attribué. Pour les conducteurs qui ne prennent pas en charge le deuxième **HSTMT**, la bibliothèque de curseurs simulera cette fonctionnalité. Malheureusement, cela peut parfois signifier forcer la requête actuelle sur le premier **HSTMT** à se terminer avant de traiter la demande du deuxième **HSTMT.**

`SQLFreeStmt SQL_CLOSE`et **SQL_RESET_PARAMS** et `SQLGetCursorName` sera appelé pendant les opérations de mise à jour.

S’il y a **des CLongBinarys** dans les **outputColumns**, la fonctionnalité **DATA_AT_EXEC** d’ODBC doit être prise en charge. Cela comprend **SQL_NEED_DATA** le retour `SQLExecDirect`SQL_NEED_DATA `SQLParamData` `SQLPutData`de , et .

`SQLRowCount`est appelé après l’exécution pour vérifier que `SQLExecDirect`seulement 1 enregistrement a été mis à jour par le .

## <a name="forwardonly-cursors"></a>ForwardOnly Cursors

Il `SQLFetch` n’est `Move` nécessaire que pour les opérations. Notez que les curseurs **forwardOnly** ne prennent pas en charge les mises à jour.

## <a name="snapshot-cursors"></a>Cursors instantanés

La fonctionnalité `SQLExtendedFetch` d’instantané nécessite un support. Comme nous l’avons mentionné ci-dessus, la bibliothèque de `SQLExtendedFetch`curseurs de l’ODBC détectera quand un conducteur ne prend pas en charge et fournira le soutien nécessaire lui-même.

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** doit soutenir **SQL_SO_STATIC**.

## <a name="dynaset-cursors"></a>Curseurs Dynaset

Voici le support minimum requis pour ouvrir un dynaset :

`SQLGetInfo`, **SQL_ODBC_VER** doit retourner > "01".

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** doit soutenir **SQL_SO_KEYSET_DRIVEN**.

`SQLGetInfo`, **SQL_ROW_UPDATES** doit retourner "Y".

`SQLGetInfo`, **SQL_POSITIONED_UPDATES** doit soutenir **SQL_PS_POSITIONED_DELETE** et **SQL_PS_POSITIONED_UPDATE**.

En outre, si un verrouillage pessimiste `SQLSetPos` est demandé, un appel à irow 1, fRefresh FALSE et fLock **SQL_LCK_EXCLUSIVE** sera faite.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
