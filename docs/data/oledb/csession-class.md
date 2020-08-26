---
title: CSession, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
ms.openlocfilehash: 6858c26df5f5ee364717d089704117e650282278
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841101"
---
# <a name="csession-class"></a>CSession, classe

Représente une session d’accès à la base de données unique.

## <a name="syntax"></a>Syntaxe

```cpp
class CSession
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[Abandon](#abort)|Annule (termine) la transaction.|
|[Close](#close)|Ferme la session.|
|[Commiter](#commit)|Valide la transaction.|
|[GetTransactionInfo](#gettransactioninfo)|Retourne des informations concernant une transaction.|
|[Ouvrir](#open)|Ouvre une nouvelle session pour l’objet source de données.|
|[StartTransaction](#starttransaction)|Commence une nouvelle transaction pour cette session.|

## <a name="remarks"></a>Notes

Une ou plusieurs sessions peuvent être associées à chaque connexion de fournisseur (source de données), qui est représentée par un objet [CDataSource](../../data/oledb/cdatasource-class.md) . Pour créer un nouveau `CSession` pour un `CDataSource` , appelez [CSession :: Open](../../data/oledb/csession-open.md). Pour commencer une transaction de base de données, `CSession` fournit la `StartTransaction` méthode. Une fois qu’une transaction est démarrée, vous pouvez la valider à l’aide de la `Commit` méthode ou l’annuler à l’aide de la `Abort` méthode.

## <a name="csessionabort"></a><a name="abort"></a> CSession :: Abort

Met fin à la transaction.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Abort(BOID* pboidReason = NULL,
   BOOL bRetaining = FALSE,
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ITransaction :: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="csessionclose"></a><a name="close"></a> CSession :: Close

Ferme la session, qui a été ouverte par [CSession :: Open](../../data/oledb/csession-open.md).

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

### <a name="remarks"></a>Notes

Libère le `m_spOpenRowset` pointeur.

## <a name="csessioncommit"></a><a name="commit"></a> CSession :: Commit

Valide la transaction.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Commit(BOOL bRetaining = FALSE,
   DWORD grfTC = XACTTC_SYNC,
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ITransaction :: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ITransaction :: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)).

## <a name="csessiongettransactioninfo"></a><a name="gettransactioninfo"></a> CSession :: GetTransactionInfo

Retourne des informations concernant une transaction.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ITransaction :: GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ITransaction :: GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="csessionopen"></a><a name="open"></a> CSession :: Open

Ouvre une nouvelle session pour l’objet source de données.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Paramètres

*SD*<br/>
dans Source de données pour laquelle la session doit être ouverte.

*pPropSet*<br/>
dans Pointeur vers un tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) contenant des propriétés et des valeurs à définir. Consultez [jeux de propriétés et groupes de propriétés](/previous-versions/windows/desktop/ms713696(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows.

*ulPropSets*<br/>
dans Nombre de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) passées dans l’argument *pPropSet* .

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Vous devez ouvrir l’objet de source de données à l’aide de [CDataSource :: Open](../../data/oledb/cdatasource-open.md) avant de le passer à `CSession::Open` .

## <a name="csessionstarttransaction"></a><a name="starttransaction"></a> CSession :: StartTransaction

Commence une nouvelle transaction pour cette session.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ITransactionLocal :: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ITransactionLocal :: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[CatDB](../../overview/visual-cpp-samples.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
