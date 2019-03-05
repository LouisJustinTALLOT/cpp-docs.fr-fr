---
title: Ipersiststreaminitimpl, classe
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
ms.openlocfilehash: b5ab433ed08b150e6c344d65657a910542856e77
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290028"
---
# <a name="ipersiststreaminitimpl-class"></a>Ipersiststreaminitimpl, classe

Cette classe implémente `IUnknown` et fournit une implémentation par défaut de la [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interface.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPersistStreamInitImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Récupère la taille du flux requis pour enregistrer les données de l’objet. L’implémentation de ATL retourne E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Initialise un objet nouvellement créé.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Vérifie si les données de l’objet a été modifiée depuis son dernier enregistrement.|
|[IPersistStreamInitImpl::Load](#load)|Charge les propriétés de l’objet à partir du flux spécifié.|
|[IPersistStreamInitImpl::Save](#save)|Enregistre les propriétés de l’objet dans le flux spécifié.|

## <a name="remarks"></a>Notes

Le [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interface permet à un client demander que votre objet se charge et enregistre ses données persistantes dans un seul flux. Classe `IPersistStreamInitImpl` fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID

Récupère le CLSID de l’objet.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Notes

Consultez [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) dans le Kit de développement logiciel Windows.

##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax

Récupère la taille du flux requis pour enregistrer les données de l’objet.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IPersistStreamInit::GetSizeMax](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) dans le Kit de développement logiciel Windows.

##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew

Initialise un objet nouvellement créé.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Notes

Consultez [qu’IPersistStreamInit::InitNew](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) dans le Kit de développement logiciel Windows.

##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty

Vérifie si les données de l’objet a été modifiée depuis son dernier enregistrement.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Notes

Consultez [IPersistStreamInit::IsDirty](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) dans le Kit de développement logiciel Windows.

##  <a name="load"></a>  IPersistStreamInitImpl::Load

Charge les propriétés de l’objet à partir du flux spécifié.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet à récupérer ces informations.

Consultez [IPersistStreamInit::Load](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-load) dans le Kit de développement logiciel Windows.

##  <a name="save"></a>  IPersistStreamInitImpl::Save

Enregistre les propriétés de l’objet dans le flux spécifié.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Notes

ATL utilise le mappage des propriétés de l’objet pour stocker ces informations.

Consultez [IPersistStreamInit::Save](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-save) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[Flux et stockages](/windows/desktop/Stg/storages-and-streams)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
