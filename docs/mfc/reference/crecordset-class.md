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
ms.openlocfilehash: ab6cde9f478dc6f2e3cb0ba5bb338a3852f083fd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750505"
---
# <a name="crecordset-class"></a>Classe CRecordset

Représente un ensemble d'enregistrements sélectionnés à partir d'une source de données.

## <a name="syntax"></a>Syntaxe

```
class CRecordset : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRecordset::CRecordset](#crecordset)|Construit un objet `CRecordset`. Votre classe dérivée doit fournir un constructeur qui appelle celui-ci.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRecordset::AddNew](#addnew)|Se prépare à l’ajout d’un nouvel album. Appelez `Update` pour compléter l’ajout.|
|[CRecordset::CanAppend](#canappend)|Retourne nonzero si de nouveaux enregistrements peuvent `AddNew` être ajoutés à l’ensemble d’enregistrements via la fonction membre.|
|[CRecordset::CanBookmark](#canbookmark)|Retourne nonzero si le livre prend en charge les signets.|
|[CRecordset::Annuler](#cancel)|Annule une opération asynchrone ou un processus à partir d’un deuxième thread.|
|[CRecordset::CancelUpdate](#cancelupdate)|Annule toute mise à jour `AddNew` `Edit` en attente en raison d’une ou d’une opération.|
|[CRecordset::CanRestart](#canrestart)|Retourne nonzero `Requery` si peut être appelé pour exécuter la requête du recordet à nouveau.|
|[CRecordset::CanScroll](#canscroll)|Retourne nonzero si vous pouvez faire défiler les enregistrements.|
|[CRecordset::CanTransact](#cantransact)|Retourne nonzero si la source de données prend en charge les transactions.|
|[CRecordset::CanUpdate](#canupdate)|Retourne nonzero si le jeu d’enregistrement peut être mis à jour (vous pouvez ajouter, mettre à jour ou supprimer des enregistrements).|
|[CRecordset::CheckRowsetError](#checkrowseterror)|Appelé pour gérer les erreurs générées lors de la récupération d’enregistrement.|
|[CRecordset::Fermer](#close)|Ferme le recordet et le HSTMT ODBC qui lui est associé.|
|[CRecordset::Déléte](#delete)|Supprime l’enregistrement actuel de l’enregistrement. Vous devez faire défiler explicitement vers un autre enregistrement après la suppression.|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Appelé à échanger des rangées de données en vrac de la source de données à l’enregistrement. Implémente l’échange de records en vrac sur le terrain (Bulk RFX).|
|[CRecordset::DoFieldExchange](#dofieldexchange)|Appelé à échanger des données (dans les deux sens) entre les membres des données sur le terrain de l’enregistrement et l’enregistrement correspondant sur la source de données. Implémente l’échange record sur le terrain (RFX).|
|[CRecordset::Edit](#edit)|Se prépare aux changements apportés au dossier actuel. Appelez `Update` pour terminer la modification.|
|[CRecordset::FlushResultSet](#flushresultset)|Retourne nonzero s’il y a un autre résultat à récupérer, lors de l’utilisation d’une requête prédéfinie.|
|[CRecordset::GetBookmark](#getbookmark)|Attribue la valeur de signet d’un enregistrement à l’objet de paramètre.|
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Appelé pour obtenir la chaîne de connexion par défaut.|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Appelé pour obtenir la chaîne SQL par défaut à exécuter.|
|[CRecordset::GetFieldValue](#getfieldvalue)|Retourne la valeur d’un champ dans un jeu d’enregistrement.|
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Retourne le nombre de champs dans l’enregistrement.|
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Renvoie des types spécifiques d’informations sur les champs dans un jeu d’enregistrement.|
|[CRecordset::GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements dans l’enregistrement.|
|[CRecordset::GetRowsetSize](#getrowsetsize)|Retourne le nombre d’enregistrements que vous souhaitez récupérer lors d’un seul aller.|
|[CRecordset::GetRowsFetched](#getrowsfetched)|Retourne le nombre réel de rangées récupérées lors d’un aller chercher.|
|[CRecordset::GetRowStatus](#getrowstatus)|Retourne l’état de la rangée après un aller chercher.|
|[CRecordset::GetSQL](#getsql)|Obtient la chaîne SQL utilisé pour sélectionner les enregistrements pour le nombre d’enregistrements.|
|[CRecordset::GetStatus](#getstatus)|Obtient l’état du record : l’indice du dossier actuel et la question de savoir si un décompte final des enregistrements a été obtenu.|
|[CRecordset::GetTableName](#gettablename)|Obtient le nom de la table sur laquelle le tableau est basé.|
|[CRecordset::IsBOF](#isbof)|Retourne nonzero si le recordet a été positionné avant le premier enregistrement. Aucun enregistrement actif.|
|[CRecordset::IsDeleted](#isdeleted)|Retourne nonzero si le recordet est positionné sur un enregistrement supprimé.|
|[CRecordset::IsEOF](#iseof)|Retourne nonzero si le recordet a été positionné après le dernier enregistrement. Aucun enregistrement actif.|
|[CRecordset::IsFieldDirty](#isfielddirty)|Retourne nonzero si le champ spécifié dans l’enregistrement actuel a été modifié.|
|[CRecordset::IsFieldNull](#isfieldnull)|Retourne nonzero si le champ spécifié dans le dossier actuel est nul (n’a aucune valeur).|
|[CRecordset::IsFieldNullable](#isfieldnullable)|Retourne nonzero si le champ spécifié dans le dossier actuel peut être mis à null (n’ayant aucune valeur).|
|[CRecordset::IsOpen](#isopen)|Retourne nonzero `Open` si a été appelé précédemment.|
|[CRecordset::Déplacer](#move)|Positionne l’enregistrement à un nombre précis d’enregistrements de l’enregistrement actuel dans les deux sens.|
|[CRecordset::MoveFirst](#movefirst)|Positionne le record actuel du premier enregistrement dans le dossier. Test `IsBOF` pour le premier.|
|[CRecordset::MoveLast](#movelast)|Positionne le record actuel sur le dernier enregistrement ou sur le dernier ligne. Test `IsEOF` pour le premier.|
|[CRecordset::MoveNext](#movenext)|Positionne le record actuel sur le prochain enregistrement ou sur le jeu de ligne suivant. Test `IsEOF` pour le premier.|
|[CRecordset::MovePrev](#moveprev)|Positionne le record actuel de l’enregistrement précédent ou sur le jeu de ligne précédent. Test `IsBOF` pour le premier.|
|[CRecordset::OnSetOptions](#onsetoptions)|Appelé à définir des options (utilisées sur la sélection) pour l’énoncé spécifié de l’ODBC.|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Appelé à définir des options (utilisées sur la mise à jour) pour l’énoncé spécifié ODBC.|
|[CRecordset::Ouvert](#open)|Ouvre le tableau d’enregistrement en récupérant la table ou en exécutant la requête que représente le recordet.|
|[CRecordset::RefreshRowset](#refreshrowset)|Rafraîchit les données et l’état de la ligne spécifiée.|
|[CRecordset::Requery](#requery)|Exécute la requête du recordet à nouveau pour rafraîchir les enregistrements sélectionnés.|
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Positionne l’enregistrement de l’enregistrement correspondant au nombre record spécifié.|
|[CRecordset::SetBookmark](#setbookmark)|Positionne l’enregistrement sur l’enregistrement spécifié par le signet.|
|[CRecordset::SetFieldDirty](#setfielddirty)|Marque le champ spécifié dans le dossier actuel tel que modifié.|
|[CRecordset::SetFieldNull](#setfieldnull)|Définit la valeur du champ spécifié dans le dossier actuel à nulle (n’ayant aucune valeur).|
|[CRecordset::SetLockingMode](#setlockingmode)|Définit le mode de verrouillage à verrouillage « optimiste » (par défaut) ou « pessimiste ». Détermine comment les enregistrements sont verrouillés pour les mises à jour.|
|[CRecordset::SetParamNull](#setparamnull)|Définit le paramètre spécifié à nul (n’ayant aucune valeur).|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Positionne le curseur sur la ligne spécifiée à l’intérieur de l’acart.|
|[CRecordset::SetRowsetSize](#setrowsetsize)|Précise le nombre d’enregistrements que vous souhaitez récupérer lors d’un aller chercher.|
|[CRecordset::Mise à jour](#update)|Termine une `AddNew` `Edit` ou une opération en économisant les données nouvelles ou modifiées sur la source de données.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRecordset::m_hstmt](#m_hstmt)|Contient la poignée de relevé oDBC pour l’enregistrement. Tapez `HSTMT`.|
|[CRecordset::m_nFields](#m_nfields)|Contient le nombre de membres des données sur le terrain dans l’enregistrement. Tapez `UINT`.|
|[CRecordset::m_nParams](#m_nparams)|Contient le nombre de paramètres membres dans le jeu d’enregistrement. Tapez `UINT`.|
|[CRecordset::m_pDatabase](#m_pdatabase)|Contient un pointeur sur l’objet `CDatabase` par lequel le jeu d’enregistrement est connecté à une source de données.|
|[CRecordset::m_strFilter](#m_strfilter)|Contient `CString` un qui spécifie une clause `WHERE` de langue de requête structurée (SQL). Utilisé comme filtre pour sélectionner uniquement les enregistrements qui répondent à certains critères.|
|[CRecordset::m_strSort](#m_strsort)|Contient `CString` un qui spécifie une clause SQL. `ORDER BY` Utilisé pour contrôler la façon dont les enregistrements sont triés.|

## <a name="remarks"></a>Notes concernant <a name="remarks"></a>

Connus sous le `CRecordset` nom de « records », les objets sont généralement utilisés sous deux formes : les dynasets et les instantanés. Un dynaset reste synchronisé avec les mises à jour de données faites par d’autres utilisateurs. Un instantané est une vue statique des données. Chaque formulaire représente un ensemble d’enregistrements fixés au moment où le jeu d’enregistrement est ouvert, mais lorsque vous faites défiler vers un enregistrement dans un dynaset, il reflète les modifications apportées ultérieurement à l’enregistrement, soit par d’autres utilisateurs ou par d’autres enregistrements dans votre application.

> [!NOTE]
> Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt qu’avec les classes de connectivité à base de données ouvertes (ODBC), utilisez plutôt la classe [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Pour plus d’informations, voir l’article [Aperçu: Programmation de base de données](../../data/data-access-programming-mfc-atl.md).

Pour travailler avec l’un ou l’autre type d’enregistrement, vous dérivez généralement une classe de documents spécifiques à l’application de `CRecordset`. Les enregistrements sélectionnent les enregistrements à partir d’une source de données, et vous pouvez alors :

- Faites défiler les enregistrements.

- Mettez à jour les enregistrements et spécifier un mode de verrouillage.

- Filtrer le groupe d’enregistrement pour limiter les enregistrements qu’il sélectionne parmi ceux disponibles sur la source de données.

- Trier le recordet.

- Paramélisez le tableau d’enregistrement pour personnaliser sa sélection avec des informations non connues avant l’heure d’exécution.

Pour utiliser votre classe, ouvrez une base de données et construisez un objet de la taille d’enregistrement, en passant le constructeur un pointeur sur votre `CDatabase` objet. Ensuite, appelez la `Open` fonction de membre du livre, où vous pouvez spécifier si l’objet est un dynaset ou un instantané. L’appel `Open` sélectionne les données de la source de données. Une fois l’objet de l’enregistrement ouvert, utilisez ses fonctions de membre et les membres des données pour faire défiler les enregistrements et les utiliser. Les opérations disponibles dépendent de la question de savoir si l’objet est un dynaset ou un instantané, qu’il soit updatable ou lu uniquement (cela dépend de la capacité de la source de données Open Database Connectivity (ODBC), et si vous avez implémenté la capture en vrac. Pour actualiser les enregistrements qui peuvent `Open` avoir été modifiés `Requery` ou ajoutés depuis l’appel, appelez la fonction de membre de l’objet. Appelez la fonction `Close` membre de l’objet et détruisez l’objet lorsque vous en avez terminé.

Dans une `CRecordset` catégorie dérivée, l’échange de champs de disques (RFX) ou l’échange de records en vrac (Bulk RFX) est utilisé pour soutenir la lecture et la mise à jour des champs d’enregistrement.

Pour plus d’informations sur les enregistrements et l’échange de records sur le terrain, voir les articles [Aperçu: Database Programming](../../data/data-access-programming-mfc-atl.md), [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md). Pour mettre l’accent sur les dynasets et les instantanés, voir les articles [Dynaset](../../data/odbc/dynaset.md) et [Snapshot](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset::AddNew

Se prépare à ajouter un nouvel enregistrement à la table.

```
virtual void AddNew();
```

### <a name="remarks"></a>Notes

Vous devez appeler la fonction membre [Requery](#requery) pour voir le dossier nouvellement ajouté. Les champs de l’enregistrement sont d’abord Nuls. (Dans la terminologie de la base de données, Null signifie « n’avoir aucune valeur » et n’est pas le même que NULL dans C.) Pour terminer l’opération, vous devez appeler la fonction membre [de mise à jour.](#update) `Update`enregistre vos modifications à la source de données.

> [!NOTE]
> Si vous avez implémenté la `AddNew`ligne en vrac aller chercher, vous ne pouvez pas appeler . Cela se traduira par une affirmation ratée. Bien `CRecordset` que la classe ne fournit pas un mécanisme pour mettre à jour les lignes de `SQLSetPos`données en vrac, vous pouvez écrire vos propres fonctions en utilisant la fonction API ODBC . Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew`prépare un nouvel enregistrement vide à l’aide des membres des données sur le terrain du recordet. Après votre `AddNew`appel, définissez les valeurs que vous souhaitez dans les membres de données de champ du recordet. (Vous n’avez pas [Edit](#edit) à appeler la fonction `Edit` membre Edit à cette fin; utiliser uniquement pour les enregistrements existants.) Lorsque vous `Update`appelez par la suite, les valeurs modifiées dans les données de terrain sont enregistrées sur la source de données.

> [!CAUTION]
> Si vous faites défiler vers `Update`un nouvel enregistrement avant d’appeler, le nouvel enregistrement est perdu, et aucun avertissement n’est donné.

Si la source de données prend `AddNew` en charge les transactions, vous pouvez effectuer une partie de votre appel d’une transaction. Pour plus d’informations sur les transactions, voir classe [CDatabase](../../mfc/reference/cdatabase-class.md). Notez que vous devez appeler [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) avant d’appeler `AddNew`.

> [!NOTE]
> Pour les dynasets, de nouveaux enregistrements sont ajoutés à l’enregistrement comme le dernier enregistrement. Les enregistrements ajoutés ne sont pas ajoutés aux instantanés; vous devez `Requery` appeler pour rafraîchir le recordet.

Il est illégal `AddNew` d’appeler `Open` à un dossier dont la fonction de membre n’a pas été appelée. A `CDBException` est lancé `AddNew` si vous appelez pour un enregistrement qui ne peut pas être joint à. Vous pouvez déterminer si le recordet est updatable en appelant [CanAppend](#canappend).

Pour plus d’informations, voir les articles suivants: [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Recordset: Adding, Updating, and Deleting Records (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), et [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Exemple

Voir l’article [Transaction: Performing a Transaction in a Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="crecordsetcanappend"></a><a name="canappend"></a>CRecordset::CanAppend

Détermine si le recordet précédemment ouvert vous permet d’ajouter de nouveaux enregistrements.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet permet d’ajouter de nouveaux enregistrements; sinon 0. `CanAppend`reviendra 0 si vous avez ouvert le recordet comme lu uniquement.

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>CRecordset::CanBookmark

Détermine si le jeu d’enregistrement vous permet de marquer des enregistrements à l’aide de signets.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le livreur prend en charge les signets; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est `CRecordset::useBookmarks` indépendante de l’option dans le paramètre *dwOptions* de la fonction membre [Open.](#open) `CanBookmark`indique si le conducteur et le support de type curseur donnés. `CRecordset::useBookmarks`indique si des signets seront disponibles, à condition qu’ils soient pris en charge.

> [!NOTE]
> Les signets ne sont pas pris en charge sur les enregistrements avant seuls.

Pour plus d’informations sur les signets et la navigation de recordset, voir les articles [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcancel"></a><a name="cancel"></a>CRecordset::Annuler

Demande que la source de données annule soit une opération asynchrone en cours, soit un processus à partir d’un deuxième thread.

```cpp
void Cancel();
```

### <a name="remarks"></a>Notes

Notez que les classes MFC ODBC n’utilisent plus de traitement asynchrone; pour effectuer une opération asychrone, vous devez appeler directement `SQLSetConnectOption`la fonction API ODBC . Pour plus d’informations, voir le thème "Exécution des fonctions asynchrone" dans le *Guide du programmeur SDK de l’ODBC*.

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>CRecordset::CancelUpdate

Annule toute mise à jour en attente, causée par une opération [Edit](#edit) ou [AddNew,](#addnew) avant [que la mise à jour](#update) ne soit appelée.

```cpp
void CancelUpdate();
```

### <a name="remarks"></a>Notes

> [!NOTE]
> Cette fonction de membre n’est pas applicable sur les enregistrements qui `Edit` `AddNew`utilisent `Update`la ligne en vrac aller chercher, puisque ces enregistrements ne peuvent pas appeler , , ou . Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Si la vérification automatique `CancelUpdate` du champ sale est activée, `Edit` `AddNew` rétablira les variables du membre aux valeurs qu’ils avaient avant ou qu’on l’appelle; autrement, toute modification de valeur restera. Par défaut, la vérification automatique du champ est activée lorsque le jeu d’enregistrement est ouvert. Pour le désactiver, vous `CRecordset::noDirtyFieldCheck` devez spécifier le paramètre *dwOptions* de la fonction membre [Open.](#open)

Pour plus d’informations sur la mise à jour des données, consultez l’article [Recordset: Adding, Updating, and Deleting Records (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>CRecordset::CanRestart

Détermine si la fiche permet de redémarrer sa requête (pour `Requery` actualiser ses dossiers) en appelant la fonction membre.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la requery est autorisée; sinon 0.

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset::CanScroll

Détermine si l’enregistrement permet le défilement.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet permet de faire défiler; sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le défilement, voir l’article [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset::CanTransact

Détermine si l’enregistrement permet les transactions.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le dossier permet les transactions; sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset::CanUpdate

Détermine si le jeu d’enregistrement peut être mis à jour.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le jeu d’enregistrement peut être mis à jour; sinon 0.

### <a name="remarks"></a>Notes

Un jeu d’enregistrement peut être lu uniquement si la source `CRecordset::readOnly` de données sous-jacente est lue uniquement ou si vous avez spécifié dans le paramètre *dwOptions* lorsque vous avez ouvert le jeu d’enregistrement.

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>CRecordset::CheckRowsetError

Appelé pour gérer les erreurs générées lors de la récupération d’enregistrement.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Paramètres

*nRetCode (nRetCode)*<br/>
Un code de retour de fonction ODBC API. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Cette fonction de membre virtuel gère les erreurs qui se produisent lorsque les enregistrements sont récupérés, et est utile pendant la mise à l’allier en vrac. Vous pouvez envisager de `CheckRowsetError` passer à l’avant pour implémenter votre propre traitement des erreurs.

`CheckRowsetError`est appelé automatiquement dans une opération de `Open` `Requery`navigation curseur, comme , , ou toute `Move` opération. Il est passé la valeur de retour `SQLExtendedFetch`de la fonction ODBC API . Le tableau suivant répertorie les valeurs possibles pour le *paramètre nRetCode.*

|nRetCode (nRetCode)|Description|
|--------------|-----------------|
|SQL_SUCCESS|Fonction complétée avec succès; aucune information supplémentaire n’est disponible.|
|SQL_SUCCESS_WITH_INFO|Fonction complétée avec succès, peut-être avec une erreur non mortelle. Des informations supplémentaires peuvent `SQLError`être obtenues en appelant .|
|SQL_NO_DATA_FOUND|Toutes les lignes de l’ensemble de résultats ont été récupérées.|
|SQL_ERROR|La fonction a échoué. Des informations supplémentaires peuvent `SQLError`être obtenues en appelant .|
|SQL_INVALID_HANDLE|Fonction défectueuse en raison d’une poignée d’environnement invalide, poignée de connexion, ou poignée de déclaration. Cela indique une erreur de programmation. Aucune information supplémentaire `SQLError`n’est disponible à partir de .|
|SQL_STILL_EXECUTING|Une fonction qui a été commencée asynchronement est toujours en cours d’exécution. Notez que par défaut, MFC ne `CheckRowsetError`transmettra jamais cette valeur à ; MFC continuera `SQLExtendedFetch` d’appeler jusqu’à ce qu’il ne revienne plus SQL_STILL_EXECUTING.|

Pour plus `SQLError`d’informations sur , voir le Windows SDK. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset::Fermer

Ferme le recordet.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

L’ODBC HSTMT et toute la mémoire du cadre alloué à l’ensemble d’enregistrements sont deallocated. Habituellement, `Close`après l’appel , vous supprimez l’objet de recordset C 's’il a été alloué avec **de nouveaux**.

Vous pouvez `Open` appeler `Close`à nouveau après avoir appelé . Cela vous permet de réutiliser l’objet de l’enregistrement. L’alternative est `Requery`d’appeler .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>CRecordset::CRecordset

Construit un objet `CRecordset`.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Paramètres

*base de pData*<br/>
Contient un pointeur à un `CDatabase` objet ou la valeur NULL. Si ce n’est `Open` pas NULL et la fonction membre de l’objet `CDatabase` n’a pas été `Open` appelé pour le connecter à la source de données, le recordet tente de l’ouvrir pour vous lors de son propre appel. Si vous passez NULL, un `CDatabase` objet est construit et connecté pour vous en utilisant les informations de source de données que vous avez spécifiées lorsque vous avez dérivé votre classe de nombres d’enregistrements avec ClassWizard.

### <a name="remarks"></a>Notes

Vous pouvez `CRecordset` soit utiliser directement ou tirer `CRecordset`une classe spécifique à l’application de . Vous pouvez utiliser ClassWizard pour dériver vos classes de records.

> [!NOTE]
> Une classe dérivée *doit* fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur, `CRecordset::CRecordset`en passant les paramètres appropriés le long de lui.

Passez NULL à votre constructeur de `CDatabase` records pour qu’un objet soit construit et connecté automatiquement pour vous. Il s’agit d’un raccourci utile qui `CDatabase` ne vous oblige pas à construire et connecter un objet avant de construire votre ensemble d’enregistrements.

### <a name="example"></a>Exemple

Pour plus d’informations, voir l’article [Recordset: Déclarer une classe pour une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

## <a name="crecordsetdelete"></a><a name="delete"></a>CRecordset::Déléte

Supprime l’enregistrement actuel.

```
virtual void Delete();
```

### <a name="remarks"></a>Notes

Après une suppression réussie, les membres des données de terrain du recordet sont réglés `Move` à une valeur nulle, et vous devez appeler explicitement l’une des fonctions afin de se déplacer hors de l’enregistrement supprimé. Une fois que vous vous éloignez de l’enregistrement supprimé, il n’est pas possible d’y revenir. Si la source de données prend `Delete` en charge les transactions, vous pouvez effectuer la partie d’appel d’une transaction. Pour plus d’informations, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
> Si vous avez implémenté la `Delete`ligne en vrac aller chercher, vous ne pouvez pas appeler . Cela se traduira par une affirmation ratée. Bien `CRecordset` que la classe ne fournit pas un mécanisme pour mettre à jour les lignes de `SQLSetPos`données en vrac, vous pouvez écrire vos propres fonctions en utilisant la fonction API ODBC . Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
> Le tableau de dossier doit être updatable et il doit y `Delete`avoir un courant d’enregistrement valide dans le dossier lorsque vous appelez; autrement, une erreur se produit. Par exemple, si vous supprimez un enregistrement mais ne `Delete` faites `Delete` pas défiler vers un nouvel enregistrement avant d’appeler à nouveau, lance un [CDBException](../../mfc/reference/cdbexception-class.md).

Contrairement à [AddNew](#addnew) et `Delete` [Edit](#edit), un appel à n’est pas suivi d’un appel à mettre à [jour](#update). Si `Delete` un appel échoue, les membres des données sur le terrain sont laissés inchangés.

### <a name="example"></a>Exemple

Cet exemple montre un enregistrement créé sur le cadre d’une fonction. L’exemple suppose l’existence `m_dbCust`d’une `CDatabase` variable de type membre déjà connectée à la source de données.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange

Appelé à échanger des rangées de données en vrac de la source de données à l’enregistrement. Implémente l’échange de records en vrac sur le terrain (Bulk RFX).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Le cadre aura déjà mis en place cet objet pour spécifier un contexte pour l’opération d’échange sur le terrain.

### <a name="remarks"></a>Notes

Lorsque la ligne en vrac est implémentée, le cadre appelle cette fonction membre pour transférer automatiquement les données de la source de données à votre objet de nombre. `DoBulkFieldExchange`lie également vos membres de données de paramètres, le cas échéant, aux paramètres des participants dans la chaîne de relevés SQL pour la sélection du groupe d’enregistrement.

Si la ligne en vrac n’est pas mise en œuvre, le cadre appelle [DoFieldExchange](#dofieldexchange). Pour implémenter la ramage `CRecordset::useMultiRowFetch` en vrac, vous devez spécifier l’option du paramètre *dwOptions* dans la fonction membre [Open.](#open)

> [!NOTE]
> `DoBulkFieldExchange`n’est disponible que si vous `CRecordset`utilisez une classe dérivée de . Si vous avez créé un `CRecordset`objet de numérot directement à partir de , vous devez appeler la fonction membre [GetFieldValue](#getfieldvalue) pour récupérer des données.

L’échange de champs de disques en vrac (Bulk RFX) est similaire à l’échange record sur le terrain (RFX). Les données sont automatiquement transférées de la source de données à l’objet de l’enregistrement. Cependant, vous `AddNew`ne `Edit` `Delete`pouvez `Update` pas appeler , , ou pour transférer des modifications vers la source de données. À `CRecordset` l’heure actuelle, la catégorie ne fournit pas de mécanisme pour mettre à jour les rangées de données en vrac; cependant, vous pouvez écrire vos propres fonctions en `SQLSetPos`utilisant la fonction ODBC API .

Notez que ClassWizard ne prend pas en charge l’échange de records en vrac sur le terrain; par conséquent, vous `DoBulkFieldExchange` devez passer outre manuellement en écrivant des appels aux fonctions RFX en vrac. Pour plus d’informations sur ces fonctions, consultez le sujet [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md).

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus d’informations connexes, voir l’article [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset::DoFieldExchange

Appelé à échanger des données (dans les deux sens) entre les membres des données sur le terrain de l’enregistrement et l’enregistrement correspondant sur la source de données. Implémente l’échange record sur le terrain (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Le cadre aura déjà mis en place cet objet pour spécifier un contexte pour l’opération d’échange sur le terrain.

### <a name="remarks"></a>Notes

Lorsque la ligne en vrac n’est pas implémentée, le cadre appelle cette fonction membre pour échanger automatiquement des données entre les membres des données de champ de votre objet de l’enregistrement et les colonnes correspondantes de l’enregistrement actuel sur la source de données. `DoFieldExchange`lie également vos membres de données de paramètres, le cas échéant, aux paramètres des participants dans la chaîne de relevés SQL pour la sélection du groupe d’enregistrement.

Si la ligne en vrac est mise en œuvre, le cadre appelle [DoBulkFieldExchange](#dobulkfieldexchange). Pour implémenter la ramage `CRecordset::useMultiRowFetch` en vrac, vous devez spécifier l’option du paramètre *dwOptions* dans la fonction membre [Open.](#open)

> [!NOTE]
> `DoFieldExchange`n’est disponible que si vous `CRecordset`utilisez une classe dérivée de . Si vous avez créé un `CRecordset`objet de numérot directement à partir de , vous devez appeler la fonction membre [GetFieldValue](#getfieldvalue) pour récupérer des données.

L’échange de données sur le terrain, appelée échange de champs record (RFX), fonctionne dans les deux sens : des membres des données de terrain de l’objet de l’enregistrement aux champs de l’enregistrement sur la source de données, et de l’enregistrement sur la source de données à l’objet de l’ensemble de disques.

La seule action que vous `DoFieldExchange` devez normalement prendre pour implémenter pour votre classe de recordet dérivé est de créer la classe avec ClassWizard et de spécifier les noms et les types de données des membres de données sur le terrain. Vous pouvez également ajouter du code à ce que ClassWizard écrit pour spécifier les membres des données de paramètres ou pour traiter toutes les colonnes que vous liez dynamiquement. Pour plus d’informations, voir l’article [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Lorsque vous déclarez votre classe de disques dérivés avec `DoFieldExchange` ClassWizard, l’assistant vous écrit un remplacement, qui ressemble à l’exemple suivant :

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Pour plus d’informations sur les fonctions RFX, consultez le sujet [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md).

Pour plus d’exemples et de détails sur `DoFieldExchange`, voir l’article Record Field [Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour plus d’informations générales sur RFX, voir l’article [Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset::Edit

Permet des modifications à l’enregistrement actuel.

```
virtual void Edit();
```

### <a name="remarks"></a>Notes

Après votre `Edit`appel, vous pouvez modifier les membres des données de terrain en réinitialisant directement leurs valeurs. L’opération est terminée lorsque vous appelez par la suite la fonction membre [de la Mise à jour](#update) pour enregistrer vos modifications sur la source de données.

> [!NOTE]
> Si vous avez implémenté la `Edit`ligne en vrac aller chercher, vous ne pouvez pas appeler . Cela se traduira par une affirmation ratée. Bien `CRecordset` que la classe ne fournit pas un mécanisme pour mettre à jour les lignes de `SQLSetPos`données en vrac, vous pouvez écrire vos propres fonctions en utilisant la fonction API ODBC . Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit`enregistre les valeurs des membres des données du recordet. Si vous `Edit`appelez, faites `Edit` des modifications, puis appelez à nouveau, les `Edit` valeurs de l’enregistrement sont restaurées à ce qu’elles étaient avant le premier appel.

Dans certains cas, vous pouvez mettre à jour une colonne en la rendant nulle (ne contenant aucune donnée). Pour ce faire, appelez [SetFieldNull](#setfieldnull) avec un paramètre de TRUE pour marquer le champ Null; cela provoque également la mise à jour de la colonne. Si vous voulez qu’un champ soit écrit à la source de données même si sa valeur n’a pas changé, appelez [SetFieldDirty](#setfielddirty) avec un paramètre de TRUE. Cela fonctionne même si le champ avait la valeur Null.

Si la source de données prend `Edit` en charge les transactions, vous pouvez effectuer la partie d’appel d’une transaction. Notez que vous devez appeler [CDatabase:BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) avant d’appeler `Edit` et après l’enregistrement a été ouvert. Notez également que l’appel [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) n’est pas un substitut pour appeler `Update` pour terminer l’opération. `Edit` Pour plus d’informations sur les transactions, voir classe [CDatabase](../../mfc/reference/cdatabase-class.md).

Selon le mode de verrouillage actuel, l’enregistrement `Edit` mis `Update` à jour peut être verrouillé jusqu’à `Edit` ce que vous appeliez ou faites défiler vers un autre enregistrement, ou il ne peut être verrouillé que pendant l’appel. Vous pouvez modifier le mode de verrouillage avec [SetLockingMode](#setlockingmode).

La valeur précédente de l’enregistrement actuel est restaurée `Update`si vous faites défiler vers un nouvel enregistrement avant d’appeler . A `CDBException` est lancé `Edit` si vous appelez pour un jeu d’enregistrement qui ne peut pas être mis à jour ou s’il n’y a pas d’enregistrement actuel.

Pour plus d’informations, voir les articles [Transaction (ODBC)](../../data/odbc/transaction-odbc.md) et [Recordset: Locking Records (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>CRecordset::FlushResultSet

Récupère l’ensemble de résultat suivant d’une requête prédéfinie (procédure stockée), s’il y a plusieurs ensembles de résultats.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Valeur de retour

Nonzero s’il y a plus d’ensembles de résultats à récupérer; sinon 0.

### <a name="remarks"></a>Notes

Vous ne `FlushResultSet` devez appeler que lorsque vous avez complètement terminé avec le curseur sur l’ensemble de résultats actuel. Notez que lorsque vous récupérez `FlushResultSet`le prochain résultat défini par appel, votre curseur n’est pas valide sur cet ensemble de résultats; vous devez appeler la fonction membre `FlushResultSet` [MoveNext](#movenext) après avoir appelé .

Si une requête prédéfinie utilise un paramètre de sortie `FlushResultSet` ou des `FALSE` paramètres d’entrée/sortie, vous devez appeler jusqu’à ce qu’elle revienne (la valeur 0), afin d’obtenir ces valeurs de paramètres.

`FlushResultSet`appelle la fonction `SQLMoreResults`API ODBC . Si `SQLMoreResults` les retours SQL_ERROR ou SQL_INVALID_HANDLE, alors `FlushResultSet` jetez une exception. Pour plus `SQLMoreResults`d’informations sur , voir le Windows SDK.

Votre procédure stockée doit avoir des champs `FlushResultSet`liés si vous voulez appeler .

### <a name="example"></a>Exemple

Le code suivant `COutParamRecordset` suppose `CRecordset`qu’il s’agit d’un objet dérivé basé sur une requête prédéfinie avec un paramètre d’entrée et un paramètre de sortie, et ayant plusieurs ensembles de résultats. Notez la structure du remplacement [de DoFieldExchange.](#dofieldexchange)

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset::GetBookmark

Obtient la valeur de signet pour l’enregistrement actuel.

```cpp
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Paramètres

*varBookmark (en)*<br/>
Une référence à un objet [CDBVariant](../../mfc/reference/cdbvariant-class.md) représentant le signet de l’enregistrement actuel.

### <a name="remarks"></a>Notes

Pour déterminer si les signets sont pris en charge sur le jeu d’enregistrement, appelez [CanBookmark](#canbookmark). Pour rendre les signets disponibles s’ils `CRecordset::useBookmarks` sont pris en charge, vous devez définir l’option dans le paramètre *dwOptions* de la fonction membre [Open.](#open)

> [!NOTE]
> Si les signets ne sont pas pris `GetBookmark` en compte ou indisponibles, l’appel entraînera la mise en œil d’une exception. Les signets ne sont pas pris en charge sur les enregistrements avant seuls.

`GetBookmark`attribue la valeur du signet de l’enregistrement actuel à un `CDBVariant` objet. Pour revenir à cet enregistrement à tout moment après avoir passé `CDBVariant` à un enregistrement différent, appelez [SetBookmark](#setbookmark) avec l’objet correspondant.

> [!NOTE]
> Après certaines opérations de registre, les signets peuvent ne plus être valides. Par exemple, si `GetBookmark` vous `Requery`appelez suivi par , vous ne `SetBookmark`pouvez pas être en mesure de revenir à l’enregistrement avec . Appelez [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si `SetBookmark`vous pouvez appeler en toute sécurité .

Pour plus d’informations sur les signets et la navigation de recordset, voir les articles [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect

Appelé pour obtenir la chaîne de connexion par défaut.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient la chaîne de connexion par défaut.

### <a name="remarks"></a>Notes

Le cadre appelle cette fonction membre pour obtenir la chaîne de connexion par défaut pour la source de données sur laquelle le jeu d’enregistrement est basé. ClassWizard implémente cette fonction pour vous en identifiant la même source de données que vous utilisez dans ClassWizard pour obtenir des informations sur les tableaux et les colonnes. Vous trouverez probablement pratique de compter sur cette connexion par défaut lors du développement de votre application. Mais la connexion par défaut peut ne pas convenir aux utilisateurs de votre application. Si c’est le cas, vous devez réimplanter cette fonction, rejetant la version de ClassWizard. Pour plus d’informations sur les chaînes de connexion, voir l’article [Data Source (ODBC)](../../data/odbc/data-source-odbc.md).

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CRecordset::GetDefaultSQL

Appelé pour obtenir la chaîne SQL par défaut à exécuter.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Valeur de retour

A `CString` qui contient la déclaration SQL par défaut.

### <a name="remarks"></a>Notes

Le cadre appelle cette fonction membre pour obtenir la déclaration SQL par défaut sur laquelle le dossier est basé. Il peut s’agir d’un nom de table ou d’une déclaration **SQL SELECT.**

Vous définissez indirectement la déclaration SQL par défaut en déclarant votre classe de disques avec ClassWizard, et ClassWizard effectue cette tâche pour vous.

Si vous avez besoin de la chaîne `GetSQL`de relevé SQL pour votre propre utilisation, appelez, qui renvoie la déclaration SQL utilisée pour sélectionner les enregistrements du record lorsqu’il a été ouvert. Vous pouvez modifier la chaîne SQL par défaut `GetDefaultSQL`dans le remplacement de votre classe de . Par exemple, vous pouvez spécifier un appel à une requête prédéfinie à l’aide d’une déclaration **CALL.** (Remarquez, cependant, que `GetDefaultSQL`si vous modifiez, vous devez également modifier `m_nFields` pour correspondre au nombre de colonnes dans la source de données.)

Pour plus d’informations, voir l’article [Recordset: Déclarer une classe pour une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
> Le nom de table sera vide si le cadre ne pouvait pas identifier un nom de table, si plusieurs noms de table ont été fournis, ou si une déclaration **CALL** ne pouvait pas être interprétée. Notez que lorsque vous utilisez une déclaration **CALL,** vous ne devez pas insérer l’espace blanc entre l’accolade bouclée et le mot clé **CALL,** ni vous insérer l’espace blanc avant l’accolade bouclée ou avant le mot clé **SELECT** dans une déclaration **SELECT.**

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CRecordset::GetFieldValue

Récupère les données sur le terrain dans l’enregistrement actuel.

```cpp
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

*lpszName (en)*<br/>
Le nom d’un champ.

*varValu*e Une référence à un objet [CDBVariant](../../mfc/reference/cdbvariant-class.md) qui stockera la valeur du champ.

*nFieldType (en)*<br/>
Le type de données ODBC C du champ. En utilisant la valeur par défaut, DEFAULT_FIELD_TYPE, oblige `GetFieldValue` à déterminer le type de données C à partir du type de données SQL, en fonction du tableau suivant. Dans le cas contraire, vous pouvez spécifier directement le type de données ou choisir un type de données compatible ; par exemple, vous pouvez stocker n’importe quel type de données en SQL_C_CHAR.

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

Pour plus d’informations sur les types de données ODBC, consultez les thèmes « Types de données SQL » et « Types de données C » à l’annexe D du SDK Windows.

*nIndex*<br/>
L’indice zéro du champ.

*strValue*<br/>
Une référence à un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui stockera la valeur du champ convertie en texte, quel que soit le type de données du champ.

### <a name="remarks"></a>Notes

Vous pouvez rechercher un champ par nom ou par index. Vous pouvez stocker la valeur `CDBVariant` du `CString` champ dans un objet ou un objet.

Si vous avez implémenté la ligne en vrac, le dossier actuel est toujours positionné sur le premier enregistrement dans un ensemble de rangées. Pour `GetFieldValue` utiliser sur un enregistrement dans un jeu de ligne donné, vous devez d’abord appeler la fonction [membre SetRowsetCursorPosition](#setrowsetcursorposition) pour déplacer le curseur à la ligne désirée dans ce jeu de rangée. Alors `GetFieldValue` appelle à cette rangée. Pour implémenter la ramage `CRecordset::useMultiRowFetch` en vrac, vous devez spécifier l’option du paramètre *dwOptions* dans la fonction membre [Open.](#open)

Vous pouvez `GetFieldValue` utiliser pour aller chercher dynamiquement champs à l’heure de course plutôt que de les lier statiquement au moment de la conception. Par exemple, si vous avez déclaré `CRecordset`un objet `GetFieldValue` de recordet directement à partir , vous devez utiliser pour récupérer les données sur le terrain; l’échange record sur le terrain (RFX), ou échange de champ de disques en vrac (Bulk RFX), n’est pas mis en œuvre.

> [!NOTE]
> Si vous déclarez un objet de `CRecordset`la liste des documents sans en déduire, ne pas avoir la bibliothèque de cursor ODBC chargée. La bibliothèque de curseurs exige que le dossier ait au moins une colonne liée; cependant, lorsque `CRecordset` vous utilisez directement, aucune des colonnes n’est liée. Le membre fonctionne [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) et [CDatabase::Contrôle ouvert](../../mfc/reference/cdatabase-class.md#open) si la bibliothèque de curseur sera chargée.

`GetFieldValue`appelle la fonction `SQLGetData`API ODBC . Si votre pilote produit la valeur SQL_NO_TOTAL pour la durée `GetFieldValue` réelle de la valeur du champ, lance une exception. Pour plus `SQLGetData`d’informations sur , voir le Windows SDK.

### <a name="example"></a>Exemple

Le code d’échantillon `GetFieldValue` suivant illustre les appels `CRecordset`à un objet de recordet déclaré directement à partir de .

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> Contrairement à la `CDaoRecordset` `CRecordset` classe DAO `SetFieldValue` , n’a pas de fonction de membre. Si vous créez un `CRecordset`objet directement à partir , il est effectivement lu-seulement.

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount

Récupère le nombre total de champs dans votre objet de recordet.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de champs dans le dossier.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la création d’enregistrements, voir l’article [Recordset: Creating and Closing Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo

Obtient des informations sur les champs dans le dossier.

```cpp
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Le nom d’un champ.

*Fieldinfo*<br/>
Une référence `CODBCFieldInfo` à une structure.

*nIndex*<br/>
L’indice zéro du champ.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un champ par nom. L’autre version vous permet de rechercher un champ par index.

Pour une description de l’information retournée, consultez la structure [CODBCFieldInfo.](../../mfc/reference/codbcfieldinfo-structure.md)

Pour plus d’informations sur la création d’enregistrements, voir l’article [Recordset: Creating and Closing Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>CRecordset::GetRecordCount

Détermine la taille de l’enregistrement.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’enregistrements dans l’enregistrement; 0 si le registre ne contient pas d’enregistrements; ou -1 si le nombre d’enregistrements ne peut pas être déterminé.

### <a name="remarks"></a>Notes

> [!CAUTION]
> Le nombre d’enregistrements est maintenu comme une « marque d’eau élevée », l’enregistrement le plus élevé jamais vu lorsque l’utilisateur se déplace à travers les enregistrements. Le nombre total d’enregistrements n’est connu qu’après que l’utilisateur est allé au-delà du dernier enregistrement. Pour des raisons de performance, le `MoveLast`nombre n’est pas mis à jour lorsque vous appelez . Pour compter les enregistrements `MoveNext` vous-même, appelez à plusieurs reprises jusqu’à ce que `IsEOF` les retours nonzero. Ajout d’un enregistrement via `CRecordset:AddNew` et `Update` augmente le nombre; la suppression d’un enregistrement via `CRecordset::Delete` diminue le nombre.

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>CRecordset::GetRowsetSize

Obtient le paramètre actuel pour le nombre de lignes que vous souhaitez récupérer lors d’une remise en état.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de lignes à récupérer lors d’une remise d’un prix à l’autre.

### <a name="remarks"></a>Notes

Si vous utilisez la rame en vrac, la taille de l’ensemble de ligne par défaut lorsque le jeu d’enregistrement est ouvert est de 25; sinon, c’est 1.

Pour implémenter la ramage `CRecordset::useMultiRowFetch` en vrac, vous devez spécifier l’option dans le paramètre *dwOptions* de la fonction membre [Open.](#open) Pour modifier le paramètre pour la taille de l’acart, appelez [SetRowsetSize](#setrowsetsize).

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset::GetRowsFetched

Détermine le nombre d’enregistrements qui ont été effectivement récupérés après un aller chercher.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de lignes récupérées à partir de la source de données après une remise en jeu.

### <a name="remarks"></a>Notes

Ceci est utile lorsque vous avez implémenté la ligne en vrac aller chercher. La taille de l’aviron indique normalement combien de lignes seront récupérées à partir d’un aller chercher; cependant, le nombre total de lignes dans le jeu d’enregistrement affecte également le nombre de lignes qui seront récupérées dans un ensemble de rangées. Par exemple, si votre recordet a 10 enregistrements avec un réglage de taille encastré de 4, puis en boucle à travers le recordet en appelant `MoveNext` se traduira par le jeu de ligne finale ayant seulement 2 enregistrements.

Pour implémenter la ramage `CRecordset::useMultiRowFetch` en vrac, vous devez spécifier l’option dans le paramètre *dwOptions* de la fonction membre [Open.](#open) Pour spécifier la taille de l’acart, appelez [SetRowsetSize](#setrowsetsize).

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>CRecordset::GetRowStatus

Obtient le statut d’affilée dans le rowset actuel.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Paramètres

*wRow (wRow)*<br/>
La position à une seule ligne dans le rowset actuel. Cette valeur peut varier de 1 à la taille de l’acart.

### <a name="return-value"></a>Valeur de retour

Une valeur de statut pour la ligne. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

`GetRowStatus`retourne une valeur qui indique soit tout changement de statut à la ligne depuis qu’il a été récupéré pour la dernière fois à partir de la source de données, ou qu’aucune ligne correspondant à *wRow* n’a été récupérée. Le tableau ci-dessous répertorie les valeurs de retour possibles.

|Valeur d’état|Description|
|------------------|-----------------|
|SQL_ROW_SUCCESS|La ligne est inchangée.|
|SQL_ROW_UPDATED|La ligne a été mise à jour.|
|SQL_ROW_DELETED|La ligne a été supprimée.|
|SQL_ROW_ADDED|La rangée a été ajoutée.|
|SQL_ROW_ERROR|La ligne est irrésable en raison d’une erreur.|
|SQL_ROW_NOROW|Il n’y a pas de ligne qui correspond à *wRow*.|

Pour plus d’informations, consultez la `SQLExtendedFetch` fonction API ODBC dans le SDK Windows.

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset::GetStatus

Détermine l’indice du dossier actuel dans l’enregistrement et si le dernier enregistrement a été vu.

```cpp
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Paramètres

*rStatus*<br/>
Référence à un objet `CRecordsetStatus`. Pour plus d'informations, consultez la section Remarques.

### <a name="remarks"></a>Notes

`CRecordset`tentatives de suivre l’indice, mais dans certaines circonstances, cela peut ne pas être possible. Voir [GetRecordCompte](#getrecordcount) pour une explication.

La `CRecordsetStatus` structure a la forme suivante :

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Les deux `CRecordsetStatus` membres ont les significations suivantes :

- `m_lCurrentRecord`Contient l’indice zéro de l’enregistrement actuel dans l’enregistrement, s’il est connu. Si l’indice ne peut pas être déterminé, ce membre contient AFX_CURRENT_RECORD_UNDEFINED (-2). S’il `IsBOF` est VRAI (enregistrement vide ou tentative `m_lCurrentRecord` de faire défiler avant le premier enregistrement), puis est réglé pour AFX_CURRENT_RECORD_BOF (-1). Si sur le premier enregistrement, alors il est fixé à 0, deuxième record 1, et ainsi de suite.

- `m_bRecordCountFinal`Nonzero si le nombre total d’enregistrements dans le dossier a été déterminé. En général, cela doit être accompli en commençant `MoveNext` `IsEOF` au début de l’enregistrement et en appelant jusqu’à ce que retourne nonzero. Si ce membre est nul, le `GetRecordCount`nombre d’enregistrements retournés par , sinon -1, n’est qu’un nombre de « marques d’eau élevées » des dossiers.

## <a name="crecordsetgetsql"></a><a name="getsql"></a>CRecordset::GetSQL

Appelez cette fonction de membre pour obtenir la déclaration SQL qui a été utilisée pour sélectionner les dossiers du dossier lors de son ouverture.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence **const** à un `CString` qui contient la déclaration SQL.

### <a name="remarks"></a>Notes

Il s’agira généralement d’une déclaration **SQL SELECT.** La ficelle `GetSQL` retournée par est lu-seulement.

La chaîne `GetSQL` retournée par est généralement différente de n’importe quelle chaîne que vous pouvez `Open` avoir passé à l’ensemble d’enregistrements dans le paramètre *lpszSQL* à la fonction membre. C’est parce que le document construit une déclaration SQL complète basée sur ce que vous avez passé à `Open`, ce que vous avez spécifié avec ClassWizard, ce que vous avez peut-être spécifié dans les `m_strFilter` membres et `m_strSort` les données, et tous les paramètres que vous avez peut-être spécifié. Pour plus de détails sur la façon dont le document construit cette déclaration SQL, voir l’article [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
> Appelez cette fonction de membre seulement après avoir appelé [Open](#open).

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>CRecordset::GetTableName

Obtient le nom de la table SQL sur laquelle la requête du recordet est basée.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence **const** à un `CString` qui contient le nom de table, si le tableau est basé sur une table; sinon, une ficelle vide.

### <a name="remarks"></a>Notes

`GetTableName`n’est valide que si le tableau d’enregistrement est basé sur une table, et non sur une jointure de plusieurs tables ou une requête prédéfinie (procédure stockée). Le nom est lu uniquement.

> [!NOTE]
> Appelez cette fonction de membre seulement après avoir appelé [Open](#open).

## <a name="crecordsetisbof"></a><a name="isbof"></a>CRecordset::IsBOF

Retourne nonzero si le recordet a été positionné avant le premier enregistrement. Aucun enregistrement actif.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet ne contient pas d’enregistrements ou si vous avez fait défiler vers l’arrière avant le premier enregistrement; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre avant de faire défiler de l’enregistrement à l’enregistrement pour savoir si vous êtes allé avant le premier enregistrement de l’enregistrement. Vous pouvez `IsBOF` également `IsEOF` utiliser avec pour déterminer si le jeu d’enregistrement contient des enregistrements ou est vide. Immédiatement après `Open`votre appel, si le `IsBOF` recordet ne contient pas d’enregistrements, renvoie nonzero. Lorsque vous ouvrez un record qui a au moins un `IsBOF` enregistrement, le premier enregistrement est le record actuel et retourne 0.

Si le premier enregistrement est l’enregistrement actuel et que vous appelez, `MovePrev` `IsBOF` retournera par la suite nonzero. Si `IsBOF` les retours nonzero et vous appelez, `MovePrev`une erreur se produit. Si `IsBOF` les déclarations non zéro, l’enregistrement actuel n’est pas défini, et toute action qui nécessite un enregistrement actuel entraînera une erreur.

### <a name="example"></a>Exemple

Cet exemple `IsBOF` `IsEOF` utilise et détecte les limites d’un enregistrement lorsque le code défile le numéro dans les deux directions.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset::IsDeleted

Détermine si l’enregistrement actuel a été supprimé.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet est positionné sur un enregistrement supprimé; sinon 0.

### <a name="remarks"></a>Notes

Si vous faites défiler vers un enregistrement et `IsDeleted` retourne TRUE (nonzero), alors vous devez faire défiler vers un autre enregistrement avant de pouvoir effectuer d’autres opérations de nombre d’enregistrements.

Le résultat `IsDeleted` dépend de nombreux facteurs, tels que votre type de dossier, si `CRecordset::skipDeletedRecords` votre pack est updatable, si vous avez spécifié l’option lorsque vous avez ouvert le dossier, si vos packs de pilote supprimés enregistrements, et s’il ya plusieurs utilisateurs.

Pour plus `CRecordset::skipDeletedRecords` d’informations sur et l’emballage des pilotes, consultez la fonction membre [Open.](#open)

> [!NOTE]
> Si vous avez implémenté la `IsDeleted`ligne en vrac aller chercher, vous ne devriez pas appeler . Au lieu de cela, appelez la fonction membre [GetRowStatus.](#getrowstatus) Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetiseof"></a><a name="iseof"></a>CRecordset::IsEOF

Retourne nonzero si le recordet a été positionné après le dernier enregistrement. Aucun enregistrement actif.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet ne contient pas d’enregistrements ou si vous avez fait défiler au-delà du dernier enregistrement; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pendant que vous faites défiler d’enregistrement à enregistrement pour savoir si vous êtes allé au-delà du dernier enregistrement de l’enregistrement. Vous pouvez `IsEOF` également utiliser pour déterminer si le jeu d’enregistrement contient des enregistrements ou est vide. Immédiatement après `Open`votre appel, si le `IsEOF` recordet ne contient pas d’enregistrements, renvoie nonzero. Lorsque vous ouvrez un record qui a au moins un `IsEOF` enregistrement, le premier enregistrement est le record actuel et retourne 0.

Si le dernier enregistrement est l’enregistrement actuel lorsque vous appelez, `MoveNext` `IsEOF` retournera par la suite nonzero. Si `IsEOF` les retours nonzero et vous appelez, `MoveNext`une erreur se produit. Si `IsEOF` les déclarations non zéro, l’enregistrement actuel n’est pas défini, et toute action qui nécessite un enregistrement actuel entraînera une erreur.

### <a name="example"></a>Exemple

Voir l’exemple pour [IsBOF](#isbof).

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>CRecordset::IsFieldDirty

Détermine si le membre spécifié des données sur le terrain a été modifié depuis [l’appel d’Edit](#edit) ou [AddNew.](#addnew)

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Un pointeur pour le membre des données sur le terrain dont vous souhaitez vérifier le statut, ou NULL pour déterminer si l’un des champs sont sales.

### <a name="return-value"></a>Valeur de retour

Nonzero si le membre spécifié des `AddNew` `Edit`données sur le terrain a changé depuis l’appel ou ; sinon 0.

### <a name="remarks"></a>Notes

Les données dans tous les membres de données de champ sale seront transférées au dossier sur la source de `Edit` `AddNew`données lorsque l’enregistrement actuel est mis à jour par un appel à la fonction membre de mise à [jour](#update) de `CRecordset` (suite à un appel à ou à ).

> [!NOTE]
> Cette fonction de membre n’est pas applicable sur les enregistrements qui utilisent la ligne en vrac. Si vous avez mis en `IsFieldDirty` œuvre la ligne en vrac aller chercher, alors retournera toujours FALSE et se traduira par une affirmation échouée. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

L’appel `IsFieldDirty` réinitialisera les effets des appels précédents à [SetFieldDirty](#setfielddirty) puisque le statut sale du champ est réévalué. Dans `AddNew` le cas, si la valeur de champ actuelle diffère de la valeur pseudo nulle, l’état du champ est mis sale. Dans `Edit` le cas, si la valeur du champ diffère de la valeur mise en cache, alors l’état du champ est mis sale.

`IsFieldDirty`est implémenté par [DoFieldExchange](#dofieldexchange).

Pour plus d’informations sur le drapeau sale, voir l’article [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>CRecordset::IsFieldNull

Retourne nonzero si le champ spécifié dans le dossier actuel est Null (n’a aucune valeur).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Un pointeur pour le membre des données sur le terrain dont vous souhaitez vérifier le statut, ou NULL pour déterminer si l’un des champs sont nuls.

### <a name="return-value"></a>Valeur de retour

Nonzero si le membre spécifié des données sur le terrain est signalé comme Null; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour déterminer si le membre spécifié des données sur le terrain d’un jeu d’enregistrement a été signalé comme null. (Dans la terminologie de la base de données, Null signifie « n’avoir aucune valeur » et n’est pas le même que NULL dans C.) Si un membre des données sur le terrain est signalé comme null, il est interprété comme une colonne de l’enregistrement actuel pour lequel il n’y a aucune valeur.

> [!NOTE]
> Cette fonction de membre n’est pas applicable sur les enregistrements qui utilisent la ligne en vrac. Si vous avez mis en `IsFieldNull` œuvre la ligne en vrac aller chercher, alors retournera toujours FALSE et se traduira par une affirmation échouée. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull`est implémenté par [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CRecordset::IsFieldNullable

Retourne nonzero si le champ spécifié dans l’enregistrement actuel peut être réglé à Null (n’ayant aucune valeur).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Un pointeur pour le membre des données sur le terrain dont vous souhaitez vérifier le statut, ou NULL pour déterminer si l’un des champs peut être réglé à une valeur nulle.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour déterminer si le membre spécifié des données sur le terrain est « nul » (peut être réglé à une valeur nulle; LE NULL n’est pas le même que Null, ce qui, selon la terminologie de la base de données, signifie « n’avoir aucune valeur »).

> [!NOTE]
> Si vous avez implémenté la `IsFieldNullable`ligne en vrac aller chercher, vous ne pouvez pas appeler . Au lieu de cela, appelez la fonction membre [GetODBCFieldInfo](#getodbcfieldinfo) pour déterminer si un champ peut être réglé à une valeur nulle. Notez que vous `GetODBCFieldInfo`pouvez toujours appeler, peu importe si vous avez implémenté la ligne en vrac aller chercher. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Un champ qui ne peut pas être Null doit avoir une valeur. Si vous essayez de définir un tel champ à Null lors de l’ajout ou de la mise à jour d’un enregistrement, la source de données rejette l’ajout ou la mise à jour, et [Update](#update) lancera une exception. L’exception se `Update`produit lorsque vous appelez , pas lorsque vous appelez [SetFieldNull](#setfieldnull).

L’utilisation de NULL pour le premier argument `outputColumn` de `param` la fonction n’appliquera la fonction qu’aux champs, et non aux champs. Par exemple, l’appel

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

ne fixera que `outputColumn` des champs à NULL; `param` champs ne seront pas affectés.

Pour travailler `param` sur des champs, vous devez `param` fournir l’adresse réelle de la personne sur laquelle vous souhaitez travailler, comme :

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Cela signifie que `param` vous ne pouvez pas `outputColumn` définir tous les champs à NULL, comme vous le pouvez avec les champs.

`IsFieldNullable`est implémenté par [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset::IsOpen

Détermine si le recordet est déjà ouvert.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction de membre [Open](#open) ou [Requery](#requery) de l’objet de l’enregistrement a déjà été appelée et que le recordet n’a pas été fermé; sinon 0.

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CRecordset::m_hstmt

Contient une poignée à la structure de données de relevé oDBC, de type HSTMT, associée à l’enregistrement.

### <a name="remarks"></a>Notes

Chaque requête à une source de données ODBC est associée à un HSTMT.

> [!CAUTION]
> Ne pas `m_hstmt` utiliser avant [Open](#open) a été appelé.

Normalement, vous n’avez pas besoin d’accéder directement au HSTMT, mais vous pourriez en avoir besoin pour l’exécution directe des relevés SQL. La `ExecuteSQL` fonction membre `CDatabase` de la `m_hstmt`classe fournit un exemple d’utilisation .

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset::m_nFields

Contient le nombre de membres des données sur le terrain dans la classe des documents; c’est-à-dire le nombre de colonnes sélectionnées par le recordet à partir de la source de données.

### <a name="remarks"></a>Notes

Le constructeur de la classe de `m_nFields` la série d’enregistrements doit être initialisé avec le bon numéro. Si vous n’avez pas implémenté la ligne en vrac, ClassWizard écrit cette initialisation pour vous lorsque vous l’utilisez pour déclarer votre classe de recordet. Vous pouvez également l’écrire manuellement.

Le cadre utilise ce nombre pour gérer l’interaction entre les membres des données sur le terrain et les colonnes correspondantes de l’enregistrement actuel sur la source de données.

> [!CAUTION]
> Ce numéro doit correspondre au nombre de `DoFieldExchange` " `DoBulkFieldExchange` colonnes de sortie " enregistrées dans ou après un appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) avec le paramètre `CFieldExchange::outputColumn`.

Vous pouvez lier les colonnes dynamiquement, comme expliqué dans l’article "Recordset: Dynamically Binding Data Columns." Si vous le faites, vous `m_nFields` devez augmenter le nombre pour refléter le nombre d’appels de fonction RFX ou RFX en vrac dans votre `DoFieldExchange` fonction ou `DoBulkFieldExchange` partie pour les colonnes dynamiquement liées.

Pour plus d’informations, voir les articles [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) et [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

Voir l’article [Record Field Exchange: Using RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CRecordset::m_nParams

Contient le nombre de paramètres membres dans la classe des enregistrements; c’est-à-dire le nombre de paramètres passés avec la requête du recordet.

### <a name="remarks"></a>Notes

Si votre classe de nombre a des membres de données `m_nParams` de paramètres, le constructeur de la classe doit être parastérisé avec le bon numéro. La valeur `m_nParams` des défauts à 0. Si vous ajoutez des membres de données de paramètres (que vous devez faire manuellement), vous devez également ajouter manuellement une initialisation dans le constructeur de `m_strFilter` `m_strSort` classe pour refléter le nombre de paramètres (qui doivent être au moins aussi grand que le nombre de «» placesholders dans votre ou chaîne).

Le cadre utilise ce nombre lorsqu’il paramélise la requête du recordet.

> [!CAUTION]
> Ce numéro doit correspondre au nombre de "params" enregistrés dans `DoFieldExchange` ou `DoBulkFieldExchange` après un appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) avec une valeur de paramètres de `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, ou `CFieldExchange::inoutParam`.

### <a name="example"></a>Exemple

  Voir les articles [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) et [Record Field Exchange: Using RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset::m_pDatabase

Contient un pointeur sur l’objet `CDatabase` par lequel le jeu d’enregistrement est connecté à une source de données.

### <a name="remarks"></a>Notes

Cette variable est définie de deux façons. En règle générale, vous passez `CDatabase` un pointeur à un objet déjà connecté lorsque vous construisez l’objet de l’enregistrement. Si vous passez NULL `CRecordset` à `CDatabase` la place, crée un objet pour vous et le connecte. Dans les `CRecordset` deux cas, stocke le pointeur dans cette variable.

Normalement, vous n’aurez pas directement `m_pDatabase`besoin d’utiliser le pointeur stocké dans . Si vous écrivez vos `CRecordset`propres extensions à , cependant, vous pourriez avoir besoin d’utiliser le pointeur. Par exemple, vous pourriez avoir besoin `CDBException`du pointeur si vous lancez votre propre s. Ou vous pourriez en avoir besoin si `CDatabase` vous avez besoin de faire quelque chose en `ExecuteSQL` utilisant le `CDatabase` même objet, comme l’exécution des transactions, l’établissement des délais, ou d’appeler la fonction membre de la classe pour exécuter les déclarations SQL directement.

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CRecordset::m_strFilter

Après avoir construit l’objet de la `Open` liste d’enregistrement, mais `CString` avant d’appeler sa fonction de membre, utilisez ce membre de données pour stocker une clause SQL **WHERE** contenant.

### <a name="remarks"></a>Notes

Le groupe d’enregistrement utilise cette chaîne pour limiter (ou `Requery` filtrer) les enregistrements qu’il sélectionne au cours de l’appel ou l’appeler. `Open` Ceci est utile pour choisir un sous-ensemble d’enregistrements, tels que «tous les vendeurs basés en Californie» («état - CA»). La syntaxe SQL ODBC pour une clause **WHERE** est

`WHERE search-condition`

Notez que vous n’incluez pas le mot clé **WHERE** dans votre chaîne. Le cadre le fournit.

Vous pouvez également paramétiser votre chaîne de filtre en y plaçant des espaces « » qui y sont réservés, en déclarant un membre des données de paramètres dans votre catégorie pour chaque placeholder et en passant les paramètres à l’ensemble d’enregistrements au moment de l’exécution. Cela vous permet de construire le filtre au moment de l’exécution. Pour plus d’informations, voir l’article [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Pour plus d’informations sur SQL **WHERE** clauses, voir l’article [SQL](../../data/odbc/sql.md). Pour plus d’informations sur la sélection et le filtrage des enregistrements, voir l’article [Recordset: Filtering Records (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset::m_strSort

Après avoir construit l’objet de la `Open` liste d’enregistrement, mais `CString` avant d’appeler sa fonction de membre, utilisez ce membre de données pour stocker une clause DE **CORRESPONDANCE APPROPRIÉE.**

### <a name="remarks"></a>Notes

Le groupe d’enregistrement utilise cette chaîne pour `Open` `Requery` trier les enregistrements qu’il sélectionne au cours de l’appel ou l’appel. Vous pouvez utiliser cette fonctionnalité pour trier un jeu d’enregistrements sur une ou plusieurs colonnes. La syntaxe SQL ODBC pour une clause **ORDER BY** est

`ORDER BY sort-specification [, sort-specification]...`

lorsqu’une spécification de tri est un nom d’intégrant ou de colonne. Vous pouvez également spécifier l’ordre ascendant ou descendant (l’ordre monte par défaut) en appending "ASC" ou "DESC" à la liste de colonnes dans la chaîne de tri. Les enregistrements sélectionnés sont triés d’abord par la première colonne répertoriée, puis par la seconde, et ainsi de suite. Par exemple, vous pouvez commander un enregistrement "Clients" par nom de famille, puis prénom. Le nombre de colonnes que vous pouvez énumérer dépend de la source de données. Pour plus d’informations, voir le Windows SDK.

Notez que vous n’incluez pas le mot clé **ORDER BY** dans votre chaîne. Le cadre le fournit.

Pour plus d’informations sur les clauses SQL, voir l’article [SQL](../../data/odbc/sql.md). Pour plus d’informations sur les enregistrements de tri, voir l’article [Recordset: Triing Records (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>CRecordset::Déplacer

Déplace le pointeur d’enregistrement actuel dans le dossier, soit vers l’avant ou vers l’arrière.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Paramètres

*nRows*<br/>
Le nombre de rangées pour aller de l’avant ou vers l’arrière. Les valeurs positives avancent, vers la fin de l’enregistrement. Les valeurs négatives reculent, vers le début.

*wFetchType (en)*<br/>
Détermine le rame `Move` qui va chercher. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Si vous passez une valeur de 0 `Move` pour *nRows*, rafraîchit le record actuel; `Move` mettra fin `AddNew` à `Edit` tout courant ou mode, et `AddNew` restaurera la valeur de l’enregistrement actuel avant ou `Edit` a été appelé.

> [!NOTE]
> Lorsque vous passez par un enregistrement, vous ne pouvez pas sauter les enregistrements supprimés. Voir [CRecordset:IsDeleted](#isdeleted) pour plus d’informations. Lorsque vous `CRecordset` ouvrez `skipDeletedRecords` un `Move` avec l’ensemble d’option, affirme si le paramètre *nRows* est de 0. Ce comportement empêche la remise en état des lignes qui sont supprimées par d’autres applications client à l’aide des mêmes données. Voir le *paramètre dwOption* dans `skipDeletedRecords` [Open](#open) pour une description de .

`Move`repositionne le recordet par des rames. Basé sur les valeurs pour *les nRows* et *wFetchType*, `Move` récupère le rowset approprié et fait ensuite le premier enregistrement dans ce rowset le record actuel. Si vous n’avez pas implémenté la ligne en vrac aller chercher, alors la taille rowset est toujours 1. Lorsque vous allez chercher `Move` un aviron, appelle directement la fonction membre [CheckRowsetError](#checkrowseterror) pour gérer les erreurs résultant de l’aller chercher.

Selon les valeurs que `Move` vous transmettez, est équivalent à d’autres `CRecordset` fonctions membres. En particulier, la valeur de *wFetchType* peut indiquer une fonction de membre qui est plus intuitive et souvent la méthode préférée pour déplacer le dossier actuel.

Le tableau suivant énumère les valeurs possibles pour *wFetchType*, le `Move` rowset qui va chercher en fonction de *wFetchType* et *nRows*, et toute fonction de membre équivalent correspondant à *wFetchType*.

|wFetchType (en)|Encastré|Fonction de membre équivalent|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (la valeur par défaut)|La ligne de départ *nRows* ligne (s) de la première rangée dans le rowset actuel.||
|SQL_FETCH_NEXT|Le rame suivant; *nRows* est ignoré.|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|Le rame précédent; *nRows* est ignoré.|[MovePrev (en)](#moveprev)|
|SQL_FETCH_FIRST|Le premier jeu de ligne dans le jeu d’enregistrement; *nRows* est ignoré.|[MoveFirst (en)](#movefirst)|
|SQL_FETCH_LAST|Le dernier rame complet dans le jeu d’enregistrement; *nRows* est ignoré.|[MoveLast (en)](#movelast)|
|SQL_FETCH_ABSOLUTE|Si *nRows* > 0, la ligne de départ *nRows* ligne (s) depuis le début de l’enregistrement. Si *nRows* < 0, la ligne de départ *nRows* ligne (s) de la fin de l’enregistrement. Si *nRows* 0, alors une condition de début de fichier (BOF) est retournée.|[SetAbsolutePosition (setAbsolutePosition)](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Le rowset à partir de la ligne dont la valeur de signet correspond à *nRows*.|[SetBookmark SetBookmark SetBookmark SetBook](#setbookmark)|

> [!NOTE]
> Pour les enregistrements avant-seulement, `Move` n’est valable qu’avec une valeur de SQL_FETCH_NEXT pour *wFetchType*.

> [!CAUTION]
> Appeler `Move` jette une exception si le recordet n’a pas de dossiers. Pour déterminer si le recordet a des enregistrements, appelez [IsBOF](#isbof) et [IsEOF](#iseof).

> [!NOTE]
> Si vous avez fait défiler au-delà`IsBOF` du `IsEOF` début ou de `Move` la fin de `CDBException`l’enregistrement (ou retourne nonzero), appeler une fonction sera peut-être jeter un . Par exemple, `IsEOF` si les `IsBOF` retours nonzero et ne le fait pas, alors `MoveNext` jetez une exception, mais `MovePrev` ne sera pas.

> [!NOTE]
> Si vous `Move` appelez pendant la mise à jour ou l’ajout de l’enregistrement actuel, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation de recordset, voir les articles [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus d’informations connexes, consultez `SQLExtendedFetch` la fonction API ODBC dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>CRecordset::MoveFirst

Fait le premier enregistrement dans la première rangée le record actuel.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Notes

Peu importe si la mise en œuvre de la ligne en vrac a été mise en œuvre, ce sera toujours le premier enregistrement dans le dossier.

Vous n’avez `MoveFirst` pas à appeler immédiatement après avoir ouvert le dossier. À ce moment-là, le premier enregistrement (le cas échéant) est automatiquement l’enregistrement actuel.

> [!NOTE]
> Cette fonction de membre n’est pas valide pour les enregistrements avant-seulement.

> [!NOTE]
> Lorsque vous passez par un enregistrement, vous ne pouvez pas sauter les enregistrements supprimés. Consultez la fonction membre [IsDeleted](#isdeleted) pour plus de détails.

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. Pour déterminer si le dossier a `IsBOF` `IsEOF`des dossiers, appelez et .

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation de recordset, voir les articles [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsBOF](#isbof).

## <a name="crecordsetmovelast"></a><a name="movelast"></a>CRecordset::MoveLast

Fait le premier enregistrement dans le dernier rowset complet le record actuel.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas implémenté la ligne en vrac `MoveLast` aller chercher, votre recordet a une taille rowset de 1, donc se déplace simplement vers le dernier enregistrement dans le jeu d’enregistrement.

> [!NOTE]
> Cette fonction de membre n’est pas valide pour les enregistrements avant-seulement.

> [!NOTE]
> Lorsque vous passez par un enregistrement, vous ne pouvez pas sauter les enregistrements supprimés. Consultez la fonction membre [IsDeleted](#isdeleted) pour plus de détails.

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. Pour déterminer si le dossier a `IsBOF` `IsEOF`des dossiers, appelez et .

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation de recordset, voir les articles [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsBOF](#isbof).

## <a name="crecordsetmovenext"></a><a name="movenext"></a>CRecordset::MoveNext

Fait le premier enregistrement dans le prochain rowset le record actuel.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas implémenté la ligne en vrac `MoveNext` aller chercher, votre recordet a une taille rowset de 1, donc il suffit de se déplacer à l’enregistrement suivant.

> [!NOTE]
> Lorsque vous passez par un enregistrement, vous ne pouvez pas sauter les enregistrements supprimés. Consultez la fonction membre [IsDeleted](#isdeleted) pour plus de détails.

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. Pour déterminer si le dossier a `IsBOF` `IsEOF`des dossiers, appelez et .

> [!NOTE]
> Il est également recommandé `IsEOF` que `MoveNext`vous appeliez avant d’appeler . Par exemple, si vous avez fait défiler `IsEOF` au-delà de la fin de l’enregistrement, retournera nonzero; un appel `MoveNext` ultérieur pour jeter une exception.

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation de recordset, voir les articles [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsBOF](#isbof).

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>CRecordset::MovePrev

Fait le premier enregistrement dans le rowset précédent le record actuel.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas implémenté la ligne en vrac `MovePrev` aller chercher, votre recordet a une taille rowset de 1, donc se déplace simplement à l’enregistrement précédent.

> [!NOTE]
> Cette fonction de membre n’est pas valide pour les enregistrements avant-seulement.

> [!NOTE]
> Lorsque vous passez par un enregistrement, vous ne pouvez pas sauter les enregistrements supprimés. Consultez la fonction membre [IsDeleted](#isdeleted) pour plus de détails.

> [!CAUTION]
> Appeler l’une `Move` des fonctions jette une exception si le recordet n’a pas d’enregistrements. Pour déterminer si le dossier a `IsBOF` `IsEOF`des dossiers, appelez et .

> [!NOTE]
> Il est également recommandé `IsBOF` que `MovePrev`vous appeliez avant d’appeler . Par exemple, si vous avez fait défiler avant `IsBOF` le début de l’enregistrement, retournera nonzero; un appel `MovePrev` ultérieur pour jeter une exception.

> [!NOTE]
> Si vous appelez `Move` l’une des fonctions pendant que l’enregistrement actuel est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.

Pour plus d’informations sur la navigation de recordset, voir les articles [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsBOF](#isbof).

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset::OnSetOptions

Appelé à définir des options (utilisées sur la sélection) pour l’énoncé spécifié de l’ODBC.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*hstmt*<br/>
Le HSTMT de la déclaration ODBC dont les options doivent être définies.

### <a name="remarks"></a>Notes

Appelez `OnSetOptions` pour définir les options (utilisées sur la sélection) pour l’énoncé ODBC spécifié. Le cadre appelle cette fonction membre à définir les options initiales pour le jeu d’enregistrement. `OnSetOptions`détermine le support de la source de données pour les curseurs défilants et pour la concurrence du curseurur et définit les options du recordet en conséquence. (Considérant `OnSetOptions` qu’il est `OnSetUpdateOptions` utilisé pour les opérations de sélection, est utilisé pour les opérations de mise à jour.)

Remplacement `OnSetOptions` des options de définis spécifiques au conducteur ou à la source de données. Par exemple, si votre source de données prend `OnSetOptions` en charge l’ouverture pour un accès exclusif, vous pouvez remplacer pour profiter de cette capacité.

Pour plus d’informations sur les curseurs, voir l’article [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions

Appelé à définir des options (utilisées sur la mise à jour) pour l’énoncé spécifié ODBC.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*hstmt*<br/>
Le HSTMT de la déclaration ODBC dont les options doivent être définies.

### <a name="remarks"></a>Notes

Appelez `OnSetUpdateOptions` pour définir les options (utilisées sur la mise à jour) pour l’énoncé spécifié ODBC. Le cadre appelle cette fonction de membre après qu’il crée un HSTMT pour mettre à jour les enregistrements dans un dossier. (Considérant `OnSetOptions` qu’il est `OnSetUpdateOptions` utilisé pour les opérations de sélection, est utilisé pour les opérations de mise à jour.) `OnSetUpdateOptions` détermine le support de la source de données pour les curseurs défilants et pour la concurrence du curseurur et définit les options du recordet en conséquence.

Remplacement `OnSetUpdateOptions` des options de définie d’une déclaration ODBC avant que cette déclaration ne soit utilisée pour accéder à une base de données.

Pour plus d’informations sur les curseurs, voir l’article [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetopen"></a><a name="open"></a>CRecordset::Ouvert

Ouvre le tableau d’enregistrement en récupérant la table ou en exécutant la requête que représente le recordet.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Paramètres

*nOpenType (en)*<br/>
Acceptez la valeur par défaut, AFX_DB_USE_DEFAULT_TYPE ou utilisez l’une des valeurs suivantes à partir de la `enum OpenType`:

- `CRecordset::dynaset`Un recordet avec défilement bidirectionnel. L’adhésion et la commande des enregistrements sont déterminées lorsque le jeu d’enregistrement est ouvert, mais les modifications apportées par d’autres utilisateurs aux valeurs de données sont visibles à la suite d’une opération d’aller chercher. Les dynasets sont également connus sous le nom de records pilotés par keyset.

- `CRecordset::snapshot`Un ensemble d’enregistrements statique avec défilement bidirectionnel. L’adhésion et la commande des dossiers sont déterminées lorsque le dossier est ouvert; les valeurs de données sont déterminées lorsque les enregistrements sont récupérés. Les modifications apportées par d’autres utilisateurs ne sont pas visibles jusqu’à ce que le recordet soit fermé, puis rouvert.

- `CRecordset::dynamic`Un recordet avec défilement bidirectionnel. Les modifications apportées par d’autres utilisateurs à l’adhésion, à la commande et aux valeurs de données sont visibles à la suite d’une opération d’aller chercher. Notez que de nombreux conducteurs de l’ODBC ne prennent pas en charge ce type d’enregistrement.

- `CRecordset::forwardOnly`Un recordet de lecture seulement avec seulement défilement vers l’avant.

   Pour `CRecordset`, la `CRecordset::snapshot`valeur par défaut est . Le mécanisme de valeur par défaut permet aux assistants Visual `CRecordset` CMD `CDaoRecordset`d’interagir avec ODBC et DAO , qui ont des défauts différents.

Pour plus d’informations sur ces types de documents, voir l’article [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour obtenir des informations connexes, consultez l’article « Using Block and Scrollable Cursors » dans le SDK Windows.

> [!CAUTION]
> Si le type demandé n’est pas pris en charge, le cadre prévoit une exception.

*lpszSQL*<br/>
Un pointeur de chaîne contenant l’un des éléments suivants :

- Un pointeur NULL.

- Nom d'une table.

- Une déclaration SQL **SELECT** (optionnelle avec une clause SQL **WHERE** ou **ORDER BY).**

- Une déclaration **DE CALL** précisant le nom d’une requête prédéfinie (procédure stockée). Veillez à ce que vous n’insérez pas d’espace blanc entre l’accolade bouclée et le mot clé **CALL.**

Pour plus d’informations sur cette chaîne, voir la table et la discussion du rôle de ClassWizard dans la section [Remarques.](#remarks)

> [!NOTE]
> L’ordre des colonnes dans votre ensemble de résultat doit correspondre à l’ordre des appels de fonction RFX ou Bulk RFX dans votre fonction [DoFieldExchange](#dofieldexchange) ou [DoBulkFieldExchange.](#dobulkfieldexchange)

*dwOptions*<br/>
Un bitmask qui peut spécifier une combinaison des valeurs énumérées ci-dessous. Certains d’entre eux sont mutuellement exclusifs. La valeur par défaut **n’est pas**.

- `CRecordset::none`Aucune option définie. Cette valeur de paramètre s’exclut mutuellement de toutes les autres valeurs. Par défaut, le jeu d’enregistrement peut être mis à jour avec [Modifier](#edit) ou [Supprimer](#delete) et permet d’ajouter de nouveaux enregistrements avec [AddNew](#addnew). L’updatabilité dépend de la source de données ainsi que de *l’option nOpenType* que vous spécifiez. L’optimisation des ajouts en vrac n’est pas disponible. La mise à l’alliage en vrac ne sera pas mise en œuvre. Les enregistrements supprimés ne seront pas ignorés pendant la navigation de recordset. Les signets ne sont pas disponibles. La vérification automatique du champ sale est implémentée.

- `CRecordset::appendOnly`Ne pas `Edit` `Delete` autoriser ou sur l’enregistrement. Autoriser `AddNew` seulement. Cette option est mutuellement `CRecordset::readOnly`exclusive avec .

- `CRecordset::readOnly`Ouvrez le recordet comme lu uniquement. Cette option est mutuellement `CRecordset::appendOnly`exclusive avec .

- `CRecordset::optimizeBulkAdd`Utilisez une déclaration SQL préparée pour optimiser l’ajout de nombreux enregistrements en même temps. S’applique uniquement si vous n’utilisez `SQLSetPos` pas la fonction API ODBC pour mettre à jour le dossier. La première mise à jour détermine quels champs sont marqués sales. Cette option est mutuellement `CRecordset::useMultiRowFetch`exclusive avec .

- `CRecordset::useMultiRowFetch`Implémentez l’aller chercher en vrac pour permettre de récupérer plusieurs rangées en une seule opération d’aller chercher. Il s’agit d’une fonctionnalité avancée conçue pour améliorer les performances; cependant, l’échange de records en vrac sur le terrain n’est pas soutenu par ClassWizard. Cette option est mutuellement `CRecordset::optimizeBulkAdd`exclusive avec . Notez que `CRecordset::useMultiRowFetch`si vous `CRecordset::noDirtyFieldCheck` spécifiez, alors l’option sera activée automatiquement (double tampon ne sera pas disponible); sur les enregistrements à terme `CRecordset::useExtendedFetch` seulement, l’option sera activée automatiquement. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords`Passer tous les enregistrements supprimés lors de la navigation à travers le dossier. Cela ralentira les performances dans certains allers-retours relatifs. Cette option n’est pas valable sur les enregistrements avant seuls. Si vous appelez [Move](#move) avec le paramètre *nRows* réglé à 0, et l’option `CRecordset::skipDeletedRecords` définie, `Move` s’affirmera. Notez `CRecordset::skipDeletedRecords` que c’est similaire à *l’emballage du conducteur*, ce qui signifie que les lignes supprimées sont supprimées de l’enregistrement. Toutefois, si votre pilote emballe des enregistrements, alors il ne sautera que les enregistrements que vous supprimez; il ne sautera pas les enregistrements supprimés par d’autres utilisateurs pendant que le recordet est ouvert. `CRecordset::skipDeletedRecords`sautera les lignes supprimées par d’autres utilisateurs.

- `CRecordset::useBookmarks`Peut utiliser des signets sur l’éterlet, s’il est pris en charge. Les signets ralentissent la récupération des données, mais améliorent les performances de la navigation des données. Non valide sur les enregistrements avant seuls. Pour plus d’informations, voir l’article [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck`Éteignez la vérification automatique du champ sale (double tampon). Cela améliorera les performances; cependant, vous devez marquer manuellement les `SetFieldDirty` `SetFieldNull` champs comme sales en appelant les fonctions et les membres. Notez que le `CRecordset` double tampon en classe `CDaoRecordset`est similaire à la double mise en mémoire tampon en classe . Cependant, `CRecordset`dans, vous ne pouvez pas activer la double mise en mémoire tampon sur des champs individuels; vous l’activez pour tous les champs ou le désactiver pour tous les champs. Notez que si `CRecordset::useMultiRowFetch`vous `CRecordset::noDirtyFieldCheck` spécifiez l’option, alors sera activé automatiquement; cependant, `SetFieldDirty` `SetFieldNull` et ne peut pas être utilisé sur les enregistrements qui implémentent la rame en vrac.

- `CRecordset::executeDirect`N’utilisez pas de relevé SQL préparé. Pour améliorer les performances, `Requery` spécifiez cette option si la fonction membre ne sera jamais appelée.

- `CRecordset::useExtendedFetch`Implémenter `SQLExtendedFetch` au lieu de `SQLFetch`. Ceci est conçu pour mettre en œuvre la ligne en vrac aller chercher sur les enregistrements avant-seulement. Si vous spécifiez l’option `CRecordset::useMultiRowFetch` `CRecordset::useExtendedFetch` sur un dossier avant seulement, alors sera activé automatiquement.

- `CRecordset::userAllocMultiRowBuffers`L’utilisateur allouera des tampons de stockage pour les données. Utilisez cette option `CRecordset::useMultiRowFetch` en conjonction avec si vous souhaitez allouer votre propre stockage; sinon, le cadre allouera automatiquement le stockage nécessaire. Pour plus d’informations, voir l’article [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Notez que `CRecordset::userAllocMultiRowBuffers` le `CRecordset::useMultiRowFetch` spécifier sans spécifier entraînera un échec de l’affirmation.

### <a name="return-value"></a>Valeur de retour

Nonzero si `CRecordset` l’objet a été ouvert avec succès; autrement 0 si [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (si appelé) retourne 0.

### <a name="remarks"></a>Notes

Vous devez appeler cette fonction de membre pour exécuter la requête définie par l’enregistrement. Avant `Open`d’appeler, vous devez construire l’objet de l’enregistrement.

La connexion de ce recordet à la source de données `Open`dépend de la façon dont vous construisez le jeu d’enregistrement avant d’appeler . Si vous passez un objet [CDatabase](../../mfc/reference/cdatabase-class.md) au constructeur de documents qui n’a pas été connecté à la source de données, cette fonction membre utilise [GetDefaultConnect](#getdefaultconnect) pour tenter d’ouvrir l’objet de base de données. Si vous passez NULL au constructeur de l’ensemble `CDatabase` d’enregistrements, `Open` le constructeur construit un objet pour vous et tente de connecter l’objet de base de données. Pour plus de détails sur la clôture de l’ensemble d’enregistrements et la connexion dans ces circonstances variables, voir [Close](#close).

> [!NOTE]
> L’accès à une `CRecordset` source de données via un objet est toujours partagé. Contrairement `CDaoRecordset` à la classe, `CRecordset` vous ne pouvez pas utiliser un objet pour ouvrir une source de données avec un accès exclusif.

Lorsque vous `Open`appelez, une requête, habituellement une déclaration **SQL SELECT,** sélectionne les enregistrements en fonction des critères indiqués dans le tableau suivant.

|Valeur du paramètre lpszSQL|Les enregistrements sélectionnés sont déterminés par|Exemple|
|------------------------------------|----------------------------------------|-------------|
|NULL|La chaîne `GetDefaultSQL`est revenue par .||
|Nom de table SQL|Toutes les colonnes de `DoFieldExchange` `DoBulkFieldExchange`la liste de table dans ou .|`"Customer"`|
|Nom de la requête prédéfinie (procédure stockée)|Les colonnes de la requête est définie pour revenir.|`"{call OverDueAccts}"`|
|**LISTE** DE colonne SELECT **FROM** table-list|Les colonnes spécifiées à partir de la table spécifiée.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> Veillez à ce que vous n’insérez pas d’espace blanc supplémentaire dans votre chaîne SQL. Par exemple, si vous insérez de l’espace blanc entre l’attelle bouclée et le mot clé **CALL,** MFC interprète mal la chaîne SQL comme un nom de table et l’incorporera dans une déclaration **SELECT,** ce qui entraînera le fait qu’une exception sera projetée. De même, si votre requête prédéfinie utilise un paramètre de sortie, n’insérez pas d’espace blanc entre l’accolade bouclée et le symbole ' Enfin, vous ne devez pas insérer l’espace blanc avant l’accolade bouclée dans une déclaration **CALL** ou avant le mot clé **SELECT** dans une déclaration **SELECT.**

La procédure habituelle consiste à `Open`passer NULL à ; dans ce `Open` cas, appelle [GetDefaultSQL](#getdefaultsql). Si vous utilisez `CRecordset` une `GetDefaultSQL` classe dérivée, donne le nom de table(s) que vous avez spécifié dans ClassWizard. Vous pouvez plutôt spécifier d’autres informations dans le `lpszSQL` paramètre.

Quoi que vous `Open` passiez, construit une chaîne SQL finale pour la requête (la chaîne peut `lpszSQL` avoir SQL **WHERE** et ORDER **BY** clauses annexées à la chaîne que vous avez passé) et exécute ensuite la requête. Vous pouvez examiner la chaîne construite en `Open`appelant [GetSQL](#getsql) après avoir appelé . Pour plus de détails sur la façon dont le document construit une déclaration SQL et sélectionne les enregistrements, voir l’article [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Les membres des données de terrain de votre classe de documents sont liés aux colonnes des données sélectionnées. Si des enregistrements sont retournés, le premier enregistrement devient le record actuel.

Si vous souhaitez définir des options pour le jeu d’enregistrement, comme un filtre ou `Open`une sorte, spécifiez-les après avoir construit l’objet de l’enregistrement, mais avant d’appeler . Si vous voulez rafraîchir les enregistrements dans le recordet après le recordet est déjà ouvert, appelez [Requery](#requery).

Pour plus d’informations, y compris d’autres exemples, voir les articles [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), et [Recordset: Creating and Closing Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Exemple

Les exemples de code `Open` suivants montrent différentes formes de l’appel.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>CRecordset::RefreshRowset

Mise à jour des données et de l’état d’une rangée dans le rowset actuel.

```cpp
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Paramètres

*wRow (wRow)*<br/>
La position à une seule ligne dans le rowset actuel. Cette valeur peut varier de zéro à la taille de l’acart.

*wLockType (en)*<br/>
Une valeur indiquant comment verrouiller la ligne après qu’elle a été rafraîchie. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Si vous passez une valeur de zéro pour *wRow*, puis chaque rangée dans le rame sera rafraîchie.

Pour `RefreshRowset`utiliser, vous devez avoir implémenté `CRecordset::useMulitRowFetch` la ligne en vrac aller chercher en spécifiant l’option dans la fonction membre [Open.](#open)

`RefreshRowset`appelle la fonction `SQLSetPos`API ODBC . Le *paramètre wLockType* spécifie `SQLSetPos` l’état de verrouillage de la ligne après a exécuté. Le tableau suivant décrit les valeurs possibles pour *wLockType*.

|wLockType (en)|Description|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (la valeur par défaut)|Le conducteur ou la source de données s’assure que la ligne `RefreshRowset` est dans le même état verrouillé ou déverrouillé qu’il était avant a été appelé.|
|SQL_LOCK_EXCLUSIVE|Le conducteur ou la source de données verrouille la ligne exclusivement. Toutes les sources de données ne prennent pas en charge ce type de verrouillage.|
|SQL_LOCK_UNLOCK|Le conducteur ou la source de données déverrouille la ligne. Toutes les sources de données ne prennent pas en charge ce type de verrouillage.|

Pour plus `SQLSetPos`d’informations sur , voir le Windows SDK. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetrequery"></a><a name="requery"></a>CRecordset::Requery

Reconstruit (rafraîchit) un recordet.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le recordet a été reconstruit avec succès; sinon 0.

### <a name="remarks"></a>Notes

Si des enregistrements sont retournés, le premier enregistrement devient le record actuel.

Afin que le carnet de données reflète les ajouts et les suppressions que vous ou d’autres `Requery`utilisateurs faites à la source de données, vous devez reconstruire le jeu d’enregistrement en appelant . Si le jeu d’enregistrement est un dynaset, il reflète automatiquement les mises à jour que vous ou d’autres utilisateurs faites à ses enregistrements existants (mais pas des ajouts). Si le livre est un instantané, vous devez appeler `Requery` pour refléter les modifications par d’autres utilisateurs ainsi que les ajouts et les suppressions.

Pour un dynaset ou un `Requery` instantané, appelez chaque fois que vous voulez reconstruire le jeu d’enregistrement à l’aide d’un nouveau filtre ou d’une tri, ou de nouvelles valeurs de paramètres. Réglez le nouveau filtre ou triez `m_strSort` la `Requery`propriété en attribuant de nouvelles valeurs à `m_strFilter` et avant d’appeler . Définissez de nouveaux paramètres en affectant de `Requery`nouvelles valeurs aux membres des données de paramètre avant d’appeler . Si le filtre et les chaînes de tri sont inchangés, vous pouvez réutiliser la requête, ce qui améliore les performances.

Si la tentative de reconstruction du recordet échoue, le recordet est fermé. Avant d’appeler, `Requery`vous pouvez déterminer si le dossier peut `CanRestart` être requeried en appelant la fonction membre. `CanRestart`ne garantit `Requery` pas que cela réussira.

> [!CAUTION]
> Appelez `Requery` seulement après que vous avez appelé [Open](#open).

### <a name="example"></a>Exemple

Cet exemple reconstitue un jeu d’enregistrement pour appliquer un ordre de tri différent.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition

Positionne l’enregistrement de l’enregistrement correspondant au nombre record spécifié.

```cpp
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Paramètres

*nRows*<br/>
La position ordinaire à un seul niveau pour le dossier actuel dans le dossier.

### <a name="remarks"></a>Notes

`SetAbsolutePosition`déplace le pointeur de record actuel en fonction de cette position ordinaire.

> [!NOTE]
> Cette fonction de membre n’est pas valide sur les enregistrements avant-seulement.

Pour les enregistrements de l’ODBC, un classement absolu de 1 fait référence au premier record de l’ensemble des records; un paramètre de 0 se réfère à la position de début de fichier (BOF).

Vous pouvez également passer `SetAbsolutePosition`des valeurs négatives à . Dans ce cas, la position du recordet est évaluée à partir de la fin de l’enregistrement. Par exemple, `SetAbsolutePosition( -1 )` déplace le pointeur d’enregistrement actuel au dernier enregistrement dans le record.

> [!NOTE]
> La position absolue n’est pas destinée à être utilisée comme numéro de dossier de substitution. Les signets sont toujours le moyen recommandé de conserver et de revenir à une position donnée, puisque la position d’un enregistrement change lorsque les enregistrements précédents sont supprimés. De plus, vous ne pouvez pas être assuré qu’un enregistrement donné aura la même position absolue si le carnet est recréé à nouveau parce que l’ordre des enregistrements individuels dans un dossier n’est pas garanti à moins qu’il ne soit créé avec une déclaration SQL à l’aide d’une clause **ORDER BY.**

Pour plus d’informations sur la navigation et les signets, voir les articles [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset::SetBookmark

Positionne l’enregistrement sur l’enregistrement contenant le signet spécifié.

```cpp
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Paramètres

*varBookmark (en)*<br/>
Une référence à un objet [CDBVariant](../../mfc/reference/cdbvariant-class.md) contenant la valeur de signet pour un enregistrement spécifique.

### <a name="remarks"></a>Notes

Pour déterminer si les signets sont pris en charge sur le jeu d’enregistrement, appelez [CanBookmark](#canbookmark). Pour rendre les signets disponibles s’ils `CRecordset::useBookmarks` sont pris en charge, vous devez définir l’option dans le paramètre *dwOptions* de la fonction membre [Open.](#open)

> [!NOTE]
> Si les signets ne sont pas pris `SetBookmark` en compte ou indisponibles, l’appel entraînera la mise en œil d’une exception. Les signets ne sont pas pris en charge sur les enregistrements avant seuls.

Pour d’abord récupérer le signet pour l’enregistrement en cours, `CDBVariant` appelez [GetBookmark](#getbookmark), qui enregistre la valeur du signet à un objet. Plus tard, vous pouvez revenir `SetBookmark` à cet enregistrement en appelant en utilisant la valeur de signet enregistré.

> [!NOTE]
> Après certaines opérations de recordet, vous devriez `SetBookmark`vérifier la persistance du signet avant d’appeler . Par exemple, si vous récupérez un signet avec `GetBookmark` puis appelez, `Requery`le signet peut ne plus être valide. Appelez [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si `SetBookmark`vous pouvez appeler en toute sécurité .

Pour plus d’informations sur les signets et la navigation de recordset, voir les articles [Recordset: Bookmarks and Absolute Positions (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>CRecordset::SetFieldDirty

Signale un membre des données sur le terrain de l’enregistrement comme modifié ou inchangé.

```cpp
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Contient l’adresse d’un membre des données sur le terrain dans l’enregistrement ou NULL. Si NULL, tous les membres des données sur le terrain dans le jeu d’enregistrement sont signalés. (C-NULL n’est pas le même que Null dans la terminologie de base de données, ce qui signifie « n’avoir aucune valeur. »)

*bDirty (en)*<br/>
VRAI si le membre des données sur le terrain doit être signalé comme «sale» (changé). Autrement FALSE si le membre des données sur le terrain doit être signalé comme «propre» (inchangé).

### <a name="remarks"></a>Notes

Le marquage des champs, aussi inchangés, assure que le champ n’est pas mis à jour et entraîne moins de trafic SQL.

> [!NOTE]
> Cette fonction de membre n’est pas applicable sur les enregistrements qui utilisent la ligne en vrac. Si vous avez mis en `SetFieldDirty` œuvre la ligne en vrac, alors entraînera une affirmation échouée. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Le cadre marque les données modifiées des membres des données sur le terrain pour s’assurer qu’ils seront écrits au dossier sur la source de données par le mécanisme d’échange de champs record (RFX). Changer la valeur d’un champ définit généralement le champ `SetFieldDirty` sale automatiquement, de sorte que vous aurez rarement besoin de vous appeler, mais vous voudrez peut-être parfois s’assurer que les colonnes seront explicitement mis à jour ou insérés quelle que soit la valeur dans le membre des données de champ.

> [!CAUTION]
> Appelez cette fonction de membre seulement après que vous avez appelé [Edit](#edit) ou [AddNew](#addnew).

L’utilisation de NULL pour le premier argument `outputColumn` de `param` la fonction n’appliquera la fonction qu’aux champs, et non aux champs. Par exemple, l’appel

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

ne fixera que `outputColumn` des champs à NULL; `param` champs ne seront pas affectés.

Pour travailler `param` sur des champs, vous devez `param` fournir l’adresse réelle de la personne sur laquelle vous souhaitez travailler, comme :

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Cela signifie que `param` vous ne pouvez pas `outputColumn` définir tous les champs à NULL, comme vous le pouvez avec les champs.

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>CRecordset::SetFieldNull

Signale un membre des données sur le terrain de l’enregistrement comme Null (n’ayant aucune valeur) ou comme non-Null.

```cpp
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pv*<br/>
Contient l’adresse d’un membre des données sur le terrain dans l’enregistrement ou NULL. Si NULL, tous les membres des données sur le terrain dans le jeu d’enregistrement sont signalés. (C-NULL n’est pas le même que Null dans la terminologie de base de données, ce qui signifie « n’avoir aucune valeur. »)

*bNull (en)*<br/>
Nonzero si le membre des données sur le terrain doit être signalé comme n’ayant aucune valeur (Null). Sinon 0 si le membre des données sur le terrain doit être signalé comme non-Null.

### <a name="remarks"></a>Notes

Lorsque vous ajoutez un nouvel enregistrement à un ensemble d’enregistrements, tous les membres des données sur le terrain sont initialement définis à une valeur nulle et signalés comme « sales » (modifiés). Lorsque vous récupérez un enregistrement à partir d’une source de données, ses colonnes ont déjà des valeurs ou sont nulles.

> [!NOTE]
> N’appelez pas cette fonction de membre sur les enregistrements qui utilisent la ligne en vrac aller chercher. Si vous avez mis en `SetFieldNull` œuvre la ligne en vrac aller chercher, l’appel donne des résultats dans une affirmation échouée. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Si vous souhaitez spécifiquement désigner un champ du dossier actuel `SetFieldNull` comme n’ayant pas de valeur, appelez avec *bNull* mis à TRUE pour le signaler comme Null. Si un champ était auparavant marqué Null et que vous voulez maintenant lui donner une valeur, il suffit de définir sa nouvelle valeur. Vous n’avez pas à `SetFieldNull`enlever le drapeau Null avec . Pour déterminer si le champ est `IsFieldNullable`autorisé à être Null, appelez .

> [!CAUTION]
> Appelez cette fonction de membre seulement après que vous avez appelé [Edit](#edit) ou [AddNew](#addnew).

L’utilisation de NULL pour le premier argument `outputColumn` de `param` la fonction n’appliquera la fonction qu’aux champs, et non aux champs. Par exemple, l’appel

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

ne fixera que `outputColumn` des champs à NULL; `param` champs ne seront pas affectés.

Pour travailler `param` sur des champs, vous devez `param` fournir l’adresse réelle de la personne sur laquelle vous souhaitez travailler, comme :

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

Cela signifie que `param` vous ne pouvez pas `outputColumn` définir tous les champs à NULL, comme vous le pouvez avec les champs.

> [!NOTE]
> Lors de l’établissement des `SetFieldNull` paramètres de Null, un appel avant l’ouverture du livre d’enregistrement entraîne une affirmation. Dans ce cas, appelez [SetParamNull](#setparamnull).

`SetFieldNull`est implémenté par [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>CRecordset::SetLockingMode

Définit le mode de verrouillage à verrouillage « optimiste » (par défaut) ou « pessimiste ». Détermine comment les enregistrements sont verrouillés pour les mises à jour.

```cpp
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Paramètres

*nMode*<br/>
Contient l’une des `enum LockMode`valeurs suivantes de la :

- `optimistic`Le verrouillage optimiste verrouille le dossier étant `Update`mis à jour seulement pendant l’appel à .

- `pessimistic`Le verrouillage pessimiste verrouille l’enregistrement dès `Edit` qu’il `Update` est appelé et le maintient verrouillé jusqu’à ce que l’appel se termine ou vous passez à un nouvel enregistrement.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre si vous devez spécifier laquelle des deux stratégies de verrouillage des enregistrements le nombre d’enregistrements utilise pour les mises à jour. Par défaut, le mode de verrouillage `optimistic`d’un jeu d’enregistrement est . Vous pouvez changer cela `pessimistic` pour une stratégie de verrouillage plus prudente. Appelez `SetLockingMode` après avoir construit et ouvert l’objet de la maison d’enregistrement, mais avant d’appeler `Edit`.

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>CRecordset::SetParamNull

Signale un paramètre comme Null (n’ayant aucune valeur) ou comme non-Null.

```cpp
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro du paramètre.

*bNull (en)*<br/>
Si TRUE (la valeur par défaut), le paramètre est signalé comme Null. Dans le cas contraire, le paramètre est signalé comme non-Null.

### <a name="remarks"></a>Notes

Contrairement à [SetFieldNull](#setfieldnull) `SetParamNull` , vous pouvez appeler avant d’avoir ouvert le jeu d’enregistrement.

`SetParamNull`est généralement utilisé avec des requêtes prédéfinies (procédures stockées).

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition

Déplace le curseur à une rangée dans l’ensemble de rangées actuel.

```cpp
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Paramètres

*wRow (wRow)*<br/>
La position à une seule ligne dans le rowset actuel. Cette valeur peut varier de 1 à la taille de l’acart.

*wLockType (en)*<br/>
Valeur indiquant comment verrouiller la ligne après qu’elle a été rafraîchie. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Lors de la mise en œuvre de la mise en œuvre de la ligne en vrac, les enregistrements sont récupérés par des ramets, où le premier enregistrement dans le rowset récupéré est le record actuel. Afin de faire un autre enregistrement dans le `SetRowsetCursorPosition`rowset le record actuel, appelez . Par exemple, vous `SetRowsetCursorPosition` pouvez combiner avec la fonction membre [GetFieldValue](#getfieldvalue) pour récupérer dynamiquement les données de n’importe quel enregistrement de votre jeu de disques.

Pour `SetRowsetCursorPosition`utiliser, vous devez avoir implémenté `CRecordset::useMultiRowFetch` la ligne en vrac aller chercher en spécifiant l’option du paramètre *dwOptions* dans la fonction membre [Open.](#open)

`SetRowsetCursorPosition`appelle la fonction `SQLSetPos`API ODBC . Le *paramètre wLockType* spécifie `SQLSetPos` l’état de verrouillage de la ligne après a exécuté. Le tableau suivant décrit les valeurs possibles pour *wLockType*.

|wLockType (en)|Description|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (la valeur par défaut)|Le conducteur ou la source de données s’assure que la ligne `SetRowsetCursorPosition` est dans le même état verrouillé ou déverrouillé qu’il était avant a été appelé.|
|SQL_LOCK_EXCLUSIVE|Le conducteur ou la source de données verrouille la ligne exclusivement. Toutes les sources de données ne prennent pas en charge ce type de verrouillage.|
|SQL_LOCK_UNLOCK|Le conducteur ou la source de données déverrouille la ligne. Toutes les sources de données ne prennent pas en charge ce type de verrouillage.|

Pour plus `SQLSetPos`d’informations sur , voir le Windows SDK. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>CRecordset::SetRowsetSize

Précise le nombre d’enregistrements que vous souhaitez récupérer lors d’un aller chercher.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Paramètres

*dwNewRowsetSize*<br/>
Le nombre de lignes à récupérer lors d’une remise d’un prix à l’autre.

### <a name="remarks"></a>Notes

Cette fonction de membre virtuel précise le nombre de lignes que vous souhaitez récupérer lors d’une seule utilisation lors de l’utilisation de la ligne en vrac aller chercher. Pour implémenter la ramage `CRecordset::useMultiRowFetch` en vrac, vous devez définir l’option dans le paramètre *dwOptions* de la fonction membre [Open.](#open)

> [!NOTE]
> Appeler `SetRowsetSize` sans mettre en œuvre la ligne en vrac aller chercher se traduira par une affirmation échouée.

Appelez `SetRowsetSize` avant `Open` d’appeler pour définir d’abord la taille de l’acart pour le recordet. La taille de l’aviron par défaut lors de la mise en œuvre de la ligne en vrac fetching est de 25.

> [!NOTE]
> Faites preuve `SetRowsetSize`de prudence lorsque vous appelez . Si vous allouez manuellement le stockage pour `CRecordset::userAllocMultiRowBuffers` les données (comme spécifié `Open`par l’option du paramètre dwOptions), `SetRowsetSize`vous devez vérifier si vous avez besoin de réaffecter ces tampons de stockage après votre appel, mais avant d’effectuer une opération de navigation curseur.

Pour obtenir le réglage actuel pour la taille de l’aviron, appelez [GetRowsetSize](#getrowsetsize).

Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset::Mise à jour

Termine une `AddNew` `Edit` ou une opération en économisant les données nouvelles ou modifiées sur la source de données.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si un enregistrement a été mis à jour avec succès; sinon 0 si aucune colonne n’a changé. Si aucun enregistrement n’a été mis à jour ou si plus d’un enregistrement a été mis à jour, une exception est projetée. Une exception est également prévue pour toute autre défaillance sur la source de données.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre après un appel à la fonction [membre AddNew](#addnew) ou [Edit.](#edit) Cet appel est nécessaire `AddNew` `Edit` pour compléter le ou l’opération.

> [!NOTE]
> Si vous avez implémenté la `Update`ligne en vrac aller chercher, vous ne pouvez pas appeler . Cela se traduira par une affirmation ratée. Bien `CRecordset` que la classe ne fournit pas un mécanisme pour mettre à jour les lignes de `SQLSetPos`données en vrac, vous pouvez écrire vos propres fonctions en utilisant la fonction API ODBC . Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Les `AddNew` `Edit` deux et préparer un tampon de modification dans lequel les données ajoutées ou modifiées sont placées pour l’enregistrement à la source de données. `Update`enregistre les données. Seuls les champs marqués ou détectés tels qu’ils sont modifiés sont mis à jour.

Si la source de données prend `Update` en charge `AddNew` les `Edit` transactions, vous pouvez effectuer la partie d’appel (et de son appel correspondant ou de son appel) d’une transaction. Pour plus d’informations sur les transactions, voir l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
> Si vous `Update` appelez sans `AddNew` `Edit`appeler `Update` d’abord ou , jette un `CDBException`. Si vous `AddNew` `Edit`appelez ou `Update` , vous `Move` devez appeler avant d’appeler une opération ou avant de fermer le jeu d’enregistrement ou la connexion source de données. Sinon, vos modifications sont perdues sans notification.

Pour plus `Update` de détails sur les défaillances de traitement, voir l’article [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Exemple

Voir l’article [Transaction: Performing a Transaction in a Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView, classe](../../mfc/reference/crecordview-class.md)
