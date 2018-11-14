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
ms.openlocfilehash: bb44af102f08e05edddc2fb692d1e30dd7e31717
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556671"
---
# <a name="cenumerator-class"></a>CEnumerator, classe

Utilise un objet énumérateur OLE DB, qui expose le [ISourcesRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms715969(v=vs.85)) interface à retourner un ensemble de lignes décrivant toutes les sources de données et les énumérateurs.

## <a name="syntax"></a>Syntaxe

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Find](#find)|Recherches via des fournisseurs disponibles (sources de données) en recherchant une avec le nom spécifié.|
|[GetMoniker](#getmoniker)|Récupère le `IMoniker` interface pour l’enregistrement en cours.|
|[Ouvrir](#open)|Ouvre l’énumérateur.|

## <a name="remarks"></a>Notes

Vous pouvez récupérer le `ISourcesRowset` données indirectement à partir de cette classe.

## <a name="find"></a> CEnumerator::Find

Recherche d’un nom spécifique parmi les fournisseurs disponibles.

### <a name="syntax"></a>Syntaxe

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>Paramètres

*szSearchName*<br/>
[in] Nom à rechercher.

### <a name="return-value"></a>Valeur de retour

**true** si le nom a été trouvé. Sinon, **false**.

### <a name="remarks"></a>Notes

Ce nom ne correspond à la `SOURCES_NAME` membre de la [ISourcesRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms715969(v=vs.85)) interface.

## <a name="getmoniker"></a> CEnumerator::GetMoniker

Analyse le nom d’affichage pour extraire le composant de la chaîne qui peut être converti en un moniker.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>Paramètres

*ppMoniker*<br/>
[out] Le moniker est analysé à partir du nom d’affichage ([CEnumeratorAccessor::m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) de la ligne actuelle.

*lpszDisplayName*<br/>
[in] Nom complet à analyser.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="open"></a> CEnumerator::Open

Lie le moniker de l’énumérateur, si un est spécifié, puis récupère l’ensemble de lignes de l’énumérateur en appelant [ISourcesRowset::GetSourcesRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms711200(v=vs.85)).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>Paramètres

*pMoniker*<br/>
[in] Pointeur vers un moniker de l’énumérateur.

*pClsid*<br/>
[in] Un pointeur vers le `CLSID` d’un énumérateur.

*enumerator*<br/>
[in] Une référence à un énumérateur.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[DBViewer](../../visual-cpp-samples.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)