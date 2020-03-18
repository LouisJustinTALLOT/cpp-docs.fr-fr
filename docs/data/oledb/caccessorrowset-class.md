---
title: CAccessorRowset, classe
ms.date: 11/04/2016
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
ms.openlocfilehash: 77c4eebae6ede5d74e24421cc4d3951c78e08777
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447272"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset, classe

Encapsule un ensemble de lignes et ses accesseurs associés dans une classe unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset>
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Classe d’accesseur.

*TRowset*<br/>
Classe d’ensemble de lignes.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Bind](#bind)|Crée des liaisons (utilisé lorsque `bBind` est spécifié avec la **valeur false** dans [CCommand :: Open](../../data/oledb/ccommand-open.md)).|
|[CAccessorRowset,](#caccessorrowset)|Constructeur.|
|[Close](#close)|Ferme l’ensemble de lignes et tous les accesseurs.|
|[FreeRecordMemory](#freerecordmemory)|Libère toutes les colonnes de l’enregistrement actif qui doivent être libérées.|
|[GetColumnInfo](#getcolumninfo)|Implémente [IColumnsInfo :: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)).|

## <a name="remarks"></a>Notes

La classe `TAccessor` gère l’accesseur. La classe *TRowset* gère l’ensemble de lignes.

## <a name="bind"></a>CAccessorRowset :: bind

Crée les liaisons si vous avez spécifié `bBind` la **valeur false** dans [CCommand :: Open](../../data/oledb/ccommand-open.md).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="caccessorrowset"></a>CAccessorRowset :: CAccessorRowset

Initialise l'objet `CAccessorRowset`.

### <a name="syntax"></a>Syntaxe

```cpp
CAccessorRowset();
```

## <a name="close"></a>CAccessorRowset :: Close

Libère les accesseurs actifs et l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Libère toute mémoire associée.

## <a name="freerecordmemory"></a>CAccessorRowset :: FreeRecordMemory

Libère toutes les colonnes de l’enregistrement actif qui doivent être libérées.

### <a name="syntax"></a>Syntaxe

```cpp
void FreeRecordMemory();
```

## <a name="getcolumninfo"></a>CAccessorRowset :: GetColumnInfo

Obtient les informations de colonne à partir de l’ensemble de lignes ouvert.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,
   DBCOLUMNINFO** ppColumnInfo,
   LPOLESTR* ppStrings) const;

HRESULT GetColumnInfo(DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo);
```

#### <a name="parameters"></a>Paramètres

Consultez [IColumnsInfo :: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

L’utilisateur doit libérer les informations de colonne retournées et la mémoire tampon de chaîne. Utilisez la deuxième version de cette méthode lorsque vous utilisez [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) et que vous devez substituer les liaisons.

Pour plus d’informations, consultez [IColumnsInfo :: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)