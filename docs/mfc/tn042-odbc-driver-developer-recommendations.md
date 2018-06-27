---
title: 'TN042 : Recommandations du développeur le pilote ODBC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.odbc
dev_langs:
- C++
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec79ad70f02581d5ea4481c9b2638d522b554eff
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950573"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042 : Recommandations du développeur concernant le pilote ODBC
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note décrit les recommandations pour les rédacteurs de pilotes ODBC. Il décrit les exigences générales et les hypothèses de la fonctionnalité ODBC qui les classes de base de données MFC et divers détails sémantiques attendues. Requis pour prendre en charge les trois fonctionnalités du pilote `CRecordset` ouvrir modes (**forwardOnly**, **instantané** et **dynaset**) sont décrites.  
  
## <a name="odbcs-cursor-library"></a>Bibliothèque de curseurs ODBC  
 Les classes de base de données MFC présentent les fonctionnalités à l’utilisateur qui, dans de nombreux cas, dépasse les fonctionnalités fournies par la plupart des pilotes ODBC de niveau 1. Heureusement, bibliothèque de curseurs ODBC se superpose entre les classes de base de données et le pilote et vous propose automatiquement la plupart de ces fonctionnalités supplémentaires.  
  
 Par exemple, la plupart des pilotes 1.0 ne gèrent pas le défilement vers l’arrière. La bibliothèque de curseurs peut détecter et sera mettre en cache les lignes à partir du pilote et de les présenter comme demandé sur les appels FETCH_PREV dans `SQLExtendedFetch`.  
  
 Constitue un exemple de dépendance de bibliothèque de curseur est mises à jour positionnées. La plupart des pilotes 1.0 n’ont pas plus de mises à jour positionnées, mais la bibliothèque de curseurs génère des instructions de mise à jour permettant d’identifier une ligne cible sur la source de données en fonction de ses valeurs de données mises en cache en cours, ou une valeur d’horodatage mis en cache.  
  
 La bibliothèque de classes utilise jamais plusieurs ensembles de lignes. Par conséquent, les quelques `SQLSetPos` instructions sont toujours appliquées pour la ligne 1 de l’ensemble de lignes.  
  
## <a name="cdatabases"></a>CDatabases  
 Chaque `CDatabase` alloue une seule **pas**. (Si `CDatabase`de `ExecuteSQL` fonction est utilisée, une **HSTMT** temporairement alloué.) Par conséquent, si plusieurs `CDatabase`de sont requis, plusieurs **pas**s par **HENV** doit être pris en charge.  
  
 Les classes de base de données nécessitent la bibliothèque de curseurs. Cela se reflète dans un `SQLSetConnections` appeler **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.  
  
 `SQLDriverConnect`, **SQL_DRIVER_COMPLETE** est utilisé par `CDatabase::Open` pour établir la connexion à la source de données.  
  
 Le pilote doit prendre en charge `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >=  **SQL_OAC_LEVEL1**, `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**.  
  
 Dans l’ordre pour les transactions à être pris en charge pour le `CDatabase` et ses jeux d’enregistrements dépendant, `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` et **SQL_CURSOR_ROLLBACK_BEHAVIOR** doit avoir **SQL_CR_PRESERVE**. Dans le cas contraire, tente d’effectuer le contrôle de transaction sera ignoré.  
  
 `SQLGetInfo SQL_DATA_SOURCE_READ_ONLY` doit être pris en charge. Si elle retourne « Y », aucune opération de mise à jour n’est effectuée sur la source de données.  
  
 Si le `CDatabase` est ouvert en lecture seule, une tentative de définition de la source de données en lecture seulement sera effectuée avec `SQLSetConnectOption SQL_ACCESS_MODE`, **SQL_MODE_READ_ONLY**.  
  
 Si les identificateurs nécessitent la mise entre guillemets, ces informations doivent être retournées par le pilote avec une `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` appeler.  
  
 Pour le débogage, `SQLGetInfo SQL_DBMS_VER` et **SQL_DBMS_NAME** sont récupérés à partir du pilote.  
  
 `SQLSetStmtOption SQL_QUERY_TIMEOUT` et **SQL_ASYNC_ENABLE** peut être appelée sur un `CDatabase`de **pas**.  
  
 `SQLError` peut être appelée avec un ou tous les arguments NULL.  
  
 Bien entendu, `SQLAllocEnv`, `SQLAllocConnect`, `SQLDisconnect` et `SQLFreeConnect` doivent être pris en charge.  
  
## <a name="executesql"></a>ExecuteSQL  
 Outre l’allocation et la libération temporaire **HSTMT**, `ExecuteSQL` appelle `SQLExecDirect`, `SQLFetch`, `SQLNumResultCol` et `SQLMoreResults`. `SQLCancel` peut être appelée sur le **HSTMT**.  
  
## <a name="getdatabasename"></a>GetDatabaseName  
 `SQLGetInfo SQL_DATABASE_NAME` est appelée.  
  
## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans et Rollback  
 `SQLSetConnectOption SQL_AUTOCOMMIT` et `SQLTransact SQL_COMMIT`, **SQL_ROLLBACK** et **SQL_AUTOCOMMIT** sera appelée si les demandes de transaction sont effectuées.  
  
## <a name="crecordsets"></a>CRecordsets  
 `SQLAllocStmt`, `SQLPrepare`, `SQLExecute` (Pour `Open` et `Requery`), `SQLExecDirect` (pour les opérations de mise à jour), `SQLFreeStmt` doit être pris en charge. `SQLNumResultCols` et `SQLDescribeCol` seront appelées sur les résultats à des moments différents.  
  
 `SQLSetParam` est largement utilisé pour la liaison de données de paramètre et **DATA_AT_EXEC** fonctionnalité.  
  
 `SQLBindCol` largement utilisée pour inscrire des emplacements de stockage de données de colonne avec ODBC de sortie.  
  
 Deux `SQLGetData` appels sont utilisés pour récupérer **SQL_LONG_VARCHAR** et **SQL_LONG_VARBINARY** données. Le premier appel tente de trouver la longueur totale de la valeur de colonne en appelant `SQLGetData` cbMaxValue 0, mais avec un pcbValue valid. Si sa valeur est pcbValue **SQL_NO_TOTAL**, une exception est levée. Sinon, une **HGLOBAL** est alloué et un autre `SQLGetData` appel effectuée pour extraire l’ensemble de résultats.  
  
## <a name="updating"></a>Mise à jour  
 Si le verrouillage pessimiste est demandé, `SQLGetInfo SQL_LOCK_TYPES` sera interrogé. Si **SQL_LCK_EXCLUSIVE** est ne pas pris en charge, une exception sera levée.  
  
 Tente de mettre à jour un `CRecordset` (**instantané** ou **dynaset**) entraînera une seconde **HSTMT** à allouer. Pour les pilotes qui ne gèrent pas seconde **HSTMT**, la bibliothèque de curseurs simule cette fonctionnalité. Malheureusement, cela peut signifier parfois forcer la requête en cours sur le premier **HSTMT** jusqu'à la fin avant le traitement de la seconde **HSTMT**de demande.  
  
 `SQLFreeStmt SQL_CLOSE` et **SQL_RESET_PARAMS** et `SQLGetCursorName` sera appelé pendant les opérations de mise à jour.  
  
 S’il n’y **CLongBinarys** dans les **outputColumns**, ODBC **DATA_AT_EXEC** fonctionnalité doit être prise en charge. Cela inclut le retour **SQL_NEED_DATA** de `SQLExecDirect`, `SQLParamData` et `SQLPutData`.  
  
 `SQLRowCount` est appelée après l’exécution pour vérifier que (1) seul enregistrement a été mis à jour par le `SQLExecDirect`.  
  
## <a name="forwardonly-cursors"></a>Curseurs ForwardOnly  
 Uniquement `SQLFetch` est requis pour la `Move` opérations. Notez que **forwardOnly** les curseurs ne prennent pas en charge les mises à jour.  
  
## <a name="snapshot-cursors"></a>Curseurs de capture instantanée  
 Fonctionnalité de captures instantanées nécessite `SQLExtendedFetch` prend en charge. Comme indiqué ci-dessus, la bibliothèque de curseurs ODBC détecte lorsqu’un pilote ne prend pas en charge `SQLExtendedFetch`et fournir la prise en charge nécessaire lui-même.  
  
 `SQLGetInfo`, **SQL_SCROLL_OPTIONS** doit prendre en charge **SQL_SO_STATIC**.  
  
## <a name="dynaset-cursors"></a>Curseurs de feuille de réponse dynamique  
 Vous trouverez ci-dessous la prise en charge minimale requise pour ouvrir une feuille de réponse dynamique :  
  
 `SQLGetInfo`, **SQL_ODBC_VER** doit retourner > « 01 ».  
  
 `SQLGetInfo`, **SQL_SCROLL_OPTIONS** doit prendre en charge **SQL_SO_KEYSET_DRIVEN**.  
  
 `SQLGetInfo`, **SQL_ROW_UPDATES** doit retourner « Y ».  
  
 `SQLGetInfo`, **SQL_POSITIONED_UPDATES** doit prendre en charge **SQL_PS_POSITIONED_DELETE** et **SQL_PS_POSITIONED_UPDATE**.  
  
 En outre, si le verrouillage pessimiste est demandé, un appel à `SQLSetPos` avec irow 1, fRefresh FALSE et généalogique **SQL_LCK_EXCLUSIVE** sera établie.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

