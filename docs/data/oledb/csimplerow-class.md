---
title: CSimpleRow, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
ms.openlocfilehash: c0d7ea0966b9a582e4a6969573458bca2e8a0fea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507231"
---
# <a name="csimplerow-class"></a>CSimpleRow, classe

Fournit une implémentation par défaut pour le handle de ligne, qui est utilisé dans la classe [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) .

## <a name="syntax"></a>Syntax

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[AddRefRow](#addrefrow)|Ajoute un décompte de références à un handle de ligne existant.|
|[Compare](#compare)|Compare deux lignes pour voir si elles font référence à la même instance de ligne.|
|[CSimpleRow](#csimplerow)|Constructeur.|
|[ReleaseRow](#releaserow)|Libère des lignes.|

### <a name="data-members"></a>Données membres

| Nom | Description |
|-|-|
|[m_dwRef](#dwref)|Décompte de références à un handle de ligne existant.|
|[m_iRowset](#irowset)|Index de l’ensemble de lignes représentant le curseur.|

## <a name="remarks"></a>Remarques

Un descripteur de ligne est logiquement une étiquette unique pour une ligne de résultats. `IRowsetImpl` crée un nouveau `CSimpleRow` pour chaque ligne demandée dans [IRowsetImpl :: GetNextRows](./irowsetimpl-class.md#getnextrows). `CSimpleRow` peut également être remplacé par votre propre implémentation du handle de ligne, car il s’agit d’un argument de modèle par défaut pour `IRowsetImpl` . La seule exigence de remplacer cette classe est d’avoir la classe de remplacement qui fournit un constructeur qui accepte un paramètre unique de type **long**.

## <a name="csimplerowaddrefrow"></a><a name="addrefrow"></a> CSimpleRow :: AddRefRow

Ajoute un décompte de références à un handle de ligne existant de manière thread-safe.

### <a name="syntax"></a>Syntax

```cpp
DWORD AddRefRow();
```

## <a name="csimplerowcompare"></a><a name="compare"></a> CSimpleRow :: compare

Compare deux lignes pour voir si elles font référence à la même instance de ligne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Paramètres

*pRow*<br/>
Pointeur vers un objet `CSimpleRow`.

### <a name="return-value"></a>Valeur renvoyée

Une valeur HRESULT, généralement S_OK, indiquant que les deux lignes sont la même instance de ligne, ou S_FALSE, indiquant que les deux lignes sont différentes. Consultez [IRowsetIdentity :: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* pour d’autres valeurs de retour possibles.

## <a name="csimplerowcsimplerow"></a><a name="csimplerow"></a> CSimpleRow :: CSimpleRow

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Paramètres

*iRowsetCur*<br/>
dans Index de l’ensemble de lignes actif.

### <a name="remarks"></a>Remarques

Définit [m_iRowset](#irowset) sur *iRowsetCur*.

## <a name="csimplerowreleaserow"></a><a name="releaserow"></a> CSimpleRow :: ReleaseRow

Libère les lignes de manière thread-safe.

### <a name="syntax"></a>Syntax

```cpp
DWORD ReleaseRow();
```

## <a name="csimplerowm_dwref"></a><a name="dwref"></a> CSimpleRow :: m_dwRef

Décompte de références à un handle de ligne existant.

### <a name="syntax"></a>Syntax

```cpp
DWORD m_dwRef;
```

## <a name="csimplerowm_irowset"></a><a name="irowset"></a> CSimpleRow :: m_iRowset

Index de l’ensemble de lignes représentant le curseur.

### <a name="syntax"></a>Syntaxe

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl, classe](../../data/oledb/irowsetimpl-class.md)
