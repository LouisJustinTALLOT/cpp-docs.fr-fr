---
description: 'En savoir plus sur : classe IRowsetCreatorImpl,'
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
ms.openlocfilehash: 6a478e86bdb09851afed091c99ed0d0931a9115e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317400"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl, classe

Exécute les mêmes fonctions que, `IObjectWithSite` mais active également les propriétés de OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` .

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `IRowsetCreator` .

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[SetSite](#setsite)|Définit le site qui contient l’objet rowset.|

## <a name="remarks"></a>Notes

Cette classe hérite de [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) et remplace [IObjectWithSite :: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Lorsqu’une commande fournisseur ou un objet de session crée un ensemble de lignes, il appelle `QueryInterface` sur l’objet rowset qui recherche `IObjectWithSite` et appelle le `SetSite` passage de l’interface de l’objet rowset `IUnkown` comme interface de site.

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a> IRowsetCreatorImpl, :: SetSite

Définit le site qui contient l’objet rowset. Pour plus d’informations, consultez [IObjectWithSite :: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Paramètres

*pCreator*<br/>
dans Pointeur vers le `IUnknown` pointeur d’interface du site gérant l’objet rowset.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

En outre, `IRowsetCreatorImpl::SetSite` active les `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` propriétés OLE DB.

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
