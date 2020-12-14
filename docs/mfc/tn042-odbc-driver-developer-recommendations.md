---
description: 'En savoir plus sur : TN042 : recommandations pour les développeurs de pilotes ODBC'
title: 'TN042 : Recommandations du développeur concernant le pilote ODBC'
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 896c99ffeba98f1ea38771676475c85abf13d983
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215298"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042 : Recommandations du développeur concernant le pilote ODBC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les instructions pour les writers de pilote ODBC. Il décrit les exigences générales et les hypothèses concernant les fonctionnalités ODBC effectuées par les classes de base de données MFC et les divers détails sémantiques attendus. La fonctionnalité de pilote requise pour prendre en charge les trois `CRecordset` modes ouverts (**ForwardOnly**, **snapshot** et **Dynaset**) est décrite.

## <a name="odbcs-cursor-library"></a>Bibliothèque de curseurs ODBC

Les classes de base de données MFC présentent des fonctionnalités à l’utilisateur qui, dans de nombreux cas, dépasse la fonctionnalité fournie par la plupart des pilotes ODBC de niveau 1. Heureusement, la bibliothèque de curseurs ODBC se couchera entre les classes de base de données et le pilote et fournira automatiquement la plupart de ces fonctionnalités supplémentaires.

Par exemple, la plupart des pilotes 1,0 ne prennent pas en charge le défilement arrière. La bibliothèque de curseurs peut détecter cela et met en cache les lignes du pilote et les présente comme demandé sur les appels de FETCH_PREV dans `SQLExtendedFetch` .

Un autre exemple important de dépendance de la bibliothèque de curseurs est le positionnement des mises à jour. La plupart des pilotes 1,0 n’ont pas non plus de mises à jour positionnées, mais la bibliothèque de curseurs génère des instructions UPDATE qui identifient une ligne cible sur la source de données en fonction de ses valeurs de données mises en cache actuelles ou d’une valeur timestamp mise en cache.

La bibliothèque de classes n’utilise jamais plusieurs ensembles de lignes. Par conséquent, les quelques `SQLSetPos` instructions sont toujours appliquées à la ligne 1 de l’ensemble de lignes.

## <a name="cdatabases"></a>CDatabases

Chaque `CDatabase` alloue un **hdbc** unique. (Si `CDatabase` la `ExecuteSQL` fonction est utilisée, un **HSTMT** est alloué temporairement.) Si plusieurs `CDatabase` sont nécessaires, plusieurs **hdbc** s par **henv** doivent être pris en charge.

Les classes de base de données nécessitent la bibliothèque de curseurs. Cela se reflète dans un `SQLSetConnections` appel **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.

`SQLDriverConnect`, **SQL_DRIVER_COMPLETE** est utilisé par `CDatabase::Open` pour établir la connexion à la source de données.

Le pilote doit prendre en charge `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >=  **SQL_OAC_LEVEL1**, `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**.

Pour que les transactions soient prises en charge pour le `CDatabase` et ses recordsets dépendants, `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` et **SQL_CURSOR_ROLLBACK_BEHAVIOR** doivent avoir des **SQL_CR_PRESERVE**. Sinon, les tentatives d’exécution du contrôle de transaction seront ignorées.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY` doit être pris en charge. Si elle retourne « Y », aucune opération de mise à jour ne sera effectuée sur la source de données.

Si le `CDatabase` est ouvert en lecture seule, une tentative de définition de la source de données en lecture seule est effectuée avec `SQLSetConnectOption SQL_ACCESS_MODE` , **SQL_MODE_READ_ONLY**.

Si les identificateurs requièrent des guillemets, ces informations doivent être retournées par le pilote à l’aide d’un `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` appel.

À des fins de débogage, `SQLGetInfo SQL_DBMS_VER` et **SQL_DBMS_NAME** sont récupérés à partir du pilote.

`SQLSetStmtOption SQL_QUERY_TIMEOUT` et **SQL_ASYNC_ENABLE** peuvent être appelés sur le `CDatabase` **hdbc** d’un.

`SQLError` peut être appelée avec tout ou partie des arguments NULL.

Bien entendu, `SQLAllocEnv` , `SQLAllocConnect` `SQLDisconnect` et `SQLFreeConnect` doivent être pris en charge.

## <a name="executesql"></a>ExecuteSQL

En plus d’allouer et de libérer un **HSTMT** temporaire `ExecuteSQL` , `SQLExecDirect` appelle `SQLFetch` , `SQLNumResultCol` et `SQLMoreResults` . `SQLCancel` peut être appelé sur **HSTMT**.

## <a name="getdatabasename"></a>GetDatabaseName,

`SQLGetInfo SQL_DATABASE_NAME` sera appelé.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans, Rollback

`SQLSetConnectOption SQL_AUTOCOMMIT` et `SQLTransact SQL_COMMIT` , **SQL_ROLLBACK** et **SQL_AUTOCOMMIT** sont appelés si les demandes de transaction sont effectuées.

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`, `SQLPrepare` , `SQLExecute` (Pour `Open` et `Requery` ), `SQLExecDirect` (pour les opérations de mise à jour), `SQLFreeStmt` doit être pris en charge. `SQLNumResultCols` et `SQLDescribeCol` sont appelées sur le jeu de résultats à différents moments.

`SQLSetParam` est largement utilisé pour lier les données de paramètres et les fonctionnalités de **DATA_AT_EXEC** .

`SQLBindCol` est largement utilisé pour enregistrer les emplacements de stockage des données de la colonne de sortie avec ODBC.

Deux `SQLGetData` appels sont utilisés pour récupérer des données **SQL_LONG_VARCHAR** et **SQL_LONG_VARBINARY** . Le premier appel tente de trouver la longueur totale de la valeur de colonne en appelant `SQLGetData` avec cbMaxValue 0, mais avec un pcbValue valide. Si pcbValue contient **SQL_NO_TOTAL**, une exception est levée. Dans le cas contraire, un **HGLOBAL** est alloué et un autre `SQLGetData` appel est effectué pour récupérer le résultat entier.

## <a name="updating"></a>Mise à jour

Si le verrouillage pessimiste est demandé, `SQLGetInfo SQL_LOCK_TYPES` sera interrogé. Si **SQL_LCK_EXCLUSIVE** n’est pas pris en charge, une exception est levée.

Toute tentative de mise à jour d’un `CRecordset` (**instantané** ou d’une **feuille de réponse**) entraîne l’allocation d’un second **HSTMT** . Pour les pilotes qui ne prennent pas en charge le second **HSTMT**, la bibliothèque de curseurs simule cette fonctionnalité. Malheureusement, cela peut parfois signifier forcer la fin de la requête actuelle sur le premier **HSTMT** avant de traiter la demande du deuxième **HSTMT**.

`SQLFreeStmt SQL_CLOSE` et **SQL_RESET_PARAMS** et `SQLGetCursorName` seront appelés pendant les opérations de mise à jour.

S’il existe **CLongBinarys** dans le **outputColumns**, les fonctionnalités de **DATA_AT_EXEC** ODBC doivent être prises en charge. Cela comprend le retour de **SQL_NEED_DATA** à partir de `SQLExecDirect` et de `SQLParamData` `SQLPutData` .

`SQLRowCount` est appelé après l’exécution de pour vérifier que seul un enregistrement a été mis à jour par le `SQLExecDirect` .

## <a name="forwardonly-cursors"></a>Curseurs ForwardOnly

Seul `SQLFetch` est requis pour les `Move` opérations. Notez que les curseurs **ForwardOnly** ne prennent pas en charge les mises à jour.

## <a name="snapshot-cursors"></a>Curseurs d’instantanés

La fonctionnalité d’instantané requiert la `SQLExtendedFetch` prise en charge. Comme indiqué ci-dessus, la bibliothèque de curseurs ODBC détecte quand un pilote ne prend pas en charge `SQLExtendedFetch` et fournit le support nécessaire lui-même.

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** doit prendre en charge les **SQL_SO_STATIC**.

## <a name="dynaset-cursors"></a>Curseurs de feuille de réponse dynamique

Voici la prise en charge minimale requise pour ouvrir une feuille de réponse dynamique :

`SQLGetInfo`, **SQL_ODBC_VER** doit retourner la > « 01 ».

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** doit prendre en charge les **SQL_SO_KEYSET_DRIVEN**.

`SQLGetInfo`, **SQL_ROW_UPDATES** doit retourner « Y ».

`SQLGetInfo`, **SQL_POSITIONED_UPDATES** doit prendre en charge **SQL_PS_POSITIONED_DELETE** et **SQL_PS_POSITIONED_UPDATE**.

En outre, si le verrouillage pessimiste est demandé, un appel à `SQLSetPos` avec IRow 1, FREFRESH false et troupeau **SQL_LCK_EXCLUSIVE** sera effectué.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
