---
title: Classe IPersistPropertyBagImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: f656ecc76b175eae523059c60bb8a3efc6f0b312
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326487"
---
# <a name="ipersistpropertybagimpl-class"></a>Classe IPersistPropertyBagImpl

Cette classe `IUnknown` met en œuvre et permet à un objet d’enregistrer ses propriétés dans un sac de propriété fourni par le client.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IPersistPropertyBagImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID IPersistPropertyBagImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Initialise un objet nouvellement créé. La mise en œuvre d’ATL S_OK.|
|[IPersistPropertyBagImpl::Load](#load)|Charge les propriétés de l’objet à partir d’un sac de propriété fourni par le client.|
|[IPersistPropertyBagImpl::Save](#save)|Enregistre les propriétés de l’objet dans un sac de propriété fourni par le client.|

## <a name="remarks"></a>Notes

[L’interface IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) permet à un objet d’enregistrer ses propriétés dans un sac de propriété fourni par le client. La `IPersistPropertyBagImpl` classe fournit une implémentation par défaut de cette interface et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

`IPersistPropertyBag`fonctionne en collaboration avec [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) et [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Ces deux dernières interfaces doivent être implémentées par le client. Grâce `IPropertyBag`à , le client enregistre et charge les propriétés individuelles de l’objet. Grâce `IErrorLog`à , l’objet et le client peuvent signaler toutes les erreurs rencontrées.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID IPersistPropertyBagImpl::GetClassID

Récupère le CLSID de l’objet.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Notes

Voir [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) dans le SDK Windows.

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a>IPersistPropertyBagImpl::InitNew

Initialise un objet nouvellement créé.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IPersistPropertyBag::InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) in the Windows SDK.

## <a name="ipersistpropertybagimplload"></a><a name="load"></a>IPersistPropertyBagImpl::Load

Charge les propriétés de l’objet à partir d’un sac de propriété fourni par le client.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Notes

ATL utilise la carte des biens de l’objet pour récupérer ces informations.

Voir [IPersistPropertyBag:Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) in the Windows SDK.

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a>IPersistPropertyBagImpl::Save

Enregistre les propriétés de l’objet dans un sac de propriété fourni par le client.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Notes

ATL utilise la carte des biens de l’objet pour stocker ces informations. Par défaut, cette méthode sauve toutes les propriétés, quelle que soit la valeur de *fSaveAllProperties*.

Voir [IPersistPropertyBag:Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
