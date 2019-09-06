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
ms.openlocfilehash: 8c4253d469c510f5e6eb996ed510ef836844899d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311957"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl, classe

Exécute les mêmes fonctions que `IObjectWithSite` , mais active également les propriétés `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`de OLE DB.

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `IRowsetCreator`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[SetSite](#setsite)|Définit le site qui contient l’objet rowset.|

## <a name="remarks"></a>Notes

Cette classe hérite de [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) et remplace [IObjectWithSite :: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Lorsqu’une commande fournisseur ou un objet de session crée un ensemble de `QueryInterface` lignes, il appelle sur l' `IObjectWithSite` objet rowset qui recherche et appelle `IUnkown` `SetSite` le passage de l’interface de l’objet rowset comme interface de site.

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite

Définit le site qui contient l’objet rowset. Pour plus d’informations, consultez [IObjectWithSite :: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Paramètres

*pCreator*<br/>
dans Pointeur vers le `IUnknown` pointeur d’interface du site gérant l’objet rowset.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

En outre, `IRowsetCreatorImpl::SetSite` active les propriétés `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` OLE DB.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)