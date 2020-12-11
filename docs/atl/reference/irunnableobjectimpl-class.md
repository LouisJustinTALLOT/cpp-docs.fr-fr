---
description: 'En savoir plus sur : classe IRunnableObjectImpl'
title: IRunnableObjectImpl, classe
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
ms.openlocfilehash: ecae31d23eb68ce45e9b140a3e5034fb6c5400fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158112"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl, classe

Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IRunnableObjectImpl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Retourne le CLSID du contrôle en cours d’exécution. L’implémentation ATL définit le CLSID à GUID_NULL et retourne E_UNEXPECTED.|
|[IRunnableObjectImpl :: IsRunning](#isrunning)|Détermine si le contrôle est en cours d’exécution. L’implémentation ATL retourne la valeur TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Verrouille le contrôle à l’État en cours d’exécution. L’implémentation ATL retourne S_OK.|
|[IRunnableObjectImpl :: Run](#run)|Force le contrôle à s’exécuter. L’implémentation ATL retourne S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indique que le contrôle est incorporé. L’implémentation ATL retourne S_OK.|

## <a name="remarks"></a>Notes

L’interface [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) permet à un conteneur de déterminer si un contrôle est en cours d’exécution, de le forcer à s’exécuter ou de le verrouiller à l’État en cours d’exécution. `IRunnableObjectImpl`La classe fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a> IRunnableObjectImpl::GetRunningClass

Retourne le CLSID du contrôle en cours d’exécution.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation ATL affecte \* à *lpClsid* la valeur GUID_NULL et retourne E_UNEXPECTED.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject :: GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) dans le SDK Windows.

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a> IRunnableObjectImpl :: IsRunning

Détermine si le contrôle est en cours d’exécution.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation ATL retourne la valeur TRUE.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject :: IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) dans le SDK Windows.

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a> IRunnableObjectImpl::LockRunning

Verrouille le contrôle à l’État en cours d’exécution.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation ATL retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject :: LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) dans le SDK Windows.

## <a name="irunnableobjectimplrun"></a><a name="run"></a> IRunnableObjectImpl :: Run

Force le contrôle à s’exécuter.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation ATL retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject :: Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) dans le SDK Windows.

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a> IRunnableObjectImpl::SetContainedObject

Indique que le contrôle est incorporé.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Valeur renvoyée

L’implémentation ATL retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject :: SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
