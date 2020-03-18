---
title: CArrayRowset, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
ms.openlocfilehash: 66b7607eb28392196f6b7d3790aee976a861f2b6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441722"
---
# <a name="carrayrowset-class"></a>CArrayRowset, classe

Accède aux éléments d’un ensemble de lignes à l’aide de la syntaxe de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>,
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Type de classe d’accesseur que vous souhaitez que l’ensemble de lignes utilise.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CArrayRowset](#carrayrowset)|Constructeur.|
|[Instantané](#snapshot)|Lit la totalité de l’ensemble de lignes en mémoire.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[And&#91;&#93;](#operator)|Accède à un élément de l’ensemble de lignes.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[CArrayRowset::m_nRowsRead](#nrowsread)|Nombre de lignes déjà lues.|

## <a name="carrayrowset"></a>CArrayRowset :: CArrayRowset

Crée un objet `CArrayRowset`.

### <a name="syntax"></a>Syntaxe

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>Paramètres

*nMax*<br/>
dans Nombre maximal de lignes dans l’ensemble de lignes.

## <a name="snapshot"></a>CArrayRowset :: Snapshot

Lit la totalité de l’ensemble de lignes en mémoire, en créant une image ou un instantané de celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Snapshot() throw();
```

## <a name="operator"></a>CArrayRowset :: Operator

Fournit une syntaxe de type tableau pour accéder à une ligne de l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Paramètre basé sur un modèle qui spécifie le type d’accesseur stocké dans l’ensemble de lignes.

*nRow*<br/>
dans Numéro de la ligne (élément de tableau) à laquelle vous souhaitez accéder.

### <a name="return-value"></a>Valeur de retour

Contenu de la ligne demandée.

### <a name="remarks"></a>Notes

Si *nRow* dépasse le nombre de lignes dans l’ensemble de lignes, une exception est levée.

## <a name="nrowsread"></a>CArrayRowset :: m_nRowsRead

Contient le nombre de lignes de l’ensemble de lignes qui ont déjà été lues.

### <a name="syntax"></a>Syntaxe

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset, classe](../../data/oledb/crowset-class.md)