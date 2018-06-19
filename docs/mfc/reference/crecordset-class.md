---
title: Classe CRecordset | Documents Microsoft
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
ms.openlocfilehash: 683f1d612a57e4f6e2d8661af17faa73f725d3d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378733"
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
|[CRecordset::CRecordset](#crecordset)|Construit un objet `CRecordset`. Votre classe dérivée doit fournir un constructeur qui appelle ce.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|Prépare pour ajouter un nouvel enregistrement. Appelez `Update` pour terminer l’ajout.|  
|[CRecordset::CanAppend](#canappend)|Retourne zéro si les nouveaux enregistrements peuvent être ajoutés à l’ensemble d’enregistrements par le biais du `AddNew` fonction membre.|  
|[CRecordset::CanBookmark](#canbookmark)|Retourne zéro si le jeu d’enregistrements prend en charge les signets.|  
|[CRecordset::Cancel](#cancel)|Annule une opération asynchrone ou un processus à partir d’un deuxième thread.|  
|[CRecordset::CancelUpdate](#cancelupdate)|Annule les mises à jour en attente due à une `AddNew` ou `Edit` opération.|  
|[CRecordset::CanRestart](#canrestart)|Retourne zéro si `Requery` peut être appelée pour exécuter de nouveau la requête du recordset.|  
|[CRecordset::CanScroll](#canscroll)|Retourne zéro si vous pouvez faire défiler les enregistrements.|  
|[CRecordset::CanTransact](#cantransact)|Retourne zéro si la source de données prend en charge les transactions.|  
|[CRecordset::CanUpdate](#canupdate)|Retourne zéro si le jeu d’enregistrements peut être mis à jour (vous pouvez ajouter, mettre à jour ou supprimer des enregistrements).|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|Appelé pour gérer les erreurs générées lors de l’extraction des enregistrements.|  
|[Préférence CRecordset::Close](#close)|Ferme l’objet recordset et ODBC **HSTMT** associé.|  
|[CRecordset::Delete](#delete)|Supprime l’enregistrement actif du jeu d’enregistrements. Vous devez explicitement accéder à un autre enregistrement après la suppression.|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Appelé pour échanger des lignes en bloc des données de la source de données vers le jeu d’enregistrements. Implémente en bloc d’échange de champs d’enregistrements (RFX en bloc).|  
|[CRecordset::DoFieldExchange](#dofieldexchange)|Appelé pour échanger des données (dans les deux sens) entre les membres de données de champ de l’objet recordset et l’enregistrement correspondant de la source de données. Implémente enregistre l’échange de champs (RFX).|  
|[CRecordset::Edit](#edit)|Prépare les modifications à l’enregistrement actif. Appelez `Update` pour terminer la modification.|  
|[CRecordset::FlushResultSet](#flushresultset)|Retourne zéro s’il existe un autre résultat défini à récupérer, lors de l’utilisation d’une requête prédéfinie.|  
|[CRecordset::GetBookmark](#getbookmark)|Affecte la valeur du signet d’un enregistrement à l’objet de paramètre.|  
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Appelé pour obtenir la chaîne de connexion par défaut.|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Appelé pour obtenir la chaîne SQL par défaut à exécuter.|  
|[CRecordset::GetFieldValue](#getfieldvalue)|Retourne la valeur d’un champ dans un jeu d’enregistrements.|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Retourne le nombre de champs dans le jeu d’enregistrements.|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Retourne des informations sur les champs particuliers dans un jeu d’enregistrements.|  
|[CRecordset::GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements dans le jeu d’enregistrements.|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|Retourne le nombre d’enregistrements que vous souhaitez récupérer lors d’une extraction unique.|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|Retourne le nombre réel de lignes récupérées lors d’une extraction.|  
|[CRecordset::GetRowStatus](#getrowstatus)|Retourne l’état de la ligne après une extraction.|  
|[CRecordset::GetSQL](#getsql)|Obtient la chaîne SQL utilisée pour sélectionner des enregistrements pour l’ensemble d’enregistrements.|  
|[CRecordset::GetStatus](#getstatus)|Obtient l’état de l’objet recordset : l’index de l’enregistrement actif et indique si un nombre final des enregistrements a été obtenu.|  
|[CRecordset::GetTableName](#gettablename)|Obtient le nom de la table sur laquelle repose le jeu d’enregistrements.|  
|[CRecordset::IsBOF](#isbof)|Retourne zéro si le jeu d’enregistrements a été positionné avant le premier enregistrement. Il n’existe aucun enregistrement actif.|  
|[CRecordset::IsDeleted](#isdeleted)|Retourne zéro si le jeu d’enregistrements est positionné sur un enregistrement supprimé.|  
|[CRecordset::IsEOF](#iseof)|Retourne zéro si le jeu d’enregistrements a été positionné après le dernier enregistrement. Il n’existe aucun enregistrement actif.|  
|[CRecordset::IsFieldDirty](#isfielddirty)|Retourne zéro si le champ spécifié dans l’enregistrement actif a été modifié.|  
|[CRecordset::IsFieldNull](#isfieldnull)|Retourne zéro si le champ spécifié dans l’enregistrement actif est null (n’a aucune valeur).|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|Retourne zéro si le champ spécifié dans l’enregistrement actif peut être défini à null (n’ayant aucune valeur).|  
|[CRecordset::IsOpen](#isopen)|Retourne zéro si `Open` a été appelé précédemment.|  
|[CRecordset::Move](#move)|Positionne le jeu d’enregistrements à un nombre spécifié d’enregistrements à partir de l’enregistrement actif dans les deux sens.|  
|[CRecordset::MoveFirst](#movefirst)|Positionne l’enregistrement actif sur le premier enregistrement dans le jeu d’enregistrements. Vérifier la présence de `IsBOF` première.|  
|[CRecordset::MoveLast](#movelast)|Positionne l’enregistrement actif sur le dernier enregistrement ou sur le dernier ensemble de lignes. Vérifier la présence de `IsEOF` première.|  
|[CRecordset::MoveNext](#movenext)|Positionne l’enregistrement en cours sur l’enregistrement suivant ou sur l’ensemble de lignes suivant. Vérifier la présence de `IsEOF` première.|  
|[CRecordset::MovePrev](#moveprev)|Positionne l’enregistrement en cours sur l’enregistrement précédent ou sur l’ensemble de lignes précédente. Vérifier la présence de `IsBOF` première.|  
|[CRecordset::OnSetOptions](#onsetoptions)|Appelé pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée.|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Appelé pour définir les options (utilisées sur la mise à jour) pour l’instruction ODBC spécifiée.|  
|[CRecordset::Open](#open)|Ouvre le recordset par la récupération de la table ou l’exécution de la requête représentant le jeu d’enregistrements.|  
|[CRecordset::RefreshRowset](#refreshrowset)|Actualise les données et l’état de la ligne (s) spécifié.|  
|[CRecordset::Requery](#requery)|Exécute la requête du recordset pour actualiser les enregistrements sélectionnés.|  
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Positionne le jeu d’enregistrements sur l’enregistrement correspondant au numéro d’enregistrement spécifié.|  
|[CRecordset::SetBookmark](#setbookmark)|Positionne le jeu d’enregistrements sur l’enregistrement spécifié par le signet.|  
|[CRecordset::SetFieldDirty](#setfielddirty)|Marque le champ spécifié dans l’enregistrement actif comme modifié.|  
|[CRecordset::SetFieldNull](#setfieldnull)|Définit la valeur du champ spécifié dans l’enregistrement actif null (n’ayant aucune valeur).|  
|[CRecordset::SetLockingMode](#setlockingmode)|Définit le mode de verrouillage « optimiste » (la valeur par défaut) de verrouillage ou de verrouillage « pessimiste ». Détermine la façon dont les enregistrements sont verrouillés pour les mises à jour.|  
|[CRecordset::SetParamNull](#setparamnull)|Définit le paramètre spécifié en valeur null (n’ayant aucune valeur).|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Positionne le curseur sur la ligne spécifiée dans l’ensemble de lignes.|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|Spécifie le nombre d’enregistrements que vous souhaitez récupérer lors d’une extraction.|  
|[CRecordset::Update](#update)|Termine une `AddNew` ou `Edit` opération en enregistrant les données nouvelles ou modifiées sur la source de données.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CRecordset::m_hstmt](#m_hstmt)|Contient le handle d’instruction ODBC pour l’ensemble d’enregistrements. Tapez `HSTMT`.|  
|[CRecordset::m_nFields](#m_nfields)|Contient le nombre de membres de données de champ dans le jeu d’enregistrements. Tapez `UINT`.|  
|[CRecordset::m_nParams](#m_nparams)|Contient le nombre de membres de données de paramètre dans le jeu d’enregistrements. Tapez `UINT`.|  
|[CRecordset::m_pDatabase](#m_pdatabase)|Contient un pointeur vers le `CDatabase` objet via lequel le jeu d’enregistrements est connecté à une source de données.|  
|[CRecordset::m_strFilter](#m_strfilter)|Contient un `CString` qui spécifie un langage SQL (Structured Query) `WHERE` clause. Utilisé en tant que filtre pour sélectionner uniquement les enregistrements qui répondent à certains critères.|  
|[CRecordset::m_strSort](#m_strsort)|Contient un `CString` qui spécifie une SQL `ORDER BY` clause. Utilisé pour contrôler la façon dont les enregistrements sont triés.|  
  
## <a name="remarks"></a>Notes  
 Appelé « jeux d’enregistrements, » `CRecordset` objets sont généralement utilisés dans les deux formes : feuilles de réponse dynamiques et les instantanés. Une feuille de réponse dynamique reste synchronisé avec les mises à jour de données effectuées par d’autres utilisateurs. Un instantané est une vue statique des données. Chaque formulaire représente un ensemble d’enregistrements au moment de que l’ensemble d’enregistrements est ouvert, mais lorsque vous faites défiler un enregistrement dans une feuille de réponse dynamique, il reflète les modifications apportées par la suite à l’enregistrement, par d’autres utilisateurs ou par d’autres jeux d’enregistrements dans votre application.  
  
> [!NOTE]
>  Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt que les classes de base de données ODBC (Open Connectivity), utilisez la classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de base de données](../../data/data-access-programming-mfc-atl.md).  
  
 Pour travailler avec un type de jeu d’enregistrements, vous généralement dérivez une classe de jeu d’enregistrements spécifiques à l’application à partir de `CRecordset`. Jeux d’enregistrements de sélectionner des enregistrements à partir d’une source de données, et vous pouvez ensuite :  
  
-   Faites défiler les enregistrements.  
  
-   Mettre à jour les enregistrements et spécifier un mode de verrouillage.  
  
-   Filtrer le jeu d’enregistrements pour limiter les enregistrements qu’il sélectionne parmi ceux disponibles sur la source de données.  
  
-   Trier le jeu d’enregistrements.  
  
-   Paramétrer le recordset pour personnaliser sa sélection avec des informations ne pas connues jusqu'à l’exécution.  
  
 Pour utiliser votre classe, ouvrez une base de données et construire un objet recordset, en passant le constructeur un pointeur vers votre `CDatabase` objet. Appelez ensuite le jeu d’enregistrements **ouvrir** fonction membre, où vous pouvez spécifier si l’objet est une feuille de réponse dynamique ou un instantané. Appel de **ouvrir** sélectionne des données de la source de données. Une fois que l’objet recordset est ouvert, utilisez ses membres de données et des fonctions membres pour parcourir les enregistrements et opérer sur les. Les opérations disponibles varient selon que l’objet est une feuille de réponse dynamique ou un instantané, s’il est en lecture seule ou être mise à jour (Cela dépend de la capacité de la source de données ODBC Open Database Connectivity ()), et si vous avez implémenté l’extraction de lignes en bloc. Pour actualiser les enregistrements qui ont été être modifiés ou ajoutés depuis la **ouvrir** appeler, appelez l’objet **Requery** fonction membre. Appelez l’objet **fermer** membre de la fonction et détruire l’objet lorsque vous avez terminé avec lui.  
  
 Dans une dérivée `CRecordset` de classe, d’enregistrer l’échange de champs (RFX) ou RFX en bloc (RFX en bloc) est utilisé pour prendre en charge la lecture et mise à jour des champs d’enregistrement.  
  
 Pour plus d’informations sur l’échange de champs d’enregistrement et de jeux d’enregistrements, consultez les articles [vue d’ensemble : programmation de base de données](../../data/data-access-programming-mfc-atl.md), [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset : extraction globale d’enregistrements en bloc (ODBC) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md). Pour une vue sur des feuilles de réponse dynamiques et les instantanés, consultez les articles [Dynaset](../../data/odbc/dynaset.md) et [instantané](../../data/odbc/snapshot.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdb.h  
  
##  <a name="addnew"></a>  CRecordset::AddNew  
 Prépare pour ajouter un nouvel enregistrement à la table.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler la [Requery](#requery) fonction membre pour afficher le dernier enregistrement ajouté. Champs de l’enregistrement sont initialement Null. (Dans la terminologie de base de données, Null donne « aucune valeur » et n’est pas le même que **NULL** en C++.) Pour terminer l’opération, vous devez appeler la [mise à jour](#update) fonction membre. **Mise à jour** enregistre vos modifications dans la source de données.  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `AddNew`. Cela entraîne un échec d’assertion. Bien que classe `CRecordset` ne fournit pas de mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction d’API ODBC **SQLSetPos**. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `AddNew` prépare un nouvel enregistrement vide à l’aide des membres de données de champ du jeu d’enregistrements. Après avoir appelé `AddNew`, définissez les valeurs souhaitées dans les données membres de champ du jeu d’enregistrements. (Vous n’avez pas à appeler le [modifier](#edit) fonction membre à cet effet ; utilisez **modifier** uniquement pour les enregistrements existants.) Lorsque vous appelez ensuite **mise à jour**, modifié les valeurs dans les membres de données de champ sont enregistrées sur la source de données.  
  
> [!CAUTION]
>  Si vous accédez à un nouvel enregistrement avant d’appeler **mise à jour**, le nouvel enregistrement est perdu et aucun avertissement n’est donnée.  
  
 Si la source de données prend en charge les transactions, vous pouvez rendre votre `AddNew` appeler partie d’une transaction. Pour plus d’informations sur les transactions, consultez la classe [CDatabase](../../mfc/reference/cdatabase-class.md). Notez que vous devez appeler [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) avant d’appeler `AddNew`.  
  
> [!NOTE]
>  Pour les feuilles de réponse dynamiques, les nouveaux enregistrements sont ajoutés à l’objet recordset en tant que le dernier enregistrement. Les enregistrements ajoutés ne sont pas ajoutés aux instantanés ; Vous devez appeler **Requery** pour actualiser le jeu d’enregistrements.  
  
 N’est pas autorisé à appeler `AddNew` pour un jeu d’enregistrements dont **ouvrir** fonction membre n’a pas été appelée. A `CDBException` est levée si vous appelez `AddNew` pour un jeu d’enregistrements qui ne peut pas être ajouté au. Vous pouvez déterminer si le jeu d’enregistrements est modifiable en appelant [CanAppend](#canappend).  
  
 Pour plus d’informations, consultez les articles suivants : [Recordset : mise à jour des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Recordset : ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), et [(de Transaction ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’article [Transaction : exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="canappend"></a>  CRecordset::CanAppend  
 Détermine si l’ensemble d’enregistrements précédemment ouvert autorise vous permet d’ajouter de nouveaux enregistrements.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements permet d’ajouter de nouveaux enregistrements ; Sinon, 0. `CanAppend` retourne 0 si vous avez ouvert le jeu d’enregistrements en lecture seule.  
  
##  <a name="canbookmark"></a>  CRecordset::CanBookmark  
 Détermine si l’ensemble d’enregistrements vous permet de marquer les enregistrements à l’aide de signets.  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements prend en charge les signets ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est indépendante de la **CRecordset::useBookmarks** option dans le `dwOptions` paramètre de la [ouvrir](#open) fonction membre. `CanBookmark` Indique si le pilote ODBC et le curseur type de prise en charge des signets. **CRecordset::useBookmarks** indique si signets seront disponibles, à condition qu’ils sont pris en charge.  
  
> [!NOTE]
>  Les signets ne sont pas pris en charge sur les recordsets avant uniquement.  
  
 Pour plus d’informations sur les signets et de navigation du jeu d’enregistrements, consultez les articles [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cancel"></a>  CRecordset::Cancel  
 Demande que la source de données annule une opération asynchrone en cours d’exécution ou un processus à partir d’un deuxième thread.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Notes  
 Notez que les classes ODBC MFC ne plus utilisent le traitement asynchrone ; Pour effectuer une opération asynchrone, vous devez appeler directement la fonction d’API ODBC **SQLSetConnectOption**. Pour plus d’informations, consultez la rubrique « L’exécution de fonctions en mode asynchrone » dans le *Guide du programmeur ODBC SDK*.  
  
##  <a name="cancelupdate"></a>  CRecordset::CancelUpdate  
 Annule les en attente de mises à jour, provoqués par une [modifier](#edit) ou [AddNew](#addnew) opération, avant de [mise à jour](#update) est appelée.  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les jeux d’enregistrements qui est l’extraction de lignes en bloc, dans la mesure où ces jeux d’enregistrements ne peuvent pas appeler **modifier**, `AddNew`, ou **mise à jour**. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Si la vérification de champ dirty automatique est activée, `CancelUpdate` restaure les variables membres pour les valeurs qu’ils avaient avant **modifier** ou `AddNew` a été appelé ; sinon, toutes les modifications de la valeur reste. Par défaut, la vérification de champ automatique est activée lorsque le jeu d’enregistrements est ouvert. Pour cela, vous devez spécifier le **CRecordset::noDirtyFieldCheck** dans le `dwOptions` paramètre de la [ouvrir](#open) fonction membre.  
  
 Pour plus d’informations sur la mise à jour des données, consultez l’article [Recordset : ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).  
  
##  <a name="canrestart"></a>  CRecordset::CanRestart  
 Détermine si le jeu d’enregistrements autorise le redémarrage de la requête (pour actualiser ses enregistrements) en appelant le **Requery** fonction membre.  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si requery est autorisée ; Sinon, 0.  
  
##  <a name="canscroll"></a>  CRecordset::CanScroll  
 Détermine si le jeu d’enregistrements autorise le défilement.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements autorise le défilement ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur le défilement, consultez l’article [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cantransact"></a>  CRecordset::CanTransact  
 Détermine si l’objet recordset permet aux transactions.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements permet aux transactions ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>  CRecordset::CanUpdate  
 Détermine si le jeu d’enregistrements peut être mis à jour.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements peut être mis à jour ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un jeu d’enregistrements peut être en lecture seule si la source de données sous-jacente est en lecture seule ou si vous avez spécifié **CRecordset::readOnly** dans le `dwOptions` paramètre lorsque vous avez ouvert le jeu d’enregistrements.  
  
##  <a name="checkrowseterror"></a>  CRecordset::CheckRowsetError  
 Appelé pour gérer les erreurs générées lors de l’extraction des enregistrements.  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>Paramètres  
 `nRetCode`  
 Code de retour de fonction d’API ODBC. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre virtuelle gère les erreurs qui se produisent lorsque les enregistrements sont récupérés, et est utile lors de l’extraction de lignes en bloc. Vous souhaiterez peut-être envisager de substituer `CheckRowsetError` pour implémenter votre propre gestion des erreurs.  
  
 `CheckRowsetError` est appelé automatiquement dans une opération de navigation de curseur, tels que **ouvrir**, **Requery**, ou n’importe quel **déplacer** opération. Il est passé à la valeur de retour de la fonction d’API ODBC **SQLExtendedFetch**. Le tableau suivant répertorie les valeurs possibles pour le `nRetCode` paramètre.  
  
|nRetCode|Description|  
|--------------|-----------------|  
|**SQL_SUCCESS**|Fonction a été exécutée avec succès ; Aucune information supplémentaire n’est disponible.|  
|**SQL_SUCCESS_WITH_INFO**|Fonction s’est terminée avec succès, éventuellement avec une erreur non fatale. Informations supplémentaires peuvent être obtenues en appelant **SQLError**.|  
|**SQL_NO_DATA_FOUND**|Toutes les lignes du jeu de résultats qui ont été extraites.|  
|**SQL_ERROR**|Échoué de la fonction. Informations supplémentaires peuvent être obtenues en appelant **SQLError**.|  
|**SQL_INVALID_HANDLE**|Échec de la fonction en raison d’un handle d’environnement non valide, le handle de connexion ou le handle d’instruction. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible à partir de **SQLError**.|  
|`SQL_STILL_EXECUTING`|Une fonction qui a été démarrée en mode asynchrone est en cours d’exécution. Notez que, par défaut, MFC ne passent jamais cette valeur à `CheckRowsetError`; MFC continuer à appeler **SQLExtendedFetch** jusqu'à ce qu’il ne retourne plus `SQL_STILL_EXECUTING`.|  
  
 Pour plus d’informations sur **SQLError**, consultez le Kit de développement logiciel Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="close"></a>  Préférence CRecordset::Close  
 Ferme l’ensemble d’enregistrements.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Notes  
 ODBC **HSTMT** et toute la mémoire le framework alloué pour le jeu d’enregistrements sont libérés. Généralement après l’appel **fermer**, vous supprimez l’objet de jeu d’enregistrements de C++, si elle a été alloué avec **nouveau**.  
  
 Vous pouvez appeler **ouvrir** à nouveau après l’appel **fermer**. Cela vous permet de réutiliser l’objet recordset. L’alternative consiste à appeler **Requery**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>  CRecordset::CRecordset  
 Construit un objet `CRecordset`.  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDatabase`  
 Contient un pointeur vers un `CDatabase` objet ou la valeur **NULL**. Si ce n’est pas **NULL** et `CDatabase` l’objet **ouvrir** fonction membre n’a pas été appelée pour le connecter à la source de données, le jeu d’enregistrements tente d’ouvrir pour vous lors de son propre **ouvrir**  appeler. Si vous passez **NULL**, un `CDatabase` objet est construit et connecté automatiquement à l’aide des informations de source de données vous avez spécifié lorsque vous dérivée de la classe de recordset avec ClassWizard.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser `CRecordset` directement ou dériver une classe spécifique à l’application de `CRecordset`. Vous pouvez utiliser ClassWizard pour dériver vos classes de jeu d’enregistrements.  
  
> [!NOTE]
>  Une classe dérivée *doit* fournir son propre constructeur. Dans le constructeur de votre classe dérivée, appelez le constructeur `CRecordset::CRecordset`, en passant les paramètres appropriés sur lui.  
  
 Passer **NULL** au constructeur de votre jeu d’enregistrements d’avoir un `CDatabase` objet construit et connecté automatiquement pour vous. Il s’agit d’un raccourci utile qui ne requiert pas construire et connecter un `CDatabase` objet avant de créer le jeu d’enregistrements.  
  
### <a name="example"></a>Exemple  
 Pour plus d’informations, consultez l’article [Recordset : déclaration de la classe d’une Table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
##  <a name="delete"></a>  CRecordset::Delete  
 Supprime l’enregistrement actif.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Notes  
 Après une suppression réussie, les membres de données de champ du jeu d’enregistrements sont définies sur une valeur Null, et vous devez appeler explicitement une de le **déplacer** fonctions afin de déplacer l’enregistrement supprimé. Une fois que vous quittez l’enregistrement supprimé, il n’est pas possible de revenir à ce dernier. Si la source de données prend en charge les transactions, vous pouvez rendre le **supprimer** appeler partie d’une transaction. Pour plus d’informations, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler **supprimer**. Cela entraîne un échec d’assertion. Bien que classe `CRecordset` ne fournit pas de mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction d’API ODBC **SQLSetPos**. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!CAUTION]
>  Le jeu d’enregistrements doive être mis à jour et il doit y avoir un enregistrement valide dans le jeu d’enregistrements lorsque vous appelez **supprimer**; sinon, une erreur se produit. Par exemple, si vous supprimez un enregistrement, mais ne pas faire défiler vers un nouvel enregistrement avant d’appeler **supprimer** , **supprimer** lève une [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Contrairement aux [AddNew](#addnew) et [modifier](#edit), un appel à **supprimer** n’est pas suivi par un appel à [mise à jour](#update). Si un **supprimer** appel échoue, les données des champs membres restent inchangées.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre un jeu d’enregistrements créé dans le cadre d’une fonction. L’exemple suppose l’existence de `m_dbCust`, une variable membre de type `CDatabase` déjà connecté à la source de données.  
  
 [!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>  CRecordset::DoBulkFieldExchange  
 Appelé pour échanger des lignes en bloc des données de la source de données vers le jeu d’enregistrements. Implémente en bloc d’échange de champs d’enregistrements (RFX en bloc).  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Paramètres  
 `pFX`  
 Un pointeur vers un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objet. Le framework sera déjà avoir configuré cet objet permet de spécifier un contexte pour l’opération d’échange de champs.  
  
### <a name="remarks"></a>Notes  
 Lors de l’extraction de lignes en bloc est implémentée, l’infrastructure appelle cette fonction membre pour transférer automatiquement les données à partir de la source de données à votre objet recordset. `DoBulkFieldExchange` lie également les membres de données de paramètre, cas échéant, aux espaces réservés de paramètre dans la chaîne d’instruction SQL pour la sélection du jeu d’enregistrements.  
  
 Si l’extraction de lignes en bloc n’est pas implémentée, le framework appelle [DoFieldExchange](#dofieldexchange). Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` option de le `dwOptions` paramètre dans le [ouvrir](#open) fonction membre.  
  
> [!NOTE]
> `DoBulkFieldExchange` est disponible uniquement si vous utilisez une classe dérivée de `CRecordset`. Si vous avez créé un objet recordset directement à partir de `CRecordset`, vous devez appeler la [GetFieldValue](#getfieldvalue) fonction membre pour récupérer des données.  
  
 RFX en bloc (RFX en bloc) est similaire à l’échange de champs d’enregistrements (RFX). Données sont automatiquement transférées à partir de la source de données à l’objet recordset. Toutefois, vous ne pouvez pas appeler `AddNew`, **modifier**, **supprimer**, ou **mise à jour** pour transférer les modifications apportées à la source de données. Classe `CRecordset` actuellement ne fournit pas d’un mécanisme de mise à jour en bloc des lignes de données ; Toutefois, vous pouvez écrire vos propres fonctions à l’aide de la fonction d’API ODBC **SQLSetPos**.  
  
 Notez que ClassWizard ne prend pas en charge RFX en bloc ; Par conséquent, vous devez substituer `DoBulkFieldExchange` manuellement en écrivant les appels aux fonctions RFX en bloc. Pour plus d’informations sur ces fonctions, consultez la rubrique [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md).  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus d’informations, consultez l’article [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="dofieldexchange"></a>  CRecordset::DoFieldExchange  
 Appelé pour échanger des données (dans les deux sens) entre les membres de données de champ de l’objet recordset et l’enregistrement correspondant de la source de données. Implémente enregistre l’échange de champs (RFX).  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Paramètres  
 `pFX`  
 Un pointeur vers un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objet. Le framework sera déjà avoir configuré cet objet permet de spécifier un contexte pour l’opération d’échange de champs.  
  
### <a name="remarks"></a>Notes  
 Lors de l’extraction de lignes en bloc n’est pas implémentée, l’infrastructure appelle cette fonction membre pour échanger automatiquement des données entre les membres de données de champ de votre objet recordset et les colonnes correspondantes de l’enregistrement actif sur la source de données. `DoFieldExchange` lie également les membres de données de paramètre, cas échéant, aux espaces réservés de paramètre dans la chaîne d’instruction SQL pour la sélection du jeu d’enregistrements.  
  
 Si l’extraction de lignes en bloc est implémentée, le framework appelle [DoBulkFieldExchange](#dobulkfieldexchange). Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` option de le `dwOptions` paramètre dans le [ouvrir](#open) fonction membre.  
  
> [!NOTE]
> `DoFieldExchange` est disponible uniquement si vous utilisez une classe dérivée de `CRecordset`. Si vous avez créé un objet recordset directement à partir de `CRecordset`, vous devez appeler la [GetFieldValue](#getfieldvalue) fonction membre pour récupérer des données.  
  
 L’échange de données de champ, appelées l’échange de champs d’enregistrements (RFX), fonctionne dans les deux sens : de membres de données de champ de l’objet recordset vers les champs de l’enregistrement sur la source de données et de l’enregistrement de la source de données à l’objet recordset.  
  
 La seule action que vous devez normalement suivre pour implémenter `DoFieldExchange` pour votre jeu d’enregistrements dérivée classe consiste à créer la classe avec ClassWizard et spécifiez les noms et types de données des membres de données du champ. Vous pouvez également ajouter le code à ce que ClassWizard écrit pour spécifier des membres de données de paramètre ou pour traiter toutes les colonnes que vous liez dynamiquement. Pour plus d’informations, consultez l’article [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Lorsque vous déclarez la classe de recordset dérivée avec ClassWizard, l’Assistant écrit une substitution de `DoFieldExchange` , qui ressemble à l’exemple suivant :  
  
 [!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 Pour plus d’informations sur les fonctions RFX, consultez la rubrique [fonctions Record Field Exchange](../../mfc/reference/record-field-exchange-functions.md).  
  
 Pour plus d’exemples et les détails de `DoFieldExchange`, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour obtenir des informations générales sur RFX, consultez l’article [Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="edit"></a>  CRecordset::Edit  
 Autorise les modifications à l’enregistrement actif.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Notes  
 Après avoir appelé **modifier**, vous pouvez modifier les membres de données de champ par directement la réinitialisation de leurs valeurs. L’opération est terminée lorsque vous appelez ensuite la [mise à jour](#update) fonction membre pour enregistrer vos modifications sur la source de données.  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler **modifier**. Cela entraîne un échec d’assertion. Bien que classe `CRecordset` ne fournit pas de mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction d’API ODBC **SQLSetPos**. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 **Modifier** enregistre les valeurs des membres de données du jeu d’enregistrements. Si vous appelez **modifier**, apporter des modifications, puis appelez **modifier** là encore, les valeurs de l’enregistrement sont restaurés qu’ils étaient avant le premier **modifier** appeler.  
  
 Dans certains cas, vous souhaiterez mettre à jour une colonne en le rendant Null (ne contenant pas de données). Pour ce faire, appelez [SetFieldNull](#setfieldnull) avec un paramètre de **TRUE** pour marquer le champ Null ; cela entraîne également la colonne à mettre à jour. Si vous souhaitez un champ pour être écrites dans la source de données, même si sa valeur n’a pas changé, appelez [SetFieldDirty](#setfielddirty) avec un paramètre de **TRUE**. Cela fonctionne même si le champ a la valeur Null.  
  
 Si la source de données prend en charge les transactions, vous pouvez rendre le **modifier** appeler partie d’une transaction. Notez que vous devez appeler [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) avant d’appeler **modifier** et après le jeu d’enregistrements a été ouvert. Notez également que l’appel [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) n’est pas un substitut pour appeler **mise à jour** pour terminer le **modifier** opération. Pour plus d’informations sur les transactions, consultez la classe [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 Selon le mode de verrouillage en cours, l’enregistrement mis à jour est peut-être verrouillé par **modifier** jusqu'à ce que vous appeliez **mise à jour** ou faites défiler jusqu'à un autre enregistrement, ou il peut être verrouillé uniquement pendant la **modifier** appeler. Vous pouvez modifier le mode de verrouillage avec [SetLockingMode](#setlockingmode).  
  
 La valeur précédente de l’enregistrement actif est restaurée si vous accédez à un nouvel enregistrement avant d’appeler **mise à jour**. A `CDBException` est levée si vous appelez **modifier** pour un jeu d’enregistrements qui ne peut pas être mis à jour ou s’il n’existe aucun enregistrement actif.  
  
 Pour plus d’informations, consultez les articles [Transaction (ODBC)](../../data/odbc/transaction-odbc.md) et [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>  CRecordset::FlushResultSet  
 Récupère le jeu de résultats suivant d’une requête prédéfinie (procédure stockée), s’il existe plusieurs jeux de résultats.  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro s’il existe plusieurs jeux de résultats à récupérer ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler `FlushResultSet` uniquement lorsque vous avez complètement terminé avec le curseur sur le jeu de résultats actuel. Notez que lorsque vous récupérez le résultat suivant est défini en appelant `FlushResultSet`, le curseur n’est pas valide sur ce jeu de résultats ; vous devez appeler la [MoveNext](#movenext) fonction membre après avoir appelé `FlushResultSet`.  
  
 Si une requête prédéfinie utilise un paramètre de sortie ou les paramètres d’entrée/sortie, vous devez appeler `FlushResultSet` jusqu'à ce qu’elle retourne `FALSE` (la valeur 0), afin d’obtenir ces valeurs de paramètre.  
  
 `FlushResultSet` appelle la fonction d’API ODBC `SQLMoreResults`. Si `SQLMoreResults` retourne `SQL_ERROR` ou `SQL_INVALID_HANDLE`, puis `FlushResultSet` lève une exception. Pour plus d’informations sur `SQLMoreResults`, consultez le Kit de développement logiciel Windows.  
  
 La procédure stockée doit avoir lié les champs si vous souhaitez appeler `FlushResultSet`.  
  
### <a name="example"></a>Exemple  
 Le code suivant suppose que `COutParamRecordset` est un `CRecordset`-objet dérivé basé sur une requête prédéfinie avec un paramètre d’entrée et un paramètre de sortie et avoir plusieurs jeux de résultats. Remarque la structure de la [DoFieldExchange](#dofieldexchange) remplacer.  
  
 [!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>  CRecordset::GetBookmark  
 Obtient la valeur du signet pour l’enregistrement actif.  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Paramètres  
 `varBookmark`  
 Une référence à un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objet représentant le signet sur l’enregistrement actif.  
  
### <a name="remarks"></a>Notes  
 Pour déterminer si les signets sont pris en charge sur l’ensemble d’enregistrements, appelez [CanBookmark](#canbookmark). Pour rendre les signets disponibles si elles sont prises en charge, vous devez définir le **CRecordset::useBookmarks** option dans le `dwOptions` paramètre de la [ouvrir](#open) fonction membre.  
  
> [!NOTE]
>  Si les signets sont pris en charge ou non disponible, l’appel `GetBookmark` entraîne une exception est levée. Les signets ne sont pas pris en charge sur les recordsets avant uniquement.  
  
 `GetBookmark` assigne la valeur du signet pour l’enregistrement actif à un `CDBVariant` objet. Pour revenir à cet enregistrement à tout moment après avoir déplacé vers un autre enregistrement, appelez [SetBookmark](#setbookmark) avec correspondant `CDBVariant` objet.  
  
> [!NOTE]
>  Après certaines opérations de jeu d’enregistrements, les signets peuvent ne plus être valides. Par exemple, si vous appelez `GetBookmark` suivie **Requery**, vous n’êtes peut-être pas en mesure de retourner à l’enregistrement avec `SetBookmark`. Appelez [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si vous pouvez appeler en toute sécurité `SetBookmark`.  
  
 Pour plus d’informations sur les signets et de navigation du jeu d’enregistrements, consultez les articles [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="getdefaultconnect"></a>  CRecordset::GetDefaultConnect  
 Appelé pour obtenir la chaîne de connexion par défaut.  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` qui contient la chaîne de connexion par défaut.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction membre pour obtenir la chaîne de connexion par défaut pour la source de données sur laquelle repose le jeu d’enregistrements. ClassWizard implémente cette fonction pour vous en identifiant la source de données que vous utilisez dans ClassWizard pour obtenir des informations sur les tables et colonnes. Il sera probablement utile s’appuyer sur cette connexion par défaut lors du développement de votre application. Mais la connexion par défaut peut ne pas convenir pour les utilisateurs de votre application. Si tel est le cas, vous devez réimplémenter cette fonction, en ignorant les version de ClassWizard. Pour plus d’informations sur les chaînes de connexion, consultez l’article [Source de données (ODBC)](../../data/odbc/data-source-odbc.md).  
  
##  <a name="getdefaultsql"></a>  CRecordset::GetDefaultSQL  
 Appelé pour obtenir la chaîne SQL par défaut à exécuter.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` qui contient l’instruction SQL par défaut.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction membre pour obtenir de l’instruction SQL par défaut sur lequel repose le jeu d’enregistrements. Cela peut être un nom de table ou une SQL **sélectionnez** instruction.  
  
 Vous définissez indirectement l’instruction SQL par défaut par déclarer votre classe de recordset avec ClassWizard et ClassWizard effectue cette tâche pour vous.  
  
 Si vous avez besoin de la chaîne de l’instruction SQL pour votre propre usage, appelez `GetSQL`, qui retourne l’instruction SQL utilisée pour sélectionner les enregistrements du jeu d’enregistrements lorsqu’il a été ouvert. Vous pouvez modifier la chaîne SQL par défaut dans la substitution de votre classe de `GetDefaultSQL`. Par exemple, vous pouvez spécifier un appel à une requête prédéfinie à l’aide un **appeler** instruction. (Notez, toutefois, que si vous modifiez `GetDefaultSQL`, vous devez également modifier `m_nFields` correspondre au nombre de colonnes dans la source de données.)  
  
 Pour plus d’informations, consultez l’article [Recordset : déclaration de la classe d’une Table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
> [!CAUTION]
>  Le nom de table sera vide si l’infrastructure n’a pas pu identifier un nom de table, si plusieurs noms de tables ont été fournies, ou si un **appeler** instruction n’a pas pu être interprétée. Notez que lorsque vous utilisez un **appeler** instruction, vous ne devez pas insérer un espace blanc entre les accolades et le **appeler** (mot clé), ni vous devez insérer un espace blanc avant l’accolade ou avant le  **Sélectionnez** mot clé dans un **sélectionnez** instruction.  
  
##  <a name="getfieldvalue"></a>  CRecordset::GetFieldValue  
 Récupère les données du champ dans l’enregistrement actif.  
  
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
 `lpszName`  
 Le nom d’un champ.  
  
 *varValu*e  
 Une référence à un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objet permettant de stocke la valeur du champ.  
  
 `nFieldType`  
 Le type de données ODBC C du champ. À l’aide de la valeur par défaut, **DEFAULT_FIELD_TYPE**, force `GetFieldValue` pour déterminer le type de données C à partir du type de données SQL, selon le tableau suivant. Sinon, vous pouvez spécifier les données de type directement ou choisir un type de données compatibles ; par exemple, vous pouvez stocker n’importe quel type de données dans **SQL_C_CHAR**.  
  
|Type de données C|Type de données SQL|  
|-----------------|-------------------|  
|**SQL_C_BIT**|**SQL_BIT**|  
|**SQL_C_UTINYINT**|**SQL_TINYINT**|  
|**SQL_C_SSHORT**|**SQL_SMALLINT**|  
|**SQL_C_SLONG**|**SQL_INTEGER**|  
|**SQL_C_FLOAT**|**SQL_REAL**|  
|**SQL_C_DOUBLE**|**SQL_FLOATSQL_DOUBLE**|  
|**SQL_C_TIMESTAMP**|**SQL_DATESQL_TIMESQL_TIMESTAMP**|  
|**SQL_C_CHAR**|**SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR**|  
|**SQL_C_BINARY**|**SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY**|  
  
 Pour plus d’informations sur les types de données ODBC, consultez les rubriques « Types de données SQL » et « Types de données C » dans l’annexe D du Kit de développement.  
  
 `nIndex`  
 Index de base zéro du champ.  
  
 `strValue`  
 Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet permettant de stocke la valeur du champ est converti en texte, quel que soit le type de données.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez rechercher un champ par nom ou par index. Vous pouvez stocker la valeur du champ, que ce soit un `CDBVariant` objet ou un `CString` objet.  
  
 Si vous avez implémenté l’extraction de lignes en bloc, l’enregistrement actif est toujours positionnée sur le premier enregistrement dans un ensemble de lignes. Pour utiliser `GetFieldValue` sur un enregistrement dans un ensemble de lignes donné, vous devez d’abord appeler la [SetRowsetCursorPosition](#setrowsetcursorposition) fonction membre pour déplacer le curseur à la ligne de votre choix au sein de cet ensemble de lignes. Appelez ensuite `GetFieldValue` pour cette ligne. Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` option de le `dwOptions` paramètre dans le [ouvrir](#open) fonction membre.  
  
 Vous pouvez utiliser `GetFieldValue` pour extraire dynamiquement des champs au moment de l’exécution, plutôt que de les lier statiquement au moment du design. Par exemple, si vous avez déclaré un objet recordset directement à partir de `CRecordset`, vous devez utiliser `GetFieldValue` pour récupérer les données du champ ; échange de champs d’enregistrements (RFX) ou RFX en bloc (RFX en bloc), n’est pas implémentée.  
  
> [!NOTE]
>  Si vous déclarez un objet recordset sans dériver `CRecordset`, n’ont pas de charger la bibliothèque de curseurs ODBC. La bibliothèque de curseurs requiert que le jeu d’enregistrements ont au moins une colonne dépendante ; Toutefois, lorsque vous utilisez `CRecordset` directement, aucune des colonnes sont liés. Les fonctions membres [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) et [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) contrôler si la bibliothèque de curseurs est chargée.  
  
 `GetFieldValue` appelle la fonction d’API ODBC **SQLGetData**. Si votre pilote génère la valeur **SQL_NO_TOTAL** pour la longueur réelle de la valeur du champ, `GetFieldValue` lève une exception. Pour plus d’informations sur **SQLGetData**, consultez le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant illustre des appels à `GetFieldValue` pour un objet recordset déclarée directement à partir de `CRecordset`.  
  
 [!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  Contrairement à la classe DAO `CDaoRecordset`, `CRecordset` n’a pas un `SetFieldValue` fonction membre. Si vous créez un objet directement à partir de `CRecordset`, il est en réalité en lecture seule.  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getodbcfieldcount"></a>  CRecordset::GetODBCFieldCount  
 Récupère le nombre total de champs dans l’objet recordset.  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de champs dans le jeu d’enregistrements.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur la création de jeux d’enregistrements, consultez l’article [Recordset : création et fermeture de Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getodbcfieldinfo"></a>  CRecordset::GetODBCFieldInfo  
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
 `lpszName`  
 Le nom d’un champ.  
  
 `fieldinfo`  
 Une référence à un `CODBCFieldInfo` structure.  
  
 `nIndex`  
 Index de base zéro du champ.  
  
### <a name="remarks"></a>Notes  
 Une version de la fonction vous permet de rechercher un champ par nom. L’autre version vous permet de rechercher un champ par index.  
  
 Pour obtenir une description sur les informations renvoyées, consultez la [CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md) structure.  
  
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
>  Le nombre d’enregistrements est conservé comme une « borne, « l’enregistrement le plus élevé numérotées encore considéré comme l’utilisateur parcourt les enregistrements. Le nombre total d’enregistrements est uniquement appelée une fois que l’utilisateur a été déplacé au-delà du dernier enregistrement. Pour des raisons de performances, le nombre n’est pas actualisé lorsque vous appelez `MoveLast`. Pour compter les enregistrements vous-même, appelez `MoveNext` à plusieurs reprises jusqu'à ce que `IsEOF` retourne différente de zéro. Ajout d’un enregistrement via **CRecordset:AddNew** et **mise à jour** augmente le nombre ; la suppression d’un enregistrement via `CRecordset::Delete` diminue le nombre.  
  
##  <a name="getrowsetsize"></a>  CRecordset::GetRowsetSize  
 Obtient le paramètre actuel pour le nombre de lignes que vous souhaitez récupérer lors d’une extraction donnée.  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de lignes à récupérer durant une extraction donnée.  
  
### <a name="remarks"></a>Notes  
 Si vous utilisez l’extraction de lignes en bloc, la taille d’ensemble de lignes par défaut lorsque le jeu d’enregistrements est ouvert est 25 ; dans le cas contraire, il est 1.  
  
 Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` option dans le `dwOptions` paramètre de la [ouvrir](#open) fonction membre. Pour modifier le paramètre de la taille de l’ensemble de lignes, appelez [SetRowsetSize](#setrowsetsize).  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getrowsfetched"></a>  CRecordset::GetRowsFetched  
 Détermine le nombre d’enregistrements qui ont été réellement récupéré après une extraction.  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de lignes récupérées à partir de la source de données après une extraction donnée.  
  
### <a name="remarks"></a>Notes  
 Cela est utile lorsque vous avez implémenté l’extraction de lignes en bloc. La taille de l’ensemble de lignes indique généralement le nombre de lignes est extraites d’une extraction ; Toutefois, le nombre total de lignes dans le jeu d’enregistrements affecte également le nombre de lignes sera extrait dans un ensemble de lignes. Par exemple, si votre jeu d’enregistrements a 10 enregistrements avec un paramètre de taille d’ensemble de lignes de 4, puis exécuter une boucle dans le jeu d’enregistrements en appelant `MoveNext` entraîne l’ensemble de lignes final ayant des enregistrements seulement 2.  
  
 Pour implémenter l’extraction de lignes en bloc, vous devez spécifier le `CRecordset::useMultiRowFetch` option dans le `dwOptions` paramètre de la [ouvrir](#open) fonction membre. Pour spécifier la taille de l’ensemble de lignes, appelez [SetRowsetSize](#setrowsetsize).  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>  CRecordset::GetRowStatus  
 Obtient l’état d’une ligne dans l’ensemble de lignes en cours.  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `wRow`  
 La position de base un d’une ligne dans l’ensemble de lignes en cours. Cette valeur peut varier de 1 à la taille de l’ensemble de lignes.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur d’état de la ligne. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 `GetRowStatus` Retourne une valeur qui indique une modification de statut à la ligne depuis le dernier récupérées à partir de la source de données, ou qui aucune ligne correspondant à `wRow` a été extraite. Le tableau ci-dessous répertorie les valeurs de retour possibles.  
  
|Valeur d’état|Description|  
|------------------|-----------------|  
|`SQL_ROW_SUCCESS`|La ligne est inchangée.|  
|`SQL_ROW_UPDATED`|La ligne a été mis à jour.|  
|`SQL_ROW_DELETED`|La ligne a été supprimée.|  
|`SQL_ROW_ADDED`|La ligne a été ajoutée.|  
|`SQL_ROW_ERROR`|La ligne n’est pas récupérables en raison d’une erreur.|  
|`SQL_ROW_NOROW`|Il n’existe aucune ligne qui correspond à `wRow`.|  
  
 Pour plus d’informations, consultez la fonction d’API ODBC **SQLExtendedFetch** dans le Kit de développement logiciel Windows.  
  
##  <a name="getstatus"></a>  CRecordset::GetStatus  
 Détermine l’index de l’enregistrement actif dans le jeu d’enregistrements et si le dernier enregistrement a été affiché.  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `rStatus`  
 Une référence à un **CRecordsetStatus** objet. Pour plus d'informations, consultez la section Notes.  
  
### <a name="remarks"></a>Notes  
 `CRecordset` tente d’effectuer le suivi de l’index, mais sous certaines circonstances il sera peut-être pas possible. Consultez [GetRecordCount](#getrecordcount) pour obtenir une explication.  
  
 Le **CRecordsetStatus** structure a la forme suivante :  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 Les deux membres de **CRecordsetStatus** ont les significations suivantes :  
  
- **m_lCurrentRecord** contient l’index de base zéro de l’enregistrement actif dans le jeu d’enregistrements, s’il est connu. Si l’index ne peut pas être déterminé, ce membre contient **AFX_CURRENT_RECORD_UNDEFINED** (-2). Si `IsBOF` est **TRUE** (vider le jeu d’enregistrements ou de la tentative de défilement avant le premier enregistrement), puis **m_lCurrentRecord** a la valeur **AFX_CURRENT_RECORD_BOF** (-1). Si sur le premier enregistrement, puis elle est définie sur 0, deuxième enregistrement 1 et ainsi de suite.  
  
- **m_bRecordCountFinal** Nonzero si le nombre total d’enregistrements dans le jeu d’enregistrements a été déterminé. Cela doit généralement être accompli en partant du début de l’objet recordset et en appelant `MoveNext` jusqu'à ce que `IsEOF` retourne différente de zéro. Si ce membre est égal à zéro, l’enregistrement de nombre tel que retourné par `GetRecordCount`, si pas -1, n'est que le nombre « limite supérieure » des enregistrements.  
  
##  <a name="getsql"></a>  CRecordset::GetSQL  
 Appelez cette fonction membre pour obtenir de l’instruction SQL qui a été utilisée pour sélectionner les enregistrements du jeu d’enregistrements lorsqu’il a été ouvert.  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A **const** font référence à un `CString` qui contient l’instruction SQL.  
  
### <a name="remarks"></a>Notes  
 Il s’agit généralement d’un SQL **sélectionnez** instruction. La chaîne retournée par `GetSQL` est en lecture seule.  
  
 La chaîne retournée par `GetSQL` est généralement différent à partir de n’importe quelle chaîne que vous avez peut-être passé à l’ensemble d’enregistrements dans la `lpszSQL` paramètre à la **ouvrir** fonction membre. C’est parce que l’objet recordset construit l’instruction SQL complète en fonction de ce que vous avez passé à **ouvrir**, ce que vous avez spécifié avec ClassWizard, ce que vous avez spécifié dans le **m_strFilter** et `m_strSort` membres de données et tous les paramètres que vous avez spécifié. Pour plus d’informations sur la façon dont le recordset construit cette instruction SQL, consultez l’article [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
> [!NOTE]
>  Appelez cette fonction membre uniquement après avoir appelé [ouvrir](#open).  
  
##  <a name="gettablename"></a>  CRecordset::GetTableName  
 Obtient le nom de la table SQL sur lequel repose la requête du recordset.  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A **const** font référence à un `CString` qui contient la table name, si le jeu d’enregistrements est basée sur une table ; sinon, une chaîne vide.  
  
### <a name="remarks"></a>Notes  
 `GetTableName` est valide uniquement si le jeu d’enregistrements est basé sur une table, pas une jointure de plusieurs tables ou d’une requête prédéfinie (procédure stockée). Le nom est en lecture seule.  
  
> [!NOTE]
>  Appelez cette fonction membre uniquement après avoir appelé [ouvrir](#open).  
  
##  <a name="isbof"></a>  CRecordset::IsBOF  
 Retourne zéro si le jeu d’enregistrements a été positionné avant le premier enregistrement. Il n’existe aucun enregistrement actif.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements ne contient aucun enregistrement ou si vous avez le défilement arrière avant le premier enregistrement ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre avant que vous accédez à partir de l’enregistrement à enregistrement pour savoir si vous avez vérifié avant le premier enregistrement de l’objet recordset. Vous pouvez également utiliser `IsBOF` avec `IsEOF` pour déterminer si le jeu d’enregistrements contient des enregistrements ou est vide. Immédiatement après avoir appelé **ouvrir**, si le jeu d’enregistrements ne contient aucun enregistrement, `IsBOF` retourne différente de zéro. Lorsque vous ouvrez un jeu d’enregistrements qui a au moins un enregistrement, le premier enregistrement est l’enregistrement actif et `IsBOF` retourne 0.  
  
 Si le premier enregistrement est l’enregistrement actif et que vous appelez `MovePrev`, `IsBOF` retournera ensuite différente de zéro. Si `IsBOF` retourne différente de zéro et que vous appelez `MovePrev`, une erreur se produit. Si `IsBOF` retourne différente de zéro, l’enregistrement actif n’est pas défini, et toute action qui nécessite un enregistrement en cours génère une erreur.  
  
### <a name="example"></a>Exemple  
 Cet exemple utilise `IsBOF` et `IsEOF` pour détecter les limites d’un jeu d’enregistrements que le code défile dans le jeu d’enregistrements dans les deux sens.  
  
 [!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>  CRecordset::IsDeleted  
 Détermine si l’enregistrement actif a été supprimé.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements est positionné sur un enregistrement supprimé. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si vous accédez à un enregistrement et `IsDeleted` retourne **TRUE** (différente de zéro), puis vous devez accéder à un autre enregistrement avant d’effectuer d’autres opérations de jeu d’enregistrements.  
  
 Le résultat de `IsDeleted` dépend de nombreux facteurs, tels que votre type de jeu d’enregistrements, si le jeu d’enregistrements est mis à jour, si vous avez spécifié le **CRecordset::skipDeletedRecords** option lorsque vous avez ouvert le jeu d’enregistrements, si votre packs de pilote supprimé des enregistrements, et s’il existe plusieurs utilisateurs.  
  
 Pour plus d’informations sur **CRecordset::skipDeletedRecords** et le pilote de compression, consultez la [ouvrir](#open) fonction membre.  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne devez pas appeler `IsDeleted`. Au lieu de cela, appelez le [GetRowStatus](#getrowstatus) fonction membre. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="iseof"></a>  CRecordset::IsEOF  
 Retourne zéro si le jeu d’enregistrements a été positionné après le dernier enregistrement. Il n’existe aucun enregistrement actif.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements ne contient aucun enregistrement ou si vous avez déplacé au-delà du dernier enregistrement ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre que vous accédez à partir de l’enregistrement à enregistrement pour savoir si vous avez dépassé le dernier enregistrement de l’objet recordset. Vous pouvez également utiliser `IsEOF` pour déterminer si le jeu d’enregistrements contient des enregistrements ou est vide. Immédiatement après avoir appelé **ouvrir**, si le jeu d’enregistrements ne contient aucun enregistrement, `IsEOF` retourne différente de zéro. Lorsque vous ouvrez un jeu d’enregistrements qui a au moins un enregistrement, le premier enregistrement est l’enregistrement actif et `IsEOF` retourne 0.  
  
 Si le dernier enregistrement est l’enregistrement actif lorsque vous appelez `MoveNext`, `IsEOF` retournera ensuite différente de zéro. Si `IsEOF` retourne différente de zéro et que vous appelez `MoveNext`, une erreur se produit. Si `IsEOF` retourne différente de zéro, l’enregistrement actif n’est pas défini, et toute action qui nécessite un enregistrement en cours génère une erreur.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="isfielddirty"></a>  CRecordset::IsFieldDirty  
 Détermine si le membre de données du champ spécifié a été modifié depuis [modifier](#edit) ou [AddNew](#addnew) a été appelée.  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 `pv`  
 Un pointeur vers le membre de données du champ dont vous souhaitez vérifier, l’état ou **NULL** pour déterminer si l’un des champs sont incorrect.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le membre de données du champ spécifié a changé depuis l’appel `AddNew` ou **modifier**; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Les données de tous les membres de données de champ modifié seront transférées à l’enregistrement sur la source de données lors de l’enregistrement actif est mis à jour par un appel à la [mise à jour](#update) fonction membre de `CRecordset` (après un appel à **modifier**ou `AddNew`).  
  
> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les jeux d’enregistrements qui est à l’aide de l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, puis `IsFieldDirty` retournera toujours **FALSE** et entraîne un échec d’assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Appel de `IsFieldDirty` va réinitialiser les effets des appels à précédentes [SetFieldDirty](#setfielddirty) étant donné que l’état de non-intégrité du champ est réévaluée. Dans la `AddNew` cas, si la valeur de champ actuelle est différente de la valeur null de pseudo, l’état du champ a la valeur incorrecte. Dans le **modifier** cas, si la valeur du champ est différente de la valeur mise en cache, puis l’état du champ est modifié.  
  
 `IsFieldDirty` est implémenté via [DoFieldExchange](#dofieldexchange).  
  
 Pour plus d’informations sur l’indicateur de changement, consultez l’article [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
##  <a name="isfieldnull"></a>  CRecordset::IsFieldNull  
 Retourne zéro si le champ spécifié dans l’enregistrement actif est Null (n’a aucune valeur).  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 `pv`  
 Un pointeur vers le membre de données du champ dont vous souhaitez vérifier, l’état ou **NULL** pour déterminer si les champs sont Null.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le membre de données du champ spécifié est marqué en tant que valeur Null. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour déterminer si le membre de données de champ spécifié d’un jeu d’enregistrements a été marquée comme Null. (Dans la terminologie de base de données, Null donne « aucune valeur » et n’est pas le même que **NULL** en C++.) Si un membre de données de champ est marqué avec la valeur Null, il est interprété en tant que colonne de l’enregistrement en cours pour lequel il n’existe aucune valeur.  
  
> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les jeux d’enregistrements qui est à l’aide de l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, puis `IsFieldNull` retournera toujours **FALSE** et entraîne un échec d’assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `IsFieldNull` est implémenté via [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isfieldnullable"></a>  CRecordset::IsFieldNullable  
 Retourne zéro si le champ spécifié dans l’enregistrement actif peut être défini avec la valeur Null (n’ayant aucune valeur).  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 `pv`  
 Un pointeur vers le membre de données du champ dont vous souhaitez vérifier, l’état ou **NULL** pour déterminer si l’un des champs peut être défini à une valeur Null.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour déterminer si le membre de données du champ spécifié est « null » (peut être définie sur une valeur Null ; C++ **NULL** n’est pas identique à Null, ce qui, dans la terminologie de base de données, signifie « aucune valeur les clauses having »).  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `IsFieldNullable`. Au lieu de cela, appelez le [GetODBCFieldInfo au](#getodbcfieldinfo) fonction membre pour déterminer si un champ peut être défini à une valeur Null. Notez que vous pouvez toujours appeler `GetODBCFieldInfo`, indépendamment de si vous avez implémenté l’extraction de lignes en bloc. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Un champ qui ne peut pas être Null doit avoir une valeur. Si vous essayez de définir un tel champ null lors de l’ajout ou la mise à jour un enregistrement, la source de données rejette l’ajout ou la mise à jour, et [mettre à jour](#update) lève une exception. L’exception se produit lorsque vous appelez **mise à jour**, pas lorsque vous appelez [SetFieldNull](#setfieldnull).  
  
 À l’aide de **NULL** pour le premier argument de la fonction appliquera la fonction uniquement à **outputColumn** ne champs pas **param** champs. Par exemple, l’appel  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 définit uniquement **outputColumn** champs **NULL**; **param** champs ne seront pas affectées.  
  
 Pour travailler sur **param** champs, vous devez fournir l’adresse réelle de la personne **param** vous souhaitez travailler, telles que :  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Cela signifie que vous ne pouvez pas définir tous les **param** champs **NULL**, comme vous pouvez le faire avec **outputColumn** champs.  
  
 `IsFieldNullable` est implémenté via [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isopen"></a>  CRecordset::IsOpen  
 Détermine si le jeu d’enregistrements est déjà ouvert.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’objet recordset [ouvrir](#open) ou [Requery](#requery) fonction membre a été précédemment appelée et le jeu d’enregistrements n’a pas été fermé ; sinon, 0.  
  
##  <a name="m_hstmt"></a>  CRecordset::m_hstmt  
 Contient un handle vers la structure de données instruction ODBC, de type **HSTMT**, associés à l’ensemble d’enregistrements.  
  
### <a name="remarks"></a>Notes  
 Chaque requête à une source de données ODBC est associé un **HSTMT**.  
  
> [!CAUTION]
>  N’utilisez pas **m_hstmt** avant [ouvrir](#open) a été appelée.  
  
 Normalement, vous n’avez pas besoin pour accéder à la **HSTMT** directement, mais vous en aurez besoin pour l’exécution directe des instructions SQL. Le `ExecuteSQL` fonction membre de classe `CDatabase` fournit un exemple d’utilisation **m_hstmt**.  
  
##  <a name="m_nfields"></a>  CRecordset::m_nFields  
 Contient le nombre de membres de données de champ dans la classe de recordset ; Autrement dit, le nombre de colonnes sélectionnées par l’ensemble d’enregistrements à partir de la source de données.  
  
### <a name="remarks"></a>Notes  
 Le constructeur de la classe de recordset doit initialiser `m_nFields` avec le nombre correct. Si vous n’avez pas implémenté l’extraction de lignes en bloc, ClassWizard écrit cette initialisation pour vous lorsque vous l’utilisez pour déclarer la classe de recordset. Vous pouvez également le créer manuellement.  
  
 L’infrastructure utilise ce numéro pour gérer l’interaction entre les membres de données de champ et les colonnes correspondantes de l’enregistrement actif sur la source de données.  
  
> [!CAUTION]
>  Ce numéro doit correspondre au nombre de « colonnes de sortie » inscrit dans `DoFieldExchange` ou `DoBulkFieldExchange` après un appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) avec le paramètre **CFieldExchange::outputColumn**.  
  
 Vous pouvez lier des colonnes dynamiquement, comme expliqué dans l’article « Recordset : dynamiquement les colonnes de données de liaison. » Si vous le faites, vous devez augmenter le nombre de `m_nFields` afin de refléter le numéro de fonction RFX et RFX en bloc appelle votre `DoFieldExchange` ou `DoBulkFieldExchange` fonction membre pour les colonnes liées dynamiquement.  
  
 Pour plus d’informations, consultez les articles [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) et [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’article [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_nparams"></a>  CRecordset::m_nParams  
 Contient le nombre de membres de données de paramètre dans la classe de recordset ; Autrement dit, le nombre de paramètres passé avec la requête du recordset.  
  
### <a name="remarks"></a>Notes  
 Si votre classe de recordset possède des membres de données de paramètre, le constructeur de la classe doit initialiser `m_nParams` avec le nombre correct. La valeur de `m_nParams` valeur par défaut est 0. Si vous ajoutez des membres de données de paramètre (ce que vous devez effectuer manuellement) vous devez également ajouter manuellement une initialisation dans le constructeur de classe pour refléter le nombre de paramètres (qui doit être au moins aussi grand que le nombre de « espaces réservés dans votre **m_strFilter**  ou `m_strSort` chaîne).  
  
 L’infrastructure utilise ce numéro lorsqu’il paramètre la requête du recordset.  
  
> [!CAUTION]
>  Ce numéro doit correspondre au nombre de « params » inscrit dans `DoFieldExchange` ou `DoBulkFieldExchange` après un appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) avec une valeur de paramètre **CFieldExchange::inputParam**,  **CFieldExchange::param**, **CFieldExchange::outputParam**, ou **CFieldExchange::inoutParam**.  
  
### <a name="example"></a>Exemple  
  Consultez les articles [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) et [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_pdatabase"></a>  CRecordset::m_pDatabase  
 Contient un pointeur vers le `CDatabase` objet via lequel le jeu d’enregistrements est connecté à une source de données.  
  
### <a name="remarks"></a>Notes  
 Cette variable est définie de deux manières. En règle générale, vous passez un pointeur à un socket déjà `CDatabase` de l’objet lorsque vous construisez l’objet recordset. Si vous passez **NULL** au lieu de cela, `CRecordset` crée un `CDatabase` de l’objet pour vous et le connecte. Dans les deux cas, `CRecordset` stocke le pointeur dans cette variable.  
  
 Normalement vous directement aurez pas à utiliser le pointeur stocké dans **m_pDatabase**. Si vous écrivez vos propres extensions `CRecordset`, toutefois, vous devrez peut-être utiliser le pointeur. Par exemple, vous devrez peut-être le pointeur si vous levez vos propres `CDBException`s. Ou vous en aurez besoin si vous avez besoin d’effectuer une action en utilisant le même `CDatabase` objet, telles que les transactions, le paramètre des délais d’attente, en cours d’exécution ou en appelant le `ExecuteSQL` fonction membre de classe `CDatabase` pour exécuter des instructions SQL directement.  
  
##  <a name="m_strfilter"></a>  CRecordset::m_strFilter  
 Après avoir construit l’objet recordset, mais avant d’appeler ses **ouvrir** membre fonction, utilisez ce membre de données pour stocker un `CString` contenant SQL **où** clause.  
  
### <a name="remarks"></a>Notes  
 Le jeu d’enregistrements utilise la chaîne pour contraindre (ou filtrer) les enregistrements qu’il sélectionne au cours de la **ouvrir** ou **Requery** appeler. Cela est utile pour sélectionner un sous-ensemble d’enregistrements, tels que « tous les vendeurs en fonction de Californie » (« état = autorité de certification »). La syntaxe ODBC SQL pour un **où** clause est  
  
 `WHERE search-condition`  
  
 Notez que vous n’incluez pas le **où** mot clé dans votre chaîne. Fournit l’infrastructure.  
  
 Vous pouvez également paramétrer la chaîne de filtre en plaçant '' des espaces réservés, déclaration d’un membre de données de paramètre dans votre classe pour chaque espace réservé et passer des paramètres à l’ensemble d’enregistrements au moment de l’exécution. Cela vous permet de construire le filtre au moment de l’exécution. Pour plus d’informations, consultez l’article [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Pour plus d’informations sur SQL **où** clauses, consultez l’article [SQL](../../data/odbc/sql.md). Pour plus d’informations sur la sélection et filtrage d’enregistrements, consultez l’article [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>  CRecordset::m_strSort  
 Après avoir construit l’objet recordset, mais avant d’appeler ses **ouvrir** membre fonction, utilisez ce membre de données pour stocker un `CString` contenant SQL **ORDER BY** clause.  
  
### <a name="remarks"></a>Notes  
 Le jeu d’enregistrements utilise la chaîne de tri des enregistrements qu’il sélectionne au cours de la **ouvrir** ou **Requery** appeler. Vous pouvez utiliser cette fonctionnalité pour trier un jeu d’enregistrements sur une ou plusieurs colonnes. La syntaxe ODBC SQL pour un **ORDER BY** clause est  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 où une spécification de tri est un entier ou un nom de colonne. Vous pouvez également spécifier l’ordre croissant ou décroissant (par défaut, l’ordre est croissant) en ajoutant « ASC » ou « DESC » à la liste des colonnes dans la chaîne de tri. Les enregistrements sélectionnés sont triés en premier lieu par la première colonne, puis par le deuxième et ainsi de suite. Par exemple, vous pouvez commander un jeu d’enregistrements « Customers » par le nom de famille, puis du prénom. Le nombre de colonnes que vous pouvez répertorier dépend de la source de données. Pour plus d’informations, consultez le Kit de développement logiciel Windows.  
  
 Notez que vous n’incluez pas le **ORDER BY** mot clé dans votre chaîne. Fournit l’infrastructure.  
  
 Pour plus d’informations sur les clauses SQL, consultez l’article [SQL](../../data/odbc/sql.md). Pour plus d’informations sur le tri d’enregistrements, consultez l’article [Recordset : tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>  CRecordset::Move  
 Déplace le pointeur d’enregistrement actif dans le jeu d’enregistrements vers l’avant ou vers l’arrière.  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>Paramètres  
 `nRows`  
 Le nombre de lignes à avancer ou reculer. Les valeurs positives déplacent vers l’avant, vers la fin de l’objet recordset. Les valeurs négatives déplacent vers le haut, vers le début.  
  
 `wFetchType`  
 Détermine l’ensemble de lignes qui **déplacer** extrait. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Si vous passez une valeur de 0 pour `nRows`, **déplacer** actualise l’enregistrement actif. **Déplacer** prendra fin toutes `AddNew` ou **modifier** mode et restaure la valeur de l’enregistrement actif avant `AddNew` ou **modifier** a été appelée.  
  
> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez [CRecordset::IsDeleted](#isdeleted) pour plus d’informations. Lorsque vous ouvrez un `CRecordset` avec la **skipDeletedRecords** option set, **déplacer** déclare si le `nRows` paramètre est 0. Ce comportement empêche l’actualisation des lignes supprimées par les autres applications clientes utilisant les mêmes données. Consultez le `dwOption` paramètre dans [ouvrir](#open) pour obtenir une description de **skipDeletedRecords**.  
  
 **Déplacer** repositionne le jeu d’enregistrements par les ensembles de lignes. Selon les valeurs pour `nRows` et `wFetchType`, **déplacer** extrait l’ensemble de lignes approprié, puis rend le premier enregistrement dans cet ensemble de lignes l’enregistrement actif. Si vous n’avez pas implémenté l’extraction de lignes en bloc, la taille de l’ensemble de lignes est toujours 1. Lors de la récupération d’un ensemble de lignes, **déplacer** appelle directement la [CheckRowsetError](#checkrowseterror) fonction membre pour gérer les erreurs résultant de l’extraction.  
  
 Selon les valeurs que vous passez, **déplacer** équivaut à d’autres `CRecordset` fonctions membres. En particulier, la valeur de `wFetchType` peut indiquer une fonction membre qui n’est plus intuitive et souvent la méthode préférée pour l’enregistrement actif.  
  
 Le tableau suivant répertorie les valeurs possibles pour `wFetchType`, l’ensemble de lignes qui **déplacer** extraira selon `wFetchType` et `nRows`et n’importe quelle fonction membre équivalent correspondant à `wFetchType`.  
  
|wFetchType|Ensemble de lignes extraite|Fonction membre équivalent|  
|----------------|--------------------|--------------------------------|  
|`SQL_FETCH_RELATIVE` (la valeur par défaut)|Le démarrage de l’ensemble de lignes `nRows` ou les lignes à partir de la première ligne dans l’ensemble de lignes en cours.||  
|`SQL_FETCH_NEXT`|L’ensemble de lignes suivant ; `nRows` est ignoré.|[MoveNext](#movenext)|  
|`SQL_FETCH_PRIOR`|L’ensemble de lignes précédente ; `nRows` est ignoré.|[MovePrev](#moveprev)|  
|`SQL_FETCH_FIRST`|Le premier ensemble de lignes dans le jeu d’enregistrements ; `nRows` est ignoré.|[MoveFirst](#movefirst)|  
|`SQL_FETCH_LAST`|Le dernier ensemble de lignes dans le jeu d’enregistrements ; `nRows` est ignoré.|[MoveLast](#movelast)|  
|`SQL_FETCH_ABSOLUTE`|Si `nRows` > 0, l’ensemble de lignes démarrant `nRows` ou les lignes à partir du début de l’objet recordset. Si `nRows` < 0, l’ensemble de lignes démarrant `nRows` ou les lignes à partir de la fin de l’objet recordset. Si `nRows` = 0, une condition de début de fichier (BOF) est retourné.|[SetAbsolutePosition](#setabsoluteposition)|  
|`SQL_FETCH_BOOKMARK`|L’ensemble de lignes en commençant à la ligne dont la valeur signet correspond à `nRows`.|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  Pour les recordsets avant uniquement, **déplacer** est valide uniquement avec une valeur de `SQL_FETCH_NEXT` pour `wFetchType`.  
  
> [!CAUTION]
>  Appel de **déplacer** lève une exception si le jeu d’enregistrements ne comporte pas d’enregistrement. Pour déterminer si des enregistrements de l’ensemble d’enregistrements, appelez [IsBOF](#isbof) et [IsEOF](#iseof).  
  
> [!NOTE]
>  Si vous avez atteint le début ou la fin de l’objet recordset ( `IsBOF` ou `IsEOF` retourne différente de zéro), l’appel un **déplacer** fonction lève éventuellement une `CDBException`. Par exemple, si `IsEOF` retourne différente de zéro et `IsBOF` n’est pas, puis `MoveNext` lève une exception, mais `MovePrev` ne seront pas.  
  
> [!NOTE]
>  Si vous appelez **déplacer** pendant que l’enregistrement actif est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Pour plus d’informations, consultez la fonction d’API ODBC **SQLExtendedFetch** dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>  CRecordset::MoveFirst  
 Sélectionne le premier enregistrement dans le premier ensemble de lignes de l’enregistrement actif.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Notes  
 Indépendamment de si l’extraction de lignes en bloc a été implémenté, ce sera toujours le premier enregistrement dans le jeu d’enregistrements.  
  
 Vous n’avez pas à appeler **MoveFirst** immédiatement après l’ouverture de l’ensemble d’enregistrements. À ce stade, le premier enregistrement (le cas échéant) est automatiquement l’enregistrement actif.  
  
> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.  
  
> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez le [IsDeleted](#isdeleted) fonction membre pour plus d’informations.  
  
> [!CAUTION]
>  L’appel de la **déplacer** fonctions lève une exception si le jeu d’enregistrements ne comporte pas d’enregistrement. Pour déterminer si des enregistrements de l’ensemble d’enregistrements, appelez `IsBOF` et `IsEOF`.  
  
> [!NOTE]
>  Si vous appelez une de le **déplacer** fonctions pendant que l’enregistrement actif est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="movelast"></a>  CRecordset::MoveLast  
 Sélectionne le premier enregistrement dans le dernier ensemble de lignes de l’enregistrement actif.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Notes  
 Si vous n’avez pas implémenté l’extraction de lignes en bloc, le jeu d’enregistrements a une taille d’ensemble de lignes de 1, si bien que `MoveLast` simplement se déplace vers le dernier enregistrement dans le jeu d’enregistrements.  
  
> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.  
  
> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez le [IsDeleted](#isdeleted) fonction membre pour plus d’informations.  
  
> [!CAUTION]
>  L’appel de la **déplacer** fonctions lève une exception si le jeu d’enregistrements ne comporte pas d’enregistrement. Pour déterminer si des enregistrements de l’ensemble d’enregistrements, appelez `IsBOF` et `IsEOF`.  
  
> [!NOTE]
>  Si vous appelez une de le **déplacer** fonctions pendant que l’enregistrement actif est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="movenext"></a>  CRecordset::MoveNext  
 Sélectionne le premier enregistrement dans l’ensemble de lignes suivant l’enregistrement actif.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Notes  
 Si vous n’avez pas implémenté l’extraction de lignes en bloc, le jeu d’enregistrements a une taille d’ensemble de lignes de 1, si bien que `MoveNext` simplement se déplace vers l’enregistrement suivant.  
  
> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez le [IsDeleted](#isdeleted) fonction membre pour plus d’informations.  
  
> [!CAUTION]
>  L’appel de la **déplacer** fonctions lève une exception si le jeu d’enregistrements ne comporte pas d’enregistrement. Pour déterminer si des enregistrements de l’ensemble d’enregistrements, appelez `IsBOF` et `IsEOF`.  
  
> [!NOTE]
>  Il est également recommandé d’appeler `IsEOF` avant d’appeler `MoveNext`. Par exemple, si vous avez atteint après la fin de l’objet recordset, `IsEOF` retournera différente de zéro ; un appel ultérieur à `MoveNext` lève une exception.  
  
> [!NOTE]
>  Si vous appelez une de le **déplacer** fonctions pendant que l’enregistrement actif est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="moveprev"></a>  CRecordset::MovePrev  
 Sélectionne le premier enregistrement dans l’ensemble de lignes précédent de l’enregistrement actif.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Notes  
 Si vous n’avez pas implémenté l’extraction de lignes en bloc, le jeu d’enregistrements a une taille d’ensemble de lignes de 1, si bien que `MovePrev` simplement se déplace vers l’enregistrement précédent.  
  
> [!NOTE]
>  Cette fonction membre n’est pas valide pour les recordsets avant uniquement.  
  
> [!NOTE]
>  Lorsque vous parcourez un jeu d’enregistrements, vous ne pouvez pas ignorer les enregistrements supprimés. Consultez le [IsDeleted](#isdeleted) fonction membre pour plus d’informations.  
  
> [!CAUTION]
>  L’appel de la **déplacer** fonctions lève une exception si le jeu d’enregistrements ne comporte pas d’enregistrement. Pour déterminer si des enregistrements de l’ensemble d’enregistrements, appelez `IsBOF` et `IsEOF`.  
  
> [!NOTE]
>  Il est également recommandé d’appeler `IsBOF` avant d’appeler `MovePrev`. Par exemple, si vous avez atteint le début de l’objet recordset, `IsBOF` retournera différente de zéro ; un appel ultérieur à `MovePrev` lève une exception.  
  
> [!NOTE]
>  Si vous appelez une de le **déplacer** fonctions pendant que l’enregistrement actif est mis à jour ou ajouté, les mises à jour sont perdues sans avertissement.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [IsBOF](#isbof).  
  
##  <a name="onsetoptions"></a>  CRecordset::OnSetOptions  
 Appelé pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Paramètres  
 `hstmt`  
 Le **HSTMT** de l’instruction ODBC dont les options doivent être définies.  
  
### <a name="remarks"></a>Notes  
 Appelez `OnSetOptions` pour définir les options (utilisées sur la sélection) pour l’instruction ODBC spécifiée. L’infrastructure appelle cette fonction membre pour définir les options initiales pour le jeu d’enregistrements. `OnSetOptions` Détermine la prise en charge de la source de données pour les curseurs permettant le défilement et d’accès concurrentiel au curseur et définit les options du jeu d’enregistrements en conséquence. (Alors que `OnSetOptions` est utilisé pour les opérations de sélection, `OnSetUpdateOptions` est utilisé pour les opérations de mise à jour.)  
  
 Substituer `OnSetOptions` pour définir les options spécifiques au pilote ou à la source de données. Par exemple, si votre source de données prend en charge l’ouverture d’un accès exclusif, vous pouvez substituer `OnSetOptions` pour tirer parti de cette capacité.  
  
 Pour plus d’informations sur les curseurs, consultez l’article [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="onsetupdateoptions"></a>  CRecordset::OnSetUpdateOptions  
 Appelé pour définir les options (utilisées sur la mise à jour) pour l’instruction ODBC spécifiée.  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Paramètres  
 `hstmt`  
 Le **HSTMT** de l’instruction ODBC dont les options doivent être définies.  
  
### <a name="remarks"></a>Notes  
 Appelez `OnSetUpdateOptions` pour définir les options (utilisées sur la mise à jour) pour l’instruction ODBC spécifiée. L’infrastructure appelle cette fonction membre après avoir créé un HSTMT pour mettre à jour des enregistrements dans un jeu d’enregistrements. (Alors que `OnSetOptions` est utilisé pour les opérations de sélection, `OnSetUpdateOptions` est utilisé pour les opérations de mise à jour.) `OnSetUpdateOptions` détermine la prise en charge de la source de données pour les curseurs permettant le défilement et d’accès concurrentiel au curseur et définit les options du jeu d’enregistrements en conséquence.  
  
 Substituer `OnSetUpdateOptions` pour définir les options d’une instruction ODBC avant que cette instruction est utilisée pour accéder à une base de données.  
  
 Pour plus d’informations sur les curseurs, consultez l’article [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="open"></a>  CRecordset::Open  
 Ouvre le recordset par la récupération de la table ou l’exécution de la requête représentant le jeu d’enregistrements.  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>Paramètres  
 `nOpenType`  
 Acceptez la valeur par défaut, **AFX_DB_USE_DEFAULT_TYPE**, ou utilisez une de ces valeurs dans le **enum OpenType**:  
  
- **CRecordset::dynaset** un jeu d’enregistrements avec défilement bidirectionnel. L’appartenance et l’ordre des enregistrements sont déterminées lors de l’ensemble d’enregistrements est ouvert, mais les modifications apportées par d’autres utilisateurs aux valeurs de données sont visibles après une opération d’extraction. Feuilles de réponse dynamiques sont également appelés curseurs pilotés par les jeux d’enregistrements.  
  
- **CRecordset::snapshot** un jeu d’enregistrements statique avec défilement bidirectionnel. L’appartenance et l’ordre des enregistrements sont déterminées lors de l’ensemble d’enregistrements est ouvert ; les valeurs de données sont déterminés lorsque les enregistrements sont extraits. Modifications apportées par d’autres utilisateurs ne sont pas visibles jusqu'à ce que le jeu d’enregistrements est fermé, puis rouvert.  
  
- **CRecordset::dynamic** un jeu d’enregistrements avec défilement bidirectionnel. Modifications apportées par d’autres utilisateurs aux valeurs d’appartenance, de classement et de données sont visibles après une opération d’extraction. Notez que de nombreux pilotes ODBC ne prennent pas en charge ce type de jeu d’enregistrements.  
  
- **CRecordset::forwardOnly** un jeu d’enregistrements en lecture seule avec défilement vers l’avant uniquement.  
  
     Pour `CRecordset`, la valeur par défaut est **CRecordset::snapshot**. Le mécanisme de valeur par défaut permet les Assistants Visual C++ interagir avec les deux ODBC `CRecordset` et DAO `CDaoRecordset`, qui ont des valeurs par défaut différentes.  
  
 Pour plus d’informations sur ces types de jeu d’enregistrements, consultez l’article [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations, consultez l’article « À l’aide d’et défilement curseurs de bloc » dans le Kit de développement logiciel Windows.  
  
> [!CAUTION]
>  Si le type demandé n’est pas pris en charge, le framework lève une exception.  
  
 `lpszSQL`  
 Un pointeur de chaîne contenant l’une des opérations suivantes :  
  
-   A **NULL** pointeur.  
  
-   Nom d'une table.  
  
-   SQL **sélectionnez** instruction (éventuellement avec un SQL **où** ou **ORDER BY** clause).  
  
-   A **appeler** instruction en spécifiant le nom d’une requête prédéfinie (procédure stockée). Veillez à ce que vous n’insérez pas d’espace blanc entre les accolades et le **appeler** (mot clé).  
  
 Pour plus d’informations sur cette chaîne, consultez la table et la description du rôle de ClassWizard sous la section Notes.  
  
> [!NOTE]
>  L’ordre des colonnes dans votre jeu de résultats doit correspondre à l’ordre de la RFX ou d’appels de fonction de RFX en bloc dans votre [DoFieldExchange](#dofieldexchange) ou [DoBulkFieldExchange](#dobulkfieldexchange) remplacement de la fonction.  
  
 `dwOptions`  
 Masque de bits qui peut spécifier une combinaison des valeurs répertoriées ci-dessous. Certains d'entre eux sont mutuellement exclusifs. La valeur par défaut est **aucun**.  
  
- **CRecordset::none** aucun jeu d’options. Cette valeur de paramètre est incompatible avec toutes les autres valeurs. Par défaut, le jeu d’enregistrements peut être mis à jour avec [modifier](#edit) ou [supprimer](#delete) et permet l’ajout de nouveaux enregistrements avec [AddNew](#addnew). Mise à jour dépend de la source de données, ainsi que dans le `nOpenType` option que vous spécifiez. Optimisation pour les compléments en bloc n’est pas disponible. L’extraction de lignes en bloc ne sera pas implémentée. Enregistrements supprimés ne seront pas ignorés lors de la navigation de jeu d’enregistrements. Les signets ne sont pas disponibles. Vérification du champ dirty automatique est implémentée.  
  
- **CRecordset::appendOnly** n’autorisent pas **modifier** ou **supprimer** sur l’ensemble d’enregistrements. Autoriser `AddNew` uniquement. Cette option s’excluent mutuellement avec **CRecordset::readOnly**.  
  
- **CRecordset::readOnly** ouvrir l’objet recordset en lecture seule. Cette option s’excluent mutuellement avec **CRecordset::appendOnly**.  
  
- **CRecordset::optimizeBulkAdd** utiliser une instruction SQL préparée pour optimiser l’ajout de plusieurs enregistrements à la fois. S’applique uniquement si vous n’utilisez pas la fonction d’API ODBC **SQLSetPos** pour mettre à jour le jeu d’enregistrements. La première mise à jour détermine quels champs sont marqués modifiés. Cette option s’excluent mutuellement avec `CRecordset::useMultiRowFetch`.  
  
- `CRecordset::useMultiRowFetch` Implémenter l’extraction de lignes en bloc pour autoriser plusieurs lignes doivent être extraites par une opération d’extraction unique. Il s’agit d’une fonctionnalité avancée conçue pour améliorer les performances. Toutefois, RFX en bloc n’est pas pris en charge par ClassWizard. Cette option s’excluent mutuellement avec **CRecordset::optimizeBulkAdd**. Notez que si vous spécifiez `CRecordset::useMultiRowFetch`, puis l’option **CRecordset::noDirtyFieldCheck** sera activé automatiquement (mécanisme de double tampon sera pas disponible) ; sur les recordsets avant uniquement, l’option  **CRecordset::useExtendedFetch** sera activé automatiquement. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
- **CRecordset::skipDeletedRecords** ignorer tous les enregistrements supprimés lors de la navigation dans le jeu d’enregistrements. Cela ralentit les performances dans certaines extractions relatives. Cette option n’est pas valide sur les recordsets avant uniquement. Si vous appelez [déplacer](#move) avec la `nRows` paramètre la valeur 0 et le **CRecordset::skipDeletedRecords** option set, **déplacer** vérifie. Notez que **CRecordset::skipDeletedRecords** est similaire à *livraison du pilote*, ce qui signifie que les lignes supprimées est supprimées de l’ensemble d’enregistrements. Toutefois, si votre pilote packs d’enregistrements, puis il ignore uniquement les enregistrements que vous supprimez ; il ignore pas les enregistrements supprimés par d’autres utilisateurs, alors que le jeu d’enregistrements est ouvert. **CRecordset::skipDeletedRecords** va ignorer les lignes supprimées par d’autres utilisateurs.  
  
- **CRecordset::useBookmarks** peut utiliser des signets sur l’ensemble d’enregistrements, si pris en charge. Signets ralentir la récupération des données mais améliorent les performances pour la navigation dans les données. Non valide sur les recordsets avant uniquement. Pour plus d’informations, consultez l’article [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
- **CRecordset::noDirtyFieldCheck** Désactiver champ dirty automatique vérification (double mise en mémoire tampon). Cela permet d’améliorer les performances ; Toutefois, vous devez marquer manuellement les champs comme erronée en appelant le `SetFieldDirty` et `SetFieldNull` fonctions membres. Notez ce mécanisme de double tampon dans la classe `CRecordset` est semblable au mécanisme de double tampon dans la classe `CDaoRecordset`. Toutefois, dans `CRecordset`, vous ne pouvez pas activer le mécanisme de double tampon sur les champs individuels ; vous activez pour tous les champs ou le désactiver pour tous les champs. Notez que si vous spécifiez l’option `CRecordset::useMultiRowFetch`, puis **CRecordset::noDirtyFieldCheck** sera activé automatiquement ; Toutefois, `SetFieldDirty` et `SetFieldNull` ne peut pas être utilisé sur les jeux d’enregistrements qui implémentent l’extraction de lignes en bloc.  
  
- **CRecordset::executeDirect** n’utilisez pas une instruction SQL préparée. Pour améliorer les performances, spécifiez cette option si le **Requery** fonction membre ne sera jamais appelée.  
  
- **CRecordset::useExtendedFetch** implémentez **SQLExtendedFetch** au lieu de **SQLFetch**. Il est conçu pour l’implémentation de l’extraction de lignes en bloc sur les recordsets avant uniquement. Si vous spécifiez l’option `CRecordset::useMultiRowFetch` sur un recordset avant uniquement, puis **CRecordset::useExtendedFetch** sera activé automatiquement.  
  
- **CRecordset::userAllocMultiRowBuffers** l’utilisateur sera allouer des tampons de stockage pour les données. Utilisez cette option conjointement avec `CRecordset::useMultiRowFetch` si vous souhaitez allouer votre propre stockage ; sinon, le framework automatiquement alloue le stockage nécessaire. Pour plus d’informations, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Notez que la spécification **CRecordset::userAllocMultiRowBuffers** sans spécifier `CRecordset::useMultiRowFetch` entraîne un échec d’assertion.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la `CRecordset` objet a été correctement ouvert ; sinon, 0 si [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (s’il est appelé) renvoie la valeur 0.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler cette fonction membre pour exécuter la requête définie par l’objet recordset. Avant d’appeler **ouvrir**, vous devez construire l’objet recordset.  
  
 Connexion du jeu d’enregistrements à la source de données dépend de la façon dont vous construisez le recordset avant d’appeler **ouvrir**. Si vous passez un [CDatabase](../../mfc/reference/cdatabase-class.md) de l’objet au constructeur de jeu d’enregistrements qui n’a pas été connecté à la source de données, cette fonction membre utilise [GetDefaultConnect](#getdefaultconnect) pour essayer d’ouvrir l’objet de base de données. Si vous passez **NULL** au constructeur de jeu d’enregistrements, le constructeur construit un `CDatabase` objet, et **ouvrir** tente de se connecter à l’objet de base de données. Pour plus d’informations sur la fermeture de l’ensemble d’enregistrements et de la connexion dans ces circonstances différentes, consultez [fermer](#close).  
  
> [!NOTE]
>  Accès à une source de données via un `CRecordset` objet est toujours partagé. Contrairement à la `CDaoRecordset` (classe), vous ne pouvez pas utiliser un `CRecordset` objet pour ouvrir une source de données avec un accès exclusif.  
  
 Lorsque vous appelez **ouvrir**, une requête, généralement une SQL **sélectionnez** instruction, sélectionne les enregistrements selon des critères indiqués dans le tableau suivant.  
  
|Valeur du paramètre lpszSQL|Enregistrements sélectionnés sont déterminés par|Exemple|  
|------------------------------------|----------------------------------------|-------------|  
|**NULL**|La chaîne retournée par `GetDefaultSQL`.||  
|Nom de la table SQL|Toutes les colonnes de la liste de tables dans `DoFieldExchange` ou `DoBulkFieldExchange`.|`"Customer"`|  
|Nom de la requête prédéfinie (procédure stockée)|Les colonnes de que la requête est définie pour retourner.|`"{call OverDueAccts}"`|  
|**Sélectionnez** -liste des colonnes **FROM** liste de tables|Les colonnes spécifiées dans les tables spécifiées.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  Veillez à ce que vous n’insérez pas d’espace blanc supplémentaire dans la chaîne SQL. Par exemple, si vous insérez un espace blanc entre les accolades et le **appeler** (mot clé), MFC interprète la chaîne SQL comme nom de table et les incorporer dans une **sélectionnez** instruction, ce qui entraîne un exception levée. De même, si votre requête prédéfini utilise un paramètre de sortie, n’insérez pas d’espace entre l’accolade et '' symbole. Enfin, vous ne devez pas insérer un espace blanc avant l’accolade dans un **appeler** instruction ou avant le **sélectionnez** mot clé dans un **sélectionnez** instruction.  
  
 La procédure habituelle consiste à passer **NULL** à **ouvrir**; dans ce cas, **ouvrir** appelle [GetDefaultSQL](#getdefaultsql). Si vous utilisez une dérivée `CRecordset` (classe), **GetDefaultSQL** donne les noms de table spécifié dans ClassWizard. Vous pouvez spécifier à la place d’autres informations dans le `lpszSQL` paramètre.  
  
 Tout ce que vous passez, **ouvrir** construit une chaîne SQL finale pour la requête (la chaîne peut avoir SQL **où** et **ORDER BY** clauses ajouté à la `lpszSQL` chaîne que vous passé), puis exécute la requête. Vous pouvez examiner la chaîne construite en appelant [GetSQL](#getsql) après avoir appelé **ouvrir**. Pour des détails supplémentaires sur la façon dont le jeu d’enregistrements construit une instruction SQL et sélectionne les enregistrements, consultez l’article [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
 Données membres de champ de la classe de recordset sont liés aux colonnes de données sélectionnées. Si tous les enregistrements sont retournés, le premier enregistrement devient l’enregistrement actif.  
  
 Si vous souhaitez définir des options pour l’ensemble d’enregistrements, tel qu’un filtre ou un tri, spécifiez ces après avoir construit l’objet recordset, mais avant d’appeler **ouvrir**. Si vous souhaitez actualiser les enregistrements dans le jeu d’enregistrements après le jeu d’enregistrements est déjà ouvert, appelez [Requery](#requery).  
  
 Pour plus d’informations, y compris des exemples supplémentaires, consultez les articles [Recordset (ODBC)](../../data/odbc/recordset-odbc.md), [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), et [Recordset : création et fermeture Jeux d’enregistrements (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
### <a name="example"></a>Exemple  
 Les exemples de code suivants montrent différentes formes de la **ouvrir** appeler.  
  
 [!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>  CRecordset::RefreshRowset  
 Met à jour des données et l’état d’une ligne dans l’ensemble de lignes en cours.  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Paramètres  
 `wRow`  
 La position de base un d’une ligne dans l’ensemble de lignes en cours. Cette valeur peut être comprise entre zéro et la taille de l’ensemble de lignes.  
  
 `wLockType`  
 Une valeur indiquant le mode de verrouillage de la ligne après que qu’il a été actualisé. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Si vous passez une valeur de zéro pour `wRow`, puis chaque ligne dans l’ensemble de lignes est actualisée.  
  
 Pour utiliser `RefreshRowset`, vous devez avoir implémenté l’extraction de lignes en bloc en spécifiant le **CRecordset::useMulitRowFetch** option dans le [ouvrir](#open) fonction membre.  
  
 `RefreshRowset` appelle la fonction d’API ODBC **SQLSetPos**. Le `wLockType` paramètre spécifie l’état de la ligne après **SQLSetPos** a été exécutée. Le tableau suivant décrit les valeurs possibles pour `wLockType`.  
  
|wLockType|Description|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE` (la valeur par défaut)|La source de données ou de pilote garantit que la ligne est dans le même état verrouillé ou déverrouillé, telle qu’elle était avant `RefreshRowset` a été appelée.|  
|`SQL_LOCK_EXCLUSIVE`|La source de données ou de pilote verrouille la ligne exclusivement. Toutes les données sources ne prennent en charge ce type de verrou.|  
|`SQL_LOCK_UNLOCK`|La source de données ou de pilote déverrouille la ligne. Toutes les données sources ne prennent en charge ce type de verrou.|  
  
 Pour plus d’informations sur **SQLSetPos**, consultez le Kit de développement logiciel Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="requery"></a>  CRecordset::Requery  
 Reconstruit (actualisation) un jeu d’enregistrements.  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le jeu d’enregistrements a été régénérée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si tous les enregistrements sont retournés, le premier enregistrement devient l’enregistrement actif.  
  
 Dans l’ordre du jeu d’enregistrements afin de refléter les ajouts et suppressions que vous ou autres utilisateurs effectuent dans la source de données, vous devez reconstruire l’ensemble d’enregistrements en appelant **Requery**. Si le recordset est une feuille de réponse dynamique, il reflète automatiquement les mises à jour que vous ou autres utilisateurs apporter à ses enregistrements existants (mais pas les ajouts). Si le jeu d’enregistrements est un instantané, vous devez appeler **Requery** afin de refléter les modifications apportées par d’autres utilisateurs, ainsi que les ajouts et les suppressions.  
  
 Pour une feuille de réponse dynamique ou un instantané, appelez **Requery** n’importe quel moment vous souhaitez reconstruire le jeu d’enregistrements à l’aide d’un nouveau filtre ou de tri ou de nouvelles valeurs de paramètre. Définissez la nouvelle propriété à filtrer ou trier en assignant de nouvelles valeurs à **m_strFilter** et `m_strSort` avant d’appeler **Requery**. Définir de nouveaux paramètres en assignant de nouvelles valeurs aux membres de données de paramètre avant d’appeler **Requery**. Si les chaînes de filtre et de tri sont identiques, vous pouvez réutiliser la requête, ce qui améliore les performances.  
  
 Si la tentative pour reconstruire le recordset échoue, le jeu d’enregistrements est fermé. Avant d’appeler **Requery**, vous pouvez déterminer si le jeu d’enregistrements peut être actualisé en appelant le `CanRestart` fonction membre. `CanRestart` ne garantit pas que **Requery** réussira.  
  
> [!CAUTION]
>  Appelez **Requery** uniquement après avoir appelé [ouvrir](#open).  
  
### <a name="example"></a>Exemple  
 Cet exemple reconstruit un jeu d’enregistrements pour appliquer un ordre de tri différent.  
  
 [!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>  CRecordset::SetAbsolutePosition  
 Positionne le jeu d’enregistrements sur l’enregistrement correspondant au numéro d’enregistrement spécifié.  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>Paramètres  
 `nRows`  
 Basé sur un position ordinale de l’enregistrement actif dans le jeu d’enregistrements.  
  
### <a name="remarks"></a>Notes  
 `SetAbsolutePosition` Déplace le pointeur d’enregistrement en cours en fonction de cette position ordinale.  
  
> [!NOTE]
>  Cette fonction membre n’est pas valide sur les recordsets avant uniquement.  
  
 Pour les jeux d’enregistrements ODBC, un paramètre de position absolue 1 fait référence au premier enregistrement dans le jeu d’enregistrements ; la valeur 0 fait référence à la position (BOF) de début du fichier.  
  
 Vous pouvez également passer des valeurs négatives pour `SetAbsolutePosition`. Dans ce cas la position du jeu d’enregistrements est évaluée à partir de la fin de l’ensemble d’enregistrements. Par exemple, `SetAbsolutePosition( -1 )` déplace le pointeur d’enregistrement actif avec le dernier enregistrement dans le jeu d’enregistrements.  
  
> [!NOTE]
>  Position absolue n’est pas destinée à être utilisé comme un numéro d’enregistrement de substitution. Les signets sont toujours recommandé de conserver et revenir à une position donnée, car une modification de position d’un enregistrement lorsque les enregistrements précédents sont supprimés. En outre, vous ne peut pas être sûr qu’un enregistrement donné aura la même position absolue si le jeu d’enregistrements est recréé, car l’ordre des enregistrements individuels dans un jeu d’enregistrements n’est pas garantie, sauf si elle est créée avec une instruction SQL à l’aide d’un **ORDER BY** clause.  
  
 Pour plus d’informations sur la navigation de jeu d’enregistrements et les signets, consultez les articles [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) et [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="setbookmark"></a>  CRecordset::SetBookmark  
 Positionne le jeu d’enregistrements sur l’enregistrement qui contient le signet spécifié.  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Paramètres  
 `varBookmark`  
 Une référence à un [CDBVariant](../../mfc/reference/cdbvariant-class.md) objet contenant la valeur du signet pour un enregistrement spécifique.  
  
### <a name="remarks"></a>Notes  
 Pour déterminer si les signets sont pris en charge sur l’ensemble d’enregistrements, appelez [CanBookmark](#canbookmark). Pour rendre les signets disponibles si elles sont prises en charge, vous devez définir le **CRecordset::useBookmarks** option dans le `dwOptions` paramètre de la [ouvrir](#open) fonction membre.  
  
> [!NOTE]
>  Si les signets sont pris en charge ou non disponible, l’appel `SetBookmark` entraîne une exception est levée. Les signets ne sont pas pris en charge sur les recordsets avant uniquement.  
  
 Pour tout d’abord récupérer le signet de l’enregistrement actif, appelez [GetBookmark](#getbookmark), qui enregistre la valeur du signet à un `CDBVariant` objet. Une version ultérieure, vous pouvez revenir à cet enregistrement en appelant `SetBookmark` à l’aide de la valeur du signet enregistré.  
  
> [!NOTE]
>  Après certaines opérations de jeu d’enregistrements, vous devez vérifier la persistance de signet avant d’appeler `SetBookmark`. Par exemple, si vous récupérez un signet avec `GetBookmark` , puis appelez **Requery**, le signet peut ne plus être valide. Appelez [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) pour vérifier si vous pouvez appeler en toute sécurité `SetBookmark`.  
  
 Pour plus d’informations sur les signets et de navigation du jeu d’enregistrements, consultez les articles [Recordset : signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) et [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="setfielddirty"></a>  CRecordset::SetFieldDirty  
 Marque un membre de données de champ de l’objet recordset modifié ou inchangé.  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `pv`  
 Contient l’adresse d’un membre de données de champ dans le jeu d’enregistrements ou **NULL**. Si **NULL**, tous les membres de données de champ dans le jeu d’enregistrements marqués. (C++ **NULL** n’est pas le même que la valeur Null dans la terminologie de base de données, ce qui signifie « n’avoir aucune valeur. »)  
  
 `bDirty`  
 **TRUE** si le membre de données de champ doit être marqué comme « dirty » (modifiés). Dans le cas contraire **FALSE** si le membre de données de champ doit être marqué comme « nettoyer » (non modifié).  
  
### <a name="remarks"></a>Notes  
 Le marquage des champs restent inchangés ainsi le champ n’est pas mise à jour entraîne moins de trafic SQL.  
  
> [!NOTE]
>  Cette fonction membre n’est pas applicable sur les jeux d’enregistrements qui est à l’aide de l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, puis `SetFieldDirty` entraîne un échec d’assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Les marques de framework modifié des données membres de champ pour vous assurer qu’ils seront écrits à l’enregistrement sur la source de données par le mécanisme de record field exchange (RFX). Généralement la modification de la valeur d’un champ définit le champ modifié automatiquement, donc vous devrez rarement appeler `SetFieldDirty` vous-même, mais vous pouvez parfois souhaiter vous assurer que les colonnes seront explicitement mis à jour ou insérées, quelle que soit la valeur se trouve dans les données de champ membre.  
  
> [!CAUTION]
>  Appelez cette fonction membre uniquement après avoir appelé [modifier](#edit) ou [AddNew](#addnew).  
  
 À l’aide de **NULL** pour le premier argument de la fonction appliquera la fonction uniquement à **outputColumn** ne champs pas **param** champs. Par exemple, l’appel  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 définit uniquement **outputColumn** champs **NULL**; **param** champs ne seront pas affectées.  
  
 Pour travailler sur **param** champs, vous devez fournir l’adresse réelle de la personne **param** vous souhaitez travailler, telles que :  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Cela signifie que vous ne pouvez pas définir tous les **param** champs **NULL**, comme vous pouvez le faire avec **outputColumn** champs.  
  
##  <a name="setfieldnull"></a>  CRecordset::SetFieldNull  
 Marque un membre de données de champ de l’objet recordset comme Null (en particulier n’avoir aucune valeur) ou non Null.  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `pv`  
 Contient l’adresse d’un membre de données de champ dans le jeu d’enregistrements ou **NULL**. Si **NULL**, tous les membres de données de champ dans le jeu d’enregistrements marqués. (C++ **NULL** n’est pas le même que la valeur Null dans la terminologie de base de données, ce qui signifie « n’avoir aucune valeur. »)  
  
 `bNull`  
 Différent de zéro si le membre de données de champ doit être marquée comme en ne comportant aucun valeur (Null). 0 dans le cas contraire, si le membre de données de champ doit être marquée comme étant non Null.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous ajoutez un nouvel enregistrement à un jeu d’enregistrements, tous les membres de données de champ sont initialement définies sur une valeur Null et marqués comme « dirty » (modifiés). Lorsque vous récupérez un enregistrement à partir d’une source de données, ses colonnes déjà ont des valeurs ou sont Null.  
  
> [!NOTE]
>  N’appelez pas cette fonction membre sur les jeux d’enregistrements qui est à l’aide de l’extraction de lignes en bloc. Si vous avez implémenté l’extraction de lignes en bloc, l’appel `SetFieldNull` entraîne l’échec de l’assertion. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Si vous voulez désigner un champ de l’enregistrement actuel comme n’ayant ne pas une valeur, appelez `SetFieldNull` avec `bNull` la valeur **TRUE** à marquer comme Null. Si un champ a été marqué Null et que vous voulez lui attribuer une valeur, il vous suffit de définir sa nouvelle valeur. Vous n’êtes pas obligé de supprimer l’indicateur de valeur Null avec `SetFieldNull`. Pour déterminer si le champ peut être Null, appelez `IsFieldNullable`.  
  
> [!CAUTION]
>  Appelez cette fonction membre uniquement après avoir appelé [modifier](#edit) ou [AddNew](#addnew).  
  
 À l’aide de **NULL** pour le premier argument de la fonction appliquera la fonction uniquement à **outputColumn** ne champs pas **param** champs. Par exemple, l’appel  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 définit uniquement **outputColumn** champs **NULL**; **param** champs ne seront pas affectées.  
  
 Pour travailler sur **param** champs, vous devez fournir l’adresse réelle de la personne **param** vous souhaitez travailler, telles que :  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 Cela signifie que vous ne pouvez pas définir tous les **param** champs **NULL**, comme vous pouvez le faire avec **outputColumn** champs.  
  
> [!NOTE]
>  Lors de la définition des paramètres avec la valeur Null, un appel à `SetFieldNull` avant que le jeu d’enregistrements est ouvert entraîne une assertion. Dans ce cas, appelez [SetParamNull](#setparamnull).  
  
 `SetFieldNull` est implémenté via [DoFieldExchange](#dofieldexchange).  
  
##  <a name="setlockingmode"></a>  CRecordset::SetLockingMode  
 Définit le mode de verrouillage « optimiste » (la valeur par défaut) de verrouillage ou de verrouillage « pessimiste ». Détermine la façon dont les enregistrements sont verrouillés pour les mises à jour.  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>Paramètres  
 `nMode`  
 Contient l’une des valeurs suivantes à partir de la **enum LockMode**:  
  
- **optimiste** verrouillage optimiste verrouille l’enregistrement mis à jour uniquement lors de l’appel à **mise à jour**.  
  
- **pessimiste** verrouillage pessimiste verrouille l’enregistrement dès que **modifier** est appelée et les conserve verrouillé jusqu'à ce que le **mise à jour** fin de l’appel ou de vous déplacez vers un nouvel enregistrement.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre, si vous avez besoin de spécifier les deux stratégies de verrouillage des enregistrements à l’aide de l’ensemble d’enregistrements pour les mises à jour. Par défaut, le mode de verrouillage d’un objet recordset est **optimiste**. Vous pouvez remplacer cette plus prudent **pessimiste** la stratégie de verrouillage. Appelez `SetLockingMode` une fois que vous construisez et ouvrez l’objet recordset, mais avant d’appeler **modifier**.  
  
##  <a name="setparamnull"></a>  CRecordset::SetParamNull  
 Un paramètre d’indicateurs comme Null (en particulier n’avoir aucune valeur) ou non Null.  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de base zéro du paramètre.  
  
 `bNull`  
 Si **TRUE** (la valeur par défaut), le paramètre est marqué comme étant Null. Sinon, le paramètre est marqué comme non Null.  
  
### <a name="remarks"></a>Notes  
 Contrairement aux [SetFieldNull](#setfieldnull), vous pouvez appeler `SetParamNull` avant l’ouverture de l’ensemble d’enregistrements.  
  
 `SetParamNull` est généralement utilisé avec des requêtes prédéfinies (procédures stockées).  
  
##  <a name="setrowsetcursorposition"></a>  CRecordset::SetRowsetCursorPosition  
 Déplace le curseur d’une ligne dans l’ensemble de lignes en cours.  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Paramètres  
 `wRow`  
 La position de base un d’une ligne dans l’ensemble de lignes en cours. Cette valeur peut varier de 1 à la taille de l’ensemble de lignes.  
  
 `wLockType`  
 Valeur indiquant le mode de verrouillage de la ligne après que qu’il a été actualisé. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Lors de l’implémentation de l’extraction de lignes en bloc, les enregistrements sont récupérés en ensembles de lignes, où le premier enregistrement de l’ensemble de lignes lues est l’enregistrement actif. Pour activer un autre enregistrement dans l’ensemble de lignes, appelez `SetRowsetCursorPosition`. Par exemple, vous pouvez combiner `SetRowsetCursorPosition` avec la [GetFieldValue](#getfieldvalue) fonction membre pour récupérer dynamiquement les données à partir de n’importe quel enregistrement de votre recordset.  
  
 Pour utiliser `SetRowsetCursorPosition`, vous devez avoir implémenté l’extraction de lignes en bloc en spécifiant le `CRecordset::useMultiRowFetch` option de la `dwOptions` paramètre dans le [ouvrir](#open) fonction membre.  
  
 `SetRowsetCursorPosition` appelle la fonction d’API ODBC **SQLSetPos**. Le `wLockType` paramètre spécifie l’état de la ligne après **SQLSetPos** a été exécutée. Le tableau suivant décrit les valeurs possibles pour `wLockType`.  
  
|wLockType|Description|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE` (la valeur par défaut)|La source de données ou de pilote garantit que la ligne est dans le même état verrouillé ou déverrouillé, telle qu’elle était avant `SetRowsetCursorPosition` a été appelée.|  
|`SQL_LOCK_EXCLUSIVE`|La source de données ou de pilote verrouille la ligne exclusivement. Toutes les données sources ne prennent en charge ce type de verrou.|  
|`SQL_LOCK_UNLOCK`|La source de données ou de pilote déverrouille la ligne. Toutes les données sources ne prennent en charge ce type de verrou.|  
  
 Pour plus d’informations sur **SQLSetPos**, consultez le Kit de développement logiciel Windows. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="setrowsetsize"></a>  CRecordset::SetRowsetSize  
 Spécifie le nombre d’enregistrements que vous souhaitez récupérer lors d’une extraction.  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwNewRowsetSize*  
 Le nombre de lignes à récupérer durant une extraction donnée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre virtuelle Spécifie le nombre de lignes à extraire lors d’une seule extraction lors de l’utilisation de l’extraction de lignes en bloc. Pour implémenter l’extraction de lignes en bloc, vous devez définir le `CRecordset::useMultiRowFetch` option dans le `dwOptions` paramètre de la [ouvrir](#open) fonction membre.  
  
> [!NOTE]
>  Appel de `SetRowsetSize` sans l’implémenter en bloc l’extraction de lignes entraîne un échec d’assertion.  
  
 Appelez `SetRowsetSize` avant d’appeler **Open** de définir initialement la taille de l’ensemble de lignes du jeu d’enregistrements. La taille d’ensemble de lignes par défaut lors de l’implémentation de l’extraction de lignes en bloc est 25.  
  
> [!NOTE]
>  Soyez prudent lors de l’appel `SetRowsetSize`. Si vous affectez manuellement stockage pour les données (comme spécifié par le **CRecordset::userAllocMultiRowBuffers** option du paramètre dwOptions dans **ouvrir**), vous devez vérifier s’il faut réaffecter ces mémoires tampons de stockage après avoir appelé `SetRowsetSize`, mais avant d’effectuer toute opération de navigation du curseur.  
  
 Pour obtenir la valeur actuelle de la taille de l’ensemble de lignes, appelez [GetRowsetSize](#getrowsetsize).  
  
 Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="update"></a>  CRecordset::Update  
 Termine une `AddNew` ou **modifier** opération en enregistrant les données nouvelles ou modifiées sur la source de données.  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si un enregistrement a été correctement mis à jour ; sinon 0 si aucune colonne n’ont été modifiés. Si aucun enregistrement ont été mis à jour, ou si plus d’un enregistrement a été mis à jour, une exception est levée. Une exception est également levée pour toute autre défaillance sur la source de données.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre après un appel à la [AddNew](#addnew) ou [modifier](#edit) fonction membre. Cet appel est requis pour terminer la `AddNew` ou **modifier** opération.  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler **mise à jour**. Cela entraîne un échec d’assertion. Bien que classe `CRecordset` ne fournit pas de mécanisme de mise à jour en bloc des lignes de données, vous pouvez écrire vos propres fonctions à l’aide de la fonction d’API ODBC **SQLSetPos**. Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Les deux `AddNew` et **modifier** préparer un tampon d’édition dans lequel sont placées les données ajoutées ou modifiées pour l’enregistrement dans la source de données. **Mise à jour** enregistre les données. Seuls les champs marqués ou détecté comme étant modifiées sont mises à jour.  
  
 Si la source de données prend en charge les transactions, vous pouvez rendre le **mise à jour** appeler (et de son `AddNew` ou **modifier** appeler) dans le cadre d’une transaction. Pour plus d’informations sur les transactions, consultez l’article [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!CAUTION]
>  Si vous appelez **mise à jour** sans d’abord appeler `AddNew` ou **modifier**, **mise à jour** lève une `CDBException`. Si vous appelez `AddNew` ou **modifier**, vous devez appeler **mise à jour** avant d’appeler un **déplacer** opération ou avant de fermer le jeu d’enregistrements ou de la connexion de source de données. Dans le cas contraire, vos modifications sont perdues sans notification.  
  
 Pour plus d’informations sur la gestion des **mise à jour** échecs, consultez l’article [Recordset : modification des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’article [Transaction : exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDatabase (classe)](../../mfc/reference/cdatabase-class.md)   
 [CRecordView, classe](../../mfc/reference/crecordview-class.md)
