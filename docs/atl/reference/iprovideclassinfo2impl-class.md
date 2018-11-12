---
title: Classe de IProvideClassInfo2Impl
ms.date: 11/04/2016
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
ms.openlocfilehash: a270efa5daac8c8b608f05bdb752195f806b7935
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539644"
---
# <a name="iprovideclassinfo2impl-class"></a>Classe de IProvideClassInfo2Impl

Cette classe fournit une implémentation par défaut de la [IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) et [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) méthodes.

## <a name="syntax"></a>Syntaxe

```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```

#### <a name="parameters"></a>Paramètres

*pcoclsid*<br/>
Pointeur vers l’identificateur de la coclasse.

*psrcid*<br/>
Un pointeur vers l’identificateur par défaut de la coclasse sortants dispinterface.

*plibid*<br/>
Pointeur vers le LIBID de la bibliothèque de types qui contient des informations sur l’interface. Par défaut, la bibliothèque de types de niveau serveur est passée.

*wMajor*<br/>
Version principale de la bibliothèque de types. La valeur par défaut est 1.

*wMinor*<br/>
Version secondaire de la bibliothèque de types. La valeur par défaut est 0.

*tihclass*<br/>
La classe utilisée pour gérer les informations de type de la coclasse. La valeur par défaut est `CComTypeInfoHolder`.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Name|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Récupère un `ITypeInfo` pointeur vers les informations de type de la coclasse.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Récupère le GUID pour dispinterface sortant de l’objet.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Gère les informations de type pour la coclasse.|

## <a name="remarks"></a>Notes

Le [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) interface étend [IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) en ajoutant le `GetGUID` (méthode). Cette méthode permet à un client récupérer l’interface sortante d’un objet IID pour son jeu d’événements par défaut. Classe `IProvideClassInfo2Impl` fournit une implémentation par défaut de la `IProvideClassInfo` et `IProvideClassInfo2` méthodes.

`IProvideClassInfo2Impl` contient un membre statique de type `CComTypeInfoHolder` qui gère les informations de type pour la coclasse.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="getclassinfo"></a>  IProvideClassInfo2Impl::GetClassInfo

Récupère un `ITypeInfo` pointeur vers les informations de type de la coclasse.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

Consultez [IProvideClassInfo::GetClassInfo](/windows/desktop/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) dans le Kit de développement logiciel Windows.

##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID

Récupère le GUID pour dispinterface sortant de l’objet.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Notes

Consultez [IProvideClassInfo2::GetGUID](/windows/desktop/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) dans le Kit de développement logiciel Windows.

##  <a name="iprovideclassinfo2impl"></a>  IProvideClassInfo2Impl::IProvideClassInfo2Impl

Constructeur.

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Notes

Appels `AddRef` sur le [_tih](#_tih) membre. Le destructeur appelle `Release`.

##  <a name="_tih"></a>  IProvideClassInfo2Impl::_tih

Ce membre de données statique est une instance du paramètre de modèle de classe, *tihclass*, qui par défaut est `CComTypeInfoHolder`.

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Notes

`_tih` Gère les informations de type pour la coclasse.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
