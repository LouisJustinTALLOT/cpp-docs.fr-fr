---
title: IPersistStorageImpl, classe
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
ms.openlocfilehash: a5b5dd4e5be43d01f00687ed9b96a3f27abcad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495692"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl, classe

Cette classe implémente l’interface [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) .

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IPersistStorageImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Indique à l’objet de libérer tous les objets de stockage et d’entrer en mode HandsOff. L’implémentation ATL retourne S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Initialise un nouveau stockage.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Vérifie si les données de l’objet ont été modifiées depuis le dernier enregistrement.|
|[IPersistStorageImpl::Load](#load)|Charge les propriétés de l’objet à partir du stockage spécifié.|
|[IPersistStorageImpl::Save](#save)|Enregistre les propriétés de l’objet dans le stockage spécifié.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Avertit un objet qu’il peut retourner en mode normal pour écrire dans son objet de stockage. L’implémentation ATL retourne S_OK.|

## <a name="remarks"></a>Notes

`IPersistStorageImpl`implémente l’interface [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) , qui permet à un client de demander que votre objet charge et enregistre ses données persistantes à l’aide d’un stockage.

L’implémentation de cette classe requiert que `T` la classe rende une implémentation `IPersistStreamInit` de l’interface `QueryInterface`disponible via. En général, cela signifie `T` que la classe doit dériver de [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), `IPersistStreamInit` fournir une entrée pour dans le [mappage com](com-map-macros.md)et utiliser un [mappage de propriété](property-map-macros.md) pour décrire les données persistantes de la classe.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID

Récupère le CLSID de l’objet.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Notes

Consultez [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) dans la SDK Windows.

##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage

Indique à l’objet de libérer tous les objets de stockage et d’entrer en mode HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IPersistStorage:: HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) dans la SDK Windows.

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

Initialise un nouveau stockage.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Notes

L’implémentation ATL délègue à l’interface [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

Consultez [IPersistStorage: InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) dans le SDK Windows.

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

Vérifie si les données de l’objet ont été modifiées depuis le dernier enregistrement.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Notes

L’implémentation ATL délègue à l’interface [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

Consultez [IPersistStorage: IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) dans le SDK Windows.

##  <a name="load"></a>  IPersistStorageImpl::Load

Charge les propriétés de l’objet à partir du stockage spécifié.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Notes

L’implémentation ATL délègue à l’interface [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) . `Load`utilise un flux nommé «contents» pour récupérer les données de l’objet. La méthode [Save](#save) crée initialement ce flux.

Consultez [IPersistStorage: Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) dans le SDK Windows.

##  <a name="save"></a>  IPersistStorageImpl::Save

Enregistre les propriétés de l’objet dans le stockage spécifié.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Notes

L’implémentation ATL délègue à l’interface [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) . Lorsque `Save` est appelé pour la première fois, il crée un flux nommé «contents» sur le stockage spécifié. Ce flux est ensuite utilisé dans les appels ultérieurs à `Save` et dans les appels à [Load](#load).

Consultez [IPersistStorage: Save](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) dans le SDK Windows.

##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted

Avertit un objet qu’il peut retourner en mode normal pour écrire dans son objet de stockage.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IPersistStorage: SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Stockages et flux](/windows/win32/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl, classe](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl, classe](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
