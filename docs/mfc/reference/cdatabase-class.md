---
title: CDatabase (classe) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], ODBC
- MFC [C++], ODBC
- ODBC [C++], CDatabase class
- ODBC database class
- database connections [C++], CDatabase class
- CDatabase class
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a14025d712f09bef2b6b749d46cac1b1371fd4e3
ms.lasthandoff: 02/24/2017

---
# <a name="cdatabase-class"></a>CDatabase (classe)
Représente une connexion à une source de données, par l'intermédiaire de laquelle vous pouvez utiliser la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDatabase : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDatabase::CDatabase](#cdatabase)|Construit un objet `CDatabase`. Vous devez initialiser l’objet en appelant `OpenEx` ou **ouvrir**.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDatabase::BeginTrans](#begintrans)|Démarre une transaction « » â » une série d’appels réversibles pour le `AddNew`, **modifier**, **supprimer**, et **mise à jour** fonctions membres de classe `CRecordset` â » sur la source de données connectée. La source de données doit prendre en charge des transactions pour **BeginTrans** en vigueur.|  
|[CDatabase::BindParameters](#bindparameters)|Permet de lier des paramètres avant d’appeler `CDatabase::ExecuteSQL`.|  
|[CDatabase::Cancel](#cancel)|Annule une opération asynchrone ou un processus à partir d’un deuxième thread.|  
|[CDatabase::CanTransact](#cantransact)|Retourne zéro si la source de données prend en charge les transactions.|  
|[CDatabase::CanUpdate](#canupdate)|Retourne zéro si le `CDatabase` objet est modifiable (pas en lecture seule).|  
|[CDatabase::Close](#close)|Ferme la connexion de source de données.|  
|[CDatabase::CommitTrans](#committrans)|Termine une transaction commencée par **BeginTrans**. Commandes de la transaction qui modifie la source de données sont effectuées.|  
|[CDatabase::ExecuteSQL](#executesql)|Exécute une instruction SQL. Aucun enregistrement de données n’est retournés.|  
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Identifie les opérations par le biais duquel les signets persistent sur les objets de jeu d’enregistrements.|  
|[CDatabase::GetConnect](#getconnect)|Retourne la chaîne de connexion ODBC utilisée pour connecter le `CDatabase` objet à une source de données.|  
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifie l’effet de la validation d’une transaction sur un objet recordset ouvert.|  
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifie l’effet de la restauration d’une transaction sur un objet recordset ouvert.|  
|[CDatabase::GetDatabaseName](#getdatabasename)|Retourne le nom de la base de données actuellement en cours d’utilisation.|  
|[CDatabase::IsOpen](#isopen)|Retourne zéro si le `CDatabase` objet est actuellement connecté à une source de données.|  
|[CDatabase::OnSetOptions](#onsetoptions)|Appelé par l’infrastructure pour définir les options de connexion standard. L’implémentation par défaut définit la valeur du délai de requête. Vous pouvez définir ces options à l’avance en appelant `SetQueryTimeout`.|  
|[CDatabase::Open](#open)|Établit une connexion à une source de données (via un pilote ODBC).|  
|[CDatabase::OpenEx](#openex)|Établit une connexion à une source de données (via un pilote ODBC).|  
|[CDatabase::Rollback](#rollback)|Annule les modifications apportées pendant la transaction en cours. La source de données retourne à son état précédent, comme défini dans le **BeginTrans** appel, sans modification.|  
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Définit le nombre de secondes après lequel une tentative de connexion de source de données expire.|  
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Définit le nombre de secondes après la base de données des opérations de requête expire. Affecte le jeu d’enregistrements de toutes les **Open**, `AddNew`, **modifier**, et **supprimer** appels.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDatabase::m_hdbc](#m_hdbc)|Open Database Connectivity (ODBC) handle de connexion pour une source de données. Type **pas**.|  
  
## <a name="remarks"></a>Remarques  
 Une source de données est une instance spécifique de données hébergées par un système de gestion de base de données (SGBD). Exemples Microsoft SQL Server, Microsoft Access, Borland dBASE et xBASE. Vous pouvez avoir une ou plusieurs `CDatabase` objets actifs en même temps dans votre application.  
  
> [!NOTE]
>  Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt que les classes Open Database Connectivity (ODBC), utilisez la classe [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de base de données](../../data/data-access-programming-mfc-atl.md).  
  
 Pour utiliser `CDatabase`, construire un `CDatabase` objet et appeler ses `OpenEx` fonction membre. Cela ouvre une connexion. Lorsque vous construisez puis `CRecordset` objets pour l’exploitation de la source de données connectée, passez le constructeur de jeu d’enregistrements un pointeur vers votre `CDatabase` objet. Lorsque vous avez terminé à l’aide de la connexion, appelez le **fermer** membre de fonction et de détruire le `CDatabase` objet. **Fermer** ferme les jeux d’enregistrements que vous n’avez pas fermé précédemment.  
  
 Pour plus d’informations sur `CDatabase`, consultez les articles [Source de données (ODBC)](../../data/odbc/data-source-odbc.md) et [vue d’ensemble : programmation de base de données](../../data/data-access-programming-mfc-atl.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdb.h  
  
##  <a name="begintrans"></a>CDatabase::BeginTrans  
 Appelez cette fonction membre pour commencer une transaction avec la source de données connectée.  
  
```  
BOOL BeginTrans();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’appel a réussi et les modifications sont validées uniquement manuellement. sinon 0.  
  
### <a name="remarks"></a>Notes  
 Une transaction se compose d’un ou plusieurs appels à la `AddNew`, **modifier**, **supprimer**, et **mise à jour** les fonctions membres d’un `CRecordset` objet. Avant de commencer une transaction, le `CDatabase` objet doit déjà avoir été connecté à la source de données en appelant son `OpenEx` ou **Open** fonction membre. Pour terminer la transaction, appelez [CommitTrans](#committrans) pour accepter toutes les modifications apportées à la source de données (et les exécuter) ou appeler [restauration](#rollback) pour abandonner l’intégralité de la transaction. Appelez **BeginTrans** après vous ouvrez les jeux d’enregistrements impliqués dans la transaction et proche de la valeur réelle de mise à jour les opérations que possible.  
  
> [!CAUTION]
>  En fonction de votre pilote ODBC, ouvrir un objet recordset avant d’appeler **BeginTrans** peut provoquer des problèmes lors de l’appel **restauration**. Vous devez vérifier le pilote spécifique que vous utilisez. Par exemple, lorsque vous utilisez le pilote Microsoft Access inclus dans Microsoft ODBC Desktop Driver Pack 3.0, vous devez tenir compte pour la spécification du moteur de base de données Jet que vous ne devez pas commencer une transaction sur une base de données qui a un curseur ouvert. Dans les classes de base de données MFC, un curseur ouvert signifie ouvert `CRecordset` objet. Pour plus d’informations, consultez [Technical Note 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).  
  
 **BeginTrans** peuvent également verrouiller des enregistrements de données sur le serveur, en fonction de l’accès concurrentiel demandé et les fonctionnalités de la source de données. Pour plus d’informations sur le verrouillage des données, consultez l’article [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
 Transactions définies par l’utilisateur sont décrites dans l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 **BeginTrans** établit l’état auquel la séquence des transactions peut être annulée (inversé). Pour établir un nouvel état pour les restaurations, valider les transactions en cours, puis appelez **BeginTrans** à nouveau.  
  
> [!CAUTION]
>  Appel de **BeginTrans** sans appeler **CommitTrans** ou **restauration** est une erreur.  
  
 Appelez le [CanTransact](#cantransact) fonction membre pour déterminer si votre pilote prend en charge les transactions pour une base de données. Vous devez également appeler [GetCursorCommitBehavior](#getcursorcommitbehavior) et [GetCursorRollbackBehavior](#getcursorrollbackbehavior) pour déterminer la prise en charge pour la conservation du curseur.  
  
 Pour plus d’informations sur les transactions, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’article [Transaction : exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="bindparameters"></a>CDatabase::BindParameters  
 Substituer `BindParameters` lorsque vous devez lier les paramètres avant d’appeler [CDatabase::ExecuteSQL](#executesql).  
  
```  
virtual void BindParameters(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Paramètres  
 `hstmt`  
 Le descripteur d’instruction ODBC pour laquelle vous souhaitez lier des paramètres.  
  
### <a name="remarks"></a>Remarques  
 Cette approche est utile lorsque vous n’avez pas besoin du résultat à partir d’une procédure stockée.  
  
 Dans votre substitution, appelez **SQLBindParameters** et des fonctions ODBC pour lier les paramètres associées. MFC appelle votre remplacement avant votre appel à `ExecuteSQL`. Vous n’avez pas besoin d’appeler **SQLPrepare**; `ExecuteSQL` appelle **SQLExecDirect** et détruit le **hstmt**, qui est utilisé une seule fois.  
  
##  <a name="cancel"></a>CDatabase::Cancel  
 Appelez cette fonction membre pour demander que la source de données annule une opération asynchrone en cours ou un processus à partir d’un deuxième thread.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Remarques  
 Notez que les classes ODBC MFC ne plus utilisent le traitement asynchrone ; Pour effectuer une opération asynchrone, vous devez appeler directement la fonction API ODBC [SQLSetConnectOption](https://msdn.microsoft.com/library/ms713564.aspx). Pour plus d’informations, consultez [l’exécution asynchrone](https://msdn.microsoft.com/library/ms713563.aspx) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="cantransact"></a>CDatabase::CanTransact  
 Appelez cette fonction membre pour déterminer si la base de données autorise les transactions.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les jeux d’enregistrements à l’aide de ce `CDatabase` objet autorise les transactions ; sinon, 0.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations sur les transactions, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>CDatabase::CanUpdate  
 Appelez cette fonction membre pour déterminer si le `CDatabase` objet autorise les mises à jour.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le `CDatabase` objet autorise les mises à jour ; sinon, 0, qui indique soit que vous avez passé **TRUE** dans `bReadOnly` lorsque vous avez ouvert le `CDatabase` objet ou que la source de données lui-même est en lecture seule. La source de données est en lecture seule si un appel à la fonction API ODBC **SQLGetInfo** de **SQL_DATASOURCE_READ_ONLY** retourne « y ».  
  
### <a name="remarks"></a>Remarques  
 Pas tous les pilotes prennent en charge les mises à jour.  
  
##  <a name="cdatabase"></a>CDatabase::CDatabase  
 Construit un objet `CDatabase`.  
  
```  
CDatabase();
```  
  
### <a name="remarks"></a>Notes  
 Après la construction de l’objet, vous devez appeler sa `OpenEx` ou **Open** fonction membre pour établir une connexion à une source de données spécifiée.  
  
 Vous pouvez trouver pratique d’intégrer la `CDatabase` objet dans votre classe de document.  
  
### <a name="example"></a>Exemple  
 Cet exemple illustre l’utilisation de `CDatabase` dans un `CDocument`-classe dérivée.  
  
 [!code-cpp[NVC_MFCDatabase&#9;](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]  
  
 [!code-cpp[NVC_MFCDatabase&#10;](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]  
  
##  <a name="close"></a>CDatabase::Close  
 Appelez cette fonction membre si vous souhaitez vous déconnecter d’une source de données.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Remarques  
 Vous devez fermer tous les recordsets associés à le `CDatabase` avant d’appeler cette fonction membre de l’objet. Étant donné que **fermer** ne détruit pas le `CDatabase` de l’objet, vous pouvez réutiliser l’objet en ouvrant une nouvelle connexion à la même source de données ou une autre source de données.  
  
 Tout en attente `AddNew` ou **modifier** les instructions de jeux d’enregistrements à l’aide de la base de données, et toutes les transactions en attente sont annulées. Les jeux d’enregistrements dépend de la `CDatabase` objet sont laissés dans un état non défini.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase&#12;](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]  
  
##  <a name="committrans"></a>CDatabase::CommitTrans  
 Appelez cette fonction membre à la fin des transactions.  
  
```  
BOOL CommitTrans();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les mises à jour ont été correctement validées ; sinon 0. Si **CommitTrans** échoue, l’état de la source de données n’est pas défini. Vous devez vérifier les données pour déterminer son état.  
  
### <a name="remarks"></a>Remarques  
 Une transaction est composée d’une série d’appels à la `AddNew`, **modifier**, **supprimer**, et **mise à jour** les fonctions membres d’un `CRecordset` objet commence par un appel à la [BeginTrans](#begintrans) fonction membre. **CommitTrans** valide la transaction. Par défaut, les mises à jour sont validées immédiatement. appel de **BeginTrans** provoque l’engagement des mises à jour être différée jusqu'à ce que **CommitTrans** est appelée.  
  
 Jusqu'à ce que vous appeliez **CommitTrans** pour mettre fin à une transaction, vous pouvez appeler la [restauration](#rollback) fonction membre pour abandonner la transaction et conserver la source de données dans son état d’origine. Pour commencer une nouvelle transaction, appelez **BeginTrans** à nouveau.  
  
 Pour plus d’informations sur les transactions, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’article [Transaction : exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="executesql"></a>CDatabase::ExecuteSQL  
 Appelez cette fonction membre lorsque vous avez besoin exécuter une commande SQL directement.  
  
```  
void ExecuteSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszSQL`  
 Pointeur vers une chaîne terminée par le caractère null qui contient une commande SQL valide à exécuter. Vous pouvez passer un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Remarques  
 Créer la commande sous forme de chaîne se terminant par null. `ExecuteSQL`ne retourne pas d’enregistrements de données. Si vous souhaitez utiliser sur les enregistrements, utilisez plutôt un objet recordset.  
  
 La plupart de vos commandes pour une source de données est émise via des objets de jeu d’enregistrements, qui prennent en charge des commandes pour sélectionner des données, insérer de nouveaux enregistrements, supprimer des enregistrements et modification d’enregistrements. Toutefois, certaines fonctionnalités ODBC sont directement pris en charge par les classes de base de données, vous devrez parfois effectuer un appel SQL direct avec `ExecuteSQL`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase&#13;](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]  
  
##  <a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence  
 Appelez cette fonction membre pour déterminer la persistance des signets sur un objet recordset après certaines opérations.  
  
```  
DWORD GetBookmarkPersistence() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un masque de bits qui identifie les opérations par lesquelles les signets persistent sur un objet recordset. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Remarques  
 Par exemple, si vous appelez `CRecordset::GetBookmark`, puis `CRecordset::Requery`, le signet obtenu à partir de `GetBookmark` risque de ne plus être valide. Vous devez appeler `GetBookmarkPersistence` avant d'appeler `CRecordset::SetBookmark`.  
  
 Le tableau suivant liste les valeurs de masque de bits qui peuvent être combinées pour la valeur de retour de `GetBookmarkPersistence`.  
  
|Valeur du masque de bits|Persistance des signets|  
|-------------------|--------------------------|  
|`SQL_BP_CLOSE`|Les signets sont valides après une **Requery** opération.|  
|`SQL_BP_DELETE`|Le signet d’une ligne est valide après un **supprimer** opération sur cette ligne.|  
|`SQL_BP_DROP`|Les signets sont valides après une **fermer** opération.|  
|`SQL_BP_SCROLL`|Les signets sont valides après une **déplacer** opération. Permet simplement de déterminer si les signets sont pris en charge sur le recordset, comme cela est retourné par `CRecordset::CanBookmark`.|  
|`SQL_BP_TRANSACTION`|Les signets sont valides après qu’une transaction est validée ou restaurée.|  
|`SQL_BP_UPDATE`|Le signet d’une ligne est valide après un **mise à jour** opération sur cette ligne.|  
|`SQL_BP_OTHER_HSTMT`|Les signets associés à un objet recordset sont valides sur un deuxième recordset.|  
  
 Pour plus d’informations sur cette valeur de retour, voir la fonction d’API ODBC **SQLGetInfo** dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Pour plus d’informations sur les signets, consultez l’article [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="getconnect"></a>CDatabase::GetConnect  
 Appelez cette fonction membre pour extraire la chaîne de connexion utilisée lors de l’appel à `OpenEx` ou `Open` connecté le `CDatabase` objet à une source de données.  
  
```  
const CString GetConnect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A `const` [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant la chaîne de connexion si `OpenEx` ou `Open` a été appelé ; sinon, une chaîne vide.  
  
### <a name="remarks"></a>Remarques  
 Consultez la page [CDatabase::Open](#open) pour obtenir une description du mode de création de la chaîne de connexion.  
  
##  <a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior  
 Appelez cette fonction membre pour déterminer comment un [CommitTrans](#committrans) opération affecte les curseurs sur les objets recordset ouverts.  
  
```  
int GetCursorCommitBehavior() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur indiquant l’effet des transactions sur les objets recordset ouverts. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Remarques  
 Le tableau suivant répertorie les valeurs de retournés possibles pour `GetCursorCommitBehavior` et ses effets sur le jeu d’enregistrements ouvert.  
  
|Valeur de retour|Effet sur CRecordset (objets)|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|Appelez `CRecordset::Requery` immédiatement après la validation de transaction.|  
|`SQL_CB_DELETE`|Appelez `CRecordset::Close` immédiatement après la validation de transaction.|  
|`SQL_CB_PRESERVE`|Poursuivez normalement `CRecordset` operations.|  
  
 Pour plus d’informations sur cette valeur de retour, voir la fonction d’API ODBC **SQLGetInfo** dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Pour plus d’informations sur les transactions, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior  
 Appelez cette fonction membre pour déterminer comment un [restauration](#rollback) opération affecte les curseurs sur les objets recordset ouverts.  
  
```  
int GetCursorRollbackBehavior() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur indiquant l’effet des transactions sur les objets recordset ouverts. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Remarques  
 Le tableau suivant répertorie les valeurs de retournés possibles pour `GetCursorRollbackBehavior` et ses effets sur le jeu d’enregistrements ouvert.  
  
|Valeur de retour|Effet sur CRecordset (objets)|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|Appelez `CRecordset::Requery` immédiatement après l’annulation de la transaction.|  
|`SQL_CB_DELETE`|Appelez `CRecordset::Close` immédiatement après l’annulation de la transaction.|  
|`SQL_CB_PRESERVE`|Poursuivez normalement `CRecordset` operations.|  
  
 Pour plus d’informations sur cette valeur de retour, voir la fonction d’API ODBC **SQLGetInfo** dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Pour plus d’informations sur les transactions, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="getdatabasename"></a>CDatabase::GetDatabaseName  
 Appelez cette fonction membre pour récupérer le nom de la base de données actuellement connectée (à condition que la source de données définit un objet nommé « database »).  
  
```  
CString GetDatabaseName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le nom de la base de données de cas de réussite ; sinon, vide `CString`.  
  
### <a name="remarks"></a>Remarques  
 Cela n’est pas le même que le nom de source de données (DSN) spécifié dans le `OpenEx` ou **Open** appeler. Ce que `GetDatabaseName` retourne dépend de ODBC. En règle générale, une base de données est une collection de tables. Si cette entité a un nom, `GetDatabaseName` renvoie.  
  
 Peut, par exemple, vouloir afficher ce nom dans un titre. Si une erreur se produit lors de la récupération du nom à partir d’ODBC, `GetDatabaseName` retourne un vide **Cstring**.  
  
##  <a name="isopen"></a>CDatabase::IsOpen  
 Appelez cette fonction membre pour déterminer si le `CDatabase` objet est actuellement connecté à une source de données.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le `CDatabase` objet est actuellement connecté ; sinon, 0.  
  
##  <a name="m_hdbc"></a>CDatabase::m_hdbc  
 Contient un handle à une connexion de source de données ODBC public â » « Gestionnaire de connexion ».  
  
### <a name="remarks"></a>Remarques  
 Normalement, vous n’aurez aucun nécessaire d’accéder directement à cette variable membre. À la place, le framework alloue le handle lorsque vous appelez `OpenEx` ou **ouvrir**. Le framework libère le handle lorsque vous appelez le **supprimer** opérateur sur le `CDatabase` objet. Notez que la **fermer** fonction membre ne pas libérer le handle.  
  
 Toutefois, dans certaines circonstances, vous devrez peut-être utiliser le handle directement. Par exemple, si vous avez besoin d’appeler les fonctions API ODBC directement, plutôt que via la classe `CDatabase`, il vous faudra un handle de connexion pour transmettre en tant que paramètre. Consultez l’exemple de code ci-dessous.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase&#15;](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]  
  
##  <a name="onsetoptions"></a>CDatabase::OnSetOptions  
 L’infrastructure appelle cette fonction membre lorsque vous exécutez directement une instruction SQL avec la `ExecuteSQL` fonction membre.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Paramètres  
 `hstmt`  
 Le descripteur d’instruction ODBC pour laquelle des options sont définies.  
  
### <a name="remarks"></a>Remarques  
 `CRecordset::OnSetOptions`appelle également cette fonction membre.  
  
 `OnSetOptions`définit la valeur de délai d’expiration de connexion. Si des modifications ont été les appels précédents à la `SetQueryTimeout` et une fonction de membre `OnSetOptions` reflète les valeurs actuelles ; sinon, il définit les valeurs par défaut.  
  
> [!NOTE]
>  Avant MFC 4.2, `OnSetOptions` également définir le mode de traitement soit snychronous ou asynchrone. Depuis la version 4.2 de MFC, toutes les opérations sont synchrones. Pour effectuer une opération asynchrone, vous devez vous un appel direct à la fonction API ODBC **SQLSetPos**.  
  
 Vous n’avez pas besoin de substituer `OnSetOptions` pour modifier la valeur de délai d’attente. En revanche, pour personnaliser la valeur du délai de requête, appelez `SetQueryTimeout` avant de créer un jeu d’enregistrements ; `OnSetOptions` utilisent la nouvelle valeur. Les valeurs définies s’appliquent aux opérations suivantes sur tous les jeux d’enregistrements ou des appels SQL directs.  
  
 Substituer `OnSetOptions` si vous souhaitez définir des options supplémentaires. La substitution doit appeler la classe de base `OnSetOptions` avant ou après l’appel de la fonction API ODBC **SQLSetStmtOption**. Suivez la méthode illustrée dans l’implémentation par défaut de `OnSetOptions`.  
  
##  <a name="open"></a>CDatabase::Open  
 Appelez cette fonction membre pour initialiser un nouvellement construit `CDatabase` objet.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszDSN,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T("ODBC;"),  
    BOOL bUseCursorLib = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszDSN`  
 Spécifie le nom de source de données â « un nom enregistré avec ODBC via le programme Administrateur ODBC. Si une valeur de la source de données est spécifiée dans `lpszConnect` (sous la forme « DSN =\<source de données > »), il ne doit pas être spécifié dans `lpszDSN`. Dans ce cas, `lpszDSN` doit être **NULL**. Sinon, vous pouvez transmettre **NULL** si vous souhaitez présenter à l’utilisateur avec une boîte de dialogue Source de données dans laquelle l’utilisateur peut sélectionner une source de données. Pour plus d’informations, consultez la section Notes.  
  
 `bExclusive`  
 Non pris en charge dans cette version de la bibliothèque de classes. Actuellement, une assertion échoue si ce paramètre est **TRUE**. La source de données est toujours ouvert en tant que partagés (non exclusif).  
  
 `bReadOnly`  
 **TRUE** si vous envisagez de la connexion en lecture seule et n’autorisent pas les mises à jour de la source de données. Tous les jeux d’enregistrements dépendants hérite de cet attribut. La valeur par défaut est **FALSE**.  
  
 `lpszConnect`  
 Spécifie une chaîne de connexion. La chaîne de connexion concatène plus d’informations, notamment un nom de source de données, un nom d’utilisateur valid sur la source de données, une chaîne de l’authentification de l’utilisateur (mot de passe, si la source de données requiert un) et d’autres informations. La chaîne de connexion entière doit être précédée de la chaîne « ODBC » ; (majuscules ou minuscules). « ODBC » ; chaîne est utilisée pour indiquer que la connexion à une source de données ODBC ; Il s’agit pour la compatibilité descendante lorsque les versions ultérieures de la bibliothèque de classes peuvent prendre en charge les sources de données non-ODBC.  
  
 `bUseCursorLib`  
 **TRUE** si vous souhaitez que la DLL de bibliothèque de curseur ODBC doit être chargé. La bibliothèque de curseurs masque certaines fonctionnalités du pilote ODBC sous-jacent, empêchant ainsi l’utilisation des feuilles de réponse dynamiques (si le pilote prend en charge les). Les curseurs uniquement pris en charge si le chargement de la bibliothèque de curseurs sont des instantanés statiques et les curseurs avant uniquement. La valeur par défaut est **TRUE**. Si vous envisagez de créer un objet recordset directement à partir de `CRecordset` sans dériver à partir de celui-ci, vous ne devez pas charger la bibliothèque de curseurs.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la connexion est établie avec succès ; Sinon, 0 si l’utilisateur choisit Annuler affiche une boîte de dialogue demandant des informations de connexion plus. Dans tous les autres cas, le framework lève une exception.  
  
### <a name="remarks"></a>Notes  
 Votre objet de base de données doit être initialisée avant que vous pouvez l’utiliser pour construire un objet recordset.  
  
> [!NOTE]
>  Appel de la [OpenEx](#openex) la fonction membre est la meilleure façon de se connecter à une source de données et d’initialiser l’objet de base de données.  
  
 Si les paramètres de votre **Open** appel ne contiennent pas suffisamment d’informations pour établir la connexion, le pilote ODBC ouvre une boîte de dialogue pour obtenir les informations nécessaires auprès de l’utilisateur. Lorsque vous appelez **Open**, votre chaîne de connexion, `lpszConnect`, est stocké en privé dans le `CDatabase` de l’objet et est disponible en appelant le [GetConnect](#getconnect) fonction membre.  
  
 Si vous le souhaitez, vous pouvez ouvrir votre propre boîte de dialogue avant d’appeler **ouvrir** pour obtenir des informations à partir de l’utilisateur, comme un mot de passe, puis ajouter ces informations à la chaîne de connexion que vous passez à **ouvrir**. Vous pouvez également enregistrer la chaîne de connexion que vous passez afin de pouvoir les réutiliser la prochaine fois que votre application appelle **Open** sur une `CDatabase` objet.  
  
 Vous pouvez également utiliser la chaîne de connexion pour plusieurs niveaux d’autorisation de connexion (chacun correspondant à un autre `CDatabase` objet) ou avec d’autres informations spécifiques à la source de données. Pour plus d’informations sur les chaînes de connexion, consultez le chapitre 5 dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Il est possible qu’une tentative de connexion à expirer si, par exemple, l’hôte de SGBD n’est pas disponible. Si la tentative de connexion échoue, **Open** lève une `CDBException`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase&#14;](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]  
  
##  <a name="openex"></a>CDatabase::OpenEx  
 Appelez cette fonction membre pour initialiser un nouvellement construit `CDatabase` objet.  
  
```  
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,  
    DWORD dwOptions = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszConnectString`  
 Spécifie une chaîne de connexion ODBC. Cela inclut le nom de source de données ainsi que d’autres informations facultatives, telles que l’ID utilisateur et le mot de passe. Par exemple, « DSN = SQLServer_Source ; UID = SA ; PWD = abc123 » est une chaîne de connexion possibles. Notez que si vous transmettez **NULL** pour `lpszConnectString`, une boîte de dialogue Source de données invitera l’utilisateur à sélectionner une source de données.  
  
 `dwOptions`  
 Masque de bits qui spécifie une combinaison des valeurs suivantes. La valeur par défaut est 0, ce qui signifie que la base de données s’ouvre en tant que partagé avec accès en écriture, la DLL de bibliothèque de curseurs ODBC ne sera pas chargée, et la boîte de dialogue de connexion ODBC affichera uniquement s’il n’est pas suffisamment d’informations pour établir la connexion.  
  
- **CDatabase::openExclusive** non pris en charge dans cette version de la bibliothèque de classes. Une source de données est toujours ouvert en tant que partagés (non exclusif). Actuellement, une assertion échoue si vous spécifiez cette option.  
  
- **CDatabase::openReadOnly** ouvrir la source de données en lecture seule.  
  
- **CDatabase::useCursorLib** charger la bibliothèque de curseurs ODBC DLL. La bibliothèque de curseurs masque certaines fonctionnalités du pilote ODBC sous-jacent, empêchant ainsi l’utilisation des feuilles de réponse dynamiques (si le pilote prend en charge les). Les curseurs uniquement pris en charge si le chargement de la bibliothèque de curseurs sont des instantanés statiques et les curseurs avant uniquement. Si vous envisagez de créer un objet recordset directement à partir de `CRecordset` sans dériver à partir de celui-ci, vous ne devez pas charger la bibliothèque de curseurs.  
  
- **CDatabase::noOdbcDialog** ne pas afficher la boîte de dialogue de connexion ODBC, indépendamment de si les informations requises sont fournies.  
  
- **CDatabase::forceOdbcDialog** toujours afficher la boîte de dialogue de connexion ODBC.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la connexion est établie avec succès ; Sinon, 0 si l’utilisateur choisit Annuler affiche une boîte de dialogue demandant des informations de connexion plus. Dans tous les autres cas, le framework lève une exception.  
  
### <a name="remarks"></a>Remarques  
 Votre objet de base de données doit être initialisée avant que vous pouvez l’utiliser pour construire un objet recordset.  
  
 Si le `lpszConnectString` paramètre dans votre `OpenEx` appel ne contient-elle pas suffisamment d’informations pour établir la connexion, le pilote ODBC ouvre une boîte de dialogue pour obtenir les informations nécessaires à partir de l’utilisateur, fournie vous n’avez pas défini **CDatabase::noOdbcDialog** ou **CDatabase::forceOdbcDialog** dans le `dwOptions` paramètre. Lorsque vous appelez `OpenEx`, votre chaîne de connexion, `lpszConnectString`, est stocké en privé dans le `CDatabase` de l’objet et est disponible en appelant le [GetConnect](#getconnect) fonction membre.  
  
 Si vous le souhaitez, vous pouvez ouvrir votre propre boîte de dialogue avant d’appeler `OpenEx` pour obtenir des informations à partir de l’utilisateur, comme un mot de passe, puis ajoutez ces informations à la chaîne de connexion que vous passez à `OpenEx`. Vous pouvez également enregistrer la chaîne de connexion que vous passez afin de pouvoir les réutiliser la prochaine fois que votre application appelle `OpenEx` sur une `CDatabase` objet.  
  
 Vous pouvez également utiliser la chaîne de connexion pour plusieurs niveaux d’autorisation de connexion (chacun correspondant à un autre `CDatabase` objet) ou avec d’autres informations spécifiques à la source de données. Pour plus d’informations sur les chaînes de connexion, reportez-vous au chapitre 6 dans le *de référence du programmeur ODBC*.  
  
 Il est possible qu’une tentative de connexion à expirer si, par exemple, l’hôte de SGBD n’est pas disponible. Si la tentative de connexion échoue, `OpenEx` lève une `CDBException`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase&#11;](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]  
  
##  <a name="rollback"></a>CDatabase::Rollback  
 Appelez cette fonction membre pour annuler les modifications effectuées pendant une transaction.  
  
```  
BOOL Rollback();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la transaction a été annulée avec succès ; sinon 0. Si un **restauration** appel échoue, la source de données et la transaction États ne sont pas définis. Si **restauration** renvoie la valeur 0, vous devez vérifier la source de données pour déterminer son état.  
  
### <a name="remarks"></a>Remarques  
 Tous les `CRecordset``AddNew`, **modifier**, **supprimer**, et **mise à jour** appels exécutés depuis la dernière [BeginTrans](#begintrans) sont restaurées à l’état qui existait au moment de l’appel.  
  
 Après un appel à **restauration**, la transaction est terminée, et vous devez appeler **BeginTrans** pour une autre transaction. L’enregistrement qui était actif avant l’appel de **BeginTrans** devient à nouveau l’enregistrement actif après **restauration**.  
  
 Après une restauration, l’enregistrement en cours avant la restauration reste actif. Pour plus d’informations sur l’état de l’objet recordset et la source de données après une restauration, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’article [Transaction : exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="setlogintimeout"></a>CDatabase::SetLoginTimeout  
 Appeler ce membre fonction â €» avant d’appeler `OpenEx` ou **Open** â » pour remplacer le nombre de secondes avant une tentatives données connexion à la source arrive à expiration.  
  
```  
void SetLoginTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwSeconds`  
 Le nombre de secondes avant une tentative de connexion expire.  
  
### <a name="remarks"></a>Remarques  
 Une tentative de connexion peut expirer si, par exemple, le SGBD n’est pas disponible. Appelez **SetLoginTimeout** après avoir construit le non initialisé `CDatabase` l’objet mais avant d’appeler `OpenEx` ou **ouvrir**.  
  
 La valeur par défaut pour les délais d’attente de connexion est de 15 secondes. Toutes les données sources ne prennent en charge la possibilité de spécifier une valeur de délai d’attente de connexion. Si la source de données ne prend pas en charge le délai d’attente, vous obtenez la sortie de trace, mais pas une exception. La valeur 0 signifie « illimitée ».  
  
##  <a name="setquerytimeout"></a>CDatabase::SetQueryTimeout  
 Appelez cette fonction membre pour remplacer le nombre de secondes avant les opérations suivantes sur le délai de source de données connectée.  
  
```  
void SetQueryTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwSeconds`  
 Le nombre de secondes avant une tentative de requête arrive à expiration.  
  
### <a name="remarks"></a>Remarques  
 Une opération peut expirer en raison de problèmes d’accès réseau, le temps de traitement de requête excessive et ainsi de suite. Appelez `SetQueryTimeout` avant d’ouvrir le jeu d’enregistrements ou avant l’appel du jeu d’enregistrements `AddNew`, **mise à jour** ou **supprimer** fonctions membres si vous souhaitez modifier la valeur du délai de requête. Le paramètre affecte toutes les **Open**, `AddNew`, **mise à jour**, et **supprimer** les appels à des jeux d’enregistrements associé à ce `CDatabase` objet. Modification de la valeur du délai de requête pour un jeu d’enregistrements après ouverture ne modifie pas la valeur de l’objet recordset. Par exemple, ultérieur **déplacer** opérations n’utilisent pas la nouvelle valeur.  
  
 La valeur par défaut pour les délais d’expiration est de 15 secondes. Toutes les données sources ne prennent en charge la possibilité de définir une valeur de délai d’attente de requête. Si vous définissez une valeur de délai d’expiration de requête de 0, aucun délai d’expiration se produit ; la communication avec la source de données peut cesser de répondre. Ce comportement peut être utile lors du développement. Si la source de données ne prend pas en charge le délai d’attente, vous obtenez la sortie de trace, mais pas une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset (classe)](../../mfc/reference/crecordset-class.md)

