---
title: Classe IProvideClassInfo2Impl
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
ms.openlocfilehash: 0d1ee9acc1cfabc71ecf33fcb5919d826899c671
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329572"
---
# <a name="iprovideclassinfo2impl-class"></a>Classe IProvideClassInfo2Impl

Cette classe fournit une implémentation par défaut des méthodes [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) et [IProvideClassInfo2.](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)

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
Un pointeur à l’identifiant de la coclasse.

*psrcid*<br/>
Un pointeur à l’identifiant pour la faute de la coclasse dispinterface sortante.

*plibid*<br/>
Un pointeur pour le LIBID de la bibliothèque de type qui contient des informations sur l’interface. Par défaut, la bibliothèque de type serveur est passée.

*wMajor (en)*<br/>
Version principale de la bibliothèque de types. La valeur par défaut est 1.

*wMinor (en)*<br/>
Version secondaire de la bibliothèque de types. La valeur par défaut est 0.

*tihclass*<br/>
La classe gérait les informations de type coclass. La valeur par défaut est `CComTypeInfoHolder`.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Récupère un `ITypeInfo` pointeur sur les informations de type coclass.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Récupère le GUID pour le dispinterface sortant de l’objet.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Gère les informations de type pour la coclasse.|

## <a name="remarks"></a>Notes

[L’interface IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) étend [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) en ajoutant la `GetGUID` méthode. Cette méthode permet à un client de récupérer l’interface sortante d’un objet IID pour son ensemble d’événements par défaut. La `IProvideClassInfo2Impl` classe fournit une `IProvideClassInfo` `IProvideClassInfo2` mise en œuvre par défaut de la et des méthodes.

`IProvideClassInfo2Impl`contient un membre `CComTypeInfoHolder` statique de type qui gère les informations de type pour la coclasse.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>IProvideClassInfo2Impl::GetClassInfo

Récupère un `ITypeInfo` pointeur sur les informations de type coclass.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

Voir [IProvideClassInfo:GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) dans le SDK Windows.

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a>IProvideClassInfo2Impl::GetGUID

Récupère le GUID pour le dispinterface sortant de l’objet.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Notes

Voir [IProvideClassInfo2:GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) dans le SDK Windows.

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl

Constructeur.

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Notes

Fait `AddRef` appel au [_tih](#_tih) membre. Le destructeur appelle `Release`.

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a>IProvideClassInfo2Impl::_tih

Ce membre de données statiques est une instance du paramètre `CComTypeInfoHolder`de modèle de classe, *tihclass*, qui par défaut est .

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Notes

`_tih`gère les informations de type pour la coclasse.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
