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
- CSimpleRow
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
ms.openlocfilehash: 19b90f4454e784907366ef6cf7e3e7e1b9ada799
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023839"
---
# <a name="csimplerow-class"></a>CSimpleRow, classe

Fournit une implémentation par défaut pour le handle de ligne, qui est utilisé dans le [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) classe.

## <a name="syntax"></a>Syntaxe

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AddRefRow](#addrefrow)|Ajoute un décompte de références à un handle de ligne existant.|
|[Comparer](#compare)|Compare deux lignes pour voir s’ils font référence à la même instance de ligne.|
|[CSimpleRow](#csimplerow)|Constructeur.|
|[ReleaseRow](#releaserow)|Libère des lignes.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_dwRef](#dwref)|Le décompte de références à un handle de ligne existant.|
|[m_iRowset](#irowset)|Un index à l’ensemble de lignes qui représente le curseur.|

## <a name="remarks"></a>Notes

Un handle de ligne est logiquement une balise unique pour une ligne de résultat. `IRowsetImpl` Crée un `CSimpleRow` pour chaque ligne demandée dans [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` peut également être remplacé par votre propre implémentation de la poignée de ligne, car il s’agit d’un argument de modèle par défaut à `IRowsetImpl`. La seule exigence pour remplacer cette classe est d’avoir à la classe de remplacement de fournir un constructeur qui accepte un seul paramètre de type **LONG**.

## <a name="addrefrow"></a> CSimpleRow::AddRefRow

Ajoute un décompte de références à un handle de ligne existant de façon thread-safe.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD AddRefRow();
```

## <a name="compare"></a> CSimpleRow::Compare

Compare deux lignes pour voir s’ils font référence à la même instance de ligne.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Paramètres

*pRow*<br/>
Pointeur vers un objet `CSimpleRow` .

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT, généralement S_OK, indiquant les deux lignes sont la même instance de ligne ou S_FALSE, indiquant les deux lignes sont différents. Consultez [IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) dans le *de référence du programmeur OLE DB* pour les autres valeurs de retour possibles.

## <a name="csimplerow"></a> CSimpleRow::CSimpleRow

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Paramètres

*iRowsetCur*<br/>
[in] Index de l’ensemble de lignes en cours.

### <a name="remarks"></a>Notes

Jeux [m_iRowset](../../data/oledb/csimplerow-m-irowset.md) à *iRowsetCur*.

## <a name="releaserow"></a> CSimpleRow::ReleaseRow

Libère les lignes de manière thread-safe.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD ReleaseRow();
```

## <a name="dwref"></a> CSimpleRow::m_dwRef

Le décompte de références à un handle de ligne existant.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD m_dwRef;
```

## <a name="irowset"></a> CSimpleRow::m_iRowset

Index de l’ensemble de lignes qui représente le curseur.

### <a name="syntax"></a>Syntaxe

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl, classe](../../data/oledb/irowsetimpl-class.md)