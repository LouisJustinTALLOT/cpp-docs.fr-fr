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
ms.openlocfilehash: a53cd653258980d21e9dd297ae61c458732b7250
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210546"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl, classe

Exécute les mêmes fonctions que `IObjectWithSite`, mais active également les propriétés de OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `IRowsetCreator`.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[SetSite](#setsite)|Définit le site qui contient l’objet rowset.|

## <a name="remarks"></a>Notes

Cette classe hérite de [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) et remplace [IObjectWithSite :: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Lorsqu’une commande fournisseur ou un objet de session crée un ensemble de lignes, il appelle `QueryInterface` sur l’objet d’ensemble de lignes recherchant `IObjectWithSite` et appelle `SetSite` passant l’interface `IUnkown` de l’objet rowset comme interface de site.

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a>IRowsetCreatorImpl, :: SetSite

Définit le site qui contient l’objet rowset. Pour plus d’informations, consultez [IObjectWithSite :: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Paramètres

*pCreator*<br/>
dans Pointeur vers le pointeur d’interface `IUnknown` du site gérant l’objet rowset.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

En outre, `IRowsetCreatorImpl::SetSite` active les propriétés OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
