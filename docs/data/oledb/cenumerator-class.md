---
title: CEnumerator, classe
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: dfc358c06179d50cbf6442863fd2ed2c533cd00a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498537"
---
# <a name="cenumerator-class"></a>CEnumerator, classe

Utilise un objet énumérateur OLE DB, qui expose l’interface [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) pour retourner un ensemble de lignes décrivant toutes les sources de données et les énumérateurs.

## <a name="syntax"></a>Syntax

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[Rechercher](#find)|Recherche des fournisseurs disponibles (sources de données) en recherchant un avec le nom spécifié.|
|[GetMoniker](#getmoniker)|Récupère l' `IMoniker` interface pour l’enregistrement en cours.|
|[Ouvrir](#open)|Ouvre l’énumérateur.|

## <a name="remarks"></a>Remarques

Vous pouvez récupérer les `ISourcesRowset` données indirectement à partir de cette classe.

## <a name="cenumeratorfind"></a><a name="find"></a> CEnumerator :: find

Recherche un nom spécifié parmi les fournisseurs disponibles.

### <a name="syntax"></a>Syntaxe

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>Paramètres

*szSearchName*<br/>
dans Nom à rechercher.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le nom a été trouvé. Sinon, **`false`** .

### <a name="remarks"></a>Remarques

Ce nom est mappé au `SOURCES_NAME` membre de l’interface [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) .

## <a name="cenumeratorgetmoniker"></a><a name="getmoniker"></a> CEnumerator :: GetMoniker

Analyse le nom complet pour extraire le composant de la chaîne qui peut être converti en moniker.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>Paramètres

*ppMoniker*<br/>
à Moniker analysé à partir du nom complet ([CEnumeratorAccessor :: m_szParseName](./cenumeratoraccessor-class.md#szparsename)) de la ligne actuelle.

*lpszDisplayName*<br/>
dans Nom complet à analyser.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="cenumeratoropen"></a><a name="open"></a> CEnumerator :: Open

Lie le moniker de l’énumérateur, s’il est spécifié, puis récupère l’ensemble de lignes de l’énumérateur en appelant [ISourcesRowset :: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>Paramètres

*pMoniker*<br/>
dans Pointeur vers un moniker pour un énumérateur.

*pClsid*<br/>
dans Pointeur vers le `CLSID` d’un énumérateur.

*énumérateur*<br/>
dans Référence à un énumérateur.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="see-also"></a>Voir aussi

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
