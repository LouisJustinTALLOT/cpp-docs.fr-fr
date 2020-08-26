---
title: IOpenRowsetImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: a3c94c75db21218aae1205bf9c5c379ab772a7f8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843714"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl, classe

Fournit l’implémentation pour l' `IOpenRowset` interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Paramètres

*SessionClass*<br/>
Votre classe, dérivée de `IOpenRowsetImpl` .

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[CreateRowset](#createrowset)|Crée un objet d’ensemble de lignes. Non appelé directement par l’utilisateur.|
|[OpenRowset](#openrowset)|Ouvre et retourne un ensemble de lignes qui comprend toutes les lignes d’une table ou d’un index de base unique. (Pas dans ATLDB. Manutention|

## <a name="remarks"></a>Notes

L’interface [IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85)) est obligatoire pour un objet de session. Elle ouvre et retourne un ensemble de lignes qui comprend toutes les lignes d’une table ou d’un index de base unique.

## <a name="iopenrowsetimplcreaterowset"></a><a name="createrowset"></a> Iopenrowsetimpl, :: CreateRowset

Crée un objet d’ensemble de lignes. Non appelé directement par l’utilisateur. Consultez [IOpenRowset :: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) dans le *Guide de référence du programmeur OLE DB.*

### <a name="syntax"></a>Syntaxe

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Paramètres

*RowsetClass*<br/>
Membre de classe de modèle qui représente la classe d’ensemble de lignes de l’utilisateur. Généralement généré par l’Assistant.

*pRowsetObj*<br/>
à Pointeur vers un objet d’ensemble de lignes. En général, ce paramètre n’est pas utilisé, mais il peut être utilisé si vous devez effectuer davantage de travail sur l’ensemble de lignes avant de le passer à un objet COM. La durée de vie de *pRowsetObj* est liée par *ppRowset*.

Pour les autres paramètres, consultez [IOpenRowset :: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) dans le *Guide de référence du programmeur OLE DB.*

## <a name="iopenrowsetimplopenrowset"></a><a name="openrowset"></a> Iopenrowsetimpl, :: OpenRowset

Ouvre et retourne un ensemble de lignes qui comprend toutes les lignes d’une table ou d’un index de base unique.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Paramètres

Consultez [IOpenRowset :: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Cette méthode est introuvable dans ATLDB. Manutention. Elle est créée par l’Assistant objet ATL lorsque vous créez un fournisseur.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
