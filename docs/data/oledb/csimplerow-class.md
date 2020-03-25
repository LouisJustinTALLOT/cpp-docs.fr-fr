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
ms.openlocfilehash: 2b08e0e8f3b5b43f79019c70e3fe32ae9064dee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211118"
---
# <a name="csimplerow-class"></a>CSimpleRow, classe

Fournit une implémentation par défaut pour le handle de ligne, qui est utilisé dans la classe [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddRefRow](#addrefrow)|Ajoute un décompte de références à un handle de ligne existant.|
|[Compare](#compare)|Compare deux lignes pour voir si elles font référence à la même instance de ligne.|
|[CSimpleRow](#csimplerow)|Constructeur.|
|[ReleaseRow](#releaserow)|Libère des lignes.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_dwRef](#dwref)|Décompte de références à un handle de ligne existant.|
|[m_iRowset](#irowset)|Index de l’ensemble de lignes représentant le curseur.|

## <a name="remarks"></a>Notes

Un descripteur de ligne est logiquement une étiquette unique pour une ligne de résultats. `IRowsetImpl` crée une `CSimpleRow` pour chaque ligne demandée dans [IRowsetImpl :: GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` peut également être remplacé par votre propre implémentation du handle de ligne, car il s’agit d’un argument template par défaut pour `IRowsetImpl`. La seule exigence de remplacer cette classe est d’avoir la classe de remplacement qui fournit un constructeur qui accepte un paramètre unique de type **long**.

## <a name="csimplerowaddrefrow"></a><a name="addrefrow"></a>CSimpleRow :: AddRefRow

Ajoute un décompte de références à un handle de ligne existant de manière thread-safe.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD AddRefRow();
```

## <a name="csimplerowcompare"></a><a name="compare"></a>CSimpleRow :: compare

Compare deux lignes pour voir si elles font référence à la même instance de ligne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Paramètres

*pRow*<br/>
Pointeur vers un objet `CSimpleRow`.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT, généralement S_OK, indiquant que les deux lignes sont la même instance de ligne, ou S_FALSE, indiquant que les deux lignes sont différentes. Consultez [IRowsetIdentity :: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* pour d’autres valeurs de retour possibles.

## <a name="csimplerowcsimplerow"></a><a name="csimplerow"></a>CSimpleRow :: CSimpleRow

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Paramètres

*iRowsetCur*<br/>
dans Index de l’ensemble de lignes actif.

### <a name="remarks"></a>Notes

Définit [m_iRowset](../../data/oledb/csimplerow-m-irowset.md) sur *iRowsetCur*.

## <a name="csimplerowreleaserow"></a><a name="releaserow"></a>CSimpleRow :: ReleaseRow

Libère les lignes de manière thread-safe.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD ReleaseRow();
```

## <a name="csimplerowm_dwref"></a><a name="dwref"></a>CSimpleRow :: m_dwRef

Décompte de références à un handle de ligne existant.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD m_dwRef;
```

## <a name="csimplerowm_irowset"></a><a name="irowset"></a>CSimpleRow :: m_iRowset

Index de l’ensemble de lignes représentant le curseur.

### <a name="syntax"></a>Syntaxe

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl, classe](../../data/oledb/irowsetimpl-class.md)
