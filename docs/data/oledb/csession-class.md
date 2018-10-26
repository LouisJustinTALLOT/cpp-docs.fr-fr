---
title: CSession, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
dev_langs:
- C++
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 920ad8c48846396741d0ee2feb01855bd3b927d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063781"
---
# <a name="csession-class"></a>CSession, classe

Représente une session d’accès de base de données unique.

## <a name="syntax"></a>Syntaxe

```cpp
class CSession
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Abort](#abort)|Annule (met fin à) la transaction.|
|[Fermer](#close)|Ferme la session.|
|[Validation](#commit)|valide la transaction.|
|[GetTransactionInfo](#gettransactioninfo)|Retourne des informations concernant une transaction.|
|[Ouvrir](#open)|Ouvre une nouvelle session pour l’objet de source de données.|
|[StartTransaction](#starttransaction)|Commence une nouvelle transaction pour cette session.|

## <a name="remarks"></a>Notes

Une ou plusieurs sessions peuvent être associée à chaque connexion du fournisseur (source de données), qui est représentée par un [CDataSource](../../data/oledb/cdatasource-class.md) objet. Pour créer un nouveau `CSession` pour un `CDataSource`, appelez [CSession::Open](../../data/oledb/csession-open.md). Pour commencer une transaction de base de données, `CSession` fournit le `StartTransaction` (méthode). Une fois qu’une transaction est démarrée, vous pouvez valider à l’aide de la `Commit` (méthode), ou sur Annuler à l’aide de la `Abort` (méthode).

## <a name="abort"></a> CSession::Abort

Met fin à la transaction.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Abort(BOID* pboidReason = NULL, 
   BOOL bRetaining = FALSE, 
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ITransaction::Abort](/previous-versions/windows/desktop/ms709833) dans le *de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="close"></a> CSession::Close

Ferme la session, ce qui a été ouvert par [CSession::Open](../../data/oledb/csession-open.md).

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

### <a name="remarks"></a>Notes

Versions le `m_spOpenRowset` pointeur.

## <a name="commit"></a> CSession::Commit

valide la transaction.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Commit(BOOL bRetaining = FALSE, 
   DWORD grfTC = XACTTC_SYNC, 
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ITransaction::Commit](/previous-versions/windows/desktop/ms713008) dans le *de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ITransaction::Commit](/previous-versions/windows/desktop/ms713008).

## <a name="gettransactioninfo"></a> CSession::GetTransactionInfo

Retourne des informations concernant une transaction.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975) dans le *de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975) dans le *de référence du programmeur OLE DB*.

## <a name="open"></a> CSession::Open

Ouvre une nouvelle session pour l’objet de source de données.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Paramètres

*service d’annuaire*<br/>
[in] La source de données pour laquelle la session doit être ouvert.

*pPropSet*<br/>
[in] Un pointeur vers un tableau de [DBPROPSET](/previous-versions/windows/desktop/ms714367) structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](/previous-versions/windows/desktop/ms713696) dans le *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.

*ulPropSets*<br/>
[in] Le nombre de [DBPROPSET](/previous-versions/windows/desktop/ms714367) structures passées dans le *pPropSet* argument.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous devez ouvrir l’objet de source de données à l’aide [CDataSource::Open](../../data/oledb/cdatasource-open.md) avant leur transmission à `CSession::Open`.

## <a name="starttransaction"></a> CSession::StartTransaction

Commence une nouvelle transaction pour cette session.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786) dans le *de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786) dans le *de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[CatDB](../../visual-cpp-samples.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)