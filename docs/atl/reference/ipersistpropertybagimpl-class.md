---
description: 'En savoir plus sur : classe IPersistPropertyBagImpl'
title: IPersistPropertyBagImpl, classe
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
ms.openlocfilehash: 1e244c4349bd04a83d257280da3315f2c797003a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158164"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl, classe

Cette classe implémente `IUnknown` et permet à un objet d’enregistrer ses propriétés dans un conteneur de propriétés fourni par le client.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPersistPropertyBagImpl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPersistPropertyBagImpl :: GetClassID](#getclassid)|Récupère le CLSID de l’objet.|
|[IPersistPropertyBagImpl :: InitNew](#initnew)|Initialise un objet nouvellement créé. L’implémentation ATL retourne S_OK.|
|[IPersistPropertyBagImpl :: Load](#load)|Charge les propriétés de l’objet à partir d’un conteneur de propriétés fourni par le client.|
|[IPersistPropertyBagImpl :: enregistrer](#save)|Enregistre les propriétés de l’objet dans un conteneur de propriétés fourni par le client.|

## <a name="remarks"></a>Notes

L’interface [IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) permet à un objet d’enregistrer ses propriétés dans un conteneur de propriétés fourni par le client. `IPersistPropertyBagImpl`La classe fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

`IPersistPropertyBag` fonctionne conjointement avec [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) et [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Ces deux dernières interfaces doivent être implémentées par le client. Par `IPropertyBag` le biais de, le client enregistre et charge les propriétés individuelles de l’objet. À `IErrorLog` l’aide de, l’objet et le client peuvent signaler toutes les erreurs rencontrées.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a> IPersistPropertyBagImpl :: GetClassID

Récupère le CLSID de l’objet.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Notes

Consultez [IPersist :: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) dans la SDK Windows.

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a> IPersistPropertyBagImpl :: InitNew

Initialise un objet nouvellement créé.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IPersistPropertyBag :: InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) dans le SDK Windows.

## <a name="ipersistpropertybagimplload"></a><a name="load"></a> IPersistPropertyBagImpl :: Load

Charge les propriétés de l’objet à partir d’un conteneur de propriétés fourni par le client.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet pour récupérer ces informations.

Consultez [IPersistPropertyBag :: Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) dans le SDK Windows.

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a> IPersistPropertyBagImpl :: enregistrer

Enregistre les propriétés de l’objet dans un conteneur de propriétés fourni par le client.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet pour stocker ces informations. Par défaut, cette méthode enregistre toutes les propriétés, quelle que soit la valeur de *fSaveAllProperties*.

Consultez [IPersistPropertyBag :: Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
