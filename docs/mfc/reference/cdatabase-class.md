---
title: CDatabase, classe
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: ebc36d82af9bfe12ab30a86214e58610b5eaab95
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418754"
---
# <a name="cdatabase-class"></a>CDatabase, classe

Représente une connexion à une source de données, par l'intermédiaire de laquelle vous pouvez utiliser la source de données.

## <a name="syntax"></a>Syntaxe

```
class CDatabase : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CDatabase :: CDatabase](#cdatabase)|Construit un objet `CDatabase`. Vous devez initialiser l’objet en appelant `OpenEx` ou `Open`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CDatabase :: BeginTrans](#begintrans)|Démarre une « transaction », une série d’appels réversibles aux fonctions membres `AddNew`, `Edit`, `Delete`et `Update` de la classe `CRecordset`, sur la source de données connectée. La source de données doit prendre en charge les transactions pour que `BeginTrans` ait un effet.|
|[CDatabase :: BindParameters](#bindparameters)|Vous permet de lier des paramètres avant d’appeler `CDatabase::ExecuteSQL`.|
|[CDatabase :: Cancel](#cancel)|Annule une opération asynchrone ou un processus à partir d’un deuxième thread.|
|[CDatabase :: CanTransact](#cantransact)|Retourne une valeur différente de zéro si la source de données prend en charge les transactions.|
|[CDatabase :: CanUpdate](#canupdate)|Retourne une valeur différente de zéro si l’objet `CDatabase` peut être mis à jour (pas en lecture seule).|
|[CDatabase :: Close](#close)|Ferme la connexion à la source de données.|
|[CDatabase :: CommitTrans](#committrans)|Termine une transaction commencée par `BeginTrans`. Les commandes de la transaction qui modifient la source de données sont exécutées.|
|[CDatabase :: ExecuteSQL](#executesql)|Exécute une instruction SQL. Aucun enregistrement de données n’est retourné.|
|[CDatabase :: GetBookmarkPersistence](#getbookmarkpersistence)|Identifie les opérations par le biais desquelles les signets sont conservés sur les objets Recordset.|
|[CDatabase :: GetConnect](#getconnect)|Retourne la chaîne de connexion ODBC utilisée pour connecter l’objet `CDatabase` à une source de données.|
|[CDatabase :: GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifie l’effet de la validation d’une transaction sur un objet Recordset ouvert.|
|[CDatabase :: GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifie l’effet de la restauration d’une transaction sur un objet Recordset ouvert.|
|[CDatabase :: GetDatabaseName,](#getdatabasename)|Retourne le nom de la base de données en cours d’utilisation.|
|[CDatabase :: IsOpen](#isopen)|Retourne une valeur différente de zéro si l’objet `CDatabase` est actuellement connecté à une source de données.|
|[CDatabase :: OnSetOptions](#onsetoptions)|Appelée par l’infrastructure pour définir les options de connexion standard. L’implémentation par défaut définit la valeur du délai d’expiration de la requête. Vous pouvez définir ces options à l’avance en appelant `SetQueryTimeout`.|
|[CDatabase :: Open](#open)|Établit une connexion à une source de données (via un pilote ODBC).|
|[CDatabase :: OpenEx](#openex)|Établit une connexion à une source de données (via un pilote ODBC).|
|[CDatabase :: Rollback](#rollback)|Annule les modifications apportées pendant la transaction en cours. La source de données revient à son état précédent, comme défini lors de l’appel de `BeginTrans`, sans modification.|
|[CDatabase :: SetLoginTimeout](#setlogintimeout)|Définit le nombre de secondes au terme desquelles une tentative de connexion à la source de données expire.|
|[CDatabase :: SetQueryTimeout](#setquerytimeout)|Définit le nombre de secondes après lequel les opérations de requête de base de données expirent. Affecte tous les appels de `Open`, `AddNew`, `Edit`et `Delete` du Recordset ultérieurs.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CDatabase :: m_hdbc](#m_hdbc)|Handle de connexion Open Database Connectivity (ODBC) à une source de données. Tapez *hdbc*.|

## <a name="remarks"></a>Notes

Une source de données est une instance spécifique de données hébergées par un système de gestion de base de données (SGBD). Exemples : Microsoft SQL Server, Microsoft Access, Borland dBASE et xBASE. Vous pouvez avoir un ou plusieurs objets `CDatabase` actifs à la fois dans votre application.

> [!NOTE]
>  Si vous utilisez les classes DAO (Data Access Objects) au lieu des classes Open Database Connectivity (ODBC), utilisez la classe [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de bases de données](../../data/data-access-programming-mfc-atl.md).

Pour utiliser `CDatabase`, construisez un objet `CDatabase` et appelez sa fonction membre `OpenEx`. Cela ouvre une connexion. Lorsque vous construisez ensuite `CRecordset` objets pour fonctionner sur la source de données connectée, transmettez au constructeur du jeu d’enregistrements un pointeur vers votre objet `CDatabase`. Lorsque vous avez terminé d’utiliser la connexion, appelez la fonction membre `Close` et détruisez l’objet `CDatabase`. `Close` ferme tous les jeux d’enregistrements que vous n’avez pas fermés précédemment.

Pour plus d’informations sur `CDatabase`, consultez les articles [source de données (ODBC)](../../data/odbc/data-source-odbc.md) et [vue d’ensemble : programmation de bases de données](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXDB. h

##  <a name="begintrans"></a>CDatabase :: BeginTrans

Appelez cette fonction membre pour commencer une transaction avec la source de données connectée.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’appel a réussi et que les modifications sont validées uniquement manuellement ; Sinon, 0.

### <a name="remarks"></a>Notes

Une transaction se compose d’un ou de plusieurs appels aux fonctions membres `AddNew`, `Edit`, `Delete`et `Update` d’un objet `CRecordset`. Avant de commencer une transaction, l’objet `CDatabase` doit déjà avoir été connecté à la source de données en appelant sa fonction membre `OpenEx` ou `Open`. Pour mettre fin à la transaction, appelez [CommitTrans](#committrans) pour accepter toutes les modifications apportées à la source de données (et les exécuter) ou appelez [Rollback](#rollback) pour abandonner l’intégralité de la transaction. Appelez `BeginTrans` après avoir ouvert tous les jeux d’enregistrements impliqués dans la transaction et aussi près des opérations de mise à jour effectives que possible.

> [!CAUTION]
>  En fonction de votre pilote ODBC, l’ouverture d’un Recordset avant d’appeler `BeginTrans` peut provoquer des problèmes lors de l’appel de `Rollback`. Vous devez vérifier le pilote spécifique que vous utilisez. Par exemple, lorsque vous utilisez le pilote Microsoft Access inclus dans Microsoft ODBC Desktop Driver Pack 3,0, vous devez tenir compte du fait que le moteur de base de données Jet exige que vous ne commenciez pas une transaction sur une base de données qui possède un curseur ouvert. Dans les classes de base de données MFC, un curseur ouvert signifie un objet `CRecordset` ouvert. Pour plus d’informations, consultez la [note technique 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans` pouvez également verrouiller les enregistrements de données sur le serveur, en fonction de la concurrence demandée et des fonctionnalités de la source de données. Pour plus d’informations sur le verrouillage des données, consultez l’article [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Les transactions définies par l’utilisateur sont expliquées dans l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans` établit l’État dans lequel la séquence de transactions peut être restaurée (inversée). Pour établir un nouvel État pour les restaurations, validez toute transaction en cours, puis appelez à nouveau `BeginTrans`.

> [!CAUTION]
>  L’appel de `BeginTrans` à nouveau sans appeler `CommitTrans` ou `Rollback` est une erreur.

Appelez la fonction membre [CanTransact](#cantransact) pour déterminer si votre pilote prend en charge les transactions pour une base de données donnée. Vous devez également appeler [GetCursorCommitBehavior](#getcursorcommitbehavior) et [GetCursorRollbackBehavior](#getcursorrollbackbehavior) pour déterminer la prise en charge de la conservation de curseur.

Pour plus d’informations sur les transactions, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Exemple

  Consultez l’article [transaction : exécution d’une transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="bindparameters"></a>CDatabase :: BindParameters

Substituez `BindParameters` lorsque vous avez besoin de lier des paramètres avant d’appeler [CDatabase :: ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*risquent*<br/>
Handle d’instruction ODBC pour lequel vous souhaitez lier des paramètres.

### <a name="remarks"></a>Notes

Cette approche est utile lorsque vous n’avez pas besoin du jeu de résultats d’une procédure stockée.

Dans votre remplacement, appelez `SQLBindParameters` et les fonctions ODBC associées pour lier les paramètres. MFC appelle votre substitution avant votre appel à `ExecuteSQL`. Vous n’avez pas besoin d’appeler `SQLPrepare`; `ExecuteSQL` appelle `SQLExecDirect` et détruit le *HSTMT*, qui n’est utilisé qu’une seule fois.

##  <a name="cancel"></a>CDatabase :: Cancel

Appelez cette fonction membre pour demander que la source de données annule une opération asynchrone en cours ou un processus à partir d’un deuxième thread.

```
void Cancel();
```

### <a name="remarks"></a>Notes

Notez que les classes ODBC MFC n’utilisent plus le traitement asynchrone ; pour effectuer une opération asynchrone, vous devez appeler directement la fonction API ODBC [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Pour plus d’informations, consultez [exécution asynchrone](/sql/odbc/reference/develop-app/asynchronous-execution).

##  <a name="cantransact"></a>CDatabase :: CanTransact

Appelez cette fonction membre pour déterminer si la base de données autorise les transactions.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les recordsets qui utilisent cet objet `CDatabase` autorisent les transactions ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les transactions, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CDatabase :: CanUpdate

Appelez cette fonction membre pour déterminer si l’objet `CDatabase` autorise les mises à jour.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet `CDatabase` autorise les mises à jour ; sinon 0, ce qui indique que vous avez passé TRUE dans *bReadOnly* lorsque vous avez ouvert l’objet `CDatabase` ou que la source de données elle-même est en lecture seule. La source de données est en lecture seule si un appel à la fonction API ODBC `SQLGetInfo` pour SQL_DATASOURCE_READ_ONLY retourne « y ».

### <a name="remarks"></a>Notes

Tous les pilotes ne prennent pas en charge les mises à jour.

##  <a name="cdatabase"></a>CDatabase :: CDatabase

Construit un objet `CDatabase`.

```
CDatabase();
```

### <a name="remarks"></a>Notes

Après avoir construit l’objet, vous devez appeler sa fonction membre `OpenEx` ou `Open` pour établir une connexion à une source de données spécifiée.

Il peut s’avérer utile d’incorporer l’objet `CDatabase` dans votre classe de document.

### <a name="example"></a>Exemple

Cet exemple illustre l’utilisation de `CDatabase` dans une classe dérivée de `CDocument`.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>CDatabase :: Close

Appelez cette fonction membre si vous souhaitez vous déconnecter d’une source de données.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Vous devez fermer tous les jeux d’enregistrements associés à l’objet `CDatabase` avant d’appeler cette fonction membre. Étant donné que `Close` ne détruit pas l’objet `CDatabase`, vous pouvez réutiliser l’objet en ouvrant une nouvelle connexion à la même source de données ou à une source de données différente.

Toutes les instructions `AddNew` ou `Edit` en attente d’un jeu d’enregistrements utilisant la base de données sont annulées, et toutes les transactions en attente sont annulées. Tous les jeux d’enregistrements dépendants de l’objet `CDatabase` sont laissés dans un État indéfini.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>CDatabase :: CommitTrans

Appelez cette fonction membre lors de l’exécution des transactions.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les mises à jour ont été validées avec succès ; Sinon, 0. Si `CommitTrans` échoue, l’état de la source de données n’est pas défini. Vous devez vérifier les données pour déterminer son état.

### <a name="remarks"></a>Notes

Une transaction se compose d’une série d’appels aux fonctions membres `AddNew`, `Edit`, `Delete`et `Update` d’un objet `CRecordset` qui a commencé par un appel à la fonction membre [BeginTrans](#begintrans) . `CommitTrans` valide la transaction. Par défaut, les mises à jour sont validées immédiatement ; l’appel de `BeginTrans` entraîne le report de l’engagement des mises à jour jusqu’à ce que `CommitTrans` soit appelée.

Tant que vous n’avez pas appelé `CommitTrans` pour mettre fin à une transaction, vous pouvez appeler la fonction membre [Rollback](#rollback) pour abandonner la transaction et conserver la source de données dans son état d’origine. Pour commencer une nouvelle transaction, appelez à nouveau `BeginTrans`.

Pour plus d’informations sur les transactions, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Exemple

  Consultez l’article [transaction : exécution d’une transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="executesql"></a>CDatabase :: ExecuteSQL

Appelez cette fonction membre lorsque vous devez exécuter une commande SQL directement.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Paramètres

*lpszSQL*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient une commande SQL valide à exécuter. Vous pouvez passer une [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Créez la commande comme une chaîne se terminant par un caractère null. `ExecuteSQL` ne retourne pas d’enregistrements de données. Si vous souhaitez utiliser des enregistrements, utilisez un objet Recordset à la place.

La plupart de vos commandes pour une source de données sont émises par le biais d’objets Recordset, qui prennent en charge les commandes de sélection des données, d’insertion de nouveaux enregistrements, de suppression d’enregistrements et de modification d’enregistrements. Toutefois, toutes les fonctionnalités ODBC ne sont pas directement prises en charge par les classes de base de données. par conséquent, vous pouvez avoir besoin d’effectuer un appel direct SQL avec `ExecuteSQL`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>CDatabase :: GetBookmarkPersistence

Appelez cette fonction membre pour déterminer la persistance des signets sur un objet recordset après certaines opérations.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Valeur de retour

Un masque de bits qui identifie les opérations par lesquelles les signets persistent sur un objet recordset. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Par exemple, si vous appelez `CRecordset::GetBookmark`, puis `CRecordset::Requery`, le signet obtenu à partir de `GetBookmark` risque de ne plus être valide. Vous devez appeler `GetBookmarkPersistence` avant d'appeler `CRecordset::SetBookmark`.

Le tableau suivant liste les valeurs de masque de bits qui peuvent être combinées pour la valeur de retour de `GetBookmarkPersistence`.

|Valeur du masque de bits|Persistance des signets|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Les signets sont valides après une opération de `Requery`.|
|SQL_BP_DELETE|Le signet d’une ligne est valide après une opération `Delete` sur cette ligne.|
|SQL_BP_DROP|Les signets sont valides après une opération de `Close`.|
|SQL_BP_SCROLL|Les signets sont valides après toute opération de `Move`. Permet simplement de déterminer si les signets sont pris en charge sur le recordset, comme cela est retourné par `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Les signets sont valides après qu'une transaction est validée ou restaurée.|
|SQL_BP_UPDATE|Le signet d’une ligne est valide après une opération `Update` sur cette ligne.|
|SQL_BP_OTHER_HSTMT|Les signets associés à un objet recordset sont valides sur un deuxième recordset.|

Pour plus d’informations sur cette valeur de retour, consultez la fonction API ODBC `SQLGetInfo` dans le SDK Windows. Pour plus d’informations sur les signets, consultez l’article [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="getconnect"></a>CDatabase :: GetConnect

Appelez cette fonction membre pour récupérer la chaîne de connexion utilisée lors de l’appel à `OpenEx` ou `Open` qui a connecté l’objet `CDatabase` à une source de données.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Valeur de retour

**Const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant la chaîne de connexion si `OpenEx` ou `Open` a été appelée ; Sinon, une chaîne vide.

### <a name="remarks"></a>Notes

Consultez [CDatabase :: Open](#open) pour obtenir une description de la façon dont la chaîne de connexion est créée.

##  <a name="getcursorcommitbehavior"></a>CDatabase :: GetCursorCommitBehavior

Appelez cette fonction membre pour déterminer comment une opération [CommitTrans](#committrans) affecte les curseurs sur les objets Recordset ouverts.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur indiquant l’effet des transactions sur les objets Recordset ouverts. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs de retour possibles pour `GetCursorCommitBehavior` et l’effet correspondant sur le Recordset ouvert.

|Valeur retournée|Effet sur les objets CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Appelez `CRecordset::Requery` immédiatement après la validation de la transaction.|
|SQL_CB_DELETE|Appelez `CRecordset::Close` immédiatement après la validation de la transaction.|
|SQL_CB_PRESERVE|Procédez normalement avec les opérations de `CRecordset`.|

Pour plus d’informations sur cette valeur de retour, consultez la fonction API ODBC `SQLGetInfo` dans le SDK Windows. Pour plus d’informations sur les transactions, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getcursorrollbackbehavior"></a>CDatabase :: GetCursorRollbackBehavior

Appelez cette fonction membre pour déterminer comment une opération [Rollback](#rollback) affecte les curseurs sur les objets Recordset ouverts.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur indiquant l’effet des transactions sur les objets Recordset ouverts. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs de retour possibles pour `GetCursorRollbackBehavior` et l’effet correspondant sur le Recordset ouvert.

|Valeur retournée|Effet sur les objets CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Appelez `CRecordset::Requery` immédiatement après la restauration de la transaction.|
|SQL_CB_DELETE|Appelez `CRecordset::Close` immédiatement après la restauration de la transaction.|
|SQL_CB_PRESERVE|Procédez normalement avec les opérations de `CRecordset`.|

Pour plus d’informations sur cette valeur de retour, consultez la fonction API ODBC `SQLGetInfo` dans le SDK Windows. Pour plus d’informations sur les transactions, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getdatabasename"></a>CDatabase :: GetDatabaseName,

Appelez cette fonction membre pour récupérer le nom de la base de données actuellement connectée (à condition que la source de données définisse un objet nommé appelé « base de données »).

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Valeur de retour

[CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom de la base de données en cas de réussite ; Sinon, un `CString`vide.

### <a name="remarks"></a>Notes

Ce n’est pas le même que le nom de source de données (DSN) spécifié dans l’appel `OpenEx` ou `Open`. Ce que `GetDatabaseName` retourne dépend de ODBC. En général, une base de données est une collection de tables. Si cette entité a un nom, `GetDatabaseName` la retourne.

Vous pouvez, par exemple, souhaiter afficher ce nom dans un en-tête. Si une erreur se produit lors de la récupération du nom à partir d’ODBC, `GetDatabaseName` retourne un `CString`vide.

##  <a name="isopen"></a>CDatabase :: IsOpen

Appelez cette fonction membre pour déterminer si l’objet `CDatabase` est actuellement connecté à une source de données.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet `CDatabase` est actuellement connecté ; Sinon, 0.

##  <a name="m_hdbc"></a>CDatabase :: m_hdbc

Contient un handle public vers une connexion de source de données ODBC, un « handle de connexion ».

### <a name="remarks"></a>Notes

Normalement, vous n’aurez pas besoin d’accéder directement à cette variable membre. Au lieu de cela, le Framework alloue le handle quand vous appelez `OpenEx` ou `Open`. Le Framework libère le descripteur lorsque vous appelez l’opérateur **Delete** sur l’objet `CDatabase`. Notez que la fonction membre `Close` ne libère pas le descripteur.

Toutefois, dans certaines circonstances, vous devrez peut-être utiliser le handle directement. Par exemple, si vous avez besoin d’appeler des fonctions API ODBC directement plutôt que par le biais de la classe `CDatabase`, vous pouvez avoir besoin d’un handle de connexion pour passer en tant que paramètre. Consultez l’exemple de code ci-dessous.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>CDatabase :: OnSetOptions

L’infrastructure appelle cette fonction membre lors de l’exécution directe d’une instruction SQL avec la fonction membre `ExecuteSQL`.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*risquent*<br/>
Handle d’instruction ODBC pour lequel des options sont définies.

### <a name="remarks"></a>Notes

`CRecordset::OnSetOptions` appelle également cette fonction membre.

`OnSetOptions` définit la valeur du délai d’attente de la connexion. S’il y a eu des appels précédents à la fonction membre et `SetQueryTimeout`, `OnSetOptions` reflète les valeurs actuelles ; dans le cas contraire, il définit les valeurs par défaut.

> [!NOTE]
>  Avant MFC 4,2, `OnSetOptions` également définir le mode de traitement sur snychronous ou asynchrone. À partir de MFC 4,2, toutes les opérations sont synchrones. Pour effectuer une opération asynchrone, vous devez effectuer un appel direct à la fonction API ODBC `SQLSetPos`.

Vous n’avez pas besoin de substituer `OnSetOptions` pour modifier la valeur du délai d’attente. Au lieu de cela, pour personnaliser la valeur du délai d’expiration de la requête, appelez `SetQueryTimeout` avant de créer un Recordset. `OnSetOptions` utilisera la nouvelle valeur. Les valeurs définies s’appliquent aux opérations suivantes sur tous les jeux d’enregistrements ou appels SQL directs.

Remplacez `OnSetOptions` si vous souhaitez définir des options supplémentaires. Votre substitution doit appeler la classe de base `OnSetOptions` avant ou après l’appel de la fonction API ODBC `SQLSetStmtOption`. Suivez la méthode illustrée dans l’implémentation par défaut de `OnSetOptions`du Framework.

##  <a name="open"></a>CDatabase :: Open

Appelez cette fonction membre pour initialiser un objet `CDatabase` nouvellement construit.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszDSN*<br/>
Spécifie un nom de source de données (nom enregistré avec ODBC via le programme Administrateur ODBC). Si une valeur de DSN est spécifiée dans *lpszConnect* (sous la forme « DSN =\<> de source de données »), elle ne doit plus être spécifiée dans *lpszDSN*. Dans ce cas, *lpszDSN* doit avoir la valeur null. Dans le cas contraire, vous pouvez passer la valeur NULL si vous souhaitez présenter à l’utilisateur une boîte de dialogue de source de données dans laquelle l’utilisateur peut sélectionner une source de données. Pour plus d’informations, consultez la section Notes.

*bExclusive*<br/>
Non pris en charge dans cette version de la bibliothèque de classes. Actuellement, une assertion échoue si ce paramètre a la valeur TRUE. La source de données est toujours ouverte en tant que partagée (non exclusif).

*bReadOnly*<br/>
TRUE si vous souhaitez que la connexion soit en lecture seule et interdire les mises à jour de la source de données. Tous les jeux d’enregistrements dépendants héritent de cet attribut. La valeur par défaut est FALSE.

*lpszConnect*<br/>
Spécifie une chaîne de connexion. La chaîne de connexion concatène les informations, y compris éventuellement un nom de source de données, un ID d’utilisateur valide sur la source de données, une chaîne d’authentification utilisateur (mot de passe, si la source de données en requiert une) et d’autres informations. La chaîne de connexion entière doit être précédée de la chaîne « ODBC ; ». (en majuscules ou en minuscules). La chaîne « ODBC ; » est utilisée pour indiquer que la connexion est à une source de données ODBC ; Il s’agit d’une compatibilité ascendante lorsque les futures versions de la bibliothèque de classes peuvent prendre en charge des sources de données non ODBC.

*bUseCursorLib*<br/>
TRUE si vous souhaitez que la DLL de la bibliothèque de curseurs ODBC soit chargée. La bibliothèque de curseurs masque certaines fonctionnalités du pilote ODBC sous-jacent, ce qui empêche efficacement l’utilisation des feuilles de réponse dynamiques (si le pilote les prend en charge). Les seuls curseurs pris en charge si la bibliothèque de curseurs est chargée sont les instantanés statiques et les curseurs avant uniquement. La valeur par défaut est TRUE. Si vous envisagez de créer un objet Recordset directement à partir de `CRecordset` sans le dériver, vous ne devez pas charger la bibliothèque de curseurs.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la connexion est établie avec succès ; dans le cas contraire, 0 si l’utilisateur choisit annuler lorsqu’une boîte de dialogue s’affiche pour demander plus d’informations de connexion. Dans tous les autres cas, l’infrastructure lève une exception.

### <a name="remarks"></a>Notes

Votre objet de base de données doit être initialisé avant de pouvoir l’utiliser pour construire un objet Recordset.

> [!NOTE]
>  L’appel de la fonction membre [OpenEx](#openex) est la meilleure façon de se connecter à une source de données et d’initialiser votre objet de base de données.

Si les paramètres de votre `Open` appel ne contiennent pas suffisamment d’informations pour établir la connexion, le pilote ODBC ouvre une boîte de dialogue qui vous permet d’obtenir les informations nécessaires auprès de l’utilisateur. Lorsque vous appelez `Open`, votre chaîne de connexion, *lpszConnect*, est stockée en privé dans l’objet `CDatabase` et est disponible en appelant la fonction membre [GetConnect](#getconnect) .

Si vous le souhaitez, vous pouvez ouvrir votre propre boîte de dialogue avant d’appeler `Open` pour obtenir des informations de l’utilisateur, par exemple un mot de passe, puis ajouter ces informations à la chaîne de connexion que vous transmettez à `Open`. Vous pouvez également enregistrer la chaîne de connexion que vous transmettez afin de pouvoir la réutiliser la prochaine fois que votre application appelle `Open` sur un objet `CDatabase`.

Vous pouvez également utiliser la chaîne de connexion pour plusieurs niveaux d’autorisation de connexion (chacun pour un objet `CDatabase` différent) ou pour transmettre d’autres informations spécifiques à la source de données. Pour plus d’informations sur les chaînes de connexion, consultez le chapitre 5 de la SDK Windows.

Une tentative de connexion peut expirer si, par exemple, l’hôte SGBD n’est pas disponible. Si la tentative de connexion échoue, `Open` lève une `CDBException`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>CDatabase :: OpenEx

Appelez cette fonction membre pour initialiser un objet `CDatabase` nouvellement construit.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Paramètres

*lpszConnectString*<br/>
Spécifie une chaîne de connexion ODBC. Cela comprend le nom de la source de données ainsi que d’autres informations facultatives, telles qu’un ID d’utilisateur et un mot de passe. Par exemple, «DSN = SQLServer_Source ; UID = SA ; PWD = ABC123» est une chaîne de connexion possible. Notez que si vous transmettez la valeur NULL pour *lpszConnectString*, une boîte de dialogue de source de données invite l’utilisateur à sélectionner une source de données.

*dwOptions*<br/>
Masque de masque qui spécifie une combinaison des valeurs suivantes. La valeur par défaut est 0, ce qui signifie que la base de données sera ouverte en mode partagé avec accès en écriture, que la DLL de la bibliothèque de curseurs ODBC ne sera pas chargée et que la boîte de dialogue connexion ODBC ne s’affichera que si le nombre d’informations nécessaires à la connexion est insuffisant.

- `CDatabase::openExclusive` pas pris en charge dans cette version de la bibliothèque de classes. Une source de données est toujours ouverte comme partagée (et non exclusive). Actuellement, une assertion échoue si vous spécifiez cette option.

- `CDatabase::openReadOnly` ouvrir la source de données en lecture seule.

- `CDatabase::useCursorLib` de charger la DLL de la bibliothèque de curseurs ODBC. La bibliothèque de curseurs masque certaines fonctionnalités du pilote ODBC sous-jacent, ce qui empêche efficacement l’utilisation des feuilles de réponse dynamiques (si le pilote les prend en charge). Les seuls curseurs pris en charge si la bibliothèque de curseurs est chargée sont les instantanés statiques et les curseurs avant uniquement. Si vous envisagez de créer un objet Recordset directement à partir de `CRecordset` sans le dériver, vous ne devez pas charger la bibliothèque de curseurs.

- `CDatabase::noOdbcDialog` n’affiche pas la boîte de dialogue connexion ODBC, qu’il y ait ou non suffisamment d’informations de connexion.

- `CDatabase::forceOdbcDialog` affiche toujours la boîte de dialogue connexion ODBC.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la connexion est établie avec succès ; dans le cas contraire, 0 si l’utilisateur choisit annuler lorsqu’une boîte de dialogue s’affiche pour demander plus d’informations de connexion. Dans tous les autres cas, l’infrastructure lève une exception.

### <a name="remarks"></a>Notes

Votre objet de base de données doit être initialisé avant de pouvoir l’utiliser pour construire un objet Recordset.

Si le paramètre *lpszConnectString* dans votre appel `OpenEx` ne contient pas suffisamment d’informations pour établir la connexion, le pilote ODBC ouvre une boîte de dialogue pour obtenir les informations nécessaires auprès de l’utilisateur, à condition que vous n’ayez pas défini `CDatabase::noOdbcDialog` ou `CDatabase::forceOdbcDialog` dans le paramètre *dwOptions* . Lorsque vous appelez `OpenEx`, votre chaîne de connexion, *lpszConnectString*, est stockée en privé dans l’objet `CDatabase` et est disponible en appelant la fonction membre [GetConnect](#getconnect) .

Si vous le souhaitez, vous pouvez ouvrir votre propre boîte de dialogue avant d’appeler `OpenEx` pour obtenir des informations de l’utilisateur, par exemple un mot de passe, puis ajouter ces informations à la chaîne de connexion que vous transmettez à `OpenEx`. Vous pouvez également enregistrer la chaîne de connexion que vous transmettez afin de pouvoir la réutiliser la prochaine fois que votre application appelle `OpenEx` sur un objet `CDatabase`.

Vous pouvez également utiliser la chaîne de connexion pour plusieurs niveaux d’autorisation de connexion (chacun pour un objet `CDatabase` différent) ou pour transmettre d’autres informations spécifiques à la source de données. Pour plus d’informations sur les chaînes de connexion, consultez le chapitre 6 dans le *Guide de référence du programmeur ODBC*.

Une tentative de connexion peut expirer si, par exemple, l’hôte SGBD n’est pas disponible. Si la tentative de connexion échoue, `OpenEx` lève une `CDBException`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>CDatabase :: Rollback

Appelez cette fonction membre pour annuler les modifications apportées pendant une transaction.

```
BOOL Rollback();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la transaction a été inversée avec succès ; Sinon, 0. Si un appel de `Rollback` échoue, les États de la source de données et de la transaction ne sont pas définis. Si `Rollback` retourne 0, vous devez vérifier la source de données pour déterminer son état.

### <a name="remarks"></a>Notes

Tous les appels de `CRecordset` `AddNew`, `Edit`, `Delete`et `Update` exécutés depuis la dernière [BeginTrans](#begintrans) sont restaurés à l’État qui existait au moment de cet appel.

Après un appel à `Rollback`, la transaction est terminée, et vous devez appeler à nouveau `BeginTrans` pour une autre transaction. L’enregistrement qui était en cours avant l’appel de `BeginTrans` devient à nouveau l’enregistrement actif après `Rollback`.

Après une restauration, l’enregistrement qui était en cours avant la restauration reste en cours. Pour plus d’informations sur l’état du Recordset et de la source de données après une restauration, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Exemple

  Consultez l’article [transaction : exécution d’une transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="setlogintimeout"></a>CDatabase :: SetLoginTimeout

Appelez cette fonction membre — avant d’appeler `OpenEx` ou `Open` — pour remplacer le nombre de secondes par défaut autorisé avant l’expiration d’une tentative de connexion à la source de données.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Paramètres

*dwSeconds*<br/>
Nombre de secondes à autoriser avant l’expiration d’une tentative de connexion.

### <a name="remarks"></a>Notes

Une tentative de connexion peut expirer si, par exemple, le SGBD n’est pas disponible. Appelez `SetLoginTimeout` après avoir construit l’objet `CDatabase` non initialisé, mais avant d’appeler `OpenEx` ou `Open`.

La valeur par défaut pour les délais d’attente de connexion est de 15 secondes. Toutes les sources de données ne prennent pas en charge la possibilité de spécifier une valeur de délai d’attente de connexion. Si la source de données ne prend pas en charge le délai d’attente, vous bénéficiez d’une sortie de suivi, mais pas d’exception. La valeur 0 signifie « infini ».

##  <a name="setquerytimeout"></a>CDatabase :: SetQueryTimeout

Appelez cette fonction membre pour remplacer le nombre de secondes par défaut à autoriser avant les opérations suivantes sur le délai d’expiration de la source de données connectée.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Paramètres

*dwSeconds*<br/>
Nombre de secondes à autoriser avant l’expiration d’une tentative de requête.

### <a name="remarks"></a>Notes

Une opération peut expirer en raison de problèmes d’accès au réseau, d’un temps de traitement de requêtes excessif, etc. Appelez `SetQueryTimeout` avant d’ouvrir votre jeu d’enregistrements ou avant d’appeler les fonctions membres `AddNew`, `Update` ou `Delete` du Recordset si vous souhaitez modifier la valeur du délai d’expiration de la requête. Le paramètre affecte tous les appels de `Open`, `AddNew`, `Update`et `Delete` suivants à tous les jeux d’enregistrements associés à cet objet `CDatabase`. La modification de la valeur du délai d’expiration de la requête pour un jeu d’enregistrements après l’ouverture ne modifie pas la valeur de l’ensemble d’enregistrements. Par exemple, les opérations de `Move` suivantes n’utilisent pas la nouvelle valeur.

La valeur par défaut du délai d’expiration de la requête est de 15 secondes. Toutes les sources de données ne prennent pas en charge la possibilité de définir une valeur de délai d’attente de requête. Si vous définissez une valeur de délai d’attente de requête de 0, aucun délai d’attente n’est atteint. la communication avec la source de données peut cesser de répondre. Ce comportement peut être utile lors du développement. Si la source de données ne prend pas en charge le délai d’attente, vous bénéficiez d’une sortie de suivi, mais pas d’exception.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)
