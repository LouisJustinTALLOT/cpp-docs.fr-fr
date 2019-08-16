---
title: IPersistStreamInitImpl, classe
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
ms.openlocfilehash: 7a350a4349cb825795a18dd860a2482952b04dcb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496149"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl, classe

Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IPersistStreamInitImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Récupère la taille du flux nécessaire pour enregistrer les données de l’objet. L’implémentation ATL retourne E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Initialise un objet nouvellement créé.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Vérifie si les données de l’objet ont été modifiées depuis le dernier enregistrement.|
|[IPersistStreamInitImpl::Load](#load)|Charge les propriétés de l’objet à partir du flux spécifié.|
|[IPersistStreamInitImpl::Save](#save)|Enregistre les propriétés de l’objet dans le flux spécifié.|

## <a name="remarks"></a>Notes

L’interface [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) permet à un client de demander que votre objet se charge et enregistre ses données persistantes dans un seul flux. La `IPersistStreamInitImpl` classe fournit une implémentation par défaut de cette interface et `IUnknown` implémente en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID

Récupère le CLSID de l’objet.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Notes

Consultez [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) dans la SDK Windows.

##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax

Récupère la taille du flux nécessaire pour enregistrer les données de l’objet.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPersistStreamInit:: GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) dans le SDK Windows.

##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew

Initialise un objet nouvellement créé.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Notes

Consultez [IPersistStreamInit:: InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) dans le SDK Windows.

##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty

Vérifie si les données de l’objet ont été modifiées depuis le dernier enregistrement.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Notes

Consultez [IPersistStreamInit:: IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) dans le SDK Windows.

##  <a name="load"></a>  IPersistStreamInitImpl::Load

Charge les propriétés de l’objet à partir du flux spécifié.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet pour récupérer ces informations.

Consultez [IPersistStreamInit:: Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) dans le SDK Windows.

##  <a name="save"></a>  IPersistStreamInitImpl::Save

Enregistre les propriétés de l’objet dans le flux spécifié.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet pour stocker ces informations.

Consultez [IPersistStreamInit:: Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Stockages et flux](/windows/win32/Stg/storages-and-streams)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
