---
title: Classe IPersistStreamInitImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: 0d6ac4639ac0cfb97416ca80b7a2ec3903d7b8e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326462"
---
# <a name="ipersiststreaminitimpl-class"></a>Classe IPersistStreamInitImpl

Cette classe `IUnknown` implémente et fournit une implémentation par défaut de l’interface [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IPersistStreamInitImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Récupère la taille du flux nécessaire pour enregistrer les données de l’objet. La mise en œuvre d’ATL E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Initialise un objet nouvellement créé.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Vérifie si les données de l’objet ont changé depuis qu’elles ont été enregistrées pour la dernière fois.|
|[IPersistStreamInitImpl::Load](#load)|Charge les propriétés de l’objet à partir du flux spécifié.|
|[IPersistStreamInitImpl::Save IPersistStreamInitImpl::Save](#save)|Enregistre les propriétés de l’objet sur le flux spécifié.|

## <a name="remarks"></a>Notes

[L’interface IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) permet à un client de demander que votre objet se charge et enregistre ses données persistantes en un seul flux. La `IPersistStreamInitImpl` classe fournit une implémentation par défaut de cette interface et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a>IPersistStreamInitImpl::GetClassID

Récupère le CLSID de l’objet.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Notes

Voir [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) dans le SDK Windows.

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax

Récupère la taille du flux nécessaire pour enregistrer les données de l’objet.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IPersistStreamInit:GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) dans le SDK Windows.

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a>IPersistStreamInitImpl::InitNew

Initialise un objet nouvellement créé.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Notes

Voir [IPersistStreamInit::InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) in the Windows SDK.

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a>IPersistStreamInitImpl::IsDirty

Vérifie si les données de l’objet ont changé depuis qu’elles ont été enregistrées pour la dernière fois.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Notes

Voir [IPersistStreamInit:IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) in the Windows SDK.

## <a name="ipersiststreaminitimplload"></a><a name="load"></a>IPersistStreamInitImpl::Load

Charge les propriétés de l’objet à partir du flux spécifié.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Notes

ATL utilise la carte des biens de l’objet pour récupérer ces informations.

Voir [IPersistStreamInit:Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) in the Windows SDK.

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a>IPersistStreamInitImpl::Save IPersistStreamInitImpl::Save

Enregistre les propriétés de l’objet sur le flux spécifié.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Notes

ATL utilise la carte des biens de l’objet pour stocker ces informations.

Voir [IPersistStreamInit:Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Stockages et flux](/windows/win32/Stg/storages-and-streams)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
