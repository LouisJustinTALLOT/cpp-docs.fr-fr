---
description: 'En savoir plus sur : classe IProvideClassInfo2Impl'
title: IProvideClassInfo2Impl, classe
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
ms.openlocfilehash: 9c3422c98ebd857231f492efb77d51a0a49acb76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139255"
---
# <a name="iprovideclassinfo2impl-class"></a>IProvideClassInfo2Impl, classe

Cette classe fournit une implémentation par défaut des méthodes [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) et [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) .

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
Pointeur vers l’identificateur pour la dispinterface sortante par défaut de la coclasse.

*plibid*<br/>
Pointeur vers le LIBID de la bibliothèque de types qui contient des informations sur l’interface. Par défaut, la bibliothèque de types au niveau du serveur est passée.

*wMajor*<br/>
Version principale de la bibliothèque de types. La valeur par défaut est 1.

*wMinor*<br/>
Version secondaire de la bibliothèque de types. La valeur par défaut est 0.

*tihclass*<br/>
Classe utilisée pour gérer les informations de type de la coclasse. La valeur par défaut est `CComTypeInfoHolder`.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl :: GetClassInfo](#getclassinfo)|Récupère un `ITypeInfo` pointeur vers les informations de type de la coclasse.|
|[IProvideClassInfo2Impl :: GetGUID](#getguid)|Récupère le GUID de la dispinterface sortante de l’objet.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl :: _tih](#_tih)|Gère les informations de type pour la coclasse.|

## <a name="remarks"></a>Notes

L’interface [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) étend [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) en ajoutant la `GetGUID` méthode. Cette méthode permet à un client de récupérer l’IID d’interface sortante d’un objet pour son jeu d’événements par défaut. `IProvideClassInfo2Impl`La classe fournit une implémentation par défaut `IProvideClassInfo` des `IProvideClassInfo2` méthodes et.

`IProvideClassInfo2Impl` contient un membre statique de type `CComTypeInfoHolder` qui gère les informations de type de la coclasse.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a> IProvideClassInfo2Impl :: GetClassInfo

Récupère un `ITypeInfo` pointeur vers les informations de type de la coclasse.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

Consultez [IProvideClassInfo :: GetClassinfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) dans la SDK Windows.

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a> IProvideClassInfo2Impl :: GetGUID

Récupère le GUID de la dispinterface sortante de l’objet.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Notes

Consultez [IProvideClassInfo2 :: GetGuid](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) dans le SDK Windows.

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a> IProvideClassInfo2Impl::IProvideClassInfo2Impl

Constructeur.

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Notes

Appelle `AddRef` sur le membre [_tih](#_tih) . Le destructeur appelle `Release`.

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a> IProvideClassInfo2Impl :: _tih

Ce membre de données statique est une instance du paramètre de modèle de classe, *tihclass*, qui est par défaut `CComTypeInfoHolder` .

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Notes

`_tih` gère les informations de type pour la coclasse.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
