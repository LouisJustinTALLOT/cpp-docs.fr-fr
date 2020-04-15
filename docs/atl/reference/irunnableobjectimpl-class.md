---
title: Classe IRunnableObjectImpl
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: 2843c0c25a5c104ffbdff72255ac5d85cf53b1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329448"
---
# <a name="irunnableobjectimpl-class"></a>Classe IRunnableObjectImpl

Cette classe `IUnknown` implémente et fournit une implémentation par défaut de l’interface [IRunnableObject.](/windows/win32/api/objidl/nn-objidl-irunnableobject)

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IRunnableObjectImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Retourne le CLSID du contrôle courant. La mise en œuvre de l’ATL définit le CLSID pour GUID_NULL et renvoie E_UNEXPECTED.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Détermine si le contrôle est en cours d’exécution. La mise en œuvre ATL renvoie TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Verrouille le contrôle dans l’état courant. La mise en œuvre d’ATL S_OK.|
|[IRunnableObjectImpl::Run](#run)|Force le contrôle à courir. La mise en œuvre d’ATL S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indique que le contrôle est intégré. La mise en œuvre d’ATL S_OK.|

## <a name="remarks"></a>Notes

[L’interface IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) permet à un conteneur de déterminer si un contrôle est en marche, de le forcer à fonctionner ou de le verrouiller dans l’état de fonctionnement. La `IRunnableObjectImpl` classe fournit une implémentation par défaut de cette interface et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass

Retourne le CLSID du contrôle courant.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Valeur de retour

La mise en \* œuvre d’ATL définit *lpClsid* pour GUID_NULL et retourne E_UNEXPECTED.

### <a name="remarks"></a>Notes

Voir [IRunnableObject:GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) dans le Windows SDK.

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a>IRunnableObjectImpl::IsRunning

Détermine si le contrôle est en cours d’exécution.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre ATL renvoie TRUE.

### <a name="remarks"></a>Notes

Voir [IRunnableObject:IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) in the Windows SDK.

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a>IRunnableObjectImpl::LockRunning

Verrouille le contrôle dans l’état courant.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre d’ATL S_OK.

### <a name="remarks"></a>Notes

Voir [IRunnableObject:LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) in the Windows SDK.

## <a name="irunnableobjectimplrun"></a><a name="run"></a>IRunnableObjectImpl::Run

Force le contrôle à courir.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre d’ATL S_OK.

### <a name="remarks"></a>Notes

Voir [IRunnableObject::Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) in the Windows SDK.

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject

Indique que le contrôle est intégré.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Valeur de retour

La mise en œuvre d’ATL S_OK.

### <a name="remarks"></a>Notes

Voir [IRunnableObject:SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) dans le Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
