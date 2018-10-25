---
title: CArrayRowset, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- CArrayRowset
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
dev_langs:
- C++
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b8613372b84423a14fd995d78ca9d4c0dd1c1ae
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070374"
---
# <a name="carrayrowset-class"></a>CArrayRowset, classe

Éléments d’accès d’un ensemble de lignes à l’aide de la syntaxe de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>, 
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Le type de classe d’accesseur que vous souhaitez que l’ensemble de lignes à utiliser.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CArrayRowset](#carrayrowset)|Constructeur.|
|[Instantané](#snapshot)|Lit l’ensemble de lignes en mémoire.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur&#91;&#93;](#operator)|Accède à un élément de l’ensemble de lignes.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[CArrayRowset::m_nRowsRead](#nrowsread)|Le nombre de lignes déjà lues.|

## <a name="carrayrowset"></a> CArrayRowset::CArrayRowset

Crée un objet `CArrayRowset`.

### <a name="syntax"></a>Syntaxe

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>Paramètres

*nombre maximal*<br/>
[in] Nombre maximal de lignes dans l’ensemble de lignes.

## <a name="snapshot"></a> CArrayRowset::Snapshot

Lit l’ensemble de lignes en mémoire, création d’une image ou un instantané de celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Snapshot() throw();
```

## <a name="operator"></a> CArrayRowset::operator

Fournit la syntaxe de type tableau pour accéder à une ligne dans l’ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Un paramètre basé sur un modèle qui spécifie le type d’accesseur stockée dans l’ensemble de lignes.

*nRow*<br/>
[in] Numéro de la ligne (élément de tableau) que vous souhaitez accéder.

### <a name="return-value"></a>Valeur de retour

Le contenu de la ligne demandée.

### <a name="remarks"></a>Notes

Si *nRow* dépasse le nombre de lignes dans l’ensemble de lignes, une exception est levée.

## <a name="nrowsread"></a> CArrayRowset::m_nRowsRead

Contient le nombre de lignes dans l’ensemble de lignes qui ont déjà été lues.

### <a name="syntax"></a>Syntaxe

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset, classe](../../data/oledb/crowset-class.md)