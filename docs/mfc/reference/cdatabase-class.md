---
title: Classe CDatabase
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
ms.openlocfilehash: 260a4a38fcee8994d804267709c11279266d393c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376476"
---
# <a name="cdatabase-class"></a>Classe CDatabase

Représente une connexion à une source de données, par l'intermédiaire de laquelle vous pouvez utiliser la source de données.

## <a name="syntax"></a>Syntaxe

```
class CDatabase : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDatabase::CDatabase](#cdatabase)|Construit un objet `CDatabase`. Vous devez initialiser l’objet en appelant `OpenEx` ou `Open`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDatabase::BeginTrans](#begintrans)|Démarre une « transaction » — une `AddNew`série `Edit` `Delete`d’appels réversibles vers les fonctions de classe, `Update` `CRecordset` , et les membres — sur la source de données connectée. La source de données `BeginTrans` doit prendre en charge les transactions pour avoir un effet quelconque.|
|[CDatabase::BindParameters](#bindparameters)|Vous permet de lier `CDatabase::ExecuteSQL`les paramètres avant d’appeler .|
|[CDatabase::Annuler](#cancel)|Annule une opération asynchrone ou un processus à partir d’un deuxième thread.|
|[CDatabase::CanTransact](#cantransact)|Retourne nonzero si la source de données prend en charge les transactions.|
|[CDatabase::CanUpdate](#canupdate)|Retourne nonzero `CDatabase` si l’objet est updatable (non lu uniquement).|
|[CDatabase::Fermer](#close)|Ferme la connexion source de données.|
|[CDatabase::CommitTrans](#committrans)|Termine une transaction `BeginTrans`commencée par . Les commandes de la transaction qui modifient la source de données sont effectuées.|
|[CDatabase::ExecuteSQL](#executesql)|Exécute une déclaration SQL. Aucun enregistrement de données n’est retourné.|
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Identifie les opérations par lesquelles les signets persistent sur les objets de l’enregistrement.|
|[CDatabase::GetConnect](#getconnect)|Retourne la chaîne de connexion ODBC utilisée pour connecter l’objet `CDatabase` à une source de données.|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifie l’effet de l’engagement d’une transaction sur un objet de dossier ouvert.|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifie l’effet du recul d’une transaction sur un objet de dossier ouvert.|
|[CDatabase::GetDatabaseName](#getdatabasename)|Retourne le nom de la base de données actuellement en cours d’utilisation.|
|[CDatabase::IsOpen](#isopen)|Retourne nonzero `CDatabase` si l’objet est actuellement connecté à une source de données.|
|[CDatabase::OnSetOptions](#onsetoptions)|Appelé par le cadre pour définir des options de connexion standard. La implémentation par défaut définit la valeur de temps d’arrêt de requête. Vous pouvez établir ces options `SetQueryTimeout`à l’avance en appelant .|
|[CDatabase::Ouvert](#open)|Établit une connexion à une source de données (par l’intermédiaire d’un pilote ODBC).|
|[CDatabase::OpenEx](#openex)|Établit une connexion à une source de données (par l’intermédiaire d’un pilote ODBC).|
|[CDatabase::Rollback](#rollback)|Renverse les modifications apportées au cours de la transaction en cours. La source de données revient à `BeginTrans` son état précédent, tel que défini à l’appel, inchangé.|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Définit le nombre de secondes après laquelle une tentative de connexion source de données s’évanouira.|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Définit le nombre de secondes après lesquelles les opérations de requête de base de données s’éteil. Affecte tous les `Open` `AddNew`enregistrements `Edit`suivants `Delete` , , , et les appels.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDatabase::m_hdbc](#m_hdbc)|Poignée de connexion Open Database Connectivity (ODBC) à une source de données. Type *HDBC*.|

## <a name="remarks"></a>Notes

Une source de données est un exemple spécifique de données hébergées par un système de gestion de base de données (DBMS). Les exemples incluent Microsoft SQL Server, Microsoft Access, Borland dBASE et xBASE. Vous pouvez avoir `CDatabase` un ou plusieurs objets actifs à la fois dans votre application.

> [!NOTE]
> Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt qu’avec les classes de connectivité à base de données ouvertes (ODBC), utilisez plutôt [la base de données CDaoData.](../../mfc/reference/cdaodatabase-class.md) Pour plus d’informations, voir l’article [Aperçu: Programmation de base de données](../../data/data-access-programming-mfc-atl.md).

Pour `CDatabase`utiliser , `CDatabase` construire un `OpenEx` objet et appeler sa fonction de membre. Cela ouvre une connexion. Lorsque vous `CRecordset` construisez ensuite des objets pour fonctionner sur la source de `CDatabase` données connectée, passez le constructeur de l’enregistrement un pointeur à votre objet. Lorsque vous avez terminé l’utilisation de la connexion, appelez la `Close` fonction du membre et détruisez l’objet. `CDatabase` `Close`ferme tous les enregistrements que vous n’avez pas fermés auparavant.

Pour plus `CDatabase`d’informations sur , voir les articles [Data Source (ODBC)](../../data/odbc/data-source-odbc.md) et [Aperçu: Database Programming](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase::BeginTrans

Appelez cette fonction de membre pour commencer une transaction avec la source de données connectée.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’appel a été réussi et les changements ne sont engagés que manuellement; sinon 0.

### <a name="remarks"></a>Notes

Une transaction se compose d’un `Delete`ou `Update` plusieurs appels vers `CRecordset` le `AddNew`, `Edit`, et les fonctions des membres d’un objet. Avant de commencer `CDatabase` une transaction, l’objet doit déjà `OpenEx` avoir `Open` été connecté à la source de données en appelant sa fonction ou sa fonction de membre. Pour mettre fin à la transaction, appelez [CommitTrans](#committrans) pour accepter toutes les modifications apportées à la source de données (et les effectuer) ou appelez [Rollback](#rollback) pour annuler la totalité de la transaction. Appelez `BeginTrans` après avoir ouvert tous les enregistrements impliqués dans la transaction et le plus près possible des opérations de mise à jour réelles.

> [!CAUTION]
> Selon votre pilote ODBC, l’ouverture `BeginTrans` d’un `Rollback`dossier avant d’appeler peut causer des problèmes lors de l’appel . Vous devriez vérifier le pilote spécifique que vous utilisez. Par exemple, lorsque vous utilisez le pilote Microsoft Access inclus dans le Pack de bureau Microsoft ODBC 3.0, vous devez tenir compte de l’exigence du moteur de base de données Jet que vous ne devriez pas commencer une transaction sur une base de données qui a un curseur ouvert. Dans les classes de base de données MFC, un curseur ouvert signifie un objet ouvert. `CRecordset` Pour plus d’informations, voir [Note technique 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans`verrouiller, s’il y a lieu, les enregistrements de données sur le serveur, en fonction de la concordance demandée et des capacités de la source de données. Pour plus d’informations sur les données de verrouillage, voir l’article [Recordset: Locking Records (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Les transactions définies par l’utilisateur sont expliquées dans l’article [Transaction (ODBC).](../../data/odbc/transaction-odbc.md)

`BeginTrans`établit l’état auquel la séquence des transactions peut être annulée (inversée). Pour établir un nouvel état pour les réductions, `BeginTrans` si vous engagez toute transaction en cours, puis appelez à nouveau.

> [!CAUTION]
> Appeler `BeginTrans` à `CommitTrans` nouveau `Rollback` sans appeler ou est une erreur.

Appelez la fonction membre [CanTransact](#cantransact) pour déterminer si votre pilote prend en charge les transactions pour une base de données donnée. Vous devez également appeler [GetCursorCommitBehavior](#getcursorcommitbehavior) et [GetCursorRollbackBehavior](#getcursorrollbackbehavior) pour déterminer le support pour la préservation des curseurs.

Pour plus d’informations sur les transactions, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Exemple

  Voir l’article [Transaction: Performing a Transaction in a Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase::BindParameters

Remplacer `BindParameters` lorsque vous avez besoin de lier les paramètres avant d’appeler [CDatabase::ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*hstmt*<br/>
La poignée de déclaration ODBC pour laquelle vous souhaitez lier les paramètres.

### <a name="remarks"></a>Notes

Cette approche est utile lorsque vous n’avez pas besoin de l’ensemble de résultat d’une procédure stockée.

Dans votre remplacement, `SQLBindParameters` appelez et les fonctions connexes oDBC pour lier les paramètres. MFC appelle votre remplacement avant `ExecuteSQL`votre appel à . Vous n’avez `SQLPrepare`pas besoin d’appeler ; `ExecuteSQL` appelle `SQLExecDirect` et détruit le *hstmt*, qui n’est utilisé qu’une seule fois.

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabase::Annuler

Appelez cette fonction de membre pour demander à la source de données d’annuler soit une opération asynchrone en cours, soit un processus à partir d’un deuxième thread.

```
void Cancel();
```

### <a name="remarks"></a>Notes

Notez que les classes MFC ODBC n’utilisent plus de traitement asynchrone; pour effectuer une opération asynchrone, vous devez appeler directement la fonction API ODBC [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Pour plus d’informations, voir [Asynchrone Execution](/sql/odbc/reference/develop-app/asynchronous-execution).

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabase::CanTransact

Appelez cette fonction de membre pour déterminer si la base de données autorise les transactions.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les `CDatabase` enregistrements utilisant cet objet permettent des transactions; sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les transactions, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase::CanUpdate

Appelez cette fonction de `CDatabase` membre pour déterminer si l’objet permet des mises à jour.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CDatabase` l’objet permet des mises à jour; autrement 0, indiquant soit que vous avez passé TRUE `CDatabase` dans *bReadOnly* lorsque vous avez ouvert l’objet ou que la source de données elle-même est lu-seulement. La source de données est lue uniquement si un `SQLGetInfo` appel à la fonction API ODBC pour SQL_DATASOURCE_READ_ONLY renvoie "y".

### <a name="remarks"></a>Notes

Tous les conducteurs ne prennent pas en charge les mises à jour.

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase::CDatabase

Construit un objet `CDatabase`.

```
CDatabase();
```

### <a name="remarks"></a>Notes

Après la construction de l’objet, vous devez appeler sa `OpenEx` fonction ou `Open` sa fonction de membre pour établir une connexion à une source de données spécifiée.

Vous trouverez peut-être pratique `CDatabase` d’intégrer l’objet dans votre classe de documents.

### <a name="example"></a>Exemple

Cet exemple illustre `CDatabase` l’utilisation dans une `CDocument`classe dérivée.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabase::Fermer

Appelez cette fonction de membre si vous souhaitez vous déconnecter d’une source de données.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Vous devez fermer tous les `CDatabase` enregistrements associés à l’objet avant d’appeler cette fonction de membre. Parce `Close` que ne `CDatabase` détruit pas l’objet, vous pouvez réutiliser l’objet en ouvrant une nouvelle connexion à la même source de données ou à une source de données différente.

Toutes les `AddNew` `Edit` déclarations en attente ou les relevés des enregistrements utilisant la base de données sont annulés, et toutes les transactions en attente sont annulées. Tous les enregistrements `CDatabase` dépendants de l’objet sont laissés dans un état indéfini.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase::CommitTrans

Appelez cette fonction de membre lors de la réalisation des transactions.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les mises à jour ont été validées avec succès; sinon 0. En `CommitTrans` cas d’échec, l’état de la source de données n’est pas défini. Vous devez vérifier les données pour déterminer son état.

### <a name="remarks"></a>Notes

Une transaction se compose d’une `Edit` `Delete`série `Update` d’appels vers `CRecordset` le `AddNew`, , et les fonctions des membres d’un objet qui a commencé par un appel à la fonction membre [BeginTrans.](#begintrans) `CommitTrans`engage la transaction. Par défaut, les mises à jour sont validées immédiatement; l’appel `BeginTrans` provoque un retard `CommitTrans` de l’engagement des mises à jour jusqu’à ce qu’on l’appelle.

Jusqu’à `CommitTrans` ce que vous appeliez pour mettre fin à une transaction, vous pouvez appeler la fonction membre [Rollback](#rollback) pour annuler la transaction et laisser la source de données dans son état d’origine. Pour commencer une nouvelle `BeginTrans` transaction, appelez à nouveau.

Pour plus d’informations sur les transactions, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Exemple

  Voir l’article [Transaction: Performing a Transaction in a Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase::ExecuteSQL

Appelez cette fonction de membre lorsque vous devez exécuter une commande SQL directement.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Paramètres

*lpszSQL*<br/>
Pointeur vers une corde non terminée contenant une commande SQL valide à exécuter. Vous pouvez passer un [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Créez la commande sous forme de corde non terminée. `ExecuteSQL`ne retourne pas les enregistrements de données. Si vous souhaitez utiliser des enregistrements, utilisez plutôt un objet de recordet.

La plupart de vos commandes pour une source de données sont émises par des objets de nombre, qui prennent en charge les commandes pour la sélection des données, l’insertion de nouveaux enregistrements, la suppression d’enregistrements et l’édition d’enregistrements. Cependant, toutes les fonctionnalités ODBC ne sont pas directement prises en charge par les `ExecuteSQL`classes de base de données, de sorte que vous pouvez parfois avoir besoin de faire un appel SQL direct avec .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence

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
|SQL_BP_CLOSE|Les signets sont `Requery` valables après une opération.|
|SQL_BP_DELETE|Le signet d’une rangée `Delete` est valide après une opération sur cette rangée.|
|SQL_BP_DROP|Les signets sont `Close` valables après une opération.|
|SQL_BP_SCROLL|Les signets sont `Move` valables après toute opération. Permet simplement de déterminer si les signets sont pris en charge sur le recordset, comme cela est retourné par `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Les signets sont valides après qu'une transaction est validée ou restaurée.|
|SQL_BP_UPDATE|Le signet d’une rangée `Update` est valide après une opération sur cette rangée.|
|SQL_BP_OTHER_HSTMT|Les signets associés à un objet recordset sont valides sur un deuxième recordset.|

Pour plus d’informations sur cette valeur de `SQLGetInfo` retour, consultez la fonction API ODBC dans le SDK Windows. Pour plus d’informations sur les signets, voir l’article [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabase::GetConnect

Appelez cette fonction de membre pour récupérer `OpenEx` la `Open` chaîne `CDatabase` de connexion utilisée lors de l’appel ou qui reliait l’objet à une source de données.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Valeur de retour

Un **const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant `OpenEx` la `Open` chaîne de connexion si ou a été appelé; sinon, une ficelle vide.

### <a name="remarks"></a>Notes

Voir [CDatabase::Ouvert](#open) pour une description de la façon dont la chaîne de connexion est créée.

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior

Appelez cette fonction de membre pour déterminer comment une opération [CommitTrans](#committrans) affecte les curseurs sur les objets open recordset.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur indiquant l’effet des transactions sur les objets de registre ouvert. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs de rendement possibles `GetCursorCommitBehavior` et l’effet correspondant sur l’enregistrement ouvert.

|Valeur retournée|Effet sur les objets CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Appelez `CRecordset::Requery` immédiatement après la transaction de validation.|
|SQL_CB_DELETE|Appelez `CRecordset::Close` immédiatement après la transaction de validation.|
|SQL_CB_PRESERVE|Procédez normalement `CRecordset` avec les opérations.|

Pour plus d’informations sur cette valeur de `SQLGetInfo` retour, consultez la fonction API ODBC dans le SDK Windows. Pour plus d’informations sur les transactions, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior

Appelez cette fonction de membre pour déterminer comment une opération [Rollback](#rollback) affecte les curseurs sur les objets open recordset.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur indiquant l’effet des transactions sur les objets de registre ouvert. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs de rendement possibles `GetCursorRollbackBehavior` et l’effet correspondant sur l’enregistrement ouvert.

|Valeur retournée|Effet sur les objets CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Appelez `CRecordset::Requery` immédiatement après le retour de la transaction.|
|SQL_CB_DELETE|Appelez `CRecordset::Close` immédiatement après le retour de la transaction.|
|SQL_CB_PRESERVE|Procédez normalement `CRecordset` avec les opérations.|

Pour plus d’informations sur cette valeur de `SQLGetInfo` retour, consultez la fonction API ODBC dans le SDK Windows. Pour plus d’informations sur les transactions, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase::GetDatabaseName

Appelez cette fonction de membre pour récupérer le nom de la base de données actuellement connectée (à condition que la source de données définisse un objet nommé appelé «base de données»).

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Valeur de retour

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom de la base de données en cas de succès; autrement, un `CString`vide .

### <a name="remarks"></a>Notes

Ce n’est pas la même chose que le `OpenEx` nom `Open` source de données (DSN) spécifié dans le ou l’appel. Ce `GetDatabaseName` qui revient dépend de l’ODBC. En général, une base de données est une collection de tables. Si cette entité a `GetDatabaseName` un nom, la renvoie.

Vous pouvez, par exemple, afficher ce nom dans un titre. Si une erreur se produit lors de la `GetDatabaseName` récupération du `CString`nom de ODBC, renvoie un vide .

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase::IsOpen

Appelez cette fonction de `CDatabase` membre pour déterminer si l’objet est actuellement connecté à une source de données.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CDatabase` l’objet est actuellement connecté; sinon 0.

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabase::m_hdbc

Contient une poignée publique à une connexion de source de données ODBC — une « poignée de connexion ».

### <a name="remarks"></a>Notes

Normalement, vous n’aurez pas besoin d’accéder directement à cette variable de membre. Au lieu de cela, le `OpenEx` cadre `Open`alloue la poignée lorsque vous appelez ou . Le cadre gère la poignée lorsque vous appelez `CDatabase` l’opérateur de **suppression** de l’objet. Notez `Close` que la fonction du membre ne traite pas la poignée.

Dans certaines circonstances, cependant, vous devrez peut-être utiliser la poignée directement. Par exemple, si vous avez besoin d’appeler les fonctions API ODBC directement plutôt que par la classe, `CDatabase`vous pouvez avoir besoin d’une poignée de connexion pour passer comme un paramètre. Voir l’exemple de code ci-dessous.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase::OnSetOptions

Le cadre appelle cette fonction de membre lors `ExecuteSQL` de l’exécution directe d’une déclaration SQL avec la fonction membre.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*hstmt*<br/>
La poignée de déclaration ODBC pour quelles options sont définies.

### <a name="remarks"></a>Notes

`CRecordset::OnSetOptions`appelle également cette fonction de membre.

`OnSetOptions`définit la valeur de temps d’arrêt de connexion. S’il y a `SetQueryTimeout` eu des `OnSetOptions` appels antérieurs à la fonction et à celle des membres, reflète les valeurs actuelles; autrement, il définit les valeurs par défaut.

> [!NOTE]
> Avant MFC 4.2, `OnSetOptions` définissez également le mode de traitement à snychronous ou asynchrone. À partir du MFC 4.2, toutes les opérations sont synchrones. Pour effectuer une opération asynchrone, vous devez faire un appel `SQLSetPos`direct à la fonction API ODBC .

Vous n’avez pas `OnSetOptions` besoin de remplacer pour modifier la valeur du délai d’attente. Au lieu de cela, pour personnaliser `SetQueryTimeout` la valeur d’arrêt de requête, appelez avant de créer un jeu d’enregistrement; `OnSetOptions` utilisera la nouvelle valeur. Les valeurs établies s’appliquent aux opérations ultérieures sur tous les enregistrements ou les appels directs SQL.

Remplacer `OnSetOptions` si vous souhaitez définir des options supplémentaires. Votre remplacement devrait appeler `OnSetOptions` la classe de base avant ou après `SQLSetStmtOption`avoir appelé la fonction API ODBC . Suivez la méthode illustrée dans la `OnSetOptions`mise en œuvre par défaut du cadre .

## <a name="cdatabaseopen"></a><a name="open"></a>CDatabase::Ouvert

Appelez cette fonction de membre `CDatabase` pour initialiser un objet nouvellement construit.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszDSN (LpszDSN)*<br/>
Spécifie un nom de source de données — un nom enregistré auprès de l’ODBC dans le cadre du programme oDBC Administrator. Si une valeur DSN est spécifiée dans *lpszConnect* \<(sous la forme "DSNMD data-source>"), il ne doit pas être spécifié à nouveau dans *lpszDSN*. Dans ce cas, *lpszDSN* devrait être NULL. Sinon, vous pouvez passer NULL si vous souhaitez présenter à l’utilisateur une boîte de dialogue Data Source dans laquelle l’utilisateur peut sélectionner une source de données. Pour plus d’informations, voir Remarques.

*bExclusive*<br/>
Non pris en charge dans cette version de la bibliothèque de classe. Actuellement, une affirmation échoue si ce paramètre est VRAI. La source de données est toujours ouverte comme partagée (pas exclusive).

*bReadOnly*<br/>
VRAI si vous avez l’intention que la connexion soit lue uniquement et pour interdire les mises à jour de la source de données. Tous les documents dépendants héritent de cet attribut. La valeur par défaut est FALSE.

*lpszConnect*<br/>
Spécifie une chaîne de connexion. La chaîne de connexion concatenates informations, y compris éventuellement un nom source de données, un identifiant d’utilisateur valide sur la source de données, une chaîne d’authentification de l’utilisateur (mot de passe, si la source de données en nécessite un), et d’autres informations. La chaîne de connexion entière doit être préfixée par la chaîne "ODBC;" (uppercase ou lowercase). La chaîne " ODBC;" est utilisée pour indiquer que la connexion est à une source de données ODBC; il s’agit d’une compatibilité ascendante lorsque les versions futures de la bibliothèque de classe peuvent prendre en charge des sources de données non-ODBC.

*bUseCursorLib*<br/>
VRAI si vous voulez que la bibliothèque ODBC Cursor DLL soit chargée. La bibliothèque de curseurs masque une certaine fonctionnalité du conducteur sous-jacent ODBC, empêchant efficacement l’utilisation de dynasets (si le conducteur les soutient). Les seuls curseurs pris en charge si la bibliothèque de curseurs est chargée sont des instantanés statiques et des curseurs avant seulement. La valeur par défaut est TRUE. Si vous prévoyez de créer un `CRecordset` objet de la liste d’enregistrement directement à partir de sans en tirer, vous ne devriez pas charger la bibliothèque de curseurs.

### <a name="return-value"></a>Valeur de retour

Nonzero si la connexion est effectuée avec succès; autrement 0 si l’utilisateur choisit Annuler lorsqu’il est présenté une boîte de dialogue demandant plus d’informations de connexion. Dans tous les autres cas, le cadre fait une exception.

### <a name="remarks"></a>Notes

Votre objet de base de données doit être paradé avant de pouvoir l’utiliser pour construire un objet de recordet.

> [!NOTE]
> Appeler la fonction membre [OpenEx](#openex) est le moyen privilégié de se connecter à une source de données et d’initialiser votre objet de base de données.

Si les paramètres `Open` de votre appel ne contiennent pas suffisamment d’informations pour effectuer la connexion, le pilote ODBC ouvre une boîte de dialogue pour obtenir les informations nécessaires de l’utilisateur. Lorsque vous `Open`appelez , votre chaîne de connexion, *lpszConnect*, est stocké en privé dans l’objet `CDatabase` et est disponible en appelant la fonction membre [GetConnect.](#getconnect)

Si vous le souhaitez, vous pouvez ouvrir `Open` votre propre boîte de dialogue avant d’appeler pour obtenir des informations `Open`de l’utilisateur, comme un mot de passe, puis ajouter ces informations à la chaîne de connexion que vous passez à . Ou vous pouvez enregistrer la chaîne de connexion que vous passez afin `Open` que `CDatabase` vous puissiez la réutiliser la prochaine fois que votre application appelle sur un objet.

Vous pouvez également utiliser la chaîne de connexion pour plusieurs `CDatabase` niveaux d’autorisation de connexion (chacun pour un objet différent) ou pour transmettre d’autres informations spécifiques à la source de données. Pour plus d’informations sur les chaînes de connexion, voir le chapitre 5 dans le SDK Windows.

Il est possible pour une tentative de connexion de temps de temps si, par exemple, l’hôte DBMS n’est pas disponible. Si la tentative `Open` de connexion `CDBException`échoue, lance un .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabase::OpenEx

Appelez cette fonction de membre `CDatabase` pour initialiser un objet nouvellement construit.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Paramètres

*lpszConnectString (en)*<br/>
Spécifie une chaîne de connexion ODBC. Cela comprend le nom de source de données ainsi que d’autres informations facultatives, telles qu’un identifiant d’utilisateur et un mot de passe. Par exemple, « DSN-SQLServer_Source ; UID-SA; PWD-abc123" est une chaîne de connexion possible. Notez que si vous passez NULL pour *lpszConnectString*, une boîte de dialogue Data Source incitera l’utilisateur à sélectionner une source de données.

*dwOptions*<br/>
Un bitmask qui spécifie une combinaison des valeurs suivantes. La valeur par défaut est de 0, ce qui signifie que la base de données sera ouverte comme partagé avec l’accès à l’écriture, le DLL de la bibliothèque cursuse ODBC ne sera pas chargé, et la boîte de dialogue de connexion ODBC ne s’affichera que s’il n’y a pas assez d’informations pour effectuer la connexion.

- `CDatabase::openExclusive`Non pris en charge dans cette version de la bibliothèque de classe. Une source de données est toujours ouverte comme partagée (pas exclusive). Actuellement, une affirmation échoue si vous spécifiez cette option.

- `CDatabase::openReadOnly`Ouvrez la source de données en lecture seulement.

- `CDatabase::useCursorLib`Chargez la bibliothèque ODBC Cursor DLL. La bibliothèque de curseurs masque une certaine fonctionnalité du conducteur sous-jacent ODBC, empêchant efficacement l’utilisation de dynasets (si le conducteur les soutient). Les seuls curseurs pris en charge si la bibliothèque de curseurs est chargée sont des instantanés statiques et des curseurs avant seulement. Si vous prévoyez de créer un `CRecordset` objet de la liste d’enregistrement directement à partir de sans en tirer, vous ne devriez pas charger la bibliothèque de curseurs.

- `CDatabase::noOdbcDialog`N’affichez pas la boîte de dialogue de connexion ODBC, peu importe si suffisamment d’informations de connexion sont fournies.

- `CDatabase::forceOdbcDialog`Affichez toujours la boîte de dialogue de connexion ODBC.

### <a name="return-value"></a>Valeur de retour

Nonzero si la connexion est effectuée avec succès; autrement 0 si l’utilisateur choisit Annuler lorsqu’il est présenté une boîte de dialogue demandant plus d’informations de connexion. Dans tous les autres cas, le cadre fait une exception.

### <a name="remarks"></a>Notes

Votre objet de base de données doit être paradé avant de pouvoir l’utiliser pour construire un objet de recordet.

Si le paramètre *lpszConnectString* dans `OpenEx` votre appel ne contient pas suffisamment d’informations pour effectuer la connexion, le pilote ODBC ouvre une boîte de dialogue pour obtenir les informations nécessaires de l’utilisateur, à condition que vous n’ayez pas `CDatabase::noOdbcDialog` défini ou `CDatabase::forceOdbcDialog` dans le *paramètre dwOptions.* Lorsque vous `OpenEx`appelez , votre chaîne de connexion, *lpszConnectString*, est stocké en privé dans l’objet `CDatabase` et est disponible en appelant la fonction membre [GetConnect.](#getconnect)

Si vous le souhaitez, vous pouvez ouvrir `OpenEx` votre propre boîte de dialogue avant d’appeler pour obtenir des informations de `OpenEx`l’utilisateur, comme un mot de passe, puis ajouter ces informations à la chaîne de connexion que vous passez à . Ou vous pouvez enregistrer la chaîne de connexion que vous passez afin `OpenEx` que `CDatabase` vous puissiez la réutiliser la prochaine fois que votre application appelle sur un objet.

Vous pouvez également utiliser la chaîne de connexion pour plusieurs `CDatabase` niveaux d’autorisation de connexion (chacun pour un objet différent) ou pour transmettre d’autres informations spécifiques à la source de données. Pour plus d’informations sur les chaînes de connexion, voir le chapitre 6 dans la *référence du programmeur ODBC*.

Il est possible pour une tentative de connexion de temps de temps si, par exemple, l’hôte DBMS n’est pas disponible. Si la tentative `OpenEx` de connexion `CDBException`échoue, lance un .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase::Rollback

Appelez cette fonction de membre pour inverser les modifications apportées lors d’une transaction.

```
BOOL Rollback();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la transaction a été annulée avec succès; sinon 0. En `Rollback` cas d’échec d’un appel, la source de données et les états de transaction ne sont pas définis. Si `Rollback` vous retournez 0, vous devez vérifier la source de données pour déterminer son état.

### <a name="remarks"></a>Notes

`CRecordset` `AddNew`Tous, `Edit` `Delete`, `Update` et les appels exécutés depuis le dernier [BeginTrans](#begintrans) sont retournés à l’état qui existait au moment de cet appel.

Après un `Rollback`appel à , la transaction `BeginTrans` est terminée, et vous devez appeler à nouveau pour une autre transaction. Le dossier qui était `BeginTrans` en cours avant `Rollback`que vous appeliez redevient le record actuel après .

Après un retour en arrière, le record qui était en cours avant la restauration reste à jour. Pour plus de détails sur l’état de l’ensemble d’enregistrements et la source de données après un retour en arrière, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Exemple

  Voir l’article [Transaction: Performing a Transaction in a Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase::SetLoginTimeout

Appelez cette fonction de `OpenEx` membre `Open` — avant d’appeler ou — pour remplacer le nombre de secondes par défaut autorisés avant qu’une tentative de connexion de source de données ne soit disponible.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Paramètres

*dwSeconds dwSeconds*<br/>
Le nombre de secondes à prévoir avant une tentative de connexion s’évanouit.

### <a name="remarks"></a>Notes

Une tentative de connexion peut s’exclure si, par exemple, le DBMS n’est pas disponible. Appelez `SetLoginTimeout` après avoir construit l’objet uninitialisé, `CDatabase` mais avant d’appeler `OpenEx` ou `Open`.

La valeur par défaut pour les délais d’arrêt de connexion est de 15 secondes. Toutes les sources de données ne prennent pas en charge la possibilité de spécifier une valeur de délai de connexion. Si la source de données ne prend pas en charge le délai d’attente, vous obtenez une sortie de trace, mais pas une exception. Une valeur de 0 signifie «infini».

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase::SetQueryTimeout

Appelez cette fonction de membre pour remplacer le nombre de secondes par défaut pour permettre avant les opérations ultérieures sur le temps d’inséquement de la source de données connectée.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Paramètres

*dwSeconds dwSeconds*<br/>
Le nombre de secondes à prévoir avant qu’une tentative de requête ne s’évanouie.

### <a name="remarks"></a>Notes

Une opération peut s’éteindre en raison de problèmes d’accès au réseau, de temps de traitement excessif des requêtes, et ainsi de suite. Appelez `SetQueryTimeout` avant d’ouvrir votre jeu d’enregistrement `AddNew`ou `Update` `Delete` avant d’appeler le recordet, ou les fonctions des membres si vous souhaitez modifier la valeur de temps d’arrêt de requête. Le paramètre `Open`affecte `AddNew` `Update`tous `Delete` les résultats ultérieurs, `CDatabase` , et les appels à tous les enregistrements associés à cet objet. Changer la valeur d’un délai d’attente de requête pour un enregistrement après l’ouverture ne change pas la valeur pour l’enregistrement. Par exemple, `Move` les opérations ultérieures n’utilisent pas la nouvelle valeur.

La valeur par défaut pour les délais d’attente des requêtes est de 15 secondes. Toutes les sources de données ne prennent pas en charge la possibilité de définir une valeur de délai d’attente de requête. Si vous définissez une valeur d’arrêt de 0, aucun délai d’attente ne se produit; la communication avec la source de données peut cesser de répondre. Ce comportement peut être utile pendant le développement. Si la source de données ne prend pas en charge le délai d’attente, vous obtenez une sortie de trace, mais pas une exception.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
