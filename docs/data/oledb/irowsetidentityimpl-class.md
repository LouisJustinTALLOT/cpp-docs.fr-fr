---
description: 'En savoir plus sur : classe Irowsetidentityimpl,'
title: IRowsetIdentityImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 4cba00d16671c3efd26bc3a9b20e93e1f80a1cc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287201"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl, classe

Implémente l’interface OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85)) , qui permet de tester l’identité de ligne.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `IRowsetIdentityImpl` .

*RowClass*<br/>
Unité de stockage du `HROW` .

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[IsSameRow](#issamerow)|Compare deux handles de ligne pour voir s’ils font référence à la même ligne.|

## <a name="irowsetidentityimplissamerow"></a><a name="issamerow"></a> Irowsetidentityimpl, :: IsSameRow

Compare deux handles de ligne pour voir s’ils font référence à la même ligne.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>Paramètres

Consultez [IRowsetIdentity :: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Pour comparer des handles de ligne, cette méthode effectue un cast des `HROW` Handles vers les `RowClass` membres et appelle `memcmp` sur les pointeurs.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
