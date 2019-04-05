---
title: IGetDataSourceImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
ms.openlocfilehash: 2056b93fd6c1d32b72996970352e87670ff406de
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034207"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl, classe

Fournit une implémentation de la [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) objet.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IGetDataSourceImpl`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d’interface

|||
|-|-|
|[GetDataSource](#getdatasource)|Retourne un pointeur d’interface sur l’objet de source de données qui a créé la session.|

## <a name="remarks"></a>Notes

Il s’agit une interface obligatoire sur la session pour obtenir un pointeur d’interface à l’objet de source de données.

## <a name="getdatasource"></a> IGetDataSourceImpl::GetDataSource

Retourne un pointeur d’interface sur l’objet de source de données qui a créé la session.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Paramètres

Consultez [IGetDataSource::GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) dans le *de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Cette option est utile si vous avez besoin accéder aux propriétés de l’objet de source de données.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)