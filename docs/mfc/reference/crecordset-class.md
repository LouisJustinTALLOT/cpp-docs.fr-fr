---
title: Classe CRecordset
ms.date: 11/04/2016
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
ms.openlocfilehash: 1ebdb18254171d28b5d5e02367596b79142df284
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421015"
---
# <a name="crecordset-class"></a>Classe CRecordset

Représente un ensemble d'enregistrements sélectionnés à partir d'une source de données.

## <a name="syntax"></a>Syntaxe

```
class CRecordset : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CRecordset :: CRecordset](#crecordset)|Construit un objet `CRecordset`. Votre classe dérivée doit fournir un constructeur qui appelle celle-ci.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CRecordset :: AddNew](#addnew)|Prépare l’ajout d’un nouvel enregistrement. Appelez `Update` pour terminer l’addition.|
|[CRecordset :: CanAppend](#canappend)|Retourne une valeur différente de zéro si de nouveaux enregistrements peuvent être ajoutés au recordset via la fonction membre `AddNew`.|
|[CRecordset :: CanBookmark](#canbookmark)|Retourne une valeur différente de zéro si le Recordset prend en charge les signets.|
|[CRecordset :: Cancel](#cancel)|Annule une opération asynchrone ou un processus à partir d’un deuxième thread.|
|[CRecordset :: CancelUpdate](#cancelupdate)|Annule toutes les mises à jour en attente en raison d’une opération `AddNew` ou `Edit`.|
|[CRecordset :: CanRestart](#canrestart)|Retourne une valeur différente de zéro si `Requery` peut être appelée pour réexécuter la requête du Recordset.|
|[CRecordset :: CanScroll](#canscroll)|Retourne une valeur différente de zéro si vous pouvez faire défiler les enregistrements.|
|[CRecordset :: CanTransact](#cantransact)|Retourne une valeur différente de zéro si la source de données prend en charge les transactions.|
|[CRecordset :: CanUpdate](#canupdate)|Retourne une valeur différente de zéro si le jeu d’enregistrements peut être mis à jour (vous pouvez ajouter, mettre à jour ou supprimer des enregistrements).|
|[CRecordset :: CheckRowsetError](#checkrowseterror)|Appelé pour gérer les erreurs générées pendant l’extraction d’enregistrement.|
|[CRecordset :: Close](#close)|Ferme le Recordset et l’HSTMT ODBC qui lui est associé.|
|[CRecordset ::D supprim](#delete)|Supprime l’enregistrement actif du Recordset. Vous devez faire défiler explicitement jusqu’à un autre enregistrement après la suppression.|
|[CRecordset ::D oBulkFieldExchange](#dobulkfieldexchange)|Appelé pour échanger des lignes de données en bloc de la source de données vers le Recordset. Implémente l’échange de champs d’enregistrements en bloc (RFX en bloc).|
|[CRecordset ::D oFieldExchange](#dofieldexchange)|Appelé pour échanger des données (dans les deux sens) entre les données membres de champ du Recordset et l’enregistrement correspondant sur la source de données. Implémente RFX (Record Field Exchange).|
|[CRecordset :: Edit](#edit)|Prépare les modifications apportées à l’enregistrement en cours. Appelez `Update` pour terminer la modification.|
|[CRecordset :: FlushResultSet](#flushresultset)|Retourne une valeur différente de zéro s’il existe un autre jeu de résultats à récupérer, lors de l’utilisation d’une requête prédéfinie.|
|[CRecordset :: GetBookmark](#getbookmark)|Affecte la valeur de signet d’un enregistrement à l’objet de paramètre.|
|[CRecordset :: GetDefaultConnect](#getdefaultconnect)|Appelé pour recevoir la chaîne de connexion par défaut.|
|[CRecordset :: GetDefaultSQL](#getdefaultsql)|Appelé pour récupérer la chaîne SQL par défaut à exécuter.|
|[CRecordset :: GetFieldValue](#getfieldvalue)|Retourne la valeur d’un champ dans un Recordset.|
|[CRecordset :: GetODBCFieldCount](#getodbcfieldcount)|Retourne le nombre de champs dans le Recordset.|
|[CRecordset :: GetODBCFieldInfo](#getodbcfieldinfo)|Retourne des types spécifiques d’informations sur les champs d’un Recordset.|
|[CRecordset :: GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements dans le Recordset.|
|[CRecordset :: GetRowsetSize](#getrowsetsize)|Retourne le nombre d’enregistrements que vous souhaitez récupérer au cours d’une seule extraction.|
|[CRecordset :: GetRowsFetched](#getrowsfetched)|Retourne le nombre réel de lignes récupérées lors d’une extraction.|
|[CRecordset :: GetRowStatus](#getrowstatus)|Retourne l’état de la ligne après une extraction.|
|[CRecordset :: GetSQL](#getsql)|Obtient la chaîne SQL utilisée pour sélectionner des enregistrements pour le Recordset.|
|[CRecordset :: GetStatus](#getstatus)|Obtient l’état du Recordset : l’index de l’enregistrement en cours et si un nombre final d’enregistrements a été obtenu.|
|[CRecordset :: GetTableName](#gettablename)|Obtient le nom de la table sur laquelle est basé le Recordset.|
|[CRecordset :: IsBOF](#isbof)|Retourne une valeur différente de zéro si le jeu d’enregistrements a été placé avant le premier enregistrement. Il n’y a aucun enregistrement en cours.|
|[CRecordset :: IsDeleted](#isdeleted)|Retourne une valeur différente de zéro si le jeu d’enregistrements est positionné sur un enregistrement supprimé.|
|[CRecordset :: IsEOF](#iseof)|Retourne une valeur différente de zéro si le jeu d’enregistrements a été placé après le dernier enregistrement. Il n’y a aucun enregistrement en cours.|
|[CRecordset :: IsFieldDirty](#isfielddirty)|Retourne une valeur différente de zéro si le champ spécifié dans l’enregistrement actif a été modifié.|
|[CRecordset :: IsFieldNull](#isfieldnull)|Retourne une valeur différente de zéro si le champ spécifié dans l’enregistrement actif est null (aucune valeur).|
|[CRecordset :: IsFieldNullable](#isfieldnullable)|Retourne une valeur différente de zéro si le champ spécifié dans l’enregistrement actif peut être défini sur null (sans valeur).|
|[CRecordset :: IsOpen](#isopen)|Retourne une valeur différente de zéro si `Open` a été appelé précédemment.|
|[CRecordset :: Move](#move)|Positionne le Recordset sur un nombre spécifié d’enregistrements à partir de l’enregistrement actif dans l’une ou l’autre direction.|
|[CRecordset :: MoveFirst](#movefirst)|Positionne l’enregistrement actif sur le premier enregistrement du Recordset. Testez d’abord `IsBOF`.|
|[CRecordset :: MoveLast](#movelast)|Positionne l’enregistrement actif sur le dernier enregistrement ou sur le dernier ensemble de lignes. Testez d’abord `IsEOF`.|
|[CRecordset :: MoveNext](#movenext)|Positionne l’enregistrement actif sur l’enregistrement suivant ou sur l’ensemble de lignes suivant. Testez d’abord `IsEOF`.|
|[CRecordset :: MovePrev](#moveprev)|Positionne l’enregistrement actif sur l’enregistrement précédent ou sur l’ensemble de lignes précédent. Testez d’abord `IsBOF`.|
|[CRecordset :: OnSetOptions](#onsetoptions)|Appelé pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée.|
|[CRecordset :: OnSetUpdateOptions](#onsetupdateoptions)|Appelé pour définir les options (utilisées lors de la mise à jour) pour l’instruction ODBC spécifiée.|
|[CRecordset :: Open](#open)|Ouvre le Recordset en extrayant la table ou en exécutant la requête représentée par le Recordset.|
|[CRecordset :: RefreshRowset](#refreshrowset)|Actualise les données et l’état de la ou des lignes spécifiées.|
|[CRecordset :: Requery](#requery)|Réexécute la requête du Recordset pour actualiser les enregistrements sélectionnés.|
|[CRecordset :: SetAbsolutePosition](#setabsoluteposition)|Positionne le Recordset sur l’enregistrement correspondant au numéro d’enregistrement spécifié.|
|[CRecordset :: SetBookmark](#setbookmark)|Positionne le Recordset sur l’enregistrement spécifié par le signet.|
|[CRecordset :: SetFieldDirty](#setfielddirty)|Marque le champ spécifié dans l’enregistrement actuel comme modifié.|
|[CRecordset :: SetFieldNull](#setfieldnull)|Définit la valeur du champ spécifié dans l’enregistrement actuel sur null (sans valeur).|
|[CRecordset :: SetLockingMode](#setlockingmode)|Définit le mode de verrouillage sur le verrouillage « optimiste » (valeur par défaut) ou le verrouillage « pessimiste ». Détermine la façon dont les enregistrements sont verrouillés pour les mises à jour.|
|[CRecordset :: SetParamNull](#setparamnull)|Définit le paramètre spécifié sur null (sans valeur).|
|[CRecordset :: SetRowsetCursorPosition](#setrowsetcursorposition)|Positionne le curseur sur la ligne spécifiée au sein de l’ensemble de lignes.|
|[CRecordset :: SetRowsetSize](#setrowsetsize)|Spécifie le nombre d’enregistrements que vous souhaitez récupérer lors d’une extraction.|
|[CRecordset :: Update](#update)|Termine une opération de `AddNew` ou de `Edit` en enregistrant les données nouvelles ou modifiées sur la source de données.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CRecordset :: m_hstmt](#m_hstmt)|Contient le descripteur d’instruction ODBC pour le Recordset. Tapez `HSTMT`.|
|[CRecordset :: m_nFields](#m_nfields)|Contient le nombre de membres de données de champ dans le Recordset. Tapez `UINT`.|
|[CRecordset :: m_nParams](#m_nparams)|Contient le nombre de membres de données de paramètre dans le Recordset. Tapez `UINT`.|
|[CRecordset :: m_pDatabase](#m_pdatabase)|Contient un pointeur vers l’objet `CDatabase` par le biais duquel le Recordset est connecté à une source de données.|
|[CRecordset :: m_strFilter](#m_strfilter)|Contient une `CString` qui spécifie une clause de `WHERE` langage SQL (SQL). Utilisé comme filtre pour sélectionner uniquement les enregistrements qui répondent à certains critères.|
|[CRecordset :: m_strSort](#m_strsort)|Contient une `CString` qui spécifie une clause SQL `ORDER BY`. Utilisé pour contrôler la façon dont les enregistrements sont triés.|

## <a name="remarks"></a> Notes

Appelés « recordsets », les objets `CRecordset` sont généralement utilisés sous deux formes : les feuilles de réponse dynamiques et les instantanés. Une feuille de réponse dynamique reste synchronisée avec les mises à jour de données effectuées par d’autres utilisateurs. Un instantané est une vue statique des données. Chaque formulaire représente un ensemble d’enregistrements fixés au moment de l’ouverture du Recordset, mais lorsque vous faites défiler vers un enregistrement dans une feuille de réponse dynamique, il reflète les modifications apportées par la suite à l’enregistrement, soit par d’autres utilisateurs, soit par d’autres jeux d’enregistrements de votre application.

> [!NOTE]
>  Si vous utilisez les classes DAO (Data Access Objects) au lieu des classes Open Database Connectivity (ODBC), utilisez la classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de bases de données](../../data/data-access-programming-mfc-atl.md).

Pour utiliser l’un ou l’autre type d’objet Recordset, vous dérivez généralement une classe Recordset spécifique à l’application à partir de `CRecordset`. Les jeux d’enregistrements sélectionnent les enregistrements d’une source de données, et vous pouvez ensuite :

- Faites défiler les enregistrements.

- Mettez à jour les enregistrements et spécifiez un mode de verrouillage.

- Filtrez le Recordset pour limiter les enregistrements qu’il sélectionne parmi ceux qui sont disponibles dans la source de données.

- Triez le Recordset.

- Paramétrez le Recordset pour personnaliser sa sélection avec des informations inconnues jusqu’au moment de l’exécution.

Pour utiliser votre classe, ouvrez une base de données et construisez un objet Recordset, en passant au constructeur un pointeur vers votre objet `CDatabase`. Appelez ensuite la fonction membre `Open` du Recordset, où vous pouvez spécifier si l’objet est une feuille de réponse dynamique ou un instantané. L’appel de `Open` sélectionne des données de la source de données. Une fois l’objet Recordset ouvert, utilisez ses fonctions membres et ses membres de données pour faire défiler les enregistrements et les utiliser. Les opérations disponibles varient selon que l’objet est une feuille de réponse dynamique ou un instantané, qu’il peut être mis à jour ou en lecture seule (cela dépend de la capacité de la source de données Open Database Connectivity (ODBC)) et si vous avez implémenté l’extraction de lignes en bloc. Pour actualiser les enregistrements qui ont peut-être été modifiés ou ajoutés depuis le `Open` appel, appelez la fonction membre `Requery` de l’objet. Appelez la fonction membre `Close` de l’objet et détruisez l’objet une fois que vous l’avez terminé.

Dans une classe de `CRecordset` dérivée, l’échange de champs d’enregistrement (RFX) ou l’échange de champs d’enregistrements en bloc (RFX en bloc) est utilisé pour prendre en charge la lecture et la mise à jour des champs d’enregistrement.

Pour plus d’informations sur les jeux d’enregistrements et l’échange de champs d’enregistrements, consultez les articles [vue d’ensemble : programmation de bases de données](../../data/data-access-programming-mfc-atl.md), [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset : récupération d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)). Pour se concentrer sur les feuilles de réponse dynamiques et les instantanés, consultez les articles [feuille de réponse dynamique](../../data/odbc/dynaset.md) et [instantané](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXDB. h

##  <a name="addnew"></a>CRecordset :: AddNew

Prépare l’ajout d’un nouvel enregistrement à la table.

```
virtual void AddNew();
```

### <a name="remarks"></a>Notes

Vous devez appeler la fonction membre [Requery](#requery) pour voir l’enregistrement qui vient d’être ajouté. Les champs de l’enregistrement ont initialement la valeur null. (Dans la terminologie de base de données, null signifie « aucune valeur » et n’est pas identique C++à null dans.) Pour terminer l’opération, vous devez appeler la fonction membre [Update](#update) . `Update` enregistre les modifications apportées à la source de données.

> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `AddNew`. Cela entraînera l’échec d’une assertion. Bien que la classe `CRecordset` ne fournisse pas de mécanisme de mise à jour des lignes de données en bloc, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew` prépare un nouvel enregistrement vide à l’aide des membres de données de champ du Recordset. Après avoir appelé `AddNew`, définissez les valeurs souhaitées dans les membres de données de champ du Recordset. (Vous n’avez pas besoin d’appeler la fonction membre [Edit](#edit) à cet effet ; utilisez `Edit` uniquement pour les enregistrements existants.) Lorsque vous appelez par la suite `Update`, les valeurs modifiées dans les membres de données de champ sont enregistrées dans la source de données.

> [!CAUTION]
>  Si vous faites défiler vers un nouvel enregistrement avant d’appeler `Update`, le nouvel enregistrement est perdu et aucun avertissement n’est fourni.

Si la source de données prend en charge les transactions, vous pouvez faire en sorte que vos `AddNew` appellent une transaction. Pour plus d’informations sur les transactions, consultez la classe [CDatabase](../../mfc/reference/cdatabase-class.md). Notez que vous devez appeler [CDatabase :: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) avant d’appeler `AddNew`.

> [!NOTE]
>  Pour les feuilles de réponse dynamiques, les nouveaux enregistrements sont ajoutés au recordset comme dernier enregistrement. Les enregistrements ajoutés ne sont pas ajoutés aux captures instantanées. vous devez appeler `Requery` pour actualiser le Recordset.

Il est interdit d’appeler `AddNew` pour un jeu d’enregistrements dont la fonction membre `Open` n’a pas été appelée. Une `CDBException` est levée si vous appelez `AddNew` pour un jeu d’enregistrements qui ne peut pas être ajouté à. Vous pouvez déterminer si le jeu d’enregistrements peut être mis à jour en appelant [CanAppend](#canappend).

Pour plus d’informations, consultez les articles suivants : [Recordset : comment les recordsets mettent à jour les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Recordset : ajout, mise à jour et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)et [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Exemple

Consultez l’article [transaction : exécution d’une transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="canappend"></a>CRecordset :: CanAppend

Détermine si le Recordset précédemment ouvert vous permet d’ajouter de nouveaux enregistrements.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le Recordset autorise l’ajout de nouveaux enregistrements ; Sinon, 0. `CanAppend` retourne 0 si vous avez ouvert le Recordset en lecture seule.

##  <a name="canbookmark"></a>CRecordset :: CanBookmark

Détermine si le Recordset vous permet de marquer des enregistrements à l’aide de signets.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le Recordset prend en charge les signets ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est indépendante de l’option `CRecordset::useBookmarks` dans le paramètre *dwOptions* de la fonction membre [Open](#open) . `CanBookmark` indique si le pilote ODBC et le type de curseur spécifiés prennent en charge les signets. `CRecordset::useBookmarks` indique si les signets seront disponibles, à condition qu’ils soient pris en charge.

> [!NOTE]
>  Les signets ne sont pas pris en charge sur les recordsets avant uniquement.

Pour plus d’informations sur les signets et la navigation dans les jeux d’enregistrements, consultez les articles [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="cancel"></a>CRecordset :: Cancel

Demande à la source de données d’annuler une opération asynchrone en cours ou un processus à partir d’un deuxième thread.

```
void Cancel();
```

### <a name="remarks"></a>Notes

Notez que les classes ODBC MFC n’utilisent plus le traitement asynchrone ; pour effectuer une opération asynchrone, vous devez appeler directement la fonction API ODBC `SQLSetConnectOption`. Pour plus d’informations, consultez la rubrique « exécution de fonctions de manière asynchrone » dans le *Guide du programmeur du kit de développement logiciel (SDK) ODBC*.

##  <a name="cancelupdate"></a>CRecordset :: CancelUpdate

Annule toutes les mises à jour en attente, provoquées par une opération de [modification](#edit) ou [AddNew](#addnew) , avant l’appel de la méthode [Update](#update) .

```
void CancelUpdate();
```

### <a name="remarks"></a>Notes

> [!NOTE]
>  Cette fonction membre ne s’applique pas aux recordsets qui utilisent l’extraction de lignes en bloc, car ces recordsets ne peuvent pas appeler `Edit`, `AddNew`ou `Update`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Si la vérification automatique des champs de modification est activée, `CancelUpdate` restaure les variables membres en fonction des valeurs qu’elles avaient avant l’appel de `Edit` ou `AddNew`. dans le cas contraire, toutes les modifications de valeur sont conservées. Par défaut, la vérification automatique des champs est activée lors de l’ouverture du Recordset. Pour le désactiver, vous devez spécifier le `CRecordset::noDirtyFieldCheck` dans le paramètre *dwOptions* de la fonction membre [Open](#open) .

Pour plus d’informations sur la mise à jour des données, consultez l’article [Recordset : ajout, mise à jour et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

##  <a name="canrestart"></a>CRecordset :: CanRestart

Détermine si le Recordset autorise le redémarrage de sa requête (pour actualiser ses enregistrements) en appelant la fonction membre `Requery`.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la rerequête est autorisée ; Sinon, 0.

##  <a name="canscroll"></a>CRecordset :: CanScroll

Détermine si le jeu d’enregistrements permet le défilement.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le jeu d’enregistrements autorise le défilement ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le défilement, consultez l’article [jeu d’enregistrements : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="cantransact"></a>CRecordset :: CanTransact

Détermine si le Recordset autorise les transactions.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le Recordset autorise les transactions ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CRecordset :: CanUpdate

Détermine si le jeu d’enregistrements peut être mis à jour.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le jeu d’enregistrements peut être mis à jour ; Sinon, 0.

### <a name="remarks"></a>Notes

Un jeu d’enregistrements peut être en lecture seule si la source de données sous-jacente est en lecture seule ou si vous avez spécifié `CRecordset::readOnly` dans le paramètre *dwOptions* lorsque vous avez ouvert le Recordset.

##  <a name="checkrowseterror"></a>CRecordset :: CheckRowsetError

Appelé pour gérer les erreurs générées pendant l’extraction d’enregistrement.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Paramètres

*nRetCode*<br/>
Code de retour de la fonction d’API ODBC. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Cette fonction membre virtuelle gère les erreurs qui se produisent lorsque des enregistrements sont extraits et est utile lors de l’extraction de lignes en bloc. Vous pouvez envisager de substituer `CheckRowsetError` pour implémenter votre propre gestion des erreurs.

`CheckRowsetError` est appelé automatiquement dans une opération de navigation de curseur, comme `Open`, `Requery`ou toute opération de `Move`. La valeur de retour de la fonction d’API ODBC `SQLExtendedFetch`est passée. Le tableau suivant répertorie les valeurs possibles pour le paramètre *nRetCode* .

|nRetCode|Description|
|--------------|-----------------|
|SQL_SUCCESS|La fonction s’est terminée avec succès ; aucune information supplémentaire n’est disponible.|
|SQL_SUCCESS_WITH_INFO|La fonction s’est terminée avec succès, éventuellement avec une erreur récupérable. Vous pouvez obtenir des informations supplémentaires en appelant `SQLError`.|
|SQL_NO_DATA_FOUND|Toutes les lignes du jeu de résultats ont été extraites.|
|SQL_ERROR|Échec de la fonction. Vous pouvez obtenir des informations supplémentaires en appelant `SQLError`.|
|SQL_INVALID_HANDLE|La fonction a échoué en raison d’un handle d’environnement, d’un handle de connexion ou d’un handle d’instruction non valide. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible à partir de `SQLError`.|
|SQL_STILL_EXECUTING|Une fonction qui a été démarrée de manière asynchrone est toujours en cours d’exécution. Notez que, par défaut, MFC ne passera jamais cette valeur à `CheckRowsetError`; MFC continuera à appeler `SQLExtendedFetch` jusqu’à ce qu’il ne retourne plus SQL_STILL_EXECUTING.|

Pour plus d’informations sur `SQLError`, consultez la SDK Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="close"></a>CRecordset :: Close

Ferme le Recordset.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

L’HSTMT ODBC et la mémoire de l’infrastructure allouée pour le Recordset sont désallouées. En général, après avoir appelé `Close`, C++ vous supprimez l’objet Recordset s’il a été alloué avec **New**.

Vous pouvez appeler `Open` à nouveau après avoir appelé `Close`. Cela vous permet de réutiliser l’objet Recordset. L’alternative consiste à appeler `Requery`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>CRecordset :: CRecordset

Construit un objet `CRecordset`.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Paramètres

*pDatabase*<br/>
Contient un pointeur vers un objet `CDatabase` ou la valeur NULL. Si la valeur n’est pas NULL et que la fonction membre `Open` de l’objet `CDatabase` n’a pas été appelée pour la connecter à la source de données, le jeu d’enregistrements tente de l’ouvrir pour vous lors de son propre `Open` appel. Si vous transmettez la valeur NULL, un objet `CDatabase` est construit et connecté pour vous à l’aide des informations de source de données que vous avez spécifiées quand vous avez dérivé votre classe Recordset avec ClassWizard.

### <a name="remarks"></a>Notes

Vous pouvez utiliser `CRecordset` directement ou dériver une classe spécifique à l’application à partir de `CRecordset`. Vous pouvez utiliser ClassWizard pour dériver vos classes de Recordset.

> [!NOTE]
>  Une classe dérivée *doit* fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur `CRecordset::CRecordset`, en passant les paramètres appropriés.

Transmettez la valeur NULL au constructeur de votre jeu d’enregistrements pour qu’un objet `CDatabase` soit construit et connecté automatiquement pour vous. Il s’agit d’un raccourci utile qui ne vous oblige pas à construire et à connecter un objet `CDatabase` avant de construire votre jeu d’enregistrements.

### <a name="example"></a>Exemple

Pour plus d’informations, consultez l’article [Recordset : déclaration d’une classe pour une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

##  <a name="delete"></a>CRecordset ::D supprim

Supprime l’enregistrement en cours.

```
virtual void Delete();
```

### <a name="remarks"></a>Notes

Après une suppression réussie, les membres de données de champ du Recordset sont définis sur une valeur null, et vous devez appeler explicitement l’une des fonctions `Move` pour déplacer l’enregistrement supprimé. Une fois que vous avez quitté l’enregistrement supprimé, il n’est pas possible de le retourner. Si la source de données prend en charge les transactions, vous pouvez faire en sorte que le `Delete` appeler une partie d’une transaction. Pour plus d’informations, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `Delete`. Cela entraînera l’échec d’une assertion. Bien que la classe `CRecordset` ne fournisse pas de mécanisme de mise à jour des lignes de données en bloc, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
>  L’ensemble d’enregistrements doit pouvoir être mis à jour et un enregistrement valide doit être présent dans le recordset lorsque vous appelez `Delete`; dans le cas contraire, une erreur se produit. Par exemple, si vous supprimez un enregistrement mais que vous ne faites pas défiler vers un nouvel enregistrement avant d’appeler à nouveau `Delete`, `Delete` lève une [CDBException](../../mfc/reference/cdbexception-class.md).

Contrairement à [AddNew](#addnew) et [Edit](#edit), un appel à `Delete` n’est pas suivi d’un appel à [Update](#update). En cas d’échec d’un appel de `Delete`, les données membres de champ restent inchangées.

### <a name="example"></a>Exemple

Cet exemple montre un jeu d’enregistrements créé sur le frame d’une fonction. L’exemple suppose l’existence d' `m_dbCust`, une variable membre de type `CDatabase` déjà connectée à la source de données.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>CRecordset ::D oBulkFieldExchange

Appelé pour échanger des lignes de données en bloc de la source de données vers le Recordset. Implémente l’échange de champs d’enregistrements en bloc (RFX en bloc).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . L’infrastructure aura déjà configuré cet objet pour spécifier un contexte pour l’opération d’échange de champs.

### <a name="remarks"></a>Notes

Lors de l’implémentation de l’extraction de lignes en bloc, l’infrastructure appelle cette fonction membre pour transférer automatiquement les données de la source de données vers votre objet Recordset. `DoBulkFieldExchange` lie également vos membres de données de paramètre, le cas échéant, aux espaces réservés de paramètre dans la chaîne de l’instruction SQL pour la sélection du Recordset.

Si l’extraction de lignes en bloc n’est pas implémentée, le Framework appelle [DoFieldExchange](#dofieldexchange). Pour implémenter l’extraction de lignes en bloc, vous devez spécifier l’option `CRecordset::useMultiRowFetch` du paramètre *dwOptions* dans la fonction membre [Open](#open) .

> [!NOTE]
> `DoBulkFieldExchange` est disponible uniquement si vous utilisez une classe dérivée de `CRecordset`. Si vous avez créé un objet Recordset directement à partir de `CRecordset`, vous devez appeler la fonction membre [GetFieldValue](#getfieldvalue) pour récupérer des données.

L’échange de champs d’enregistrements en bloc (RFX en bloc) est similaire à l’échange de champs d’enregistrement (RFX). Les données sont automatiquement transférées de la source de données vers l’objet Recordset. Toutefois, vous ne pouvez pas appeler `AddNew`, `Edit`, `Delete`ou `Update` pour transférer les modifications vers la source de données. Actuellement, la classe `CRecordset` ne fournit pas de mécanisme de mise à jour des lignes de données en bloc ; Toutefois, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`.

Notez que ClassWizard ne prend pas en charge l’échange de champs d’enregistrements en bloc. par conséquent, vous devez remplacer `DoBulkFieldExchange` manuellement en écrivant des appels aux fonctions RFX en bloc. Pour plus d’informations sur ces fonctions, consultez la rubrique [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md).

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour obtenir des informations connexes, consultez l’article [échange de champs d’enregistrement (RFX)](../../data/odbc/record-field-exchange-rfx.md).

##  <a name="dofieldexchange"></a>CRecordset ::D oFieldExchange

Appelé pour échanger des données (dans les deux sens) entre les données membres de champ du Recordset et l’enregistrement correspondant sur la source de données. Implémente RFX (Record Field Exchange).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . L’infrastructure aura déjà configuré cet objet pour spécifier un contexte pour l’opération d’échange de champs.

### <a name="remarks"></a>Notes

Lorsque l’extraction de lignes en bloc n’est pas implémentée, l’infrastructure appelle cette fonction membre pour échanger automatiquement des données entre les membres de données de champ de votre objet Recordset et les colonnes correspondantes de l’enregistrement actif sur la source de données. `DoFieldExchange` lie également vos membres de données de paramètre, le cas échéant, aux espaces réservés de paramètre dans la chaîne de l’instruction SQL pour la sélection du Recordset.

Si l’extraction de lignes en bloc est implémentée, le Framework appelle [DoBulkFieldExchange](#dobulkfieldexchange). Pour implémenter l’extraction de lignes en bloc, vous devez spécifier l’option `CRecordset::useMultiRowFetch` du paramètre *dwOptions* dans la fonction membre [Open](#open) .

> [!NOTE]
> `DoFieldExchange` est disponible uniquement si vous utilisez une classe dérivée de `CRecordset`. Si vous avez créé un objet Recordset directement à partir de `CRecordset`, vous devez appeler la fonction membre [GetFieldValue](#getfieldvalue) pour récupérer des données.

L’échange de données de champ, appelé RFX (Record Field Exchange), fonctionne dans les deux sens : à partir des membres de données de champ de l’objet Recordset vers les champs de l’enregistrement sur la source de données, et de l’enregistrement sur la source de données vers l’objet Recordset.

La seule action que vous devez normalement effectuer pour implémenter `DoFieldExchange` pour votre classe de Recordset dérivée consiste à créer la classe avec ClassWizard et à spécifier les noms et les types de données des membres de données de champ. Vous pouvez également ajouter du code à ce que l’Assistant ClassWizard écrit pour spécifier des membres de données de paramètre ou gérer les colonnes que vous liez dynamiquement. Pour plus d’informations, consultez l’article [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Quand vous déclarez votre classe de Recordset dérivée avec ClassWizard, l’Assistant écrit une substitution de `DoFieldExchange` pour vous, qui ressemble à l’exemple suivant :

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Pour plus d’informations sur les fonctions RFX, consultez la rubrique [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md).

Pour obtenir des exemples supplémentaires et des détails sur `DoFieldExchange`, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour obtenir des informations générales sur RFX, consultez l’article [Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md).

##  <a name="edit"></a>CRecordset :: Edit

Autorise les modifications de l’enregistrement en cours.

```
virtual void Edit();
```

### <a name="remarks"></a>Notes

Après avoir appelé `Edit`, vous pouvez modifier les membres de données de champ en réinitialisant directement leurs valeurs. L’opération est terminée lorsque vous appelez ensuite la fonction membre [Update](#update) pour enregistrer vos modifications sur la source de données.

> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `Edit`. Cela entraînera l’échec d’une assertion. Bien que la classe `CRecordset` ne fournisse pas de mécanisme de mise à jour des lignes de données en bloc, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit` enregistre les valeurs des membres de données du Recordset. Si vous appelez `Edit`, apportez des modifications, puis appelez à nouveau `Edit`, les valeurs de l’enregistrement sont restaurées en fonction de ce qu’elles étaient avant le premier appel `Edit`.

Dans certains cas, vous souhaiterez peut-être mettre à jour une colonne en la rendant null (ne contenant aucune donnée). Pour ce faire, appelez [SetFieldNull](#setfieldnull) avec un paramètre de true pour marquer le champ comme null. Cela entraîne également la mise à jour de la colonne. Si vous souhaitez qu’un champ soit écrit dans la source de données même si sa valeur n’a pas changé, appelez [SetFieldDirty](#setfielddirty) avec un paramètre ayant la valeur true. Cela fonctionne même si le champ avait la valeur null.

Si la source de données prend en charge les transactions, vous pouvez faire en sorte que le `Edit` appeler une partie d’une transaction. Notez que vous devez appeler [CDatabase :: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) avant d’appeler `Edit` et après l’ouverture du Recordset. Notez également que l’appel de [CDatabase :: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) ne remplace pas `Update` pour terminer l’opération `Edit`. Pour plus d’informations sur les transactions, consultez la classe [CDatabase](../../mfc/reference/cdatabase-class.md).

Selon le mode de verrouillage en cours, l’enregistrement en cours de mise à jour peut être verrouillé par `Edit` jusqu’à ce que vous appeliez `Update` ou que vous défilez vers un autre enregistrement, ou qu’il ne soit verrouillé que lors de l’appel de `Edit`. Vous pouvez modifier le mode de verrouillage avec [SetLockingMode](#setlockingmode).

La valeur précédente de l’enregistrement en cours est restaurée si vous faites défiler vers un nouvel enregistrement avant d’appeler `Update`. Une `CDBException` est levée si vous appelez `Edit` pour un jeu d’enregistrements qui ne peut pas être mis à jour ou s’il n’existe aucun enregistrement en cours.

Pour plus d’informations, consultez les articles [transaction (ODBC)](../../data/odbc/transaction-odbc.md) et [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>CRecordset :: FlushResultSet

Récupère le jeu de résultats suivant d’une requête prédéfinie (procédure stockée), s’il existe plusieurs jeux de résultats.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si le nombre de jeux de résultats doit être récupéré. Sinon, 0.

### <a name="remarks"></a>Notes

Vous devez appeler `FlushResultSet` uniquement lorsque vous avez terminé avec le curseur sur le jeu de résultats actuel. Notez que lorsque vous récupérez le jeu de résultats suivant en appelant `FlushResultSet`, votre curseur n’est pas valide dans ce jeu de résultats ; vous devez appeler la fonction membre [MoveNext](#movenext) après avoir appelé `FlushResultSet`.

Si une requête prédéfinie utilise un paramètre de sortie ou des paramètres d’entrée/sortie, vous devez appeler `FlushResultSet` jusqu’à ce qu’elle retourne `FALSE` (la valeur 0), afin d’obtenir ces valeurs de paramètre.

`FlushResultSet` appelle la fonction API ODBC `SQLMoreResults`. Si `SQLMoreResults` retourne SQL_ERROR ou SQL_INVALID_HANDLE, `FlushResultSet` lèvera une exception. Pour plus d’informations sur `SQLMoreResults`, consultez la SDK Windows.

Votre procédure stockée doit avoir des champs liés si vous souhaitez appeler `FlushResultSet`.

### <a name="example"></a>Exemple

Le code suivant suppose que `COutParamRecordset` est un objet dérivé de `CRecordset`basé sur une requête prédéfinie avec un paramètre d’entrée et un paramètre de sortie, et ayant plusieurs jeux de résultats. Notez la structure de la substitution [DoFieldExchange](#dofieldexchange) .

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>CRecordset :: GetBookmark

Obtient la valeur de signet pour l’enregistrement en cours.

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Paramètres

*varBookmark*<br/>
Référence à un objet [CDBVariant](../../mfc/reference/cdbvariant-class.md) qui représente le signet sur l’enregistrement actif.

### <a name="remarks"></a>Notes

Pour déterminer si les signets sont pris en charge sur le Recordset, appelez [CanBookmark](#canbookmark). Pour rendre les signets disponibles s’ils sont pris en charge, vous devez définir l’option `CRecordset::useBookmarks` dans le paramètre *dwOptions* de la fonction membre [Open](#open) .

> [!NOTE]
>  Si les signets ne sont pas pris en charge ou ne sont pas disponibles, l’appel de `GetBookmark` entraîne la levée d’une exception. Les signets ne sont pas pris en charge sur les recordsets avant uniquement.

`GetBookmark` affecte la valeur du signet de l’enregistrement en cours à un objet `CDBVariant`. Pour revenir à cet enregistrement à tout moment après le déplacement vers un autre enregistrement, appelez [SetBookmark](#setbookmark) avec l’objet `CDBVariant` correspondant.

> [!NOTE]
>  Après certaines opérations sur les jeux d’enregistrements, les signets ne sont plus valides. Par exemple, si vous appelez `GetBookmark` suivi de `Requery`, vous risquez de ne pas pouvoir revenir à l’enregistrement avec `SetBookmark`. Appelez [CDatabase :: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si vous pouvez appeler `SetBookmark`en toute sécurité.

Pour plus d’informations sur les signets et la navigation dans les jeux d’enregistrements, consultez les articles [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="getdefaultconnect"></a>CRecordset :: GetDefaultConnect

Appelé pour recevoir la chaîne de connexion par défaut.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Valeur de retour

`CString` qui contient la chaîne de connexion par défaut.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction membre pour obtenir la chaîne de connexion par défaut pour la source de données sur laquelle le Recordset est basé. ClassWizard implémente cette fonction pour vous en identifiant la même source de données que vous utilisez dans ClassWizard pour obtenir des informations sur les tables et les colonnes. Vous trouverez probablement plus pratique d’utiliser cette connexion par défaut lors du développement de votre application. Toutefois, la connexion par défaut peut ne pas convenir aux utilisateurs de votre application. Si tel est le cas, vous devez réimplémenter cette fonction, en ignorant la version de ClassWizard. Pour plus d’informations sur les chaînes de connexion, consultez l’article [source de données (ODBC)](../../data/odbc/data-source-odbc.md).

##  <a name="getdefaultsql"></a>CRecordset :: GetDefaultSQL

Appelé pour récupérer la chaîne SQL par défaut à exécuter.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Valeur de retour

`CString` qui contient l’instruction SQL par défaut.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction membre pour recevoir l’instruction SQL par défaut sur laquelle est basé le Recordset. Il peut s’agir d’un nom de table ou d’une instruction SQL **Select** .

Vous définissez indirectement l’instruction SQL par défaut en déclarant votre classe Recordset avec ClassWizard, et ClassWizard effectue cette tâche pour vous.

Si vous avez besoin de la chaîne d’instruction SQL pour votre propre usage, appelez `GetSQL`, qui retourne l’instruction SQL utilisée pour sélectionner les enregistrements du Recordset lorsqu’elle a été ouverte. Vous pouvez modifier la chaîne SQL par défaut dans la substitution de la classe de `GetDefaultSQL`. Par exemple, vous pouvez spécifier un appel à une requête prédéfinie à l’aide d’une instruction **Call** . (Notez, toutefois, que si vous modifiez `GetDefaultSQL`, vous devez également modifier `m_nFields` pour qu’il corresponde au nombre de colonnes dans la source de données.)

Pour plus d’informations, consultez l’article [Recordset : déclaration d’une classe pour une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
>  Le nom de la table est vide si le Framework n’a pas pu identifier un nom de table, si plusieurs noms de tables ont été fournis ou si une instruction d' **appel** n’a pas pu être interprétée. Notez que lorsque vous utilisez une instruction **Call** , vous ne devez pas insérer d’espace entre l’accolade et le mot clé **Call** , ni insérer d’espace avant l’accolade ou avant le mot clé **Select** dans une instruction **Select** .

##  <a name="getfieldvalue"></a>CRecordset :: GetFieldValue

Récupère les données de champ dans l’enregistrement en cours.

```
void GetFieldValue(
    LPCTSTR lpszName,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CStringA& strValue);

void GetFieldValue(
    short nIndex,
    CStringW& strValue);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom d’un champ.

*varValu*e référence à un objet [CDBVariant](../../mfc/reference/cdbvariant-class.md) qui stocke la valeur du champ.

*nFieldType*<br/>
Type de données ODBC C du champ. À l’aide de la valeur par défaut, DEFAULT_FIELD_TYPE, force `GetFieldValue` à déterminer le type de données C à partir du type de données SQL, en fonction du tableau suivant. Dans le cas contraire, vous pouvez spécifier le type de données directement ou choisir un type de données compatible. par exemple, vous pouvez stocker n’importe quel type de données dans SQL_C_CHAR.

|Type de données C|Type de données SQL|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

Pour plus d’informations sur les types de données ODBC, consultez les rubriques « types de données SQL » et « types de données C » dans l’annexe D de la SDK Windows.

*nIndex*<br/>
Index de base zéro du champ.

*strValue*<br/>
Référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui stocke la valeur du champ convertie en texte, quel que soit le type de données du champ.

### <a name="remarks"></a>Notes

Vous pouvez rechercher un champ par nom ou par index. Vous pouvez stocker la valeur de champ dans un objet `CDBVariant` ou un objet `CString`.

Si vous avez implémenté l’extraction de lignes en bloc, l’enregistrement actif est toujours positionné sur le premier enregistrement d’un ensemble de lignes. Pour utiliser `GetFieldValue` sur un enregistrement au sein d’un ensemble de lignes donné, vous devez d’abord appeler la fonction membre [SetRowsetCursorPosition](#setrowsetcursorposition) pour déplacer le curseur vers la ligne souhaitée dans cet ensemble de lignes. Appelez ensuite `GetFieldValue` pour cette ligne. Pour implémenter l’extraction de lignes en bloc, vous devez spécifier l’option `CRecordset::useMultiRowFetch` du paramètre *dwOptions* dans la fonction membre [Open](#open) .

Vous pouvez utiliser `GetFieldValue` pour extraire dynamiquement des champs au moment de l’exécution plutôt que de les lier statiquement au moment de la conception. Par exemple, si vous avez déclaré un objet Recordset directement à partir de `CRecordset`, vous devez utiliser `GetFieldValue` pour récupérer les données de champ ; l’échange de champs d’enregistrements (RFX) ou l’échange de champs d’enregistrements en bloc (RFX en bloc) n’est pas implémenté.

> [!NOTE]
>  Si vous déclarez un objet Recordset sans dériver de `CRecordset`, la bibliothèque de curseurs ODBC n’est pas chargée. La bibliothèque de curseurs requiert que le jeu d’enregistrements ait au moins une colonne liée ; Toutefois, lorsque vous utilisez `CRecordset` directement, aucune des colonnes n’est liée. Les fonctions membres [CDatabase :: OpenEx](../../mfc/reference/cdatabase-class.md#openex) et [CDatabase :: Open](../../mfc/reference/cdatabase-class.md#open) contrôlent si la bibliothèque de curseurs sera chargée.

`GetFieldValue` appelle la fonction API ODBC `SQLGetData`. Si votre pilote génère la valeur SQL_NO_TOTAL pour la longueur réelle de la valeur de champ, `GetFieldValue` lève une exception. Pour plus d’informations sur `SQLGetData`, consultez la SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant illustre les appels à `GetFieldValue` pour un objet Recordset déclaré directement à partir de `CRecordset`.

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  Contrairement à la classe DAO `CDaoRecordset`, `CRecordset` n’a pas de fonction membre `SetFieldValue`. Si vous créez un objet directement à partir de `CRecordset`, il est en lecture seule.

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="getodbcfieldcount"></a>CRecordset :: GetODBCFieldCount

Récupère le nombre total de champs dans votre objet Recordset.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de champs dans le Recordset.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la création d’ensembles d’enregistrements, consultez l’article [Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

##  <a name="getodbcfieldinfo"></a>CRecordset :: GetODBCFieldInfo

Obtient des informations sur les champs du Recordset.

```
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Nom d’un champ.

*FieldInfo*<br/>
Référence à une structure `CODBCFieldInfo`.

*nIndex*<br/>
Index de base zéro du champ.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un champ par nom. L’autre version vous permet de rechercher un champ par index.

Pour obtenir une description des informations retournées, consultez la structure [codbcfieldinfo,](../../mfc/reference/codbcfieldinfo-structure.md) .

Pour plus d’informations sur la création d’ensembles d’enregistrements, consultez l’article [Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

##  <a name="getrecordcount"></a>CRecordset :: GetRecordCount

Détermine la taille du Recordset.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’enregistrements dans l’ensemble d’enregistrements ; 0 si le jeu d’enregistrements ne contient aucun enregistrement ; ou-1 si le nombre d’enregistrements ne peut pas être déterminé.

### <a name="remarks"></a>Notes

> [!CAUTION]
>  Le nombre d’enregistrements est conservé sous la forme d’une « borne haute », l’enregistrement numéroté le plus élevé, encore visible à mesure que l’utilisateur parcourt les enregistrements. Le nombre total d’enregistrements est connu uniquement après que l’utilisateur a dépassé le dernier enregistrement. Pour des raisons de performances, le nombre n’est pas mis à jour lorsque vous appelez `MoveLast`. Pour compter les enregistrements vous-même, appelez `MoveNext` à plusieurs reprises jusqu’à ce que `IsEOF` retourne une valeur différente de zéro. L’ajout d’un enregistrement via `CRecordset:AddNew` et `Update` augmente le nombre ; la suppression d’un enregistrement via `CRecordset::Delete` diminue le nombre.

##  <a name="getrowsetsize"></a>CRecordset :: GetRowsetSize

Obtient le paramètre actuel du nombre de lignes que vous souhaitez récupérer au cours d’une extraction donnée.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de lignes à récupérer au cours d’une extraction donnée.

### <a name="remarks"></a>Notes

Si vous utilisez l’extraction de lignes en bloc, la taille de l’ensemble de lignes par défaut lors de l’ouverture du Recordset est 25 ; dans le cas contraire, il s’agit de 1.

Pour implémenter l’extraction de lignes en bloc, vous devez spécifier l’option `CRecordset::useMultiRowFetch` dans le paramètre *dwOptions* de la fonction membre [Open](#open) . Pour modifier le paramètre de la taille de l’ensemble de lignes, appelez [SetRowsetSize](#setrowsetsize).

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="getrowsfetched"></a>CRecordset :: GetRowsFetched

Détermine le nombre d’enregistrements réellement récupérés après une extraction.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de lignes récupérées à partir de la source de données après une extraction donnée.

### <a name="remarks"></a>Notes

Cela est utile lorsque vous avez implémenté l’extraction de lignes en bloc. La taille de l’ensemble de lignes indique normalement le nombre de lignes qui seront extraites d’une extraction. Toutefois, le nombre total de lignes dans le jeu d’enregistrements affecte également le nombre de lignes qui seront extraites dans un ensemble de lignes. Par exemple, si votre jeu d’enregistrements contient 10 enregistrements avec un paramètre de taille d’ensemble de lignes de 4, puis en effectuant une boucle dans le jeu d’enregistrements en appelant `MoveNext`, l’ensemble de lignes final n’a que 2 enregistrements.

Pour implémenter l’extraction de lignes en bloc, vous devez spécifier l’option `CRecordset::useMultiRowFetch` dans le paramètre *dwOptions* de la fonction membre [Open](#open) . Pour spécifier la taille de l’ensemble de lignes, appelez [SetRowsetSize](#setrowsetsize).

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>CRecordset :: GetRowStatus

Obtient l’état d’une ligne dans l’ensemble de lignes actif.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Paramètres

*wRow*<br/>
Position de base 1 d’une ligne dans l’ensemble de lignes actif. Cette valeur peut être comprise entre 1 et la taille de l’ensemble de lignes.

### <a name="return-value"></a>Valeur de retour

Valeur d’État pour la ligne. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

`GetRowStatus` retourne une valeur qui indique soit toute modification de l’État sur la ligne depuis sa dernière récupération à partir de la source de données, soit qu’aucune ligne correspondant à *wRow* n’a été extraite. Le tableau ci-dessous répertorie les valeurs de retour possibles.

|Valeur d’état|Description|
|------------------|-----------------|
|SQL_ROW_SUCCESS|La ligne est inchangée.|
|SQL_ROW_UPDATED|La ligne a été mise à jour.|
|SQL_ROW_DELETED|La ligne a été supprimée.|
|SQL_ROW_ADDED|La ligne a été ajoutée.|
|SQL_ROW_ERROR|La ligne n’est pas récupérable en raison d’une erreur.|
|SQL_ROW_NOROW|Aucune ligne ne correspond à *wRow*.|

Pour plus d’informations, consultez la fonction API ODBC `SQLExtendedFetch` dans le SDK Windows.

##  <a name="getstatus"></a>CRecordset :: GetStatus

Détermine l’index de l’enregistrement en cours dans le Recordset et si le dernier enregistrement a été affiché.

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Paramètres

*rStatus*<br/>
Référence à un objet `CRecordsetStatus`. Pour plus d'informations, consultez la section Remarques.

### <a name="remarks"></a>Notes

`CRecordset` tente d’effectuer le suivi de l’index, mais dans certains cas cela peut ne pas être possible. Pour obtenir une explication, consultez [GetRecordCount](#getrecordcount) .

La structure `CRecordsetStatus` se présente sous la forme suivante :

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Les deux membres de `CRecordsetStatus` ont les significations suivantes :

- `m_lCurrentRecord` contient l’index de base zéro de l’enregistrement en cours dans le Recordset, s’il est connu. Si l’index ne peut pas être déterminé, ce membre contient AFX_CURRENT_RECORD_UNDEFINED (-2). Si `IsBOF` a la valeur TRUE (jeu d’enregistrements vide ou tentative de défilement avant le premier enregistrement), `m_lCurrentRecord` a la valeur AFX_CURRENT_RECORD_BOF (-1). Si sur le premier enregistrement, il est défini sur 0, deuxième enregistrement 1, et ainsi de suite.

- `m_bRecordCountFinal` une valeur différente de zéro si le nombre total d’enregistrements dans le jeu d’enregistrements a été déterminé. En général, cela doit être accompli en démarrant au début du Recordset et en appelant `MoveNext` jusqu’à ce que `IsEOF` retourne une valeur différente de zéro. Si ce membre est égal à zéro, le nombre d’enregistrements retournés par `GetRecordCount`, si ce n’est pas-1, n’est qu’un nombre « limite supérieure » des enregistrements.

##  <a name="getsql"></a>CRecordset :: GetSQL

Appelez cette fonction membre pour récupérer l’instruction SQL utilisée pour sélectionner les enregistrements du Recordset lorsqu’elle a été ouverte.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Valeur de retour

Référence **const** à un `CString` qui contient l’instruction SQL.

### <a name="remarks"></a>Notes

Il s’agit généralement d’une instruction SQL **Select** . La chaîne retournée par `GetSQL` est en lecture seule.

La chaîne retournée par `GetSQL` est généralement différente de toute chaîne que vous avez peut-être passée au jeu d’enregistrements dans le paramètre *lpszSQL* de la fonction membre `Open`. Cela est dû au fait que le jeu d’enregistrements construit une instruction SQL complète en fonction de ce que vous avez passé à `Open`, ce que vous avez spécifié avec ClassWizard, ce que vous avez spécifié dans les membres de données `m_strFilter` et `m_strSort`, ainsi que tous les paramètres que vous avez spécifiés. Pour plus d’informations sur la façon dont le recordset construit cette instruction SQL, consultez l’article [Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
>  Appelez cette fonction membre uniquement après avoir appelé [Open](#open).

##  <a name="gettablename"></a>CRecordset :: GetTableName

Obtient le nom de la table SQL sur laquelle repose la requête du Recordset.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Valeur de retour

Référence **const** à un `CString` qui contient le nom de la table, si le Recordset est basé sur une table ; Sinon, une chaîne vide.

### <a name="remarks"></a>Notes

`GetTableName` est valide uniquement si le jeu d’enregistrements est basé sur une table, non une jointure de plusieurs tables ou une requête prédéfinie (procédure stockée). Le nom est en lecture seule.

> [!NOTE]
>  Appelez cette fonction membre uniquement après avoir appelé [Open](#open).

##  <a name="isbof"></a>CRecordset :: IsBOF

Retourne une valeur différente de zéro si le jeu d’enregistrements a été placé avant le premier enregistrement. Il n’y a aucun enregistrement en cours.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si le jeu d’enregistrements ne contient aucun enregistrement ou si vous avez fait défiler vers le haut le premier enregistrement ; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction membre avant de faire défiler d’un enregistrement à un autre pour savoir si vous êtes allé avant le premier enregistrement du jeu d’enregistrements. Vous pouvez également utiliser `IsBOF` avec `IsEOF` pour déterminer si le Recordset contient des enregistrements ou s’il est vide. Immédiatement après l’appel de `Open`, si le jeu d’enregistrements ne contient aucun enregistrement, `IsBOF` retourne une valeur différente de zéro. Lorsque vous ouvrez un jeu d’enregistrements qui a au moins un enregistrement, le premier enregistrement est l’enregistrement actif et `IsBOF` retourne 0.

Si le premier enregistrement est l’enregistrement en cours et que vous appelez `MovePrev`, `IsBOF` retourne par la suite une valeur différente de zéro. Si `IsBOF` retourne une valeur différente de zéro et que vous appelez `MovePrev`, une erreur se produit. Si `IsBOF` retourne une valeur différente de zéro, l’enregistrement actif n’est pas défini et toute action qui requiert un enregistrement actif génère une erreur.

### <a name="example"></a>Exemple

Cet exemple utilise `IsBOF` et `IsEOF` pour détecter les limites d’un jeu d’enregistrements au fur et à mesure que le code fait défiler le Recordset dans les deux directions.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>CRecordset :: IsDeleted

Détermine si l’enregistrement en cours a été supprimé.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le jeu d’enregistrements est positionné sur un enregistrement supprimé ; Sinon, 0.

### <a name="remarks"></a>Notes

Si vous faites défiler vers un enregistrement et que `IsDeleted` retourne TRUE (différent de zéro), vous devez faire défiler vers un autre enregistrement avant de pouvoir effectuer d’autres opérations sur les jeux d’enregistrements.

Le résultat de `IsDeleted` dépend de nombreux facteurs, tels que le type de jeu d’enregistrements, si votre jeu d’enregistrements peut être mis à jour, que vous ayez spécifié l’option `CRecordset::skipDeletedRecords` lors de l’ouverture du Recordset, si votre pilote a supprimé des enregistrements, et s’il y a plusieurs utilisateurs.

Pour plus d’informations sur les `CRecordset::skipDeletedRecords` et la compression des pilotes, consultez la fonction membre [Open](#open) .

> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne devez pas appeler `IsDeleted`. Au lieu de cela, appelez la fonction membre [GetRowStatus](#getrowstatus) . Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="iseof"></a>CRecordset :: IsEOF

Retourne une valeur différente de zéro si le jeu d’enregistrements a été placé après le dernier enregistrement. Il n’y a aucun enregistrement en cours.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si le jeu d’enregistrements ne contient aucun enregistrement ou si vous avez défilé au-delà du dernier enregistrement. Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction membre lorsque vous faites défiler d’un enregistrement à l’autre pour savoir si vous avez dépassé le dernier enregistrement du jeu d’enregistrements. Vous pouvez également utiliser `IsEOF` pour déterminer si le jeu d’enregistrements contient des enregistrements ou s’il est vide. Immédiatement après l’appel de `Open`, si le jeu d’enregistrements ne contient aucun enregistrement, `IsEOF` retourne une valeur différente de zéro. Lorsque vous ouvrez un jeu d’enregistrements qui a au moins un enregistrement, le premier enregistrement est l’enregistrement actif et `IsEOF` retourne 0.

Si le dernier enregistrement est l’enregistrement en cours lorsque vous appelez `MoveNext`, `IsEOF` retourne par la suite une valeur différente de zéro. Si `IsEOF` retourne une valeur différente de zéro et que vous appelez `MoveNext`, une erreur se produit. Si `IsEOF` retourne une valeur différente de zéro, l’enregistrement actif n’est pas défini et toute action qui requiert un enregistrement actif génère une erreur.

### <a name="example"></a>Exemple

Consultez l’exemple de [IsBOF](#isbof).

##  <a name="isfielddirty"></a>CRecordset :: IsFieldDirty

Détermine si le membre de données de champ spécifié a été modifié depuis l’appel de [Edit](#edit) ou [AddNew](#addnew) .

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
Pointeur vers le membre de données de champ dont vous souhaitez vérifier l’État, ou NULL pour déterminer si l’un des champs est impropre.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le membre de données de champ spécifié a changé depuis l’appel de `AddNew` ou `Edit`; Sinon, 0.

### <a name="remarks"></a>Notes

Les données de tous les membres de données de champ non modifiés seront transférées vers l’enregistrement sur la source de données lorsque l’enregistrement actif est mis à jour par un appel à la fonction membre [Update](#update) de `CRecordset` (suite à un appel à `Edit` ou `AddNew`).

> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les recordsets qui utilisent l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, `IsFieldDirty` retourne toujours la valeur FALSe et entraîne l’échec d’une assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

L’appel de `IsFieldDirty` réinitialise les effets des appels précédents à [SetFieldDirty](#setfielddirty) , car l’état de modification du champ est réévalué. Dans le cas `AddNew`, si la valeur du champ actuel diffère de la valeur Pseudo-null, l’état du champ est défini sur modifié. Dans le cas `Edit`, si la valeur de champ est différente de la valeur mise en cache, l’état du champ est défini sur Dirty.

`IsFieldDirty` est implémenté par le biais de [DoFieldExchange](#dofieldexchange).

Pour plus d’informations sur l’indicateur de modification, consultez l’article [Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

##  <a name="isfieldnull"></a>CRecordset :: IsFieldNull

Retourne une valeur différente de zéro si le champ spécifié dans l’enregistrement actif est null (aucune valeur).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
Pointeur vers le membre de données de champ dont vous souhaitez vérifier l’État, ou NULL pour déterminer si l’un des champs a la valeur null.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le membre de données de champ spécifié est marqué comme null ; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour déterminer si le membre de données de champ spécifié d’un jeu d’enregistrements a été marqué comme null. (Dans la terminologie de base de données, null signifie « aucune valeur » et n’est pas identique C++à null dans.) Si un membre de données de champ est marqué comme null, il est interprété comme une colonne de l’enregistrement actif pour lequel il n’y a aucune valeur.

> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les recordsets qui utilisent l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, `IsFieldNull` retourne toujours la valeur FALSe et entraîne l’échec d’une assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull` est implémenté par le biais de [DoFieldExchange](#dofieldexchange).

##  <a name="isfieldnullable"></a>CRecordset :: IsFieldNullable

Retourne une valeur différente de zéro si le champ spécifié dans l’enregistrement actif peut être défini sur null (sans valeur).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
Pointeur vers le membre de données de champ dont vous souhaitez vérifier l’État, ou NULL pour déterminer si l’un des champs peut être défini sur une valeur null.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour déterminer si le membre de données de champ spécifié est « Nullable » (peut être défini sur une valeur null ; C++ La valeur NULL n’est pas la même que la valeur null, qui, dans la terminologie de base de données, signifie « aucune valeur »).

> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `IsFieldNullable`. Au lieu de cela, appelez la fonction membre [GetODBCFieldInfo](#getodbcfieldinfo) pour déterminer si un champ peut être défini sur une valeur null. Notez que vous pouvez toujours appeler `GetODBCFieldInfo`, que vous ayez implémenté l’extraction de lignes en bloc ou non. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Un champ qui ne peut pas être null doit avoir une valeur. Si vous tentez d’affecter la valeur null à un tel champ lors de l’ajout ou de la mise à jour d’un enregistrement, la source de données rejette l’ajout ou la mise à jour, et la [mise à jour](#update) lève une exception. L’exception se produit lorsque vous appelez `Update`, et non lorsque vous appelez [SetFieldNull](#setfieldnull).

L’utilisation de NULL pour le premier argument de la fonction applique la fonction uniquement à `outputColumn` champs, et non `param` champs. Par exemple, l’appel

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

définit uniquement les champs de `outputColumn` sur NULL ; les champs de `param` ne seront pas affectés.

Pour travailler sur des champs de `param`, vous devez fournir l’adresse réelle des `param` individuels que vous souhaitez utiliser, par exemple :

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Cela signifie que vous ne pouvez pas affecter la valeur NULL à tous les champs de `param`, comme vous pouvez le faire avec `outputColumn` champs.

`IsFieldNullable` est implémenté par le biais de [DoFieldExchange](#dofieldexchange).

##  <a name="isopen"></a>CRecordset :: IsOpen

Détermine si le jeu d’enregistrements est déjà ouvert.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction membre [Open](#open) ou [Requery](#requery) de l’objet Recordset a déjà été appelée et que le Recordset n’a pas été fermé ; Sinon, 0.

##  <a name="m_hstmt"></a>CRecordset :: m_hstmt

Contient un handle vers la structure de données de l’instruction ODBC, de type HSTMT, associée au Recordset.

### <a name="remarks"></a>Notes

Chaque requête à une source de données ODBC est associée à un HSTMT.

> [!CAUTION]
>  N’utilisez pas `m_hstmt` avant l’appel de la méthode [Open](#open) .

Normalement, vous n’avez pas besoin d’accéder directement à HSTMT, mais vous pouvez en avoir besoin pour l’exécution directe des instructions SQL. La fonction membre `ExecuteSQL` de la classe `CDatabase` fournit un exemple d’utilisation de `m_hstmt`.

##  <a name="m_nfields"></a>CRecordset :: m_nFields

Contient le nombre de membres de données de champ dans la classe Recordset ; autrement dit, le nombre de colonnes sélectionnées par le Recordset de la source de données.

### <a name="remarks"></a>Notes

Le constructeur de la classe Recordset doit initialiser `m_nFields` avec le nombre correct. Si vous n’avez pas implémenté l’extraction de lignes en bloc, ClassWizard écrit cette initialisation pour vous quand vous l’utilisez pour déclarer votre classe de Recordset. Vous pouvez également l’écrire manuellement.

L’infrastructure utilise ce nombre pour gérer l’interaction entre les membres de données de champ et les colonnes correspondantes de l’enregistrement actuel sur la source de données.

> [!CAUTION]
>  Ce nombre doit correspondre au nombre de colonnes de sortie inscrites dans `DoFieldExchange` ou `DoBulkFieldExchange` après un appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) avec le paramètre `CFieldExchange::outputColumn`.

Vous pouvez lier des colonnes de manière dynamique, comme expliqué dans l’article « Recordset : liaison dynamique des colonnes de données ». Dans ce cas, vous devez augmenter le nombre de `m_nFields` pour refléter le nombre d’appels de fonction RFX ou RFX en bloc dans votre fonction membre `DoFieldExchange` ou `DoBulkFieldExchange` pour les colonnes à liaison dynamique.

Pour plus d’informations, consultez les articles [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) et [Recordset : récupération d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

Consultez l’article [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md).

##  <a name="m_nparams"></a>CRecordset :: m_nParams

Contient le nombre de membres de données de paramètre dans la classe Recordset ; autrement dit, le nombre de paramètres transmis avec la requête du Recordset.

### <a name="remarks"></a>Notes

Si votre classe de Recordset contient des membres de données de paramètre, le constructeur de la classe doit initialiser `m_nParams` avec le nombre correct. La valeur de `m_nParams` par défaut est 0. Si vous ajoutez des membres de données de paramètre (que vous devez effectuer manuellement), vous devez également ajouter manuellement une initialisation dans le constructeur de classe pour refléter le nombre de paramètres (qui doit être au moins aussi grand que le nombre d’espaces réservés «» dans votre `m_strFilter` ou `m_strSort` chaîne).

L’infrastructure utilise ce nombre lorsqu’il paramètre la requête du Recordset.

> [!CAUTION]
>  Ce nombre doit correspondre au nombre de « params » inscrits dans `DoFieldExchange` ou `DoBulkFieldExchange` après un appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) avec la valeur de paramètre `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`ou `CFieldExchange::inoutParam`.

### <a name="example"></a>Exemple

  Consultez les articles [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) et [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md).

##  <a name="m_pdatabase"></a>CRecordset :: m_pDatabase

Contient un pointeur vers l’objet `CDatabase` par le biais duquel le Recordset est connecté à une source de données.

### <a name="remarks"></a>Notes

Cette variable est définie de deux manières. En général, vous transmettez un pointeur vers un objet `CDatabase` déjà connecté quand vous construisez l’objet Recordset. Si vous transmettez une valeur NULL à la place, `CRecordset` crée un objet `CDatabase` pour vous et le connecte. Dans les deux cas, `CRecordset` stocke le pointeur dans cette variable.

Normalement, il n’est pas nécessaire d’utiliser directement le pointeur stocké dans `m_pDatabase`. Toutefois, si vous écrivez vos propres extensions dans `CRecordset`, vous devrez peut-être utiliser le pointeur. Par exemple, vous pouvez avoir besoin du pointeur si vous levez vos propres `CDBException`s. Vous pouvez également en avoir besoin si vous devez effectuer une opération à l’aide du même `CDatabase` objet, par exemple en exécutant des transactions, en définissant des délais d’attente, ou en appelant la fonction membre `ExecuteSQL` de la classe `CDatabase` pour exécuter des instructions SQL directement.

##  <a name="m_strfilter"></a>CRecordset :: m_strFilter

Après avoir construit l’objet Recordset, mais avant d’appeler sa fonction membre `Open`, utilisez ce membre de données pour stocker un `CString` contenant une clause SQL **Where** .

### <a name="remarks"></a>Notes

Le recordset utilise cette chaîne pour contraindre (ou filtrer) les enregistrements qu’il sélectionne lors de l’appel `Open` ou `Requery`. Cela est utile pour sélectionner un sous-ensemble d’enregistrements, par exemple « tous les commerciaux basés en Californie » (« State = CA »). La syntaxe SQL ODBC pour une clause **Where** est

`WHERE search-condition`

Notez que vous n’incluez pas le mot clé **Where** dans votre chaîne. Le Framework le fournit.

Vous pouvez également paramétrer votre chaîne de filtre en plaçant des espaces réservés «» dans celle-ci, en déclarant un membre de données de paramètre dans votre classe pour chaque espace réservé et en passant des paramètres au jeu d’enregistrements au moment de l’exécution. Cela vous permet de construire le filtre au moment de l’exécution. Pour plus d’informations, consultez l’article [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Pour plus d’informations sur les clauses **Where** SQL, consultez l’article [SQL](../../data/odbc/sql.md). Pour plus d’informations sur la sélection et le filtrage des enregistrements, consultez l’article [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>CRecordset :: m_strSort

Après avoir construit l’objet Recordset, mais avant d’appeler sa fonction membre `Open`, utilisez ce membre de données pour stocker un `CString` contenant une clause **order by** SQL.

### <a name="remarks"></a>Notes

Le recordset utilise cette chaîne pour trier les enregistrements qu’il sélectionne lors de l’appel `Open` ou `Requery`. Vous pouvez utiliser cette fonctionnalité pour trier un jeu d’enregistrements sur une ou plusieurs colonnes. La syntaxe SQL ODBC pour une clause **order by** est

`ORDER BY sort-specification [, sort-specification]...`

où une spécification de tri est un entier ou un nom de colonne. Vous pouvez également spécifier l’ordre croissant ou décroissant (l’ordre est croissant par défaut) en ajoutant « ASC » ou « DESC » à la liste de colonnes dans la chaîne de tri. Les enregistrements sélectionnés sont d’abord triés en fonction de la première colonne répertoriée, puis du deuxième, et ainsi de suite. Par exemple, vous pouvez trier un jeu d’enregistrements « Customers » par nom, puis par prénom. Le nombre de colonnes que vous pouvez répertorier dépend de la source de données. Pour plus d’informations, consultez la SDK Windows.

Notez que vous n’incluez pas le mot clé **order by** dans votre chaîne. Le Framework le fournit.

Pour plus d’informations sur les clauses SQL, consultez l’article [SQL](../../data/odbc/sql.md). Pour plus d’informations sur le tri des enregistrements, consultez l’article [Recordset : tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>CRecordset :: Move

Déplace le pointeur d’enregistrement actif dans le Recordset, vers l’avant ou vers l’arrière.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Paramètres

*nRows*<br/>
Nombre de lignes à déplacer vers l’avant ou vers l’arrière. Les valeurs positives se déplacent vers la fin de l’ensemble d’enregistrements. Les valeurs négatives se déplacent vers l’arrière, vers le début.

*wFetchType*<br/>
Détermine l’ensemble de lignes que `Move` doit extraire. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Si vous transmettez la valeur 0 à *nrows*, `Move` actualise l’enregistrement en cours ; `Move` met fin à tout mode de `AddNew` ou de `Edit` en cours, et restaure la valeur de l’enregistrement actif avant `AddNew` ou `Edit` a été appelé.

> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Pour plus d’informations, consultez [CRecordset :: IsDeleted](#isdeleted) . Lorsque vous ouvrez une `CRecordset` avec l’option `skipDeletedRecords` définie, `Move` déclare si le paramètre *nrows* a la valeur 0. Ce comportement empêche l’actualisation des lignes qui sont supprimées par d’autres applications clientes à l’aide des mêmes données. Consultez le paramètre *valeur dwOption* dans [Open](#open) pour obtenir une description de `skipDeletedRecords`.

`Move` repositionne le Recordset par ensembles de lignes. En fonction des valeurs de *nrows* et *wFetchType*, `Move` extrait l’ensemble de lignes approprié, puis définit le premier enregistrement dans ce jeu de lignes comme l’enregistrement actif. Si vous n’avez pas implémenté l’extraction de lignes en bloc, la taille de l’ensemble de lignes est toujours 1. Lors de l’extraction d’un ensemble de lignes, `Move` appelle directement la fonction membre [CheckRowsetError](#checkrowseterror) pour gérer les erreurs résultant de l’extraction.

Selon les valeurs que vous transmettez, `Move` équivaut à d’autres fonctions membres `CRecordset`. En particulier, la valeur de *wFetchType* peut indiquer une fonction membre qui est plus intuitive et souvent la méthode préférée pour déplacer l’enregistrement actuel.

Le tableau suivant répertorie les valeurs possibles pour *wFetchType*, l’ensemble de lignes que `Move` extrait en fonction de *wFetchType* et *nrows*, et toute fonction membre équivalente correspondant à *wFetchType*.

|wFetchType|Ensemble de lignes extrait|Fonction membre équivalente|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (valeur par défaut)|L’ensemble de lignes démarrant *nrows* ligne (s) à partir de la première ligne de l’ensemble de lignes actif.||
|SQL_FETCH_NEXT|Ensemble de lignes suivant ; *nrows* est ignoré.|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|Ensemble de lignes précédent ; *nrows* est ignoré.|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|Premier ensemble de lignes dans le jeu d’enregistrements ; *nrows* est ignoré.|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|Dernier ensemble de lignes complet dans le Recordset ; *nrows* est ignoré.|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|Si *nRows* > 0, l’ensemble de lignes démarre *nrows* ligne (s) à partir du début de l’ensemble d’enregistrements. Si *nRows* < 0, l’ensemble de lignes démarre *nrows* ligne (s) à partir de la fin du Recordset. Si *nrows* = 0, une condition de début de fichier (BOF) est retournée.|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Ensemble de lignes à partir de la ligne dont la valeur de signet correspond à *nrows*.|[SetBookmark](#setbookmark)|

> [!NOTE]
>  Pour les recordsets avant uniquement, `Move` est valide uniquement avec une valeur de SQL_FETCH_NEXT pour *wFetchType*.

> [!CAUTION]
>  L’appel de `Move` lève une exception si le Recordset n’a pas d’enregistrement. Pour déterminer si le Recordset contient des enregistrements, appelez [IsBOF](#isbof) et [IsEOF](#iseof).

> [!NOTE]
>  Si vous avez défilé au-delà du début ou de la fin de l’ensemble d’enregistrements (`IsBOF` ou `IsEOF` retourne une valeur différente de zéro), l’appel d’une fonction `Move` lèvera probablement une `CDBException`. Par exemple, si `IsEOF` retourne une valeur différente de zéro et que `IsBOF` ne le fait pas, `MoveNext` lèvera une exception, mais `MovePrev` ne le sera pas.

> [!NOTE]
>  Si vous appelez `Move` lors de la mise à jour ou de l’ajout de l’enregistrement actif, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation dans les jeux d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour obtenir des informations connexes, consultez la fonction API ODBC `SQLExtendedFetch` dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>CRecordset :: MoveFirst

Crée le premier enregistrement dans le premier ensemble de lignes de l’enregistrement actif.

```
void MoveFirst();
```

### <a name="remarks"></a>Notes

Indépendamment de l’implémentation de l’extraction de lignes en bloc, il s’agit toujours du premier enregistrement dans le jeu d’enregistrements.

Vous n’avez pas besoin d’appeler `MoveFirst` immédiatement après avoir ouvert le Recordset. À ce moment-là, le premier enregistrement (le cas échéant) est automatiquement l’enregistrement en cours.

> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.

> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Pour plus d’informations, consultez la fonction membre [IsDeleted](#isdeleted) .

> [!CAUTION]
>  L’appel de l’une des fonctions `Move` lève une exception si le Recordset n’a pas d’enregistrement. Pour déterminer si le Recordset contient des enregistrements, appelez `IsBOF` et `IsEOF`.

> [!NOTE]
>  Si vous appelez l’une des fonctions `Move` lors de la mise à jour ou de l’ajout de l’enregistrement actif, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation dans les jeux d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsBOF](#isbof).

##  <a name="movelast"></a>CRecordset :: MoveLast

Crée le premier enregistrement dans le dernier ensemble de lignes complet de l’enregistrement en cours.

```
void MoveLast();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas implémenté l’extraction de lignes en bloc, votre jeu d’enregistrements a une taille d’ensemble de lignes de 1, donc `MoveLast` se déplace simplement vers le dernier enregistrement du Recordset.

> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.

> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Pour plus d’informations, consultez la fonction membre [IsDeleted](#isdeleted) .

> [!CAUTION]
>  L’appel de l’une des fonctions `Move` lève une exception si le Recordset n’a pas d’enregistrement. Pour déterminer si le Recordset contient des enregistrements, appelez `IsBOF` et `IsEOF`.

> [!NOTE]
>  Si vous appelez l’une des fonctions `Move` lors de la mise à jour ou de l’ajout de l’enregistrement actif, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation dans les jeux d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsBOF](#isbof).

##  <a name="movenext"></a>CRecordset :: MoveNext

Fait du premier enregistrement du jeu de lignes suivant l’enregistrement en cours.

```
void MoveNext();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas implémenté l’extraction de lignes en bloc, votre jeu d’enregistrements a une taille d’ensemble de lignes de 1, donc `MoveNext` passe simplement à l’enregistrement suivant.

> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Pour plus d’informations, consultez la fonction membre [IsDeleted](#isdeleted) .

> [!CAUTION]
>  L’appel de l’une des fonctions `Move` lève une exception si le Recordset n’a pas d’enregistrement. Pour déterminer si le Recordset contient des enregistrements, appelez `IsBOF` et `IsEOF`.

> [!NOTE]
>  Il est également recommandé d’appeler `IsEOF` avant d’appeler `MoveNext`. Par exemple, si vous avez défilé au-delà de la fin du Recordset, `IsEOF` retourne une valeur différente de zéro ; un appel ultérieur à `MoveNext` lèvera une exception.

> [!NOTE]
>  Si vous appelez l’une des fonctions `Move` lors de la mise à jour ou de l’ajout de l’enregistrement actif, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation dans les jeux d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsBOF](#isbof).

##  <a name="moveprev"></a>CRecordset :: MovePrev

Fait du premier enregistrement dans l’ensemble de lignes précédent l’enregistrement en cours.

```
void MovePrev();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas implémenté l’extraction de lignes en bloc, votre jeu d’enregistrements a une taille d’ensemble de lignes de 1, donc `MovePrev` se déplace simplement vers l’enregistrement précédent.

> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.

> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Pour plus d’informations, consultez la fonction membre [IsDeleted](#isdeleted) .

> [!CAUTION]
>  L’appel de l’une des fonctions `Move` lève une exception si le Recordset n’a pas d’enregistrement. Pour déterminer si le Recordset contient des enregistrements, appelez `IsBOF` et `IsEOF`.

> [!NOTE]
>  Il est également recommandé d’appeler `IsBOF` avant d’appeler `MovePrev`. Par exemple, si vous avez défilé avant le début de l’ensemble d’enregistrements, `IsBOF` retourne une valeur différente de zéro ; un appel ultérieur à `MovePrev` lèvera une exception.

> [!NOTE]
>  Si vous appelez l’une des fonctions `Move` lors de la mise à jour ou de l’ajout de l’enregistrement actif, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation dans les jeux d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsBOF](#isbof).

##  <a name="onsetoptions"></a>CRecordset :: OnSetOptions

Appelé pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*risquent*<br/>
HSTMT de l’instruction ODBC dont les options doivent être définies.

### <a name="remarks"></a>Notes

Appelez `OnSetOptions` pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée. L’infrastructure appelle cette fonction membre pour définir les options initiales du Recordset. `OnSetOptions` détermine la prise en charge de la source de données pour les curseurs de défilement et pour l’accès concurrentiel de curseur et définit les options du Recordset en conséquence. (Tandis que `OnSetOptions` est utilisé pour les opérations de sélection, `OnSetUpdateOptions` est utilisé pour les opérations de mise à jour.)

Remplacez `OnSetOptions` pour définir des options spécifiques au pilote ou à la source de données. Par exemple, si votre source de données prend en charge l’ouverture pour un accès exclusif, vous pouvez remplacer `OnSetOptions` pour tirer parti de cette capacité.

Pour plus d’informations sur les curseurs, consultez l’article [ODBC](../../data/odbc/odbc-basics.md).

##  <a name="onsetupdateoptions"></a>CRecordset :: OnSetUpdateOptions

Appelé pour définir les options (utilisées lors de la mise à jour) pour l’instruction ODBC spécifiée.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*risquent*<br/>
HSTMT de l’instruction ODBC dont les options doivent être définies.

### <a name="remarks"></a>Notes

Appelez `OnSetUpdateOptions` pour définir les options (utilisées lors de la mise à jour) pour l’instruction ODBC spécifiée. L’infrastructure appelle cette fonction membre après avoir créé un HSTMT pour mettre à jour les enregistrements d’un Recordset. (Tandis que `OnSetOptions` est utilisé pour les opérations de sélection, `OnSetUpdateOptions` est utilisé pour les opérations de mise à jour.) `OnSetUpdateOptions` détermine la prise en charge de la source de données pour les curseurs de défilement et pour l’accès concurrentiel de curseur et définit les options du Recordset en conséquence.

Remplacez `OnSetUpdateOptions` pour définir les options d’une instruction ODBC avant l’utilisation de cette instruction pour accéder à une base de données.

Pour plus d’informations sur les curseurs, consultez l’article [ODBC](../../data/odbc/odbc-basics.md).

##  <a name="open"></a>CRecordset :: Open

Ouvre le Recordset en extrayant la table ou en exécutant la requête représentée par le Recordset.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Paramètres

*nOpenType*<br/>
Acceptez la valeur par défaut, AFX_DB_USE_DEFAULT_TYPE ou utilisez l’une des valeurs suivantes à partir de la `enum OpenType`:

- `CRecordset::dynaset` un jeu d’enregistrements avec défilement bidirectionnel. L’appartenance et la classification des enregistrements sont déterminées lors de l’ouverture du Recordset, mais les modifications apportées par d’autres utilisateurs aux valeurs de données sont visibles après une opération d’extraction. Les feuilles de réponse dynamiques sont également appelées recordsets pilotés par keyset.

- `CRecordset::snapshot` un jeu d’enregistrements statique avec défilement bidirectionnel. L’appartenance et la classification des enregistrements sont déterminées lors de l’ouverture du Recordset. les valeurs de données sont déterminées lors de l’extraction des enregistrements. Les modifications apportées par d’autres utilisateurs ne sont pas visibles tant que le jeu d’enregistrements n’est pas fermé, puis rouvert.

- `CRecordset::dynamic` un jeu d’enregistrements avec défilement bidirectionnel. Les modifications apportées par d’autres utilisateurs aux valeurs d’appartenance, de classement et de données sont visibles après une opération d’extraction. Notez que de nombreux pilotes ODBC ne prennent pas en charge ce type de jeu d’enregistrements.

- `CRecordset::forwardOnly` un jeu d’enregistrements en lecture seule avec défilement avant uniquement.

   Par `CRecordset`, la valeur par défaut est `CRecordset::snapshot`. Le mécanisme de valeur par défaut permet aux C++ assistants visuels d’interagir avec les `CRecordset` ODBC et DAO `CDaoRecordset`, qui ont des valeurs par défaut différentes.

Pour plus d’informations sur ces types d’ensembles d’enregistrements, consultez l’article [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour obtenir des informations connexes, consultez l’article « utilisation des curseurs de bloc et de défilement » dans le SDK Windows.

> [!CAUTION]
>  Si le type demandé n’est pas pris en charge, le Framework lève une exception.

*lpszSQL*<br/>
Pointeur de chaîne contenant l’un des éléments suivants :

- Pointeur NULL.

- Nom d'une table.

- Une instruction SQL **Select** (éventuellement avec une clause SQL **Where** ou **order by** ).

- Instruction **Call** spécifiant le nom d’une requête prédéfinie (procédure stockée). Veillez à ne pas insérer d’espace entre l’accolade et le mot clé **Call** .

Pour plus d’informations sur cette chaîne, consultez le tableau et la description du rôle de ClassWizard dans la section [Notes](#remarks) .

> [!NOTE]
>  L’ordre des colonnes dans votre jeu de résultats doit correspondre à l’ordre des appels de fonction RFX ou RFX en bloc dans votre substitution de fonction [DoFieldExchange](#dofieldexchange) ou [DoBulkFieldExchange](#dobulkfieldexchange) .

*dwOptions*<br/>
Masque de masque qui peut spécifier une combinaison des valeurs indiquées ci-dessous. Certaines d’entre elles s’excluent mutuellement. La valeur par défaut est **None**.

- `CRecordset::none` aucune option n’est définie. Cette valeur de paramètre s’exclut mutuellement avec toutes les autres valeurs. Par défaut, le jeu d’enregistrements peut être mis à jour avec [Edit](#edit) ou [Delete](#delete) et permet d’ajouter de nouveaux enregistrements avec [AddNew](#addnew). La mise à jour dépend de la source de données, ainsi que de l’option *nOpenType* que vous spécifiez. L’optimisation pour les ajouts en bloc n’est pas disponible. L’extraction de lignes en bloc ne sera pas implémentée. Les enregistrements supprimés ne seront pas ignorés lors de la navigation dans l’ensemble d’enregistrements. Les signets ne sont pas disponibles. La vérification automatique des champs de modification est implémentée.

- `CRecordset::appendOnly` n’autorisent pas `Edit` ou `Delete` sur le Recordset. Autoriser uniquement les `AddNew`. Cette option s’exclut mutuellement avec `CRecordset::readOnly`.

- `CRecordset::readOnly` ouvrir le jeu d’enregistrements en lecture seule. Cette option s’exclut mutuellement avec `CRecordset::appendOnly`.

- `CRecordset::optimizeBulkAdd` utiliser une instruction SQL préparée pour optimiser l’ajout de plusieurs enregistrements à la fois. S’applique uniquement si vous n’utilisez pas la fonction API ODBC `SQLSetPos` pour mettre à jour le Recordset. La première mise à jour détermine quels champs sont marqués comme étant modifiés. Cette option s’exclut mutuellement avec `CRecordset::useMultiRowFetch`.

- `CRecordset::useMultiRowFetch` implémenter l’extraction de lignes en bloc pour permettre l’extraction de plusieurs lignes dans une seule opération d’extraction. Il s’agit d’une fonctionnalité avancée conçue pour améliorer les performances. Toutefois, l’échange de champs d’enregistrements en bloc n’est pas pris en charge par ClassWizard. Cette option s’exclut mutuellement avec `CRecordset::optimizeBulkAdd`. Notez que si vous spécifiez `CRecordset::useMultiRowFetch`, l’option `CRecordset::noDirtyFieldCheck` est activée automatiquement (la double mise en mémoire tampon n’est pas disponible); sur les recordsets avant uniquement, l’option `CRecordset::useExtendedFetch` est activée automatiquement. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords` ignorer tous les enregistrements supprimés lors de la navigation dans le jeu d’enregistrements. Cela ralentit les performances dans certaines extractions relatives. Cette option n’est pas valide sur les recordsets avant uniquement. Si vous appelez [Move](#move) avec le paramètre *nrows* défini sur 0, et l’option `CRecordset::skipDeletedRecords` définie, `Move` déclarera. Notez que `CRecordset::skipDeletedRecords` est semblable à la *compression du pilote*, ce qui signifie que les lignes supprimées sont supprimées du Recordset. Toutefois, si votre pilote compresse des enregistrements, il n’ignore que les enregistrements que vous supprimez. elle n’ignore pas les enregistrements supprimés par d’autres utilisateurs tant que le jeu d’enregistrements est ouvert. `CRecordset::skipDeletedRecords` ignore les lignes supprimées par d’autres utilisateurs.

- `CRecordset::useBookmarks` pouvez utiliser des signets sur le Recordset, s’ils sont pris en charge. Les signets ralentissent la récupération des données mais améliorent les performances de navigation dans les données. Non valide sur les recordsets avant uniquement. Pour plus d’informations, consultez l’article [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck` désactiver la vérification automatique des champs incorrects (double mise en mémoire tampon). Cela permet d’améliorer les performances. Toutefois, vous devez marquer manuellement les champs comme modifiés en appelant les fonctions membres `SetFieldDirty` et `SetFieldNull`. Notez que la double mise en mémoire tampon dans la classe `CRecordset` est semblable à la double mise en mémoire tampon dans la classe `CDaoRecordset`. Toutefois, dans `CRecordset`, vous ne pouvez pas activer la double mise en mémoire tampon sur des champs individuels. vous pouvez l’activer pour tous les champs ou le désactiver pour tous les champs. Notez que si vous spécifiez l’option `CRecordset::useMultiRowFetch`, `CRecordset::noDirtyFieldCheck` sera automatiquement activé. Toutefois, `SetFieldDirty` et `SetFieldNull` ne peuvent pas être utilisés sur les jeux d’enregistrements qui implémentent l’extraction de lignes en bloc.

- `CRecordset::executeDirect` n’utilisez pas d’instruction SQL préparée. Pour améliorer les performances, spécifiez cette option si la fonction membre `Requery` ne sera jamais appelée.

- `CRecordset::useExtendedFetch` implémenter `SQLExtendedFetch` au lieu de `SQLFetch`. Cela est conçu pour l’implémentation de l’extraction de lignes en bloc sur les recordsets avant uniquement. Si vous spécifiez l’option `CRecordset::useMultiRowFetch` sur un jeu d’enregistrements avant uniquement, `CRecordset::useExtendedFetch` sera automatiquement activé.

- `CRecordset::userAllocMultiRowBuffers` l’utilisateur va allouer des tampons de stockage pour les données. Utilisez cette option conjointement avec `CRecordset::useMultiRowFetch` si vous souhaitez allouer votre propre stockage. dans le cas contraire, le Framework alloue automatiquement le stockage nécessaire. Pour plus d’informations, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Notez que la spécification d' `CRecordset::userAllocMultiRowBuffers` sans spécifier `CRecordset::useMultiRowFetch` entraîne l’échec d’une assertion.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet `CRecordset` a été ouvert avec succès ; Sinon, 0 si [CDatabase :: Open](../../mfc/reference/cdatabase-class.md#open) (s’il est appelé) retourne 0.

### <a name="remarks"></a>Notes

Vous devez appeler cette fonction membre pour exécuter la requête définie par le Recordset. Avant d’appeler `Open`, vous devez construire l’objet Recordset.

La connexion de cet ensemble d’enregistrements à la source de données dépend de la façon dont vous construisez le Recordset avant d’appeler `Open`. Si vous transmettez un objet [CDatabase](../../mfc/reference/cdatabase-class.md) au constructeur Recordset qui n’a pas été connecté à la source de données, cette fonction membre utilise [GetDefaultConnect](#getdefaultconnect) pour tenter d’ouvrir l’objet de base de données. Si vous transmettez la valeur NULL au constructeur Recordset, le constructeur construit un objet `CDatabase` pour vous, et `Open` tente de connecter l’objet de base de données. Pour plus d’informations sur la fermeture de l’ensemble d’enregistrements et de la connexion dans ces différentes circonstances, consultez [Close](#close).

> [!NOTE]
>  L’accès à une source de données via un objet `CRecordset` est toujours partagé. Contrairement à la classe `CDaoRecordset`, vous ne pouvez pas utiliser un objet `CRecordset` pour ouvrir une source de données avec un accès exclusif.

Lorsque vous appelez `Open`, une requête, généralement une instruction SQL **Select** , sélectionne des enregistrements en fonction des critères indiqués dans le tableau suivant.

|Valeur du paramètre lpszSQL|Les enregistrements sélectionnés sont déterminés par|Exemple|
|------------------------------------|----------------------------------------|-------------|
|NULL|Chaîne retournée par `GetDefaultSQL`.||
|Nom de la table SQL|Toutes les colonnes de la liste de tables dans `DoFieldExchange` ou `DoBulkFieldExchange`.|`"Customer"`|
|Nom de la requête prédéfinie (procédure stockée)|Colonnes que la requête est définie pour retourner.|`"{call OverDueAccts}"`|
|**Sélectionner** une colonne dans la liste **des** tables|Colonnes spécifiées de la ou des tables spécifiées.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  Veillez à ne pas insérer d’espace blanc supplémentaire dans votre chaîne SQL. Par exemple, si vous insérez un espace entre l’accolade et le mot clé **Call** , MFC interprète la chaîne SQL comme un nom de table et l’incorpore dans une instruction **Select** , ce qui entraîne la levée d’une exception. De même, si votre requête prédéfinie utilise un paramètre de sortie, n’insérez pas d’espace entre l’accolade et le symbole «». Enfin, vous ne devez pas insérer d’espace avant l’accolade dans une instruction **Call** ou avant le mot clé **Select** dans une instruction **Select** .

La procédure habituelle consiste à passer la valeur NULL à `Open`; dans ce cas, `Open` appelle [GetDefaultSQL](#getdefaultsql). Si vous utilisez une classe de `CRecordset` dérivée, `GetDefaultSQL` indique le ou les noms de tables que vous avez spécifiés dans ClassWizard. À la place, vous pouvez spécifier d’autres informations dans le paramètre `lpszSQL`.

Tout ce que vous transmettez, `Open` construit une chaîne SQL finale pour la requête (la chaîne peut avoir des clauses SQL **Where** et **order by** ajoutées à la chaîne `lpszSQL` que vous avez transmise), puis exécute la requête. Vous pouvez examiner la chaîne construite en appelant [GetSQL](#getsql) après avoir appelé `Open`. Pour plus d’informations sur la façon dont le recordset construit une instruction SQL et sélectionne des enregistrements, consultez l’article [Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Les données membres de champ de votre classe Recordset sont liées aux colonnes des données sélectionnées. Si des enregistrements sont renvoyés, le premier enregistrement devient l’enregistrement en cours.

Si vous souhaitez définir des options pour l’ensemble d’enregistrements, telles qu’un filtre ou un tri, spécifiez-les après avoir construit l’objet Recordset, mais avant d’appeler `Open`. Si vous souhaitez actualiser les enregistrements dans le jeu d’enregistrements une fois que le Recordset est déjà ouvert, appelez [Requery](#requery).

Pour plus d’informations, y compris des exemples supplémentaires, consultez les articles [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset : comment les recordsets sélectionnent les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)et [Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Exemple

Les exemples de code suivants illustrent différentes formes de l’appel de `Open`.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>CRecordset :: RefreshRowset

Met à jour les données et l’état d’une ligne dans l’ensemble de lignes actif.

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Paramètres

*wRow*<br/>
Position de base 1 d’une ligne dans l’ensemble de lignes actif. Cette valeur peut être comprise entre zéro et la taille de l’ensemble de lignes.

*wLockType*<br/>
Valeur indiquant comment verrouiller la ligne après qu’elle a été actualisée. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Si vous transmettez une valeur de zéro pour *wRow*, chaque ligne de l’ensemble de lignes sera actualisée.

Pour utiliser `RefreshRowset`, vous devez avoir implémenté l’extraction de lignes en bloc en spécifiant l’option `CRecordset::useMulitRowFetch` dans la fonction membre [Open](#open) .

`RefreshRowset` appelle la fonction API ODBC `SQLSetPos`. Le paramètre *wLockType* spécifie l’état de verrouillage de la ligne après l’exécution de `SQLSetPos`. Le tableau suivant décrit les valeurs possibles pour *wLockType*.

|wLockType|Description|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (valeur par défaut)|Le pilote ou la source de données garantit que la ligne est dans le même état verrouillé ou déverrouillé qu’avant l’appel de `RefreshRowset`.|
|SQL_LOCK_EXCLUSIVE|Le pilote ou la source de données verrouille la ligne en mode exclusif. Toutes les sources de données ne prennent pas en charge ce type de verrou.|
|SQL_LOCK_UNLOCK|Le pilote ou la source de données déverrouille la ligne. Toutes les sources de données ne prennent pas en charge ce type de verrou.|

Pour plus d’informations sur `SQLSetPos`, consultez la SDK Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="requery"></a>CRecordset :: Requery

Reconstruit (actualise) un jeu d’enregistrements.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le jeu d’enregistrements a été reconstruit avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Si des enregistrements sont renvoyés, le premier enregistrement devient l’enregistrement en cours.

Pour que le recordset reflète les ajouts et les suppressions que vous ou d’autres utilisateurs apportez à la source de données, vous devez reconstruire le Recordset en appelant `Requery`. Si le Recordset est une feuille de réponse dynamique, il reflète automatiquement les mises à jour que vous ou d’autres utilisateurs apportez à ses enregistrements existants (mais pas les ajouts). Si le jeu d’enregistrements est un instantané, vous devez appeler `Requery` pour refléter les modifications apportées par d’autres utilisateurs, ainsi que les ajouts et les suppressions.

Pour une feuille de réponse dynamique ou un instantané, appelez `Requery` chaque fois que vous souhaitez reconstruire le recordset à l’aide d’un nouveau filtre ou d’un nouveau tri, ou de nouvelles valeurs de paramètres. Définissez la nouvelle propriété de filtre ou de tri en assignant de nouvelles valeurs à `m_strFilter` et `m_strSort` avant d’appeler `Requery`. Définissez de nouveaux paramètres en assignant de nouvelles valeurs aux membres de données de paramètre avant d’appeler `Requery`. Si les chaînes de filtre et de tri ne sont pas modifiées, vous pouvez réutiliser la requête, ce qui améliore les performances.

Si la tentative de régénération du Recordset échoue, le jeu d’enregistrements est fermé. Avant d’appeler `Requery`, vous pouvez déterminer si le jeu d’enregistrements peut être interrogé en appelant la fonction membre `CanRestart`. `CanRestart` ne garantit pas que `Requery` échouera.

> [!CAUTION]
>  Appelez `Requery` uniquement après avoir appelé [Open](#open).

### <a name="example"></a>Exemple

Cet exemple reconstruit un jeu d’enregistrements pour appliquer un ordre de tri différent.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>CRecordset :: SetAbsolutePosition

Positionne le Recordset sur l’enregistrement correspondant au numéro d’enregistrement spécifié.

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Paramètres

*nRows*<br/>
Position ordinale de base 1 de l’enregistrement en cours dans le Recordset.

### <a name="remarks"></a>Notes

`SetAbsolutePosition` déplace le pointeur d’enregistrement actif en fonction de cette position ordinale.

> [!NOTE]
>  Cette fonction membre n’est pas valide sur les recordsets avant uniquement.

Pour les jeux d’enregistrements ODBC, un paramètre de position absolue de 1 fait référence au premier enregistrement dans le jeu d’enregistrements ; la valeur 0 fait référence à la position de début de fichier (BOF).

Vous pouvez également passer des valeurs négatives à `SetAbsolutePosition`. Dans ce cas, la position du Recordset est évaluée à partir de la fin de l’ensemble d’enregistrements. Par exemple, `SetAbsolutePosition( -1 )` déplace le pointeur d’enregistrement actif vers le dernier enregistrement du Recordset.

> [!NOTE]
>  La position absolue n’est pas destinée à être utilisée comme numéro d’enregistrement de substitution. Les signets sont toujours la méthode recommandée pour conserver et retourner à une position donnée, car la position d’un enregistrement change lorsque les enregistrements précédents sont supprimés. En outre, vous ne pouvez pas être certain qu’un enregistrement donné aura la même position absolue si le jeu d’enregistrements est recréé parce que l’ordre des enregistrements individuels au sein d’un jeu d’enregistrements n’est pas garanti, sauf s’il est créé avec une instruction SQL à l’aide d’une clause **order by** .

Pour plus d’informations sur la navigation dans les jeux d’enregistrements et les signets, consultez les articles [jeu d’enregistrements : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="setbookmark"></a>CRecordset :: SetBookmark

Positionne le Recordset sur l’enregistrement contenant le signet spécifié.

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Paramètres

*varBookmark*<br/>
Référence à un objet [CDBVariant](../../mfc/reference/cdbvariant-class.md) contenant la valeur de signet pour un enregistrement spécifique.

### <a name="remarks"></a>Notes

Pour déterminer si les signets sont pris en charge sur le Recordset, appelez [CanBookmark](#canbookmark). Pour rendre les signets disponibles s’ils sont pris en charge, vous devez définir l’option `CRecordset::useBookmarks` dans le paramètre *dwOptions* de la fonction membre [Open](#open) .

> [!NOTE]
>  Si les signets ne sont pas pris en charge ou ne sont pas disponibles, l’appel de `SetBookmark` entraîne la levée d’une exception. Les signets ne sont pas pris en charge sur les recordsets avant uniquement.

Pour récupérer d’abord le signet de l’enregistrement actif, appelez [GetBookmark](#getbookmark), qui enregistre la valeur de signet dans un objet `CDBVariant`. Ultérieurement, vous pouvez revenir à cet enregistrement en appelant `SetBookmark` à l’aide de la valeur de signet enregistrée.

> [!NOTE]
>  Après certaines opérations sur les jeux d’enregistrements, vous devez vérifier la persistance des signets avant d’appeler `SetBookmark`. Par exemple, si vous récupérez un signet avec `GetBookmark` puis appelez `Requery`, le signet risque de ne plus être valide. Appelez [CDatabase :: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si vous pouvez appeler `SetBookmark`en toute sécurité.

Pour plus d’informations sur les signets et la navigation dans les jeux d’enregistrements, consultez les articles [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="setfielddirty"></a>CRecordset :: SetFieldDirty

Signale un membre de données de champ du Recordset comme étant modifié ou comme étant inchangé.

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
Contient l’adresse d’un membre de données de champ dans le jeu d’enregistrements ou NULL. Si la valeur est NULL, tous les membres de données de champ dans le jeu d’enregistrements sont marqués d’un indicateur. (C++ La valeur NULL n’est pas la même que la valeur null dans la terminologie de base de données, ce qui signifie « aucune valeur ».)

*bDirty*<br/>
TRUE si le membre de données de champ doit être marqué comme « impropre » (modifié). Sinon, FALSe si le membre de données de champ doit être marqué comme « Clean » (inchangé).

### <a name="remarks"></a>Notes

Le fait de marquer les champs comme inchangés garantit que le champ n’est pas mis à jour et entraîne moins de trafic SQL.

> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les recordsets qui utilisent l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, `SetFieldDirty` entraîne l’échec d’une assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Le Framework marque les membres de données de champ modifiés pour s’assurer qu’ils seront écrits dans l’enregistrement sur la source de données par le mécanisme RFX (Record Field Exchange). La modification de la valeur d’un champ définit généralement le champ modifié automatiquement. par conséquent, vous devrez rarement appeler `SetFieldDirty` vous-même, mais vous souhaiterez peut-être également vous assurer que les colonnes seront mises à jour ou insérées de manière explicite, quelle que soit la valeur du membre de données de champ.

> [!CAUTION]
>  Appelez cette fonction membre uniquement après avoir appelé [Edit](#edit) ou [AddNew](#addnew).

L’utilisation de NULL pour le premier argument de la fonction applique la fonction uniquement à `outputColumn` champs, et non `param` champs. Par exemple, l’appel

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

définit uniquement les champs de `outputColumn` sur NULL ; les champs de `param` ne seront pas affectés.

Pour travailler sur des champs de `param`, vous devez fournir l’adresse réelle des `param` individuels que vous souhaitez utiliser, par exemple :

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Cela signifie que vous ne pouvez pas affecter la valeur NULL à tous les champs de `param`, comme vous pouvez le faire avec `outputColumn` champs.

##  <a name="setfieldnull"></a>CRecordset :: SetFieldNull

Signale un membre de données de champ du Recordset comme null (sans valeur) ou en tant que valeur non null.

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Paramètres

*va*<br/>
Contient l’adresse d’un membre de données de champ dans le jeu d’enregistrements ou NULL. Si la valeur est NULL, tous les membres de données de champ dans le jeu d’enregistrements sont marqués d’un indicateur. (C++ La valeur NULL n’est pas la même que la valeur null dans la terminologie de base de données, ce qui signifie « aucune valeur ».)

*bNull*<br/>
Valeur différente de zéro si le membre de données de champ doit être marqué comme n’ayant aucune valeur (null). Sinon, 0 si le membre de données de champ doit être marqué comme non null.

### <a name="remarks"></a>Notes

Lorsque vous ajoutez un nouvel enregistrement à un Recordset, tous les membres de données de champ sont initialement définis sur une valeur null et marqués comme « modifiés » (modifiés). Lorsque vous récupérez un enregistrement d’une source de données, ses colonnes ont déjà des valeurs ou sont null.

> [!NOTE]
>  N’appelez pas cette fonction membre sur les recordsets qui utilisent l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, l’appel de `SetFieldNull` entraîne l’échec d’une assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Si vous souhaitez spécifiquement désigner un champ de l’enregistrement actif comme n’ayant pas de valeur, appelez `SetFieldNull` avec *bNull* défini sur true pour le marquer comme étant null. Si un champ a déjà été marqué comme null et que vous souhaitez maintenant lui attribuer une valeur, il vous suffit de définir sa nouvelle valeur. Vous n’avez pas besoin de supprimer l’indicateur null avec `SetFieldNull`. Pour déterminer si le champ peut être null, appelez `IsFieldNullable`.

> [!CAUTION]
>  Appelez cette fonction membre uniquement après avoir appelé [Edit](#edit) ou [AddNew](#addnew).

L’utilisation de NULL pour le premier argument de la fonction applique la fonction uniquement à `outputColumn` champs, et non `param` champs. Par exemple, l’appel

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

définit uniquement les champs de `outputColumn` sur NULL ; les champs de `param` ne seront pas affectés.

Pour travailler sur des champs de `param`, vous devez fournir l’adresse réelle des `param` individuels que vous souhaitez utiliser, par exemple :

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Cela signifie que vous ne pouvez pas affecter la valeur NULL à tous les champs de `param`, comme vous pouvez le faire avec `outputColumn` champs.

> [!NOTE]
>  Lors de la définition de paramètres avec la valeur null, un appel à `SetFieldNull` avant l’ouverture du Recordset entraîne une assertion. Dans ce cas, appelez [SetParamNull](#setparamnull).

`SetFieldNull` est implémenté par le biais de [DoFieldExchange](#dofieldexchange).

##  <a name="setlockingmode"></a>CRecordset :: SetLockingMode

Définit le mode de verrouillage sur le verrouillage « optimiste » (valeur par défaut) ou le verrouillage « pessimiste ». Détermine la façon dont les enregistrements sont verrouillés pour les mises à jour.

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Paramètres

*nMode*<br/>
Contient l’une des valeurs suivantes de l' `enum LockMode`:

- `optimistic` le verrouillage optimiste verrouille l’enregistrement en cours de mise à jour uniquement lors de l’appel à `Update`.

- `pessimistic` le verrouillage pessimiste verrouille l’enregistrement dès que `Edit` est appelé et le maintient verrouillé jusqu’à la fin de l’appel de `Update` ou lorsque vous passez à un nouvel enregistrement.

### <a name="remarks"></a>Notes

Appelez cette fonction membre si vous devez spécifier les deux stratégies de verrouillage d’enregistrement que le recordset utilise pour les mises à jour. Par défaut, le mode de verrouillage d’un jeu d’enregistrements est `optimistic`. Vous pouvez le remplacer par une stratégie de verrouillage plus prudente `pessimistic`. Appelez `SetLockingMode` après avoir construit et ouvert l’objet Recordset, mais avant d’appeler `Edit`.

##  <a name="setparamnull"></a>CRecordset :: SetParamNull

Marque un paramètre comme null (sans valeur) ou comme étant non null.

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro du paramètre.

*bNull*<br/>
Si la valeur est TRUE (valeur par défaut), le paramètre est marqué comme null. Sinon, le paramètre est marqué comme non null.

### <a name="remarks"></a>Notes

Contrairement à [SetFieldNull](#setfieldnull), vous pouvez appeler `SetParamNull` avant d’ouvrir le jeu d’enregistrements.

`SetParamNull` est généralement utilisé avec des requêtes prédéfinies (procédures stockées).

##  <a name="setrowsetcursorposition"></a>CRecordset :: SetRowsetCursorPosition

Déplace le curseur vers une ligne de l’ensemble de lignes actif.

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Paramètres

*wRow*<br/>
Position de base 1 d’une ligne dans l’ensemble de lignes actif. Cette valeur peut être comprise entre 1 et la taille de l’ensemble de lignes.

*wLockType*<br/>
Valeur indiquant comment verrouiller la ligne après qu’elle a été actualisée. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Lors de l’implémentation de l’extraction de lignes en bloc, les enregistrements sont récupérés par ensembles de lignes, où le premier enregistrement de l’ensemble de lignes extrait est l’enregistrement en cours. Pour faire d’un autre enregistrement dans l’ensemble de lignes l’enregistrement actif, appelez `SetRowsetCursorPosition`. Par exemple, vous pouvez combiner `SetRowsetCursorPosition` avec la fonction membre [GetFieldValue](#getfieldvalue) pour récupérer dynamiquement les données de n’importe quel enregistrement de votre Recordset.

Pour utiliser `SetRowsetCursorPosition`, vous devez avoir implémenté l’extraction de lignes en bloc en spécifiant l’option `CRecordset::useMultiRowFetch` du paramètre *dwOptions* dans la fonction membre [Open](#open) .

`SetRowsetCursorPosition` appelle la fonction API ODBC `SQLSetPos`. Le paramètre *wLockType* spécifie l’état de verrouillage de la ligne après l’exécution de `SQLSetPos`. Le tableau suivant décrit les valeurs possibles pour *wLockType*.

|wLockType|Description|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (valeur par défaut)|Le pilote ou la source de données garantit que la ligne est dans le même état verrouillé ou déverrouillé qu’avant l’appel de `SetRowsetCursorPosition`.|
|SQL_LOCK_EXCLUSIVE|Le pilote ou la source de données verrouille la ligne en mode exclusif. Toutes les sources de données ne prennent pas en charge ce type de verrou.|
|SQL_LOCK_UNLOCK|Le pilote ou la source de données déverrouille la ligne. Toutes les sources de données ne prennent pas en charge ce type de verrou.|

Pour plus d’informations sur `SQLSetPos`, consultez la SDK Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="setrowsetsize"></a>CRecordset :: SetRowsetSize

Spécifie le nombre d’enregistrements que vous souhaitez récupérer lors d’une extraction.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Paramètres

*dwNewRowsetSize*<br/>
Nombre de lignes à récupérer au cours d’une extraction donnée.

### <a name="remarks"></a>Notes

Cette fonction membre virtuelle spécifie le nombre de lignes que vous souhaitez récupérer lors d’une extraction unique lors de l’utilisation de l’extraction de lignes en bloc. Pour implémenter l’extraction de lignes en bloc, vous devez définir l’option `CRecordset::useMultiRowFetch` dans le paramètre *dwOptions* de la fonction membre [Open](#open) .

> [!NOTE]
>  L’appel de `SetRowsetSize` sans implémenter l’extraction de lignes en bloc entraîne l’échec d’une assertion.

Appelez `SetRowsetSize` avant d’appeler `Open` pour définir initialement la taille de l’ensemble de lignes pour le Recordset. La taille de l’ensemble de lignes par défaut lors de l’implémentation de l’extraction de lignes en bloc est 25.

> [!NOTE]
>  Soyez prudent lors de l’appel de `SetRowsetSize`. Si vous allouez manuellement le stockage pour les données (comme spécifié par l’option `CRecordset::userAllocMultiRowBuffers` du paramètre dwOptions dans `Open`), vous devez vérifier si vous devez réallouer ces mémoires tampons de stockage après avoir appelé `SetRowsetSize`, mais avant d’effectuer une opération de navigation de curseur.

Pour obtenir le paramètre actuel de la taille de l’ensemble de lignes, appelez [GetRowsetSize](#getrowsetsize).

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="update"></a>CRecordset :: Update

Termine une opération de `AddNew` ou de `Edit` en enregistrant les données nouvelles ou modifiées sur la source de données.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si un enregistrement a été correctement mis à jour ; Sinon, la valeur est 0 si aucune colonne n’a été modifiée. Si aucun enregistrement n’a été mis à jour ou si plusieurs enregistrements ont été mis à jour, une exception est levée. Une exception est également levée pour toute autre défaillance sur la source de données.

### <a name="remarks"></a>Notes

Appelez cette fonction membre après un appel à la fonction membre [AddNew](#addnew) ou [Edit](#edit) . Cet appel est requis pour terminer l’opération de `AddNew` ou de `Edit`.

> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `Update`. Cela entraînera l’échec d’une assertion. Bien que la classe `CRecordset` ne fournisse pas de mécanisme de mise à jour des lignes de données en bloc, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew` et `Edit` préparer un tampon d’édition dans lequel les données ajoutées ou modifiées sont placées pour être enregistrées dans la source de données. `Update` enregistre les données. Seuls les champs marqués ou détectés comme modifiés sont mis à jour.

Si la source de données prend en charge les transactions, vous pouvez faire de l’appel de `Update` (et de la `AddNew` ou de l’appel `Edit` correspondant) une transaction. Pour plus d’informations sur les transactions, consultez l’article [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
>  Si vous appelez `Update` sans appeler d’abord `AddNew` ou `Edit`, `Update` lève une `CDBException`. Si vous appelez `AddNew` ou `Edit`, vous devez appeler `Update` avant d’appeler une opération de `Move` ou avant de fermer le recordset ou la connexion à la source de données. Dans le cas contraire, vos modifications seront perdues sans notification.

Pour plus d’informations sur la gestion des échecs de `Update`, consultez l’article [Recordset : How recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Exemple

Consultez l’article [transaction : exécution d’une transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView, classe](../../mfc/reference/crecordview-class.md)
