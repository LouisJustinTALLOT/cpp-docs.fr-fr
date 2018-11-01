---
title: IRowsetIdentityImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 5ce4db130f4e8569b666047ca7a5c2bc4e0e6cb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593191"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl, classe

Implémente la norme OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913) interface, ce qui permet de tester pour l’identité de ligne.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Une classe dérivée de `IRowsetIdentityImpl`.

*RowClass*<br/>
L’unité de stockage pour le `HROW`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[IsSameRow](#issamerow)|Compare deux handles de ligne pour voir si elles font référence à la même ligne.|

## <a name="issamerow"></a> IRowsetIdentityImpl::IsSameRow

Compare deux handles de ligne pour voir si elles font référence à la même ligne.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629) dans le *de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Pour comparer les handles de ligne, cette méthode convertit le `HROW` gère à `RowClass` membres et appelle `memcmp` sur les pointeurs.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)