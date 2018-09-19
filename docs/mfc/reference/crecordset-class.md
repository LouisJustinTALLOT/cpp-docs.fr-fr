---
title: CRecordset, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a74edb512f545f9da8d222535f84f6bac34d094f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096234"
---
# <a name="crecordset-class"></a>CRecordset, classe
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
|[CRecordset::AddNew](#addnew)|Prépare pour l’ajout d’un nouvel enregistrement. Appelez `Update` pour terminer l’ajout.|  
|[CRecordset::CanAppend](#canappend)|Retourne zéro si les nouveaux enregistrements peuvent être ajoutés à l’ensemble d’enregistrements via le `AddNew` fonction membre.|  
|[CRecordset::CanBookmark](#canbookmark)|Retourne une valeur différente de zéro si le jeu d’enregistrements prend en charge les signets.|  
|[CRecordset::Cancel](#cancel)|Annule une opération asynchrone ou un processus à partir d’un deuxième thread.|  
|[CRecordset::CancelUpdate](#cancelupdate)|Annule les mises à jour en attente suite à une `AddNew` ou `Edit` opération.|  
|[CRecordset::CanRestart](#canrestart)|Retourne la valeur différente de zéro si `Requery` peut être appelée pour réexécuter la requête du recordset.|  
|[CRecordset::CanScroll](#canscroll)|Retourne une valeur différente de zéro si vous pouvez faire défiler les enregistrements.|  
|[CRecordset::CanTransact](#cantransact)|Retourne une valeur différente de zéro si la source de données prend en charge les transactions.|  
|[CRecordset::CanUpdate](#canupdate)|Retourne zéro si le jeu d’enregistrements peut être mis à jour (vous pouvez ajouter, mettre à jour ou supprimer des enregistrements).|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|Appelé pour gérer les erreurs générées lors de la récupération de l’enregistrement.|  
|[Préférence CRecordset::Close](#close)|Ferme le jeu d’enregistrements et le HSTMT ODBC associé.|  
|[CRecordset::Delete](#delete)|Supprime l’enregistrement en cours de l’ensemble d’enregistrements. Après la suppression, vous devez explicitement faire défiler à un autre enregistrement.|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Appelé pour échanger des lignes en bloc des données à partir de la source de données vers le recordset. Implémente en masse d’échange de champs d’enregistrements (RFX en bloc).|  
|[CRecordset::DoFieldExchange](#dofieldexchange)|Appelé pour échanger des données (dans les deux sens) entre les membres de données de champ de l’objet recordset et l’enregistrement correspondant sur la source de données. Implémente enregistre l’échange de champs (RFX).|  
|[CRecordset::Edit](#edit)|Prépare les modifications à l’enregistrement actif. Appelez `Update` pour terminer la modification.|  
|[CRecordset::FlushResultSet](#flushresultset)|Retourne zéro s’il existe un autre résultat défini à récupérer, lors de l’utilisation d’une requête prédéfinie.|  
|[CRecordset::GetBookmark](#getbookmark)|Assigne la valeur de signet d’un enregistrement à l’objet de paramètre.|  
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Appelé pour obtenir la chaîne de connexion par défaut.|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Appelé pour obtenir la chaîne SQL par défaut à exécuter.|  
|[CRecordset::GetFieldValue](#getfieldvalue)|Retourne la valeur d’un champ dans un jeu d’enregistrements.|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Retourne le nombre de champs dans le jeu d’enregistrements.|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Retourne des informations sur les champs particuliers dans un jeu d’enregistrements.|  
|[CRecordset::GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements dans le jeu d’enregistrements.|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|Retourne le nombre d’enregistrements que vous souhaitez récupérer pendant une extraction unique.|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|Retourne le nombre réel de lignes récupérées lors d’une extraction.|  
|[CRecordset::GetRowStatus](#getrowstatus)|Retourne l’état de la ligne après une extraction.|  
|[CRecordset::GetSQL](#getsql)|Obtient la chaîne SQL utilisée pour sélectionner des enregistrements pour le jeu d’enregistrements.|  
|[CRecordset::GetStatus](#getstatus)|Obtient l’état de l’objet recordset : l’index de l’enregistrement actif et indique si un nombre final d’enregistrements a été obtenu.|  
|[CRecordset::GetTableName](#gettablename)|Obtient le nom de la table sur laquelle repose le jeu d’enregistrements.|  
|[CRecordset::IsBOF](#isbof)|Retourne une valeur différente de zéro si le jeu d’enregistrements a été placé avant le premier enregistrement. Il n’existe aucun enregistrement actif.|  
|[CRecordset::IsDeleted](#isdeleted)|Retourne une valeur différente de zéro si le jeu d’enregistrements est positionné sur un enregistrement supprimé.|  
|[CRecordset::IsEOF](#iseof)|Retourne une valeur différente de zéro si le jeu d’enregistrements a été positionné après le dernier enregistrement. Il n’existe aucun enregistrement actif.|  
|[CRecordset::IsFieldDirty](#isfielddirty)|Retourne une valeur différente de zéro si le champ spécifié dans l’enregistrement actif a été modifié.|  
|[CRecordset::IsFieldNull](#isfieldnull)|Retourne zéro si le champ spécifié dans l’enregistrement actif est null (n’a aucune valeur).|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|Retourne zéro si le champ spécifié dans l’enregistrement actif peut être défini sur null (n’avoir aucune valeur).|  
|[CRecordset::IsOpen](#isopen)|Retourne la valeur différente de zéro si `Open` a été appelé précédemment.|  
|[CRecordset::Move](#move)|Positionne le jeu d’enregistrements à un nombre spécifié d’enregistrements à partir de l’enregistrement actif dans les deux sens.|  
|[CRecordset::MoveFirst](#movefirst)|Positionne l’enregistrement en cours sur le premier enregistrement dans le jeu d’enregistrements. Tester `IsBOF` première.|  
|[CRecordset::MoveLast](#movelast)|Positionne l’enregistrement en cours sur le dernier enregistrement ou sur le dernier ensemble de lignes. Tester `IsEOF` première.|  
|[CRecordset::MoveNext](#movenext)|Positionne l’enregistrement en cours sur l’enregistrement suivant ou sur l’ensemble de lignes suivant. Tester `IsEOF` première.|  
|[CRecordset::MovePrev](#moveprev)|Positionne l’enregistrement en cours sur l’enregistrement précédent ou sur l’ensemble de lignes précédent. Tester `IsBOF` première.|  
|[CRecordset::OnSetOptions](#onsetoptions)|Appelé pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée.|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Appelé pour définir les options (utilisées sur la mise à jour) pour l’instruction ODBC spécifiée.|  
|[CRecordset::Open](#open)|Ouvre le recordset en récupération de la table ou en exécutant la requête qui représente le jeu d’enregistrements.|  
|[CRecordset::RefreshRowset](#refreshrowset)|Actualise les données et l’état de la ligne (s) spécifié.|  
|[CRecordset::Requery](#requery)|Exécute la requête du recordset à nouveau pour actualiser les enregistrements sélectionnés.|  
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Positionne le jeu d’enregistrements sur l’enregistrement correspondant au numéro d’enregistrement spécifié.|  
|[CRecordset::SetBookmark](#setbookmark)|Positionne le jeu d’enregistrements sur l’enregistrement spécifié par le signet.|  
|[CRecordset::SetFieldDirty](#setfielddirty)|Marque le champ spécifié dans l’enregistrement actif comme étant modifiée.|  
|[CRecordset::SetFieldNull](#setfieldnull)|Définit la valeur du champ spécifié dans l’enregistrement actif null (n’avoir aucune valeur).|  
|[CRecordset::SetLockingMode](#setlockingmode)|Définit le mode de verrouillage « optimiste « verrouillage (il s’agit de la valeur par défaut) ou de verrouillage « pessimiste ». Détermine la façon dont les enregistrements sont verrouillés pour les mises à jour.|  
|[CRecordset::SetParamNull](#setparamnull)|Définit le paramètre spécifié à null (n’avoir aucune valeur).|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Positionne le curseur sur la ligne spécifiée dans l’ensemble de lignes.|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|Spécifie le nombre d’enregistrements que vous souhaitez récupérer pendant une extraction.|  
|[CRecordset::Update](#update)|Termine une `AddNew` ou `Edit` opération en enregistrant les données nouvelles ou modifiées sur la source de données.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CRecordset::m_hstmt](#m_hstmt)|Contient le descripteur d’instruction ODBC pour le jeu d’enregistrements. Tapez `HSTMT`.|  
|[CRecordset::m_nFields](#m_nfields)|Contient le nombre de membres de données de champ dans le jeu d’enregistrements. Tapez `UINT`.|  
|[CRecordset::m_nParams](#m_nparams)|Contient le nombre de membres de données de paramètre dans le jeu d’enregistrements. Tapez `UINT`.|  
|[CRecordset::m_pDatabase](#m_pdatabase)|Contient un pointeur vers le `CDatabase` objet via lequel le jeu d’enregistrements est connecté à une source de données.|  
|[CRecordset::m_strFilter](#m_strfilter)|Contient un `CString` qui spécifie un langage SQL (Structured Query) `WHERE` clause. Utilisé en tant que filtre pour sélectionner uniquement les enregistrements qui répondent à certains critères.|  
|[CRecordset::m_strSort](#m_strsort)|Contient un `CString` qui spécifie une instance SQL `ORDER BY` clause. Utilisé pour contrôler la façon dont les enregistrements sont triés.|  
  
## <a name="remarks"></a>Notes  
 Appelé « jeux d’enregistrements, » `CRecordset` objets sont généralement utilisées dans les deux formulaires : feuilles de réponse dynamiques et les captures instantanées. Feuille de réponse dynamique reste synchronisé avec les mises à jour de données effectuées par d’autres utilisateurs. Un instantané est une vue statique des données. Chaque formulaire représente un jeu d’enregistrements fixée à la fois que le jeu d’enregistrements est ouvert, mais lorsque vous faites défiler vers un enregistrement dans une feuille de réponse dynamique, il reflète les modifications apportées par la suite à l’enregistrement, par d’autres utilisateurs ou par d’autres jeux d’enregistrements dans votre application.  
  
> [!NOTE]
>  Si vous travaillez avec les classes d’objets DAO (Data Access) plutôt que les classes de base de données connectivité ODBC (Open), utilisez la classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de base de données](../../data/data-access-programming-mfc-atl.md).  
  
 Pour utiliser un de ces types de jeu d’enregistrements, vous dérivez généralement une classe de jeu d’enregistrements spécifiques à l’application à partir de `CRecordset`. Jeux d’enregistrements de sélectionner des enregistrements à partir d’une source de données, et vous pouvez ensuite :  
  
-   Faites défiler les enregistrements.  
  
-   Mettre à jour les enregistrements et spécifier un mode de verrouillage.  
  
-   Filtrer le jeu d’enregistrements pour limiter les enregistrements qu’il sélectionne parmi celles disponibles sur la source de données.  
  
-   Trier le jeu d’enregistrements.  
  
-   Paramétrer le recordset pour personnaliser sa sélection avec des informations inconnues jusqu’au moment de l’exécution.  
  
 Pour utiliser votre classe, ouvrez une base de données et construire un objet recordset, en passant le constructeur un pointeur vers votre `CDatabase` objet. Appelez ensuite le jeu d’enregistrements `Open` fonction membre, où vous pouvez spécifier si l’objet est une feuille de réponse dynamique ou un instantané. Appel `Open` sélectionne les données à partir de la source de données. Une fois que l’objet de jeu d’enregistrements est ouvert, utilisez ses membres de données et des fonctions de membre pour faire défiler les enregistrements et opérer sur les. Les opérations disponibles varient selon que l’objet est une feuille de réponse dynamique ou un instantané, qu’il s’agisse d’être mise à jour ou en lecture seule (Cela dépend de la capacité de la source de données ODBC Open Database Connectivity ()), et si vous avez implémenté l’extraction de lignes en bloc. Pour actualiser les enregistrements qui ont été être modifiés ou ajoutés depuis la `Open` appeler, appelez l’objet `Requery` fonction membre. Appeler l’objet `Close` membre de fonction et détruire l’objet lorsque vous avez terminé avec lui.  
  
 Dans une dérivée `CRecordset` class, enregistrer le champ RFX (exchange) ou RFX en bloc (RFX en bloc) est utilisé pour prendre en charge la lecture et mise à jour des champs d’enregistrement.  
  
 Pour plus d’informations sur l’échange de champs d’enregistrement et de jeux d’enregistrements, consultez les articles [vue d’ensemble : programmation de base de données](../../data/data-access-programming-mfc-atl.md), [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset : extraction globale d’enregistrements en bloc (ODBC) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md). Pour se concentrant sur les feuilles de réponse dynamiques et les captures instantanées, consultez les articles [Dynaset](../../data/odbc/dynaset.md) et [instantané](../../data/odbc/snapshot.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdb.h  
  
##  <a name="addnew"></a>  CRecordset::AddNew  
 Prépare pour l’ajout d’un nouvel enregistrement à la table.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler la [Requery](#requery) fonction membre pour afficher le dernier enregistrement ajouté. Champs de l’enregistrement sont initialement nulle. (Dans la terminologie de base de données, Null signifie « ne having aucune valeur » et n’est pas identique à la valeur NULL en C++.) Pour terminer l’opération, vous devez appeler la [mise à jour](#update) fonction membre. `Update` enregistre les modifications apportées à la source de données.  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `AddNew`. Cela entraîne un échec d’assertion. Bien que classe `CRecordset` ne fournit pas de mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `AddNew` prépare un nouvel enregistrement vide à l’aide des membres de données de champ du jeu d’enregistrements. Après avoir appelé `AddNew`, définissez les valeurs souhaitées dans les membres de données de champ du jeu d’enregistrements. (Vous n’avez pas à appeler le [modifier](#edit) fonction membre à cet effet ; utilisez `Edit` uniquement pour les enregistrements existants.) Lorsque vous appelez ensuite `Update`, modifié les valeurs dans les membres de données de champ sont enregistrées sur la source de données.  
  
> [!CAUTION]
>  Si vous accédez à un nouvel enregistrement avant d’appeler `Update`, le nouvel enregistrement est perdu et aucun avertissement n’est donnée.  
  
 Si la source de données prend en charge les transactions, vous pouvez rendre votre `AddNew` des appels, partie d’une transaction. Pour plus d’informations sur les transactions, consultez la classe [CDatabase](../../mfc/reference/cdatabase-class.md). Notez que vous devez appeler [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) avant d’appeler `AddNew`.  
  
> [!NOTE]
>  Pour les dynasets, les nouveaux enregistrements sont ajoutés au jeu d’enregistrements en tant que le dernier enregistrement. Les enregistrements ajoutés ne sont pas ajoutés aux instantanés ; Vous devez appeler `Requery` pour actualiser le jeu d’enregistrements.  
  
 Il est illégal d’appeler `AddNew` pour un jeu d’enregistrements dont `Open` fonction membre n’a pas été appelée. Un `CDBException` est levée si vous appelez `AddNew` pour un jeu d’enregistrements qui ne peut pas être ajouté au. Vous pouvez déterminer si le jeu d’enregistrements est modifiable en appelant [CanAppend](#canappend).  
  
 Pour plus d’informations, consultez les articles suivants : [Recordset : mise à jour des enregistrements par les Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Recordset : ajout de la mise à jour et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), et [(de Transaction ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’article [Transaction : exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="canappend"></a>  CRecordset::CanAppend  
 Détermine si le jeu d’enregistrements précédemment ouvert vous permet d’ajouter des enregistrements.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements permet d’ajouter de nouveaux enregistrements ; sinon 0. `CanAppend` retourne 0 si vous avez ouvert le jeu d’enregistrements en lecture seule.  
  
##  <a name="canbookmark"></a>  CRecordset::CanBookmark  
 Détermine si le jeu d’enregistrements vous permet de marquer les enregistrements à l’aide de signets.  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements prend en charge les signets. sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est indépendante de la `CRecordset::useBookmarks` option dans le *dwOptions* paramètre de la [Open](#open) fonction membre. `CanBookmark` Indique si le pilote ODBC et le curseur type de prise en charge des signets. `CRecordset::useBookmarks` Indique si les signets seront disponibles, sous réserve qu’ils sont pris en charge.  
  
> [!NOTE]
>  Les signets ne sont pas pris en charge sur les recordsets avant uniquement.  
  
 Pour plus d’informations sur les signets et de navigation de jeu d’enregistrements, consultez les articles [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cancel"></a>  CRecordset::Cancel  
 Demande que la source de données annule une opération asynchrone en cours ou un processus à partir d’un deuxième thread.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Notes  
 Notez que les classes ODBC MFC ne plus utilisent le traitement asynchrone ; Pour effectuer une opération asynchrone, vous devez appeler directement la fonction API ODBC `SQLSetConnectOption`. Pour plus d’informations, consultez la rubrique « L’exécution de fonctions en mode asynchrone » dans le *-Guide du programmeur ODBC SDK*.  
  
##  <a name="cancelupdate"></a>  CRecordset::CancelUpdate  
 Annule tout en attente de mises à jour, dus à un [modifier](#edit) ou [AddNew](#addnew) opération, avant de [mise à jour](#update) est appelée.  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les jeux d’enregistrements qui est l’extraction de lignes en bloc, dans la mesure où ces jeux d’enregistrements ne peuvent pas appeler `Edit`, `AddNew`, ou `Update`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Si la vérification de champ incorrect automatique est activée, `CancelUpdate` restaurera les variables de membre pour les valeurs qu’ils avaient avant `Edit` ou `AddNew` a été appelée ; sinon, le restent des modifications de valeur. Par défaut, la vérification automatique de champ est activée lorsque le jeu d’enregistrements est ouvert. Pour le désactiver, vous devez spécifier le `CRecordset::noDirtyFieldCheck` dans le *dwOptions* paramètre de la [Open](#open) fonction membre.  
  
 Pour plus d’informations sur la mise à jour des données, consultez l’article [Recordset : ajout de la mise à jour et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).  
  
##  <a name="canrestart"></a>  CRecordset::CanRestart  
 Détermine si le jeu d’enregistrements autorise le redémarrage de sa requête (pour actualiser ses enregistrements) en appelant le `Requery` fonction membre.  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si requery est autorisée ; sinon 0.  
  
##  <a name="canscroll"></a>  CRecordset::CanScroll  
 Détermine si le jeu d’enregistrements autorise le défilement.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements permet le défilement ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur le défilement, consultez l’article [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cantransact"></a>  CRecordset::CanTransact  
 Détermine si le jeu d’enregistrements autorise les transactions.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements permet aux transactions ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>  CRecordset::CanUpdate  
 Détermine si le jeu d’enregistrements peut être mis à jour.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements peut être mis à jour ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Un jeu d’enregistrements peut-être être en lecture seule si la source de données sous-jacente est en lecture seule ou si vous avez spécifié `CRecordset::readOnly` dans le *dwOptions* paramètre lorsque vous avez ouvert le jeu d’enregistrements.  
  
##  <a name="checkrowseterror"></a>  CRecordset::CheckRowsetError  
 Appelé pour gérer les erreurs générées lors de la récupération de l’enregistrement.  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>Paramètres  
 *nRetCode*  
 Code de retour une fonction API ODBC. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre virtuelle gère les erreurs qui se produisent lorsque les enregistrements sont extraits, et est utile lors de l’extraction de lignes en bloc. Vous souhaiterez substitution `CheckRowsetError` pour implémenter votre propre gestion des erreurs.  
  
 `CheckRowsetError` est appelé automatiquement dans une opération de navigation de curseur, tels que `Open`, `Requery`, ou n’importe quel `Move` opération. Il est passé à la valeur de retour de la fonction API ODBC `SQLExtendedFetch`. Le tableau suivant répertorie les valeurs possibles pour le *nRetCode* paramètre.  
  
|nRetCode|Description|  
|--------------|-----------------|  
|SQL_SUCCESS|Fonction a été exécutée avec succès ; Aucune information supplémentaire n’est disponible.|  
|SQL_SUCCESS_WITH_INFO|Fonction s’est terminée avec succès, éventuellement avec une erreur non fatale. Informations supplémentaires peuvent être obtenues en appelant `SQLError`.|  
|SQL_NO_DATA_FOUND|Toutes les lignes du jeu de résultats qui ont été extraites.|  
|SQL_ERROR|Échec de la fonction. Informations supplémentaires peuvent être obtenues en appelant `SQLError`.|  
|SQL_INVALID_HANDLE|Fonction a échoué en raison d’un handle d’environnement non valide, un handle de connexion ou un descripteur d’instruction. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible à partir de `SQLError`.|  
|SQL_STILL_EXECUTING|Une fonction qui a été démarrée en mode asynchrone est en cours d’exécution. Notez que, par défaut, MFC ne passent jamais cette valeur pour `CheckRowsetError`; MFC continuer à appeler `SQLExtendedFetch` jusqu'à ce qu’il ne retourne plus SQL_STILL_EXECUTING.|  
  
 Pour plus d’informations sur `SQLError`, consultez le kit SDK Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="close"></a>  Préférence CRecordset::Close  
 Ferme le jeu d’enregistrements.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Notes  
 Le HSTMT ODBC et toute la mémoire du framework allouée pour le jeu d’enregistrements sont libérés. Généralement après l’appel `Close`, vous supprimez l’objet de jeu d’enregistrements de C++, si elle a été allouée avec **nouveau**.  
  
 Vous pouvez appeler `Open` à nouveau après l’appel `Close`. Cela vous permet de réutiliser l’objet recordset. L’alternative consiste à appeler `Requery`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>  CRecordset::CRecordset  
 Construit un objet `CRecordset`.  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDatabase*  
 Contient un pointeur vers un `CDatabase` objet ou la valeur NULL. Si non NULL et le `CDatabase` l’objet `Open` fonction membre n’a pas été appelée pour vous connecter à la source de données, le jeu d’enregistrements tente d’ouvrir pour vous lors de son propre `Open` appeler. Si vous passez la valeur NULL, un `CDatabase` objet est construit et connecté à l’aide des informations de source de données que vous avez spécifié lorsque vous dérivé votre classe de jeu d’enregistrements avec ClassWizard.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser `CRecordset` directement ou dériver une classe spécifique à l’application à partir de `CRecordset`. Vous pouvez utiliser ClassWizard pour dériver vos classes de jeu d’enregistrements.  
  
> [!NOTE]
>  Une classe dérivée *doit* fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur `CRecordset::CRecordset`, en passant les paramètres appropriés le long de lui.  
  
 Passez la valeur NULL au constructeur de votre recordset pour avoir un `CDatabase` objet construit et connecté automatiquement à votre place. Il s’agit d’un raccourci utile ne nécessitant pas construire et connecter un `CDatabase` objet avant de créer votre jeu d’enregistrements.  
  
### <a name="example"></a>Exemple  
 Pour plus d’informations, consultez l’article [Recordset : déclaration de la classe d’une Table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
##  <a name="delete"></a>  CRecordset::Delete  
 Supprime l’enregistrement actif.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Notes  
 Après une suppression réussie, les membres de données de champ du jeu d’enregistrements sont définies sur une valeur Null, et vous devez appeler explicitement une de la `Move` fonctions afin de déplacer l’enregistrement supprimé. Une fois que vous quittez l’enregistrement supprimé, il n’est pas possible d’y revenir. Si la source de données prend en charge les transactions, vous pouvez rendre le `Delete` des appels, partie d’une transaction. Pour plus d’informations, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `Delete`. Cela entraîne un échec d’assertion. Bien que classe `CRecordset` ne fournit pas de mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!CAUTION]
>  Le jeu d’enregistrements doit être mis à jour et il doit y avoir un enregistrement valide dans le jeu d’enregistrements lorsque vous appelez `Delete`; sinon, une erreur se produit. Par exemple, si vous supprimez un enregistrement, mais ne fait pas défiler un nouvel enregistrement avant d’appeler `Delete` là encore, `Delete` lève un [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Contrairement aux [AddNew](#addnew) et [modifier](#edit), un appel à `Delete` n’est pas suivi par un appel à [mise à jour](#update). Si un `Delete` appel échoue, les données des champs membres restent inchangées.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre un jeu d’enregistrements créé dans le cadre d’une fonction. L’exemple suppose l’existence de `m_dbCust`, une variable membre de type `CDatabase` déjà connecté à la source de données.  
  
 [!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>  CRecordset::DoBulkFieldExchange  
 Appelé pour échanger des lignes en bloc des données à partir de la source de données vers le recordset. Implémente en masse d’échange de champs d’enregistrements (RFX en bloc).  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFX*  
 Un pointeur vers un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objet. Le framework est déjà avoir configuré cet objet pour spécifier un contexte pour l’opération d’échange de champ.  
  
### <a name="remarks"></a>Notes  
 Lors de l’extraction de lignes en bloc est implémentée, l’infrastructure appelle cette fonction membre pour transférer automatiquement les données à partir de la source de données sur votre objet recordset. `DoBulkFieldExchange` lie également vos membres de données de paramètre, cas échéant, aux espaces réservés de paramètre dans la chaîne d’instruction SQL pour la sélection du jeu d’enregistrements.  
  
 Si l’extraction de lignes en bloc n’est pas implémentée, le framework appelle [DoFieldExchange](#dofieldexchange). Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` possibilité du *dwOptions* paramètre dans le [Open](#open) fonction membre.  
  
> [!NOTE]
> `DoBulkFieldExchange` est disponible uniquement si vous utilisez une classe dérivée de `CRecordset`. Si vous avez créé un objet recordset directement à partir de `CRecordset`, vous devez appeler la [GetFieldValue](#getfieldvalue) fonction membre pour récupérer des données.  
  
 RFX en bloc (RFX en bloc) est similaire à l’échange de champs d’enregistrements (RFX). Données sont automatiquement transférées à partir de la source de données à l’objet recordset. Toutefois, vous ne pouvez pas appeler `AddNew`, `Edit`, `Delete`, ou `Update` pour transférer les modifications à la source de données. Classe `CRecordset` actuellement ne fournit pas un mécanisme de mise à jour en bloc des lignes de données ; Toutefois, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`.  
  
 Notez que ClassWizard ne prend pas en charge RFX en bloc ; Par conséquent, vous devez substituer `DoBulkFieldExchange` manuellement en écrivant des appels aux fonctions RFX en bloc. Pour plus d’informations sur ces fonctions, consultez la rubrique [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md).  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus d’informations, consultez l’article [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="dofieldexchange"></a>  CRecordset::DoFieldExchange  
 Appelé pour échanger des données (dans les deux sens) entre les membres de données de champ de l’objet recordset et l’enregistrement correspondant sur la source de données. Implémente enregistre l’échange de champs (RFX).  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFX*  
 Un pointeur vers un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objet. Le framework est déjà avoir configuré cet objet pour spécifier un contexte pour l’opération d’échange de champ.  
  
### <a name="remarks"></a>Notes  
 Lors de l’extraction de lignes en bloc n’est pas implémentée, l’infrastructure appelle cette fonction membre pour échanger automatiquement les données entre les membres de données de champ de votre objet de jeu d’enregistrements et les colonnes correspondantes de l’enregistrement en cours sur la source de données. `DoFieldExchange` lie également vos membres de données de paramètre, cas échéant, aux espaces réservés de paramètre dans la chaîne d’instruction SQL pour la sélection du jeu d’enregistrements.  
  
 Si l’extraction de lignes en bloc est implémentée, le framework appelle [DoBulkFieldExchange](#dobulkfieldexchange). Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` possibilité du *dwOptions* paramètre dans le [Open](#open) fonction membre.  
  
> [!NOTE]
> `DoFieldExchange` est disponible uniquement si vous utilisez une classe dérivée de `CRecordset`. Si vous avez créé un objet recordset directement à partir de `CRecordset`, vous devez appeler la [GetFieldValue](#getfieldvalue) fonction membre pour récupérer des données.  
  
 L’échange de données de champ, appelées échange de champs d’enregistrements (RFX), fonctionne dans les deux sens : à partir de membres de données de champ de l’objet recordset aux champs de l’enregistrement sur la source de données et à partir de l’enregistrement sur la source de données à l’objet recordset.  
  
 La seule action que vous devez normalement suivre pour implémenter `DoFieldExchange` pour votre jeu d’enregistrements dérivée classe consiste à créer la classe avec ClassWizard et spécifier les types de données et les noms des membres de données du champ. Vous pouvez également ajouter le code à ce que ClassWizard écrit pour spécifier les membres de données de paramètre ou à gérer des colonnes que vous liez dynamiquement. Pour plus d’informations, consultez l’article [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Lorsque vous déclarez votre classe dérivée de jeu d’enregistrements avec ClassWizard, l’Assistant écrit une substitution de `DoFieldExchange` pour vous, ce qui ressemble à l’exemple suivant :  
  
 [!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 Pour plus d’informations sur les fonctions RFX, consultez la rubrique [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md).  
  
 Pour plus d’exemples et des détails sur `DoFieldExchange`, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour obtenir des informations générales sur RFX, consultez l’article [Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="edit"></a>  CRecordset::Edit  
 Permet de modifier l’enregistrement actif.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Notes  
 Après avoir appelé `Edit`, vous pouvez modifier les membres de données de champ en réinitialisant directement leurs valeurs. L’opération est terminée lorsque vous appelez ensuite la [mise à jour](#update) fonction membre pour enregistrer vos modifications sur la source de données.  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `Edit`. Cela entraîne un échec d’assertion. Bien que classe `CRecordset` ne fournit pas de mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `Edit` enregistre les valeurs du jeu d’enregistrements membres de données. Si vous appelez `Edit`, apporter des modifications, puis appelez `Edit` là encore, les valeurs de l’enregistrement sont restaurés sur leur valeur avant le premier `Edit` appeler.  
  
 Dans certains cas, vous souhaiterez peut-être mettre à jour une colonne en le rendant Null (ne contenant aucune donnée). Pour ce faire, appelez [SetFieldNull](#setfieldnull) avec un paramètre True permet de marquer le champ de valeur Null ; cela entraîne également la colonne à mettre à jour. Si vous voulez un champ pour être écrites dans la source de données, même si sa valeur n’a pas changé, appelez [SetFieldDirty](#setfielddirty) avec un paramètre de la valeur TRUE. Cela fonctionne même si le champ a la valeur Null.  
  
 Si la source de données prend en charge les transactions, vous pouvez rendre le `Edit` des appels, partie d’une transaction. Notez que vous devez appeler [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) avant d’appeler `Edit` et une fois que le jeu d’enregistrements a été ouvert. Notez également que l’appel [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) n’est pas un substitut pour appeler `Update` pour terminer le `Edit` opération. Pour plus d’informations sur les transactions, consultez la classe [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 Selon le mode de verrouillage en cours, l’enregistrement mis à jour est peut-être verrouillé par `Edit` jusqu'à ce que vous appeliez `Update` ou faites défiler vers un autre enregistrement, ou il peut être verrouillée uniquement pendant le `Edit` appeler. Vous pouvez modifier le mode de verrouillage avec [SetLockingMode](#setlockingmode).  
  
 La valeur précédente de l’enregistrement actif est restaurée si vous faites défiler vers un nouvel enregistrement avant d’appeler `Update`. Un `CDBException` est levée si vous appelez `Edit` pour un jeu d’enregistrements qui ne peut pas être mis à jour ou s’il n’existe aucun enregistrement actif.  
  
 Pour plus d’informations, consultez les articles [Transaction (ODBC)](../../data/odbc/transaction-odbc.md) et [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>  CRecordset::FlushResultSet  
 Récupère le jeu de résultats suivant d’une requête prédéfinie (procédure stockée), s’il existe plusieurs jeux de résultats.  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro s’il existe plusieurs jeux de résultats à récupérer ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler `FlushResultSet` uniquement lorsque vous avez complètement terminé avec le curseur sur le jeu de résultats actuel. Notez que lorsque vous récupérez le résultat suivant défini en appelant `FlushResultSet`, votre curseur n’est pas valide sur ce jeu de résultats ; vous devez appeler la [MoveNext](#movenext) fonction membre après avoir appelé `FlushResultSet`.  
  
 Si une requête prédéfinie utilise un paramètre de sortie ou des paramètres d’entrée/sortie, vous devez appeler `FlushResultSet` jusqu'à ce qu’elle retourne `FALSE` (la valeur 0), afin d’obtenir ces valeurs de paramètre.  
  
 `FlushResultSet` appelle la fonction API ODBC `SQLMoreResults`. Si `SQLMoreResults` retourne SQL_ERROR ou SQL_INVALID_HANDLE, puis `FlushResultSet` lève une exception. Pour plus d’informations sur `SQLMoreResults`, consultez le kit SDK Windows.  
  
 Votre procédure stockée doit avoir des champs liés Si vous souhaitez appeler `FlushResultSet`.  
  
### <a name="example"></a>Exemple  
 Le code suivant suppose que `COutParamRecordset` est un `CRecordset`-objet dérivé basé sur une requête prédéfinie avec un paramètre d’entrée et un paramètre de sortie et avoir plusieurs jeux de résultats. Notez la structure de la [DoFieldExchange](#dofieldexchange) remplacer.  
  
 [!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>  CRecordset::GetBookmark  
 Obtient la valeur de signet de l’enregistrement actif.  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Paramètres  
 *varBookmark*  
 Une référence à un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objet représentant le signet sur l’enregistrement actif.  
  
### <a name="remarks"></a>Notes  
 Pour déterminer si les signets sont pris en charge sur le jeu d’enregistrements, appelez [CanBookmark](#canbookmark). Pour rendre les signets disponibles si elles sont prises en charge, vous devez définir le `CRecordset::useBookmarks` option dans le *dwOptions* paramètre de la [Open](#open) fonction membre.  
  
> [!NOTE]
>  Si les signets sont non pris en charge ou non disponible, l’appel `GetBookmark` entraîne une exception est levée. Les signets ne sont pas pris en charge sur les recordsets avant uniquement.  
  
 `GetBookmark` assigne la valeur du signet de l’enregistrement actuel à un `CDBVariant` objet. Pour revenir à cet enregistrement à tout moment après avoir déplacé vers un autre enregistrement, appelez [SetBookmark](#setbookmark) avec correspondant `CDBVariant` objet.  
  
> [!NOTE]
>  Après certaines opérations de jeu d’enregistrements, les signets peuvent ne plus être valides. Par exemple, si vous appelez `GetBookmark` suivie `Requery`, vous n’êtes peut-être pas en mesure de retourner à l’enregistrement avec `SetBookmark`. Appelez [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si vous pouvez appeler en toute sécurité `SetBookmark`.  
  
 Pour plus d’informations sur les signets et de navigation de jeu d’enregistrements, consultez les articles [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="getdefaultconnect"></a>  CRecordset::GetDefaultConnect  
 Appelé pour obtenir la chaîne de connexion par défaut.  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` qui contient la chaîne de connexion par défaut.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction membre pour obtenir la chaîne de connexion par défaut pour la source de données sur laquelle repose le jeu d’enregistrements. ClassWizard implémente cette fonction pour vous en identifiant la même source de données que vous utilisez dans ClassWizard pour obtenir des informations sur les tables et colonnes. Il est probablement utile à s’appuyer sur cette connexion par défaut lors du développement de votre application. Mais la connexion par défaut peut ne pas convenir pour les utilisateurs de votre application. Si tel est le cas, vous devez réimplémenter cette fonction, en ignorant la version de l’Assistant de classe. Pour plus d’informations sur les chaînes de connexion, consultez l’article [Source de données (ODBC)](../../data/odbc/data-source-odbc.md).  
  
##  <a name="getdefaultsql"></a>  CRecordset::GetDefaultSQL  
 Appelé pour obtenir la chaîne SQL par défaut à exécuter.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` qui contient l’instruction SQL par défaut.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction membre pour obtenir de l’instruction SQL par défaut sur lequel repose le jeu d’enregistrements. Cela peut être un nom de table ou d’une instance SQL **sélectionnez** instruction.  
  
 Vous définissez indirectement l’instruction SQL par défaut en déclarant votre classe de jeu d’enregistrements avec ClassWizard et ClassWizard effectue cette tâche pour vous.  
  
 Si vous avez besoin de la chaîne d’instruction SQL pour votre usage personnel, appelez `GetSQL`, qui retourne l’instruction SQL utilisée pour sélectionner les enregistrements du jeu d’enregistrements lorsqu’il a été ouvert. Vous pouvez modifier la chaîne SQL par défaut dans la substitution de votre classe du `GetDefaultSQL`. Par exemple, vous pouvez spécifier un appel à une requête prédéfinie à l’aide un **appeler** instruction. (Notez, toutefois, que si vous modifiez `GetDefaultSQL`, vous devez également modifier `m_nFields` pour faire correspondre le nombre de colonnes dans la source de données.)  
  
 Pour plus d’informations, consultez l’article [Recordset : déclaration de la classe d’une Table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
> [!CAUTION]
>  Le nom de table sera vide si l’infrastructure n’a pas pu identifier un nom de table, si plusieurs noms de table ont été fournis, ou si un **appeler** instruction n’a pas pu être interprétée. Notez que lorsque vous utilisez un **appeler** instruction, vous ne devez pas insérer un espace blanc entre l’accolade et la **appeler** mot clé, ni vous devez insérer un espace blanc avant l’accolade ou avant le  **Sélectionnez** mot clé dans un **sélectionnez** instruction.  
  
##  <a name="getfieldvalue"></a>  CRecordset::GetFieldValue  
 Récupère les données de champ dans l’enregistrement actif.  
  
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
 *Caractère*  
 Le nom d’un champ.  
  
 *varValu*e  
 Une référence à un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objet qui stocke la valeur du champ.  
  
 *nFieldType*  
 Le type de données ODBC C du champ. À l’aide de la valeur par défaut, DEFAULT_FIELD_TYPE, force `GetFieldValue` pour déterminer le type de données C à partir du type de données SQL, selon le tableau suivant. Sinon, vous pouvez spécifier les données tapez directement, ou choisissez un type de données compatibles ; par exemple, vous pouvez stocker n’importe quel type de données en SQL_C_CHAR.  
  
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
  
 Pour plus d’informations sur les types de données ODBC, consultez les rubriques « Types de données SQL » et « Types de données C » dans l’annexe D du Kit de développement Windows.  
  
 *nIndex*  
 Index de base zéro du champ.  
  
 *strValue*  
 Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet qui stocke la valeur du champ converti en texte, quel que soit le type de données.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez rechercher un champ par nom ou par index. Vous pouvez stocker la valeur du champ dans soit un `CDBVariant` objet ou un `CString` objet.  
  
 Si vous avez implémenté l’extraction de lignes en bloc, l’enregistrement actif est toujours positionnée sur le premier enregistrement dans un ensemble de lignes. Pour utiliser `GetFieldValue` sur un enregistrement au sein d’un ensemble de lignes donné, vous devez d’abord appeler la [SetRowsetCursorPosition](#setrowsetcursorposition) fonction membre pour déplacer le curseur à la ligne souhaitée au sein de cet ensemble de lignes. Appelez ensuite `GetFieldValue` pour cette ligne. Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` possibilité du *dwOptions* paramètre dans le [Open](#open) fonction membre.  
  
 Vous pouvez utiliser `GetFieldValue` pour récupérer dynamiquement des champs au moment de l’exécution plutôt que de les lier statiquement au moment du design. Par exemple, si vous avez déclaré un objet recordset directement à partir de `CRecordset`, vous devez utiliser `GetFieldValue` pour récupérer les données de champ ; exchange de champs d’enregistrements (RFX) ou RFX en bloc (RFX en bloc), n’est pas implémentée.  
  
> [!NOTE]
>  Si vous déclarez un objet recordset sans dériver `CRecordset`, n’ont pas de la bibliothèque de curseurs ODBC chargé. La bibliothèque de curseurs nécessite que le jeu d’enregistrements ont au moins une colonne dépendante ; Toutefois, lorsque vous utilisez `CRecordset` directement, aucune des colonnes sont liés. Les fonctions membres [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) et [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) contrôler si la bibliothèque de curseurs sera chargée.  
  
 `GetFieldValue` appelle la fonction API ODBC `SQLGetData`. Si votre pilote renvoie la valeur SQL_NO_TOTAL pour la longueur réelle de la valeur du champ, `GetFieldValue` lève une exception. Pour plus d’informations sur `SQLGetData`, consultez le kit SDK Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant illustre des appels à `GetFieldValue` pour un objet recordset déclarées directement à partir de `CRecordset`.  
  
 [!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  Contrairement à la classe DAO `CDaoRecordset`, `CRecordset` n’a pas un `SetFieldValue` fonction membre. Si vous créez un objet directement à partir de `CRecordset`, il est effectivement en lecture seule.  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getodbcfieldcount"></a>  CRecordset::GetODBCFieldCount  
 Récupère le nombre total de champs dans votre objet recordset.  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de champs dans le jeu d’enregistrements.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur la création de jeux d’enregistrements, consultez l’article [Recordset : création et fermeture de Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getodbcfieldinfo"></a>  CRecordset::GetODBCFieldInfo  
 Obtient des informations sur les champs dans le jeu d’enregistrements.  
  
```  
void GetODBCFieldInfo(
    LPCTSTR lpszName,  
    CODBCFieldInfo& fieldinfo);

 
void GetODBCFieldInfo(
    short nIndex,  
    CODBCFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>Paramètres  
 *Caractère*  
 Le nom d’un champ.  
  
 *FieldInfo*  
 Une référence à un `CODBCFieldInfo` structure.  
  
 *nIndex*  
 Index de base zéro du champ.  
  
### <a name="remarks"></a>Notes  
 Une version de la fonction vous permet de rechercher un champ par nom. L’autre version vous permet de rechercher un champ par index.  
  
 Pour obtenir une description sur les informations retournées, consultez le [CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md) structure.  
  
 Pour plus d’informations sur la création de jeux d’enregistrements, consultez l’article [Recordset : création et fermeture de Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getrecordcount"></a>  CRecordset::GetRecordCount  
 Détermine la taille de l’objet recordset.  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’enregistrements dans le jeu d’enregistrements ; 0 si le jeu d’enregistrements ne contient aucun enregistrement ; ou -1 si le nombre d’enregistrements ne peut pas être déterminé.  
  
### <a name="remarks"></a>Notes  
  
> [!CAUTION]
>  Le nombre d’enregistrements est maintenu comme une « borne haute, « l’enregistrement le plus élevé numérotés encore vu que l’utilisateur parcourt les enregistrements. Le nombre total d’enregistrements est connu uniquement une fois que l’utilisateur a déplacé au-delà du dernier enregistrement. Pour des raisons de performances, le nombre n'est pas mis à jour lorsque vous appelez `MoveLast`. Pour compter les enregistrements vous-même, appelez `MoveNext` à plusieurs reprises jusqu'à ce que `IsEOF` retourne différente de zéro. Ajout d’un enregistrement par le biais de `CRecordset:AddNew` et `Update` augmente le nombre ; la suppression d’un enregistrement par le biais de `CRecordset::Delete` diminue le nombre.  
  
##  <a name="getrowsetsize"></a>  CRecordset::GetRowsetSize  
 Obtient le paramètre actuel pour le nombre de lignes que vous souhaitez récupérer pendant une extraction donnée.  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de lignes à récupérer durant une extraction donnée.  
  
### <a name="remarks"></a>Notes  
 Si vous utilisez l’extraction de lignes en bloc, la taille d’ensemble de lignes par défaut lorsque le jeu d’enregistrements est ouvert est 25 ; Sinon, il est 1.  
  
 Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` option dans le *dwOptions* paramètre de la [Open](#open) fonction membre. Pour modifier le paramètre de la taille de l’ensemble de lignes, appelez [SetRowsetSize](#setrowsetsize).  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getrowsfetched"></a>  CRecordset::GetRowsFetched  
 Détermine le nombre d’enregistrements ont été réellement récupéré après une extraction.  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de lignes récupérées à partir de la source de données après une extraction donnée.  
  
### <a name="remarks"></a>Notes  
 Cela est utile lorsque vous avez implémenté l’extraction de lignes en bloc. La taille de l’ensemble de lignes indique généralement le nombre de lignes est extraites d’une extraction ; Toutefois, le nombre total de lignes dans le jeu d’enregistrements affecte également le nombre de lignes sera extrait dans un ensemble de lignes. Par exemple, si votre jeu d’enregistrements a 10 enregistrements avec un paramètre de taille d’ensemble de lignes de 4, puis une boucle dans le jeu d’enregistrements en appelant `MoveNext` entraîne l’ensemble de lignes final ayant des enregistrements seulement 2.  
  
 Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` option dans le *dwOptions* paramètre de la [Open](#open) fonction membre. Pour spécifier la taille de l’ensemble de lignes, appelez [SetRowsetSize](#setrowsetsize).  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>  CRecordset::GetRowStatus  
 Obtient l’état d’une ligne dans l’ensemble de lignes en cours.  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *wRow*  
 La position de base un d’une ligne dans l’ensemble de lignes en cours. Cette valeur peut varier de 1 à la taille de l’ensemble de lignes.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur d’état de la ligne. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 `GetRowStatus` Retourne une valeur qui indique soit toute modification dans la ligne d’état depuis son dernier extraites de la source de données, ou qui aucune ligne correspondant à *wRow* a été récupérée. Le tableau ci-dessous répertorie les valeurs de retour possibles.  
  
|Valeur d’état|Description|  
|------------------|-----------------|  
|SQL_ROW_SUCCESS|La ligne est inchangée.|  
|SQL_ROW_UPDATED|La ligne a été mis à jour.|  
|SQL_ROW_DELETED|La ligne a été supprimée.|  
|SQL_ROW_ADDED|La ligne a été ajoutée.|  
|SQL_ROW_ERROR|La ligne n’est pas récupérables en raison d’une erreur.|  
|SQL_ROW_NOROW|Il n’existe aucune ligne qui correspond à *wRow*.|  
  
 Pour plus d’informations, consultez la fonction API ODBC `SQLExtendedFetch` dans le SDK Windows.  
  
##  <a name="getstatus"></a>  CRecordset::GetStatus  
 Détermine l’index de l’enregistrement actif dans le jeu d’enregistrements et indique si le dernier enregistrement a été vu.  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *rStatus*  
 Référence à un objet `CRecordsetStatus`. Pour plus d'informations, consultez la section Notes.  
  
### <a name="remarks"></a>Notes  
 `CRecordset` tente d’effectuer le suivi de l’index, mais dans certaines circonstances cela ne peut pas être possible. Consultez [GetRecordCount](#getrecordcount) pour obtenir une explication.  
  
 Le `CRecordsetStatus` structure a la forme suivante :  
  
```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```
  
 Les deux membres de `CRecordsetStatus` ont les significations suivantes :  
  
- `m_lCurrentRecord` Contient l’index de base zéro de l’enregistrement actif dans le jeu d’enregistrements, s’il est connu. Si l’index ne peut pas être déterminé, ce membre contient AFX_CURRENT_RECORD_UNDEFINED (-2). Si `IsBOF` est la valeur TRUE (jeu d’enregistrements vide ou tentative de défilement avant le premier enregistrement), puis `m_lCurrentRecord` a la valeur AFX_CURRENT_RECORD_BOF (-1). Si sur le premier enregistrement, puis elle est définie sur 0, ensuite enregistrer 1 et ainsi de suite.  
  
- `m_bRecordCountFinal` Différent de zéro si le nombre total d’enregistrements dans le jeu d’enregistrements a été déterminé. Généralement cela doit être accompli en commençant au début de l’objet recordset et en appelant `MoveNext` jusqu'à ce que `IsEOF` retourne différente de zéro. Si ce membre est égal à zéro, l’enregistrement de nombre tel que retourné par `GetRecordCount`, si pas -1, n'est que le nombre « borne haute » des enregistrements.  
  
##  <a name="getsql"></a>  CRecordset::GetSQL  
 Appelez cette fonction membre pour obtenir de l’instruction SQL qui a été utilisée pour sélectionner les enregistrements du jeu d’enregistrements lorsqu’il a été ouvert.  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un **const** font référence à un `CString` qui contient l’instruction SQL.  
  
### <a name="remarks"></a>Notes  
 Il s’agit généralement d’une instance SQL **sélectionnez** instruction. La chaîne retournée par `GetSQL` est en lecture seule.  
  
 La chaîne retournée par `GetSQL` est généralement différent à partir de n’importe quelle chaîne que vous avez peut-être passé à l’ensemble d’enregistrements dans le *lpszSQL* paramètre à la `Open` fonction membre. Il s’agit, car l’objet recordset construit une instruction SQL complète basée sur ce que vous avez passé à `Open`, ce que vous avez spécifié avec ClassWizard, ce que vous avez spécifié dans le `m_strFilter` et `m_strSort` les membres de données et tous les paramètres que vous deviez spécifié. Pour plus d’informations sur la façon dont le jeu d’enregistrements construit cette instruction SQL, consultez l’article [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
> [!NOTE]
>  Appelez cette fonction membre uniquement après avoir appelé [Open](#open).  
  
##  <a name="gettablename"></a>  CRecordset::GetTableName  
 Obtient le nom de la table SQL sur laquelle repose la requête du recordset.  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un **const** font référence à un `CString` qui contient la table nom, si le jeu d’enregistrements est basée sur une table ; sinon, une chaîne vide.  
  
### <a name="remarks"></a>Notes  
 `GetTableName` est valide uniquement si le jeu d’enregistrements est basée sur une table, pas une jointure de plusieurs tables ou d’une requête prédéfinie (procédure stockée). Le nom est en lecture seule.  
  
> [!NOTE]
>  Appelez cette fonction membre uniquement après avoir appelé [Open](#open).  
  
##  <a name="isbof"></a>  CRecordset::IsBOF  
 Retourne une valeur différente de zéro si le jeu d’enregistrements a été placé avant le premier enregistrement. Il n’existe aucun enregistrement actif.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements ne contient aucun enregistrement ou si vous avez le défilement arrière avant le premier enregistrement ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre avant que vous accédez à partir de l’enregistrement à enregistrement pour savoir si vous avez bien effectué avant le premier enregistrement de l’objet recordset. Vous pouvez également utiliser `IsBOF` avec `IsEOF` pour déterminer si le jeu d’enregistrements contient tous les enregistrements ou est vide. Immédiatement après avoir appelé `Open`, si le jeu d’enregistrements ne contient aucun enregistrement, `IsBOF` retourne différente de zéro. Lorsque vous ouvrez un jeu d’enregistrements qui a au moins un enregistrement, le premier enregistrement est l’enregistrement actif et `IsBOF` retourne 0.  
  
 Si le premier enregistrement est l’enregistrement actif et que vous appelez `MovePrev`, `IsBOF` par la suite renverra différente de zéro. Si `IsBOF` retourne différente de zéro et que vous appelez `MovePrev`, une erreur se produit. Si `IsBOF` retourne une valeur différente de zéro, l’enregistrement en cours n’est pas défini, et toute action qui nécessite un enregistrement actuel entraîne une erreur.  
  
### <a name="example"></a>Exemple  
 Cet exemple utilise `IsBOF` et `IsEOF` pour détecter les limites d’un jeu d’enregistrements que le code parcourt le jeu d’enregistrements dans les deux sens.  
  
 [!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>  CRecordset::IsDeleted  
 Détermine si l’enregistrement en cours a été supprimé.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le recordset est positionné sur un enregistrement supprimé. sinon 0.  
  
### <a name="remarks"></a>Notes  
 Si vous accédez à un enregistrement et `IsDeleted` renvoie la valeur TRUE (différent de zéro), puis vous devez accéder à un autre enregistrement avant de pouvoir effectuer toutes les opérations de jeu d’enregistrements.  
  
 Le résultat de `IsDeleted` dépend de nombreux facteurs, tels que le type de votre jeu d’enregistrements, si votre jeu d’enregistrements est modifiable, si vous avez spécifié le `CRecordset::skipDeletedRecords` option lorsque vous avez ouvert le jeu d’enregistrements, si vos packs de pilote d’enregistrements supprimés et s’il existe plusieurs utilisateurs.  
  
 Pour plus d’informations sur `CRecordset::skipDeletedRecords` et pilote de livraison, consultez la [Open](#open) fonction membre.  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne devez pas appeler `IsDeleted`. Au lieu de cela, appelez le [GetRowStatus](#getrowstatus) fonction membre. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="iseof"></a>  CRecordset::IsEOF  
 Retourne une valeur différente de zéro si le jeu d’enregistrements a été positionné après le dernier enregistrement. Il n’existe aucun enregistrement actif.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements ne contient aucun enregistrement ou si vous avez déplacé au-delà du dernier enregistrement ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre que vous accédez à partir de l’enregistrement à enregistrement pour savoir si vous avez dépassé le dernier enregistrement de l’objet recordset. Vous pouvez également utiliser `IsEOF` pour déterminer si le jeu d’enregistrements contient tous les enregistrements ou est vide. Immédiatement après avoir appelé `Open`, si le jeu d’enregistrements ne contient aucun enregistrement, `IsEOF` retourne différente de zéro. Lorsque vous ouvrez un jeu d’enregistrements qui a au moins un enregistrement, le premier enregistrement est l’enregistrement actif et `IsEOF` retourne 0.  
  
 Si le dernier enregistrement est l’enregistrement actif lorsque vous appelez `MoveNext`, `IsEOF` par la suite renverra différente de zéro. Si `IsEOF` retourne différente de zéro et que vous appelez `MoveNext`, une erreur se produit. Si `IsEOF` retourne une valeur différente de zéro, l’enregistrement en cours n’est pas défini, et toute action qui nécessite un enregistrement actuel entraîne une erreur.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="isfielddirty"></a>  CRecordset::IsFieldDirty  
 Détermine si le membre de données du champ spécifié a été modifié depuis [modifier](#edit) ou [AddNew](#addnew) a été appelée.  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 *PV*  
 Pointeur vers le membre de données du champ dont vous souhaitez vérifier, ou NULL pour déterminer si les champs sont modifiés de l’état.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le membre de données du champ spécifié a changé depuis l’appel `AddNew` ou `Edit`; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Les données dans tous les membres de données de champ incorrectes seront transférées à l’enregistrement sur la source de données lors de l’enregistrement actif est mis à jour par un appel à la [mise à jour](#update) fonction membre de `CRecordset` (suit un appel à `Edit` ou `AddNew`).  
  
> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les jeux d’enregistrements qui est à l’aide de l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, puis `IsFieldDirty` retournera toujours FALSE et entraîne un échec d’assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Appel `IsFieldDirty` réinitialisera les effets des appels à précédentes [SetFieldDirty](#setfielddirty) étant donné que l’état de non-intégrité du champ est réévalué. Dans le `AddNew` cas, si la valeur du champ est différente de la valeur null de pseudo, l’état du champ a la valeur incorrecte. Dans le `Edit` cas, si la valeur du champ est différente de la valeur mise en cache, puis l’état du champ est modifié.  
  
 `IsFieldDirty` est implémentée via [DoFieldExchange](#dofieldexchange).  
  
 Pour plus d’informations sur l’indicateur de changement, consultez l’article [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
##  <a name="isfieldnull"></a>  CRecordset::IsFieldNull  
 Retourne zéro si le champ spécifié dans l’enregistrement actif est Null (n’a aucune valeur).  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 *PV*  
 Pointeur vers le membre de données du champ dont vous souhaitez vérifier, ou NULL pour déterminer si les champs ont la valeur Null de l’état.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le membre de données du champ spécifié est marqué en tant que valeur Null. sinon 0.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour déterminer si le membre de données de champ spécifié d’un jeu d’enregistrements a été marqué comme Null. (Dans la terminologie de base de données, Null signifie « ne having aucune valeur » et n’est pas identique à la valeur NULL en C++.) Si un membre de données de champ est marqué avec la valeur Null, il est interprété en tant que colonne de l’enregistrement en cours pour lequel il n’existe aucune valeur.  
  
> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les jeux d’enregistrements qui est à l’aide de l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, puis `IsFieldNull` retournera toujours FALSE et entraîne un échec d’assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `IsFieldNull` est implémentée via [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isfieldnullable"></a>  CRecordset::IsFieldNullable  
 Retourne une valeur différente de zéro si le champ spécifié dans l’enregistrement actif peut être défini avec la valeur Null (n’avoir aucune valeur).  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 *PV*  
 Pointeur vers le membre de données du champ dont vous souhaitez vérifier, ou NULL pour déterminer si les champs peuvent être définis avec une valeur Null de l’état.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour déterminer si le membre de données du champ spécifié est « null » (peut être définie avec une valeur Null ; C++ NULL n’est pas identique à Null, ce qui, dans la terminologie de base de données, signifie « ne having aucune valeur »).  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `IsFieldNullable`. Au lieu de cela, appelez le [GetODBCFieldInfo au](#getodbcfieldinfo) fonction membre pour déterminer si un champ peut être défini avec une valeur Null. Notez que vous pouvez toujours appeler `GetODBCFieldInfo`, indépendamment de si vous avez implémenté l’extraction de lignes en bloc. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Un champ qui ne peut pas être Null doit avoir une valeur. Si vous essayez de définir un tel champ avec la valeur Null lors de l’ajout ou la mise à jour un enregistrement, la source de données rejette l’ajout ou la mise à jour, et [mettre à jour](#update) lève une exception. L’exception se produit lorsque vous appelez `Update`, pas lorsque vous appelez [SetFieldNull](#setfieldnull).  
  
 À l’aide de la valeur NULL pour le premier argument de la fonction s’applique uniquement à la fonction `outputColumn` ne champs pas `param` champs. Par exemple, l’appel  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 définira uniquement `outputColumn` champs avec la valeur NULL ; `param` champs ne seront pas affectées.  
  
 Pour travailler sur `param` champs, vous devez fournir l’adresse réelle de l’individu `param` vous souhaitez travailler, telles que :  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Cela signifie que vous ne pouvez pas définir tous les `param` champs avec la valeur NULL, comme vous pouvez le faire avec `outputColumn` champs.  
  
 `IsFieldNullable` est implémentée via [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isopen"></a>  CRecordset::IsOpen  
 Détermine si le recordset est déjà ouvert.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’objet recordset [Open](#open) ou [Requery](#requery) fonction membre a été précédemment appelée et le jeu d’enregistrements n’a pas été fermée ; sinon, 0.  
  
##  <a name="m_hstmt"></a>  CRecordset::m_hstmt  
 Contient un handle vers la structure de données instruction ODBC, de type HSTMT, associé à l’ensemble d’enregistrements.  
  
### <a name="remarks"></a>Notes  
 Chaque requête à une source de données ODBC est associé à un HSTMT.  
  
> [!CAUTION]
>  N’utilisez pas `m_hstmt` avant [Open](#open) a été appelée.  
  
 Normalement, vous n’avez pas besoin d’accéder à la HSTMT directement, mais vous en auriez besoin pour l’exécution directe des instructions SQL. Le `ExecuteSQL` fonction membre de classe `CDatabase` fournit un exemple d’utilisation `m_hstmt`.  
  
##  <a name="m_nfields"></a>  CRecordset::m_nFields  
 Contient le nombre de membres de données de champ dans la classe de jeu d’enregistrements ; Autrement dit, le nombre de colonnes sélectionnées par le jeu d’enregistrements à partir de la source de données.  
  
### <a name="remarks"></a>Notes  
 Le constructeur de la classe de jeu d’enregistrements doit initialiser `m_nFields` avec le nombre correct. Si vous n’avez pas implémenté l’extraction de lignes en bloc, ClassWizard écrit cette initialisation pour vous lorsque vous l’utilisez pour déclarer votre classe de jeu d’enregistrements. Vous pouvez également l’écrire manuellement.  
  
 L’infrastructure utilise ce nombre pour gérer l’interaction entre les membres de données de champ et les colonnes correspondantes de l’enregistrement en cours sur la source de données.  
  
> [!CAUTION]
>  Ce numéro doit correspondre au nombre de « colonnes de sortie » inscrit dans `DoFieldExchange` ou `DoBulkFieldExchange` après un appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) avec le paramètre `CFieldExchange::outputColumn`.  
  
 Vous pouvez lier des colonnes dynamiquement, comme expliqué dans l’article « Recordset : dynamiquement les colonnes de données de liaison. » Si vous procédez ainsi, vous devez augmenter le nombre dans `m_nFields` afin de refléter le numéro de fonction RFX et RFX en bloc appelle votre `DoFieldExchange` ou `DoBulkFieldExchange` fonction membre pour les colonnes liées dynamiquement.  
  
 Pour plus d’informations, consultez les articles [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) et [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’article [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_nparams"></a>  CRecordset::m_nParams  
 Contient le nombre de membres de données de paramètre dans la classe de jeu d’enregistrements ; Autrement dit, le nombre de paramètres transmis avec la requête du recordset.  
  
### <a name="remarks"></a>Notes  
 Si votre classe de jeu d’enregistrements a des membres de données de paramètre, le constructeur de la classe doit initialiser `m_nParams` avec le nombre correct. La valeur de `m_nParams` est 0 par défaut. Si vous ajoutez des membres de données de paramètre (ce que vous devez faire manuellement) vous devez également ajouter manuellement une initialisation dans le constructeur de classe afin de refléter le nombre de paramètres (qui doit être au moins aussi grand que le nombre de « espaces réservés dans votre `m_strFilter` ou `m_strSort`chaîne).  
  
 L’infrastructure utilise ce nombre lorsqu’il paramètre la requête du recordset.  
  
> [!CAUTION]
>  Ce numéro doit correspondre au nombre de « params » inscrit dans `DoFieldExchange` ou `DoBulkFieldExchange` après un appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) avec une valeur de paramètre `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, ou `CFieldExchange::inoutParam`.  
  
### <a name="example"></a>Exemple  
  Consultez les articles [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) et [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_pdatabase"></a>  CRecordset::m_pDatabase  
 Contient un pointeur vers le `CDatabase` objet via lequel le jeu d’enregistrements est connecté à une source de données.  
  
### <a name="remarks"></a>Notes  
 Cette variable est définie de deux manières. En règle générale, vous transmettez un pointeur à un socket déjà `CDatabase` objet lorsque vous construisez l’objet recordset. Si vous passez NULL au lieu de cela, `CRecordset` crée un `CDatabase` de l’objet pour vous et le connecte. Dans les deux cas, `CRecordset` stocke le pointeur dans cette variable.  
  
 Normalement vous serez directement inutile d’utiliser le pointeur stocké dans `m_pDatabase`. Si vous écrivez vos propres extensions à `CRecordset`, toutefois, vous devrez peut-être utiliser le pointeur. Par exemple, vous devrez peut-être le pointeur si vous levez vos propres `CDBException`s. Ou vous en aurez besoin si vous avez besoin de faire quelque chose en utilisant le même `CDatabase` objet, telles que les transactions, la définition de délais, en cours d’exécution ou en appelant le `ExecuteSQL` fonction membre de classe `CDatabase` pour exécuter des instructions SQL directement.  
  
##  <a name="m_strfilter"></a>  CRecordset::m_strFilter  
 Après avoir construit l’objet recordset, mais avant d’appeler ses `Open` membre de fonction, utilisez ce membre de données pour stocker un `CString` contenant une instance SQL **où** clause.  
  
### <a name="remarks"></a>Notes  
 Le jeu d’enregistrements utilise cette chaîne pour contraindre (ou filtrer) les enregistrements qu’il sélectionne au cours de la `Open` ou `Requery` appeler. Cela est utile pour sélectionner un sous-ensemble des enregistrements, tels que « tous les vendeurs basés en Californie » (« état = autorité de certification »). La syntaxe ODBC SQL pour un **où** clause est  
  
 `WHERE search-condition`  
  
 Notez que vous n’incluez pas le **où** mot clé dans votre chaîne. L’infrastructure lui fournit.  
  
 Vous pouvez également paramétrer votre chaîne de filtre en plaçant '' des espaces réservés, déclaration d’un membre de données de paramètre dans votre classe pour chaque espace réservé et passer des paramètres à l’ensemble d’enregistrements au moment de l’exécution. Cela vous permet de construire le filtre au moment de l’exécution. Pour plus d’informations, consultez l’article [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Pour plus d’informations sur SQL **où** clauses, consultez l’article [SQL](../../data/odbc/sql.md). Pour plus d’informations sur la sélection et filtrage d’enregistrements, consultez l’article [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>  CRecordset::m_strSort  
 Après avoir construit l’objet recordset, mais avant d’appeler ses `Open` membre de fonction, utilisez ce membre de données pour stocker un `CString` contenant une instance SQL **ORDER BY** clause.  
  
### <a name="remarks"></a>Notes  
 Le jeu d’enregistrements utilise cette chaîne pour trier les enregistrements, il sélectionne au cours de la `Open` ou `Requery` appeler. Vous pouvez utiliser cette fonctionnalité pour trier un jeu d’enregistrements sur une ou plusieurs colonnes. La syntaxe ODBC SQL pour un **ORDER BY** clause est  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 où une spécification de tri est un entier ou un nom de colonne. Vous pouvez également spécifier l’ordre croissant ou décroissant (l’ordre est croissant par défaut) en ajoutant « ASC » ou « DESC » à la liste des colonnes dans la chaîne de tri. Les enregistrements sélectionnés sont triés en premier par la première colonne répertoriée, puis par la seconde et ainsi de suite. Par exemple, vous pouvez commander un jeu d’enregistrements « Customers » par le nom de famille, puis du prénom. Le nombre de colonnes que vous pouvez afficher la liste dépend de la source de données. Pour plus d’informations, consultez le Kit de développement Windows.  
  
 Notez que vous n’incluez pas le **ORDER BY** mot clé dans votre chaîne. L’infrastructure lui fournit.  
  
 Pour plus d’informations sur les clauses SQL, consultez l’article [SQL](../../data/odbc/sql.md). Pour plus d’informations sur le tri d’enregistrements, consultez l’article [Recordset : tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>  CRecordset::Move  
 Déplace le pointeur d’enregistrement actif dans le jeu d’enregistrements, vers l’avant ou vers l’arrière.  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>Paramètres  
 *nRows*  
 Le nombre de lignes à avancer ou reculer. Les valeurs positives déplacent vers l’avant, vers la fin de l’objet recordset. Déplacent vers l’arrière, des valeurs négatives vers le début.  
  
 *wFetchType*  
 Détermine l’ensemble de lignes qui `Move` extrait. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Si vous passez la valeur 0 pour *nRows*, `Move` actualise l’enregistrement actuel ; `Move` prendra fin à toute `AddNew` ou `Edit` mode et restaure la valeur de l’enregistrement actuel avant `AddNew` ou `Edit` a été appelée.  
  
> [!NOTE]
>  Lorsque vous déplacez dans un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez [CRecordset::IsDeleted](#isdeleted) pour plus d’informations. Lorsque vous ouvrez un `CRecordset` avec la `skipDeletedRecords` option set, `Move` déclare si le *nRows* paramètre est 0. Ce comportement empêche l’actualisation de lignes qui sont supprimées par les autres applications clientes utilisant les mêmes données. Consultez le *dwOption* paramètre dans [Open](#open) pour obtenir une description de `skipDeletedRecords`.  
  
 `Move` repositionne le jeu d’enregistrements par les ensembles de lignes. En fonction des valeurs pour *nRows* et *wFetchType*, `Move` extrait l’ensemble de lignes approprié, puis rend le premier enregistrement dans cet ensemble de lignes l’enregistrement actif. Si vous n’avez pas implémenté l’extraction de lignes en bloc, la taille de l’ensemble de lignes est toujours 1. Lors de l’extraction d’un ensemble de lignes, `Move` appelle directement la [CheckRowsetError](#checkrowseterror) fonction membre pour gérer les erreurs résultant de l’opération de récupération.  
  
 En fonction des valeurs que vous passez, `Move` équivaut à d’autres `CRecordset` fonctions membres. En particulier, la valeur de *wFetchType* peut indiquer une fonction membre qui est plus intuitive et souvent la méthode recommandée pour déplacer l’enregistrement actif.  
  
 Le tableau suivant répertorie les valeurs possibles pour *wFetchType*, l’ensemble de lignes qui `Move` extrait selon *wFetchType* et *nRows*et n’importe quel équivalent fonction de membre correspondant à *wFetchType*.  
  
|wFetchType|Ensemble de lignes extraite|Fonction membre équivalent|  
|----------------|--------------------|--------------------------------|  
|SQL_FETCH_RELATIVE (la valeur par défaut)|Le démarrage de l’ensemble de lignes *nRows* ou les lignes à partir de la première ligne dans l’ensemble de lignes en cours.||  
|SQL_FETCH_NEXT|L’ensemble de lignes suivant ; *nRows* est ignoré.|[MoveNext](#movenext)|  
|SQL_FETCH_PRIOR|L’ensemble de lignes précédent ; *nRows* est ignoré.|[MovePrev](#moveprev)|  
|SQL_FETCH_FIRST|Le premier ensemble de lignes dans le jeu d’enregistrements ; *nRows* est ignoré.|[MoveFirst](#movefirst)|  
|SQL_FETCH_LAST|Le dernier ensemble de lignes dans le jeu d’enregistrements ; *nRows* est ignoré.|[MoveLast](#movelast)|  
|SQL_FETCH_ABSOLUTE|Si *nRows* > 0, l’ensemble de lignes démarrant *nRows* ou les lignes à partir du début de l’objet recordset. Si *nRows* < 0, l’ensemble de lignes démarrant *nRows* ou les lignes à partir de la fin de l’objet recordset. Si *nRows* = 0, une condition de début du fichier (BOF) est retournée.|[SetAbsolutePosition](#setabsoluteposition)|  
|SQL_FETCH_BOOKMARK|L’ensemble de lignes en commençant à la ligne dont la valeur signet correspond à *nRows*.|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  Pour les recordsets avant uniquement, `Move` est uniquement valide avec une valeur de SQL_FETCH_NEXT pour *wFetchType*.  
  
> [!CAUTION]
>  Appel `Move` lève une exception si le jeu d’enregistrements ne comporte aucun enregistrement. Pour déterminer si le jeu d’enregistrements a tous les enregistrements, appelez [IsBOF](#isbof) et [IsEOF](#iseof).  
  
> [!NOTE]
>  Si vous avez atteint le début ou la fin de l’objet recordset (`IsBOF` ou `IsEOF` retourne différente de zéro), l’appel une `Move` fonction lève éventuellement une `CDBException`. Par exemple, si `IsEOF` retourne différente de zéro et `IsBOF` est pas le cas, puis `MoveNext` lève une exception, mais `MovePrev` ne sera pas.  
  
> [!NOTE]
>  Si vous appelez `Move` pendant que l’enregistrement actif est mis à jour ou ajoutée, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus d’informations, consultez la fonction API ODBC `SQLExtendedFetch` dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>  CRecordset::MoveFirst  
 Fait du premier enregistrement dans le premier ensemble de lignes de l’enregistrement actif.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Notes  
 Quelle que soit implémenté ou non l’extraction de lignes en bloc a été, ce sera toujours le premier enregistrement dans le jeu d’enregistrements.  
  
 Vous n’avez pas à appeler `MoveFirst` immédiatement après l’ouverture de l’ensemble d’enregistrements. À ce stade, le premier enregistrement (le cas échéant) est automatiquement l’enregistrement actif.  
  
> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.  
  
> [!NOTE]
>  Lorsque vous déplacez dans un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez le [IsDeleted](#isdeleted) fonction membre pour plus d’informations.  
  
> [!CAUTION]
>  Appel d’une le `Move` fonctions lève une exception si le jeu d’enregistrements ne comporte aucun enregistrement. Pour déterminer si le jeu d’enregistrements a tous les enregistrements, appelez `IsBOF` et `IsEOF`.  
  
> [!NOTE]
>  Si vous appelez une de le `Move` fonctions pendant que l’enregistrement actif est mis à jour ou ajoutée, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="movelast"></a>  CRecordset::MoveLast  
 Fait du premier enregistrement dans le dernier ensemble de lignes de l’enregistrement actif.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Notes  
 Si vous n’avez pas implémenté l’extraction de lignes en bloc, le jeu d’enregistrements a une taille d’ensemble de lignes de 1, donc `MoveLast` simplement se déplace vers le dernier enregistrement dans le jeu d’enregistrements.  
  
> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.  
  
> [!NOTE]
>  Lorsque vous déplacez dans un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez le [IsDeleted](#isdeleted) fonction membre pour plus d’informations.  
  
> [!CAUTION]
>  Appel d’une le `Move` fonctions lève une exception si le jeu d’enregistrements ne comporte aucun enregistrement. Pour déterminer si le jeu d’enregistrements a tous les enregistrements, appelez `IsBOF` et `IsEOF`.  
  
> [!NOTE]
>  Si vous appelez une de le `Move` fonctions pendant que l’enregistrement actif est mis à jour ou ajoutée, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="movenext"></a>  CRecordset::MoveNext  
 Fait du premier enregistrement dans l’ensemble de lignes suivant l’enregistrement actif.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Notes  
 Si vous n’avez pas implémenté l’extraction de lignes en bloc, le jeu d’enregistrements a une taille d’ensemble de lignes de 1, donc `MoveNext` simplement se déplace vers l’enregistrement suivant.  
  
> [!NOTE]
>  Lorsque vous déplacez dans un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez le [IsDeleted](#isdeleted) fonction membre pour plus d’informations.  
  
> [!CAUTION]
>  Appel d’une le `Move` fonctions lève une exception si le jeu d’enregistrements ne comporte aucun enregistrement. Pour déterminer si le jeu d’enregistrements a tous les enregistrements, appelez `IsBOF` et `IsEOF`.  
  
> [!NOTE]
>  Il est également recommandé que vous appelez `IsEOF` avant d’appeler `MoveNext`. Par exemple, si vous avez atteint après la fin de l’objet recordset et `IsEOF` retournera différente de zéro ; un appel ultérieur à `MoveNext` lève une exception.  
  
> [!NOTE]
>  Si vous appelez une de le `Move` fonctions pendant que l’enregistrement actif est mis à jour ou ajoutée, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="moveprev"></a>  CRecordset::MovePrev  
 Fait du premier enregistrement dans l’ensemble de lignes précédent de l’enregistrement actif.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Notes  
 Si vous n’avez pas implémenté l’extraction de lignes en bloc, le jeu d’enregistrements a une taille d’ensemble de lignes de 1, donc `MovePrev` simplement se déplace vers l’enregistrement précédent.  
  
> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.  
  
> [!NOTE]
>  Lorsque vous déplacez dans un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez le [IsDeleted](#isdeleted) fonction membre pour plus d’informations.  
  
> [!CAUTION]
>  Appel d’une le `Move` fonctions lève une exception si le jeu d’enregistrements ne comporte aucun enregistrement. Pour déterminer si le jeu d’enregistrements a tous les enregistrements, appelez `IsBOF` et `IsEOF`.  
  
> [!NOTE]
>  Il est également recommandé que vous appelez `IsBOF` avant d’appeler `MovePrev`. Par exemple, si vous avez atteint le début de l’objet recordset, `IsBOF` retournera différente de zéro ; un appel ultérieur à `MovePrev` lève une exception.  
  
> [!NOTE]
>  Si vous appelez une de le `Move` fonctions pendant que l’enregistrement actif est mis à jour ou ajoutée, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="onsetoptions"></a>  CRecordset::OnSetOptions  
 Appelé pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Paramètres  
 *HStmt*  
 HSTMT de l’instruction ODBC dont les options doivent être définies.  
  
### <a name="remarks"></a>Notes  
 Appelez `OnSetOptions` pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée. L’infrastructure appelle cette fonction membre pour définir les options initiales pour le jeu d’enregistrements. `OnSetOptions` Détermine la prise en charge de la source de données pour les curseurs avec défilement et accès concurrentiel au curseur et définit les options du jeu d’enregistrements en conséquence. (Alors que `OnSetOptions` est utilisé pour les opérations de sélection, `OnSetUpdateOptions` est utilisé pour les opérations de mise à jour.)  
  
 Substituer `OnSetOptions` pour définir les options spécifiques au pilote ou à la source de données. Par exemple, si votre source de données prend en charge de l’ouverture d’un accès exclusif, vous pouvez substituer `OnSetOptions` pour tirer parti de cette capacité.  
  
 Pour plus d’informations sur les curseurs, consultez l’article [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="onsetupdateoptions"></a>  CRecordset::OnSetUpdateOptions  
 Appelé pour définir les options (utilisées sur la mise à jour) pour l’instruction ODBC spécifiée.  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Paramètres  
 *HStmt*  
 HSTMT de l’instruction ODBC dont les options doivent être définies.  
  
### <a name="remarks"></a>Notes  
 Appelez `OnSetUpdateOptions` pour définir les options (utilisées sur la mise à jour) pour l’instruction ODBC spécifiée. L’infrastructure appelle cette fonction membre après avoir créé un HSTMT pour mettre à jour des enregistrements dans un jeu d’enregistrements. (Alors que `OnSetOptions` est utilisé pour les opérations de sélection, `OnSetUpdateOptions` est utilisé pour les opérations de mise à jour.) `OnSetUpdateOptions` détermine la prise en charge de la source de données pour les curseurs avec défilement et accès concurrentiel au curseur et définit les options du jeu d’enregistrements en conséquence.  
  
 Substituer `OnSetUpdateOptions` pour définir les options d’une instruction ODBC avant que cette instruction est utilisée pour accéder à une base de données.  
  
 Pour plus d’informations sur les curseurs, consultez l’article [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="open"></a>  CRecordset::Open  
 Ouvre le recordset en récupération de la table ou en exécutant la requête qui représente le jeu d’enregistrements.  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>Paramètres  
 *nOpenType*  
 Acceptez la valeur par défaut, AFX_DB_USE_DEFAULT_TYPE ou utilisez une de ces valeurs à partir de la `enum OpenType`:  
  
- `CRecordset::dynaset` Un jeu d’enregistrements avec défilement bidirectionnel. L’appartenance et l’ordre des enregistrements sont déterminées lorsque le jeu d’enregistrements est ouvert, mais les modifications apportées par d’autres utilisateurs aux valeurs de données sont visibles après une opération d’extraction. Feuilles de réponse dynamiques sont également appelés curseurs pilotés par les jeux d’enregistrements.  
  
- `CRecordset::snapshot` Un jeu d’enregistrements statique avec défilement bidirectionnel. L’appartenance et l’ordre des enregistrements sont déterminées lorsque le jeu d’enregistrements est ouvert ; les valeurs de données sont déterminées lorsque les enregistrements sont extraits. Modifications apportées par d’autres utilisateurs ne sont pas visibles jusqu'à ce que le jeu d’enregistrements est fermé, puis rouvert.  
  
- `CRecordset::dynamic` Un jeu d’enregistrements avec défilement bidirectionnel. Modifications apportées par d’autres utilisateurs sur les valeurs d’appartenance, de classement et de données sont visibles après une opération d’extraction. Notez que de nombreux pilotes ODBC ne prennent pas en charge ce type de jeu d’enregistrements.  
  
- `CRecordset::forwardOnly` Un jeu d’enregistrements en lecture seule avec défilement vers l’avant uniquement.  
  
     Pour `CRecordset`, la valeur par défaut est `CRecordset::snapshot`. Le mécanisme de valeur par défaut permet les Assistants Visual C++ interagir avec les deux ODBC `CRecordset` et DAO `CDaoRecordset`, qui ont différentes valeurs par défaut.  
  
 Pour plus d’informations sur ces types de jeu d’enregistrements, consultez l’article [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations, consultez l’article « À l’aide de bloc et curseurs avec défilement » dans le SDK Windows.  
  
> [!CAUTION]
>  Si le type demandé n’est pas pris en charge, le framework lève une exception.  
  
 *lpszSQL*  
 Un pointeur de chaîne qui contient l’une des opérations suivantes :  
  
-   Un pointeur NULL.  
  
-   Nom d'une table.  
  
-   SQL **sélectionnez** instruction (éventuellement avec un SQL **où** ou **ORDER BY** clause).  
  
-   Un **appeler** instruction en spécifiant le nom d’une requête prédéfinie (procédure stockée). Veillez à ce que vous n’insérez pas d’espace entre l’accolade et la **appeler** mot clé.  
  
 Pour plus d’informations sur cette chaîne, consultez la table et la discussion du rôle de ClassWizard sous la section Remarques.  
  
> [!NOTE]
>  L’ordre des colonnes dans votre jeu de résultats doit correspondre à l’ordre de la RFX ou d’appels de fonction de RFX en bloc dans votre [DoFieldExchange](#dofieldexchange) ou [DoBulkFieldExchange](#dobulkfieldexchange) remplacement de la fonction.  
  
 *dwOptions*  
 Masque de bits qui peut spécifier une combinaison des valeurs répertoriées ci-dessous. Certaines d'entre elles s’excluent mutuellement. La valeur par défaut est **aucun**.  
  
- `CRecordset::none` Aucune option définie. Cette valeur de paramètre est mutuellement exclusive avec toutes les autres valeurs. Par défaut, le jeu d’enregistrements peut être mis à jour avec [modifier](#edit) ou [supprimer](#delete) et permet l’ajout de nouveaux enregistrements avec [AddNew](#addnew). Mise à jour dépend de la source de données, ainsi que dans le *nOpenType* option que vous spécifiez. Optimisation pour les ajouts en bloc n’est pas disponible. L’extraction de lignes en bloc n’est pas implémentée. Enregistrements supprimés ne seront pas ignorées lors de la navigation de jeu d’enregistrements. Les signets ne sont pas disponibles. La vérification automatique de champ incorrecte est implémentée.  
  
- `CRecordset::appendOnly` Ne pas autoriser `Edit` ou `Delete` sur le jeu d’enregistrements. Autoriser `AddNew` uniquement. Cette option s’exclut mutuellement avec `CRecordset::readOnly`.  
  
- `CRecordset::readOnly` Ouvrez le jeu d’enregistrements en lecture seule. Cette option s’exclut mutuellement avec `CRecordset::appendOnly`.  
  
- `CRecordset::optimizeBulkAdd` Utiliser une instruction SQL préparée pour optimiser l’ajout de plusieurs enregistrements en même temps. S’applique uniquement si vous n’utilisez pas la fonction API ODBC `SQLSetPos` pour mettre à jour le jeu d’enregistrements. La première mise à jour détermine quels champs sont marqués modifiés. Cette option s’exclut mutuellement avec `CRecordset::useMultiRowFetch`.  
  
- `CRecordset::useMultiRowFetch` Implémenter l’extraction de lignes en bloc pour autoriser plusieurs lignes doivent être extraites par une opération d’extraction unique. Il s’agit d’une fonctionnalité avancée conçue pour améliorer les performances. Toutefois, RFX en bloc n’est pas pris en charge par ClassWizard. Cette option s’exclut mutuellement avec `CRecordset::optimizeBulkAdd`. Notez que si vous spécifiez `CRecordset::useMultiRowFetch`, puis l’option `CRecordset::noDirtyFieldCheck` est activé automatiquement (double mise en tampon sera pas disponible) ; sur les recordsets avant uniquement, l’option `CRecordset::useExtendedFetch` est activé automatiquement. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
- `CRecordset::skipDeletedRecords` Ignorer les enregistrements supprimés de tous les lors de la navigation dans le jeu d’enregistrements. Cela ralentit les performances dans certaines extractions relatives. Cette option n’est pas valide sur les recordsets avant uniquement. Si vous appelez [déplacer](#move) avec la *nRows* paramètre défini sur 0 et le `CRecordset::skipDeletedRecords` option set, `Move` déclarera. Notez que `CRecordset::skipDeletedRecords` est similaire à *compression du pilote*, ce qui signifie que les lignes supprimées est supprimés du jeu d’enregistrements. Toutefois, si votre pilote packs d’enregistrements, puis il ignore uniquement les enregistrements que vous supprimer ; elle ignore pas les enregistrements supprimés par d’autres utilisateurs, tandis que le jeu d’enregistrements est ouvert. `CRecordset::skipDeletedRecords` ignore les lignes supprimées par d’autres utilisateurs.  
  
- `CRecordset::useBookmarks` Peut utiliser des signets sur le jeu d’enregistrements, si pris en charge. Signets ralentissement la récupération des données mais améliorent les performances pour la navigation dans les données. Non valide sur les recordsets avant uniquement. Pour plus d’informations, consultez l’article [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
- `CRecordset::noDirtyFieldCheck` Désactiver la vérification (double mise en mémoire tampon) automatique de champ incorrecte. Cela améliorera les performances ; Toutefois, vous devez marquer manuellement les champs comme modifié en appelant le `SetFieldDirty` et `SetFieldNull` fonctions membres. Notez ce mécanisme de double tampon dans la classe `CRecordset` est similaire à la double mise en tampon dans la classe `CDaoRecordset`. Toutefois, dans `CRecordset`, vous ne pouvez pas activer la double mise en tampon sur des champs individuels ; vous l’activer pour tous les champs ou le désactiver pour tous les champs. Notez que si vous spécifiez l’option `CRecordset::useMultiRowFetch`, puis `CRecordset::noDirtyFieldCheck` sera activé automatiquement ; Toutefois, `SetFieldDirty` et `SetFieldNull` ne peut pas être utilisé sur les jeux d’enregistrements qui implémentent l’extraction de lignes en bloc.  
  
- `CRecordset::executeDirect` N’utilisez pas une instruction SQL préparée. Pour améliorer les performances, spécifiez cette option si le `Requery` fonction membre ne sera jamais appelée.  
  
- `CRecordset::useExtendedFetch` Implémentez `SQLExtendedFetch` au lieu de `SQLFetch`. Il est conçu pour l’implémentation de l’extraction de lignes en bloc sur les recordsets avant uniquement. Si vous spécifiez l’option `CRecordset::useMultiRowFetch` sur un recordset avant uniquement, puis `CRecordset::useExtendedFetch` est activé automatiquement.  
  
- `CRecordset::userAllocMultiRowBuffers` L’utilisateur sera allouer des mémoires tampons de stockage pour les données. Utilisez cette option conjointement avec `CRecordset::useMultiRowFetch` si vous souhaitez allouer votre propre stockage ; sinon, le framework automatiquement alloue le stockage nécessaire. Pour plus d’informations, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Notez que la spécification `CRecordset::userAllocMultiRowBuffers` sans spécifier `CRecordset::useMultiRowFetch` entraîne un échec d’assertion.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le `CRecordset` objet a été ouvert ; sinon 0 si [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (si appelée) retourne 0.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler cette fonction membre pour exécuter la requête définie par le jeu d’enregistrements. Avant d’appeler `Open`, vous devez construire l’objet recordset.  
  
 Connexion du jeu d’enregistrements à la source de données dépend de la façon dont vous construisez le jeu d’enregistrements avant d’appeler `Open`. Si vous passez un [CDatabase](../../mfc/reference/cdatabase-class.md) de l’objet au constructeur de jeu d’enregistrements qui n’a pas été connecté à la source de données, cette fonction membre utilise [GetDefaultConnect](#getdefaultconnect) tentative d’ouverture de l’objet de base de données. Si vous passez NULL au constructeur de jeu d’enregistrements, le constructeur construit un `CDatabase` objet pour vous, et `Open` tente de se connecter à l’objet de base de données. Pour plus d’informations sur la fermeture de l’ensemble d’enregistrements et de la connexion dans ces circonstances différentes, consultez [fermer](#close).  
  
> [!NOTE]
>  Accès à une source de données via un `CRecordset` objet est toujours partagé. Contrairement à la `CDaoRecordset` (classe), vous ne pouvez pas utiliser un `CRecordset` objet pour ouvrir une source de données avec un accès exclusif.  
  
 Lorsque vous appelez `Open`, une requête, généralement une SQL **sélectionnez** instruction, sélectionne des enregistrements selon des critères présentés dans le tableau suivant.  
  
|Valeur du paramètre lpszSQL|Enregistrements sélectionnés sont déterminés par|Exemple|  
|------------------------------------|----------------------------------------|-------------|  
|NULL|La chaîne retournée par `GetDefaultSQL`.||  
|Nom de la table SQL|Toutes les colonnes de la liste de tables dans `DoFieldExchange` ou `DoBulkFieldExchange`.|`"Customer"`|  
|Nom de la requête prédéfinie (procédure stockée)|Les colonnes de que la requête est définie pour retourner.|`"{call OverDueAccts}"`|  
|**Sélectionnez** -liste des colonnes **FROM** table-list|Les colonnes spécifiées à partir de la table (s) spécifié.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  Veillez à ce que vous n’insérez pas d’espace blanc supplémentaire dans la chaîne SQL. Par exemple, si vous insérez un espace blanc entre l’accolade et la **appeler** mot clé, MFC mal interpréter la chaîne SQL comme nom de table et les incorporer dans un **sélectionnez** instruction, ce qui entraîne un exception levée. De même, si votre requête prédéfinie utilise un paramètre de sortie, n’insérez pas d’espace entre l’accolade et la « symbole. Enfin, vous ne devez pas insérer un espace blanc avant l’accolade dans un **appeler** instruction ou avant le **sélectionnez** mot clé dans un **sélectionnez** instruction.  
  
 La procédure habituelle consiste à passer NULL pour `Open`; dans ce cas, `Open` appels [GetDefaultSQL](#getdefaultsql). Si vous utilisez une dérivée `CRecordset` classe, `GetDefaultSQL` donne les noms de table spécifié dans ClassWizard. Vous pouvez spécifier à la place d’autres informations dans le `lpszSQL` paramètre.  
  
 Ce que vous transmettez `Open` construit une chaîne SQL finale pour la requête (la chaîne peut avoir SQL **où** et **ORDER BY** clauses ajouté à la `lpszSQL` chaîne que vous avez passé), puis l’exécute la requête. Vous pouvez examiner la chaîne construite en appelant [GetSQL](#getsql) après l’appel *`Open`. Pour des détails supplémentaires sur la façon dont le jeu d’enregistrements construit une instruction SQL et sélectionne les enregistrements, consultez l’article [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
 Les membres de données de champ de votre classe de jeu d’enregistrements sont liés aux colonnes de données sélectionnées. Si tous les enregistrements sont retournés, le premier enregistrement devient l’enregistrement actif.  
  
 Si vous souhaitez définir des options pour le jeu d’enregistrements, tel qu’un filtre ou un tri, spécifiez-les après avoir construit l’objet recordset, mais avant d’appeler `Open`. Si vous souhaitez actualiser les enregistrements dans le jeu d’enregistrements après le jeu d’enregistrements est déjà ouvert, appelez [Requery](#requery).  
  
 Pour plus d’informations, y compris des exemples supplémentaires, consultez les articles [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), et [Recordset : création et fermeture Jeux d’enregistrements (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
### <a name="example"></a>Exemple  
 Les exemples de code suivants montrent différentes formes de la `Open` appeler.  
  
 [!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>  CRecordset::RefreshRowset  
 Met à jour les données et l’état d’une ligne dans l’ensemble de lignes en cours.  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Paramètres  
 *wRow*  
 La position de base un d’une ligne dans l’ensemble de lignes en cours. Cette valeur peut être comprise entre zéro et la taille de l’ensemble de lignes.  
  
 *wLockType*  
 Une valeur qui indique comment verrouiller la ligne après que qu’il a été actualisé. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Si vous passez une valeur de zéro pour *wRow*, puis chaque ligne dans l’ensemble de lignes est actualisé.  
  
 Pour utiliser `RefreshRowset`, vous devez avoir implémenté l’extraction de lignes en bloc en spécifiant le `CRecordset::useMulitRowFetch` option dans le [Open](#open) fonction membre.  
  
 `RefreshRowset` appelle la fonction API ODBC `SQLSetPos`. Le *wLockType* paramètre spécifie l’état de verrouillage de la ligne après `SQLSetPos` a été exécutée. Le tableau suivant décrit les valeurs possibles pour *wLockType*.  
  
|wLockType|Description|  
|---------------|-----------------|  
|SQL_LOCK_NO_CHANGE (la valeur par défaut)|La pilote ou source de données garantit que la ligne est dans le même état verrouillé ou déverrouillé, telle qu’elle était avant `RefreshRowset` a été appelée.|  
|SQL_LOCK_EXCLUSIVE|La source de données ou de pilote verrouille exclusivement la ligne. Toutes les données sources ne prennent en charge ce type de verrou.|  
|SQL_LOCK_UNLOCK|La source de données ou de pilote déverrouille la ligne. Toutes les données sources ne prennent en charge ce type de verrou.|  
  
 Pour plus d’informations sur `SQLSetPos`, consultez le kit SDK Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="requery"></a>  CRecordset::Requery  
 Reconstruit (actualisations) un jeu d’enregistrements.  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements a été régénérée avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Si tous les enregistrements sont retournés, le premier enregistrement devient l’enregistrement actif.  
  
 Dans l’ordre du jeu d’enregistrements afin de refléter les ajouts et suppressions que vous ou autres utilisateurs effectuent dans la source de données, vous devez reconstruire le jeu d’enregistrements en appelant `Requery`. Si le recordset est une feuille de réponse dynamique, il reflète automatiquement les mises à jour que vous ou autres utilisateurs apporter à ses enregistrements existants (mais pas d’ajouts). Si le jeu d’enregistrements est un instantané, vous devez appeler `Requery` afin de refléter les modifications apportées par d’autres utilisateurs, ainsi que les ajouts et les suppressions.  
  
 Pour une feuille de réponse dynamique ou un instantané, appelez `Requery` tout moment vous souhaitez reconstruire le jeu d’enregistrements à l’aide d’un nouveau filtre ou de tri ou de nouvelles valeurs de paramètre. Définissez la nouvelle propriété à filtrer ou trier en assignant de nouvelles valeurs à `m_strFilter` et `m_strSort` avant d’appeler `Requery`. Définir de nouveaux paramètres en assignant de nouvelles valeurs aux membres de données de paramètre avant d’appeler `Requery`. Si les chaînes de filtre et de tri sont identiques, vous pouvez réutiliser la requête, ce qui améliore les performances.  
  
 En cas de la tentative de reconstruire le jeu d’enregistrements, le recordset est fermé. Avant d’appeler `Requery`, vous pouvez déterminer si le jeu d’enregistrements peut être actualisé en appelant le `CanRestart` fonction membre. `CanRestart` ne garantit pas que `Requery` réussira.  
  
> [!CAUTION]
>  Appelez `Requery` uniquement après avoir appelé [Open](#open).  
  
### <a name="example"></a>Exemple  
 Cet exemple reconstruit un jeu d’enregistrements pour appliquer un ordre de tri différent.  
  
 [!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>  CRecordset::SetAbsolutePosition  
 Positionne le jeu d’enregistrements sur l’enregistrement correspondant au numéro d’enregistrement spécifié.  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>Paramètres  
 *nRows*  
 Basé sur un position ordinale de l’enregistrement actuel dans le jeu d’enregistrements.  
  
### <a name="remarks"></a>Notes  
 `SetAbsolutePosition` Déplace le pointeur d’enregistrement actuel en fonction de cette position ordinale.  
  
> [!NOTE]
>  Cette fonction membre n’est pas valide sur les recordsets avant uniquement.  
  
 Pour les jeux d’enregistrements ODBC, un paramètre de position absolue 1 fait référence au premier enregistrement dans le jeu d’enregistrements ; la valeur 0 fait référence à la position (BOF) de début du fichier.  
  
 Vous pouvez également transmettre des valeurs négatives pour `SetAbsolutePosition`. Dans ce cas la position du jeu d’enregistrements est évaluée à partir de la fin de l’objet recordset. Par exemple, `SetAbsolutePosition( -1 )` déplace le pointeur d’enregistrement actif vers le dernier enregistrement dans le jeu d’enregistrements.  
  
> [!NOTE]
>  Position absolue n’est pas destinée à être utilisé comme un numéro d’enregistrement de substitution. Les signets sont toujours recommandé de conserver et revenir à une position donnée, depuis les changements de position d’un enregistrement lorsque des enregistrements précédents sont supprimés. En outre, vous ne peut pas être sûr qu’un enregistrement donné aura la même position absolue si le jeu d’enregistrements est recréé à nouveau, car l’ordre des enregistrements individuels dans un jeu d’enregistrements n’est pas garanti, sauf si elle est créée avec une instruction SQL à l’aide d’un **ORDER BY** clause.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements et les signets, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="setbookmark"></a>  CRecordset::SetBookmark  
 Positionne le jeu d’enregistrements sur l’enregistrement qui contient le signet spécifié.  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Paramètres  
 *varBookmark*  
 Une référence à un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objet contenant la valeur de signet d’un enregistrement spécifique.  
  
### <a name="remarks"></a>Notes  
 Pour déterminer si les signets sont pris en charge sur le jeu d’enregistrements, appelez [CanBookmark](#canbookmark). Pour rendre les signets disponibles si elles sont prises en charge, vous devez définir le `CRecordset::useBookmarks` option dans le *dwOptions* paramètre de la [Open](#open) fonction membre.  
  
> [!NOTE]
>  Si les signets sont non pris en charge ou non disponible, l’appel `SetBookmark` entraîne une exception est levée. Les signets ne sont pas pris en charge sur les recordsets avant uniquement.  
  
 Pour tout d’abord récupérer le signet de l’enregistrement en cours, appelez [GetBookmark](#getbookmark), qui enregistre la valeur de signet à un `CDBVariant` objet. Une version ultérieure, vous pouvez revenir à cet enregistrement en appelant `SetBookmark` à l’aide de la valeur du signet enregistré.  
  
> [!NOTE]
>  Après certaines opérations de jeu d’enregistrements, vous devez vérifier la persistance de signet avant d’appeler `SetBookmark`. Par exemple, si vous récupérez un signet avec `GetBookmark` , puis appelez `Requery`, le signet peut ne plus être valid. Appelez [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si vous pouvez appeler en toute sécurité `SetBookmark`.  
  
 Pour plus d’informations sur les signets et de navigation de jeu d’enregistrements, consultez les articles [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="setfielddirty"></a>  CRecordset::SetFieldDirty  
 Marque un membre de données de champ de l’objet recordset comme modifié ou restent inchangés.  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *PV*  
 Contient l’adresse d’un membre de données de champ dans le jeu d’enregistrements ou NULL. Si NULL, tous les membres de données de champ dans le jeu d’enregistrements marqués. (C++ NULL n’est pas identique à la valeur Null dans la terminologie de base de données, ce qui signifie « ne having aucune valeur. »)  
  
 *bDirty*  
 TRUE si le membre de données de champ doit être marqué comme « modifié » (modifié). Sinon, FALSE si le membre de données de champ doit être marqué comme « nettoyer » (inchangée).  
  
### <a name="remarks"></a>Notes  
 Marquage des champs restent inchangés garantit que le champ n’est pas mis à jour et entraîne moins de trafic SQL.  
  
> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les jeux d’enregistrements qui est à l’aide de l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, puis `SetFieldDirty` entraîne un échec d’assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Les marques de framework modifié des données membres de champ pour vous assurer qu’ils seront écrites à l’enregistrement sur la source de données par le mécanisme record field exchange (RFX). Modification de la valeur d’un champ généralement définit le champ modifié automatiquement, donc vous serez rarement nécessaire d’appeler `SetFieldDirty` vous-même, mais vous pouvez parfois faire en sorte que les colonnes seront explicitement mis à jour ou insérés, quel que soit la valeur est dans les données de champ membre.  
  
> [!CAUTION]
>  Appelez cette fonction membre uniquement après avoir appelé [modifier](#edit) ou [AddNew](#addnew).  
  
 À l’aide de la valeur NULL pour le premier argument de la fonction s’applique uniquement à la fonction `outputColumn` ne champs pas `param` champs. Par exemple, l’appel  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 définira uniquement `outputColumn` champs avec la valeur NULL ; `param` champs ne seront pas affectées.  
  
 Pour travailler sur `param` champs, vous devez fournir l’adresse réelle de l’individu `param` vous souhaitez travailler, telles que :  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Cela signifie que vous ne pouvez pas définir tous les `param` champs avec la valeur NULL, comme vous pouvez le faire avec `outputColumn` champs.  
  
##  <a name="setfieldnull"></a>  CRecordset::SetFieldNull  
 Marque un membre de données de champ de l’objet recordset en tant que valeur Null (en particulier n’avoir aucune valeur) ou non Null.  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *PV*  
 Contient l’adresse d’un membre de données de champ dans le jeu d’enregistrements ou NULL. Si NULL, tous les membres de données de champ dans le jeu d’enregistrements marqués. (C++ NULL n’est pas identique à la valeur Null dans la terminologie de base de données, ce qui signifie « ne having aucune valeur. »)  
  
 *bNull*  
 Différent de zéro si le membre de données de champ doit être marquée comme en ne comportant aucun valeur (Null). Sinon, 0 si le membre de données de champ doit être marqué comme non Null.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous ajoutez un nouvel enregistrement à un jeu d’enregistrements, tous les membres de données de champ sont initialement définies sur une valeur Null et marqués comme « modifié » (modifié). Lorsque vous récupérez un enregistrement à partir d’une source de données, ses colonnes soit déjà ont des valeurs ou ont la valeur Null.  
  
> [!NOTE]
>  N’appelez pas cette fonction membre sur les jeux d’enregistrements qui est à l’aide de l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, l’appel `SetFieldNull` entraîne un échec d’assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Si vous voulez désigner un champ de l’enregistrement actuel comme n’ayant ne pas une valeur, appelez `SetFieldNull` avec *bNull* définie sur TRUE pour marquer en tant que valeur Null. Si un champ marqué Null et que vous voulez lui donner une valeur, définissez simplement sa nouvelle valeur. Vous n’êtes pas obligé de supprimer l’indicateur Null avec `SetFieldNull`. Pour déterminer si le champ est autorisé à avoir la valeur Null, appelez `IsFieldNullable`.  
  
> [!CAUTION]
>  Appelez cette fonction membre uniquement après avoir appelé [modifier](#edit) ou [AddNew](#addnew).  
  
 À l’aide de la valeur NULL pour le premier argument de la fonction s’applique uniquement à la fonction `outputColumn` ne champs pas `param` champs. Par exemple, l’appel  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 définira uniquement `outputColumn` champs avec la valeur NULL ; `param` champs ne seront pas affectées.  
  
 Pour travailler sur `param` champs, vous devez fournir l’adresse réelle de l’individu `param` vous souhaitez travailler, telles que :  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Cela signifie que vous ne pouvez pas définir tous les `param` champs avec la valeur NULL, comme vous pouvez le faire avec `outputColumn` champs.  
  
> [!NOTE]
>  Lors de la définition des paramètres avec la valeur Null, un appel à `SetFieldNull` avant que le jeu d’enregistrements est ouvert entraîne une assertion. Dans ce cas, appelez [SetParamNull](#setparamnull).  
  
 `SetFieldNull` est implémentée via [DoFieldExchange](#dofieldexchange).  
  
##  <a name="setlockingmode"></a>  CRecordset::SetLockingMode  
 Définit le mode de verrouillage « optimiste « verrouillage (il s’agit de la valeur par défaut) ou de verrouillage « pessimiste ». Détermine la façon dont les enregistrements sont verrouillés pour les mises à jour.  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>Paramètres  
 *nMode*  
 Contient l’une des valeurs suivantes à partir de la `enum LockMode`:  
  
- `optimistic` Le verrouillage optimiste verrouille l’enregistrement mis à jour uniquement pendant l’appel à `Update`.  
  
- `pessimistic` Le verrouillage pessimiste verrouille l’enregistrement dès que `Edit` est appelée et les conserve verrouillé jusqu'à ce que le `Update` fin de l’appel ou de vous déplacer vers un nouvel enregistrement.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre si vous devez spécifier laquelle des deux stratégies de verrouillage des enregistrements à l’aide de l’ensemble d’enregistrements pour les mises à jour. Par défaut, le mode de verrouillage d’un jeu d’enregistrements est `optimistic`. Vous pouvez remplacer ce plus prudent `pessimistic` la stratégie de verrouillage. Appelez `SetLockingMode` une fois que vous construisez et ouvrez l’objet recordset, mais avant d’appeler `Edit`.  
  
##  <a name="setparamnull"></a>  CRecordset::SetParamNull  
 Un paramètre d’indicateurs comme Null (en particulier n’avoir aucune valeur) ou en tant que non-Null.  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Index de base zéro du paramètre.  
  
 *bNull*  
 Si TRUE (valeur par défaut), le paramètre est marqué comme Null. Sinon, le paramètre est marqué comme non Null.  
  
### <a name="remarks"></a>Notes  
 Contrairement aux [SetFieldNull](#setfieldnull), vous pouvez appeler `SetParamNull` avant que vous avez ouvert le jeu d’enregistrements.  
  
 `SetParamNull` est généralement utilisé avec des requêtes prédéfinies (procédures stockées).  
  
##  <a name="setrowsetcursorposition"></a>  CRecordset::SetRowsetCursorPosition  
 Déplace le curseur d’une ligne dans l’ensemble de lignes en cours.  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Paramètres  
 *wRow*  
 La position de base un d’une ligne dans l’ensemble de lignes en cours. Cette valeur peut varier de 1 à la taille de l’ensemble de lignes.  
  
 *wLockType*  
 Valeur qui indique comment verrouiller la ligne après que qu’il a été actualisé. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Lors de l’implémentation de l’extraction de lignes en bloc, les enregistrements sont récupérés en ensembles de lignes, où le premier enregistrement dans l’ensemble de lignes extraite est l’enregistrement actif. Pour activer un autre enregistrement au sein de l’ensemble de lignes, appelez `SetRowsetCursorPosition`. Par exemple, vous pouvez combiner `SetRowsetCursorPosition` avec la [GetFieldValue](#getfieldvalue) fonction membre pour récupérer dynamiquement les données à partir de n’importe quel enregistrement de votre jeu d’enregistrements.  
  
 Pour utiliser `SetRowsetCursorPosition`, vous devez avoir implémenté l’extraction de lignes en bloc en spécifiant le `CRecordset::useMultiRowFetch` option de la *dwOptions* paramètre dans le [Open](#open) fonction membre.  
  
 `SetRowsetCursorPosition` appelle la fonction API ODBC `SQLSetPos`. Le *wLockType* paramètre spécifie l’état de verrouillage de la ligne après `SQLSetPos` a été exécutée. Le tableau suivant décrit les valeurs possibles pour *wLockType*.  
  
|wLockType|Description|  
|---------------|-----------------|  
|SQL_LOCK_NO_CHANGE (la valeur par défaut)|La pilote ou source de données garantit que la ligne est dans le même état verrouillé ou déverrouillé, telle qu’elle était avant `SetRowsetCursorPosition` a été appelée.|  
|SQL_LOCK_EXCLUSIVE|La source de données ou de pilote verrouille exclusivement la ligne. Toutes les données sources ne prennent en charge ce type de verrou.|  
|SQL_LOCK_UNLOCK|La source de données ou de pilote déverrouille la ligne. Toutes les données sources ne prennent en charge ce type de verrou.|  
  
 Pour plus d’informations sur `SQLSetPos`, consultez le kit SDK Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="setrowsetsize"></a>  CRecordset::SetRowsetSize  
 Spécifie le nombre d’enregistrements que vous souhaitez récupérer pendant une extraction.  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwNewRowsetSize*  
 Le nombre de lignes à récupérer durant une extraction donnée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre virtuelle Spécifie le nombre de lignes à extraire pendant une extraction unique lors de l’utilisation de l’extraction de lignes en bloc. Pour implémenter l’extraction de lignes en bloc, vous devez définir le `CRecordset::useMultiRowFetch` option dans le *dwOptions* paramètre de la [Open](#open) fonction membre.  
  
> [!NOTE]
>  Appel de `SetRowsetSize` sans avoir à implémenter en bloc l’extraction de lignes entraîne un échec d’assertion.  
  
 Appelez `SetRowsetSize` avant d’appeler `Open` pour définir initialement la taille de l’ensemble de lignes du jeu d’enregistrements. La taille d’ensemble de lignes par défaut lors de l’implémentation de l’extraction de lignes en bloc est 25.  
  
> [!NOTE]
>  Soyez prudent lors de l’appel `SetRowsetSize`. Si vous affectez manuellement le stockage pour les données (comme spécifié par le `CRecordset::userAllocMultiRowBuffers` option du paramètre dwOptions dans `Open`), vous devez vérifier s’il faut réallouer ces mémoires tampons de stockage après avoir appelé `SetRowsetSize`, mais avant de vous chaque opération de curseur navigation.  
  
 Pour obtenir la valeur actuelle de la taille de l’ensemble de lignes, appelez [GetRowsetSize](#getrowsetsize).  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="update"></a>  CRecordset::Update  
 Termine une `AddNew` ou `Edit` opération en enregistrant les données nouvelles ou modifiées sur la source de données.  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si un enregistrement a été correctement mis à jour ; Sinon, 0 si aucune colonne n’ont été modifiés. Si aucun enregistrement ont été mis à jour, ou si plus d’un enregistrement a été mis à jour, une exception est levée. Une exception est également levée pour toute autre défaillance sur la source de données.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre après un appel à la [AddNew](#addnew) ou [modifier](#edit) fonction membre. Cet appel est requis pour terminer la `AddNew` ou `Edit` opération.  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `Update`. Cela entraîne un échec d’assertion. Bien que classe `CRecordset` ne fournit pas de mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction API ODBC `SQLSetPos`. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Les deux `AddNew` et `Edit` préparer un mémoire tampon d’édition dans lequel sont placées les données ajoutées ou modifiées pour l’enregistrement dans la source de données. `Update` enregistre les données. Seuls les champs marqués ou détecté comme étant modifiée sont mis à jour.  
  
 Si la source de données prend en charge les transactions, vous pouvez rendre le `Update` appeler (et de son `AddNew` ou `Edit` appeler) dans le cadre d’une transaction. Pour plus d’informations sur les transactions, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!CAUTION]
>  Si vous appelez `Update` sans d’abord appeler `AddNew` ou `Edit`, `Update` lève un `CDBException`. Si vous appelez `AddNew` ou `Edit`, vous devez appeler `Update` avant d’appeler un `Move` opération ou avant de fermer le jeu d’enregistrements ou de la connexion de source de données. Sinon, vos modifications sont perdues sans notification.  
  
 Pour plus d’informations sur la gestion des `Update` échecs, consultez l’article [Recordset : mise à jour des enregistrements par les Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’article [Transaction : exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDatabase, classe](../../mfc/reference/cdatabase-class.md)   
 [CRecordView, classe](../../mfc/reference/crecordview-class.md)
