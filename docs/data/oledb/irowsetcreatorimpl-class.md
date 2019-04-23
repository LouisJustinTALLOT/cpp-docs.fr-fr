---
title: IRowsetCreatorImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: 3dc5cb06b3eb7f01667e4e1ec09dd60f9befae77
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026602"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl, classe

Effectue les mêmes fonctions que `IObjectWithSite` mais permet également les propriétés OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Une classe dérivée de `IRowsetCreator`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[SetSite](#setsite)|Définit le site qui contient l’objet d’ensemble de lignes.|

## <a name="remarks"></a>Notes

Cette classe hérite de [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) et remplace [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Lorsqu’un objet de commande ou de la session du fournisseur crée un ensemble de lignes, il appelle `QueryInterface` sur l’objet d’ensemble de lignes que vous recherchez `IObjectWithSite` et appelle `SetSite` en passant l’objet d’ensemble de lignes `IUnkown` interface en tant que l’interface du site.

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite

Définit le site qui contient l’objet d’ensemble de lignes. Pour plus d’informations, consultez [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Paramètres

*pCreator*<br/>
[in] Pointeur vers le `IUnknown` pointeur d’interface du site de gestion de l’objet d’ensemble de lignes.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

En outre, `IRowsetCreatorImpl::SetSite` permet OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` propriétés.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)