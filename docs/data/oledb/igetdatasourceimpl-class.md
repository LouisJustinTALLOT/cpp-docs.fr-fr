---
description: 'En savoir plus sur : classe Igetdatasourceimpl,'
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
ms.openlocfilehash: 24cf83b7eb799882f1c7da42854899bcf46fddf2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287266"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl, classe

Fournit une implémentation de l’objet [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IGetDataSourceImpl` .

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[GetDataSource](#getdatasource)|Retourne un pointeur d’interface sur l’objet source de données qui a créé la session.|

## <a name="remarks"></a>Notes

Il s’agit d’une interface obligatoire sur la session pour l’obtention d’un pointeur d’interface vers l’objet source de données.

## <a name="igetdatasourceimplgetdatasource"></a><a name="getdatasource"></a> Igetdatasourceimpl, :: GetDataSource

Retourne un pointeur d’interface sur l’objet source de données qui a créé la session.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Paramètres

Consultez [IGetDataSource :: GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Utile si vous avez besoin d’accéder aux propriétés dans l’objet source de données.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
