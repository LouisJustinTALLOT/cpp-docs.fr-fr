---
title: Classe IPersistStorageImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: b235b190f237293932705e4d290ac963088722f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326467"
---
# <a name="ipersiststorageimpl-class"></a>Classe IPersistStorageImpl

Cette classe met en œuvre l’interface [IPersistStorage.](/windows/win32/api/objidl/nn-objidl-ipersiststorage)

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IPersistStorageImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Demande à l’objet de libérer tous les objets de stockage et d’entrer en mode HandsOff. La mise en œuvre d’ATL S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Initialise un nouveau stockage.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Vérifie si les données de l’objet ont changé depuis qu’elles ont été enregistrées pour la dernière fois.|
|[IPersistStorageImpl::Load](#load)|Charge les propriétés de l’objet à partir du stockage spécifié.|
|[IPersistStorageImpl::Save IPersistStorageImpl::Save IPersistStorageImpl::Save](#save)|Enregistre les propriétés de l’objet dans le stockage spécifié.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Informe un objet qu’il peut revenir en mode Normal pour écrire à son objet de stockage. La mise en œuvre d’ATL S_OK.|

## <a name="remarks"></a>Notes

`IPersistStorageImpl`implémente l’interface [IPersistStorage,](/windows/win32/api/objidl/nn-objidl-ipersiststorage) qui permet à un client de demander que votre objet charge et enregistre ses données persistantes à l’aide d’un stockage.

La mise en œuvre de cette classe nécessite la classe `T` pour rendre une mise en œuvre de l’interface `IPersistStreamInit` disponible via `QueryInterface`. Typiquement, cela `T` signifie que la classe doit dériver de `IPersistStreamInit` [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), fournir une entrée dans la carte [COM](com-map-macros.md), et utiliser une carte [de propriété](property-map-macros.md) pour décrire les données persistantes de la classe.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ipersiststorageimplgetclassid"></a><a name="getclassid"></a>IPersistStorageImpl::GetClassID

Récupère le CLSID de l’objet.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Notes

Voir [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) dans le SDK Windows.

## <a name="ipersiststorageimplhandsoffstorage"></a><a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage

Demande à l’objet de libérer tous les objets de stockage et d’entrer en mode HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IPersistStorage::HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) in the Windows SDK.

## <a name="ipersiststorageimplinitnew"></a><a name="initnew"></a>IPersistStorageImpl::InitNew

Initialise un nouveau stockage.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Notes

La mise en œuvre d’ATL se délégué à l’interface [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Voir [IPersistStorage:InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) in the Windows SDK.

## <a name="ipersiststorageimplisdirty"></a><a name="isdirty"></a>IPersistStorageImpl::IsDirty

Vérifie si les données de l’objet ont changé depuis qu’elles ont été enregistrées pour la dernière fois.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Notes

La mise en œuvre d’ATL se délégué à l’interface [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Voir [IPersistStorage:IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) in the Windows SDK.

## <a name="ipersiststorageimplload"></a><a name="load"></a>IPersistStorageImpl::Load

Charge les propriétés de l’objet à partir du stockage spécifié.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Notes

La mise en œuvre d’ATL se délégué à l’interface [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) `Load`utilise un flux appelé "Contents" pour récupérer les données de l’objet. La méthode [Save](#save) crée à l’origine ce flux.

Voir [IPersistStorage:Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) in the Windows SDK.

## <a name="ipersiststorageimplsave"></a><a name="save"></a>IPersistStorageImpl::Save IPersistStorageImpl::Save IPersistStorageImpl::Save

Enregistre les propriétés de l’objet dans le stockage spécifié.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Notes

La mise en œuvre d’ATL se délégué à l’interface [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) Lorsqu’il `Save` est appelé pour la première fois, il crée un flux nommé "Contents" sur le stockage spécifié. Ce flux est ensuite utilisé `Save` dans les appels ultérieurs vers et dans les appels à [la charge](#load).

Voir [IPersistStorage:Save](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) in the Windows SDK.

## <a name="ipersiststorageimplsavecompleted"></a><a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted

Informe un objet qu’il peut revenir en mode Normal pour écrire à son objet de stockage.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IPersistStorage:SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Stockages et flux](/windows/win32/Stg/storages-and-streams)<br/>
[Classe IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[Classe IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
