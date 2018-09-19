---
title: Ipersiststorageimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1479ced25a741e27a195b529b6bf8825b47ce41e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099601"
---
# <a name="ipersiststorageimpl-class"></a>Ipersiststorageimpl, classe

Cette classe implémente le [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) interface.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPersistStorageImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Récupère le CLSID de l’objet.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Demande à l’objet pour libérer tous les objets de stockage et de passer en mode HandsOff. L’implémentation de ATL retourne S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Initialise un nouveau stockage.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Vérifie si les données de l’objet a été modifiée depuis son dernier enregistrement.|
|[IPersistStorageImpl::Load](#load)|Charge les propriétés de l’objet à partir du stockage spécifié.|
|[IPersistStorageImpl::Save](#save)|Enregistre les propriétés de l’objet dans le stockage spécifié.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Avertit un objet qu’elle peut retourner en mode Normal pour écrire dans son objet de stockage. L’implémentation de ATL retourne S_OK.|

## <a name="remarks"></a>Notes

`IPersistStorageImpl` implémente le [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) interface, ce qui permet à un client de demander à ce que votre charge de l’objet et enregistrer ses données persistantes à l’aide d’un stockage.

L’implémentation de cette classe nécessite classe `T` pour rendre une implémentation de la `IPersistStreamInit` interface disponible via `QueryInterface`. En général, cela signifie que cette classe `T` doit dériver de [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), fournir une entrée pour `IPersistStreamInit` dans le [mappage COM](com-map-macros.md)et utiliser un [mappage des propriétés](property-map-macros.md) pour décrire les données persistantes de la classe.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID

Récupère le CLSID de l’objet.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Notes

Consultez [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) dans le Kit de développement logiciel Windows.

##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage

Demande à l’objet pour libérer tous les objets de stockage et de passer en mode HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IPersistStorage::HandsOffStorage](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) dans le Kit de développement logiciel Windows.

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

Initialise un nouveau stockage.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Notes

L’implémentation de ATL délègue à la [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interface.

Consultez [IPersistStorage:InitNew](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-initnew) dans le Kit de développement logiciel Windows.

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

Vérifie si les données de l’objet a été modifiée depuis son dernier enregistrement.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Notes

L’implémentation de ATL délègue à la [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interface.

Consultez [IPersistStorage:IsDirty](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-isdirty) dans le Kit de développement logiciel Windows.

##  <a name="load"></a>  IPersistStorageImpl::Load

Charge les propriétés de l’objet à partir du stockage spécifié.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Notes

L’implémentation de ATL délègue à la [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interface. `Load` utilise un flux nommé « Contenu » pour récupérer les données de l’objet. Le [enregistrer](#save) méthode crée à l’origine de ce flux.

Consultez [IPersistStorage:Load](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-load) dans le Kit de développement logiciel Windows.

##  <a name="save"></a>  IPersistStorageImpl::Save

Enregistre les propriétés de l’objet dans le stockage spécifié.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Notes

L’implémentation de ATL délègue à la [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interface. Lorsque `Save` est d’abord appelée, elle crée un flux nommé « Contenu » sur le stockage spécifié. Ce flux est ensuite utilisé dans les appels ultérieurs à `Save` et dans les appels à [charge](#load).

Consultez [IPersistStorage:Save](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-save) dans le Kit de développement logiciel Windows.

##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted

Avertit un objet qu’elle peut retourner en mode Normal pour écrire dans son objet de stockage.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IPersistStorage:SaveCompleted](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-savecompleted) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[Flux et stockages](/windows/desktop/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl, classe](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl, classe](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
