---
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
ms.openlocfilehash: 6b1af7c21c6f5028ad6d3a228cb22650fa3cef42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495670"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl, classe

Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IRunnableObjectImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Retourne le CLSID du contrôle en cours d’exécution. L’implémentation ATL affecte au CLSID la valeur GUID_NULL et retourne E_UNEXPECTED.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Détermine si le contrôle est en cours d’exécution. L’implémentation ATL retourne la valeur TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Verrouille le contrôle à l’État en cours d’exécution. L’implémentation ATL retourne S_OK.|
|[IRunnableObjectImpl::Run](#run)|Force le contrôle à s’exécuter. L’implémentation ATL retourne S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indique que le contrôle est incorporé. L’implémentation ATL retourne S_OK.|

## <a name="remarks"></a>Notes

L’interface [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) permet à un conteneur de déterminer si un contrôle est en cours d’exécution, de le forcer à s’exécuter ou de le verrouiller à l’État en cours d’exécution. La `IRunnableObjectImpl` classe fournit une implémentation par défaut de cette interface et `IUnknown` implémente en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlctl. h

##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass

Retourne le CLSID du contrôle en cours d’exécution.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Valeur de retour

L’implémentation ATL affecte \* à *lpClsid* la valeur GUID_NULL et retourne E_UNEXPECTED.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject:: GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) dans le SDK Windows.

##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning

Détermine si le contrôle est en cours d’exécution.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Valeur de retour

L’implémentation ATL retourne la valeur TRUE.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject:: IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) dans le SDK Windows.

##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning

Verrouille le contrôle à l’État en cours d’exécution.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Valeur de retour

L’implémentation ATL retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject:: LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) dans le SDK Windows.

##  <a name="run"></a>  IRunnableObjectImpl::Run

Force le contrôle à s’exécuter.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Valeur de retour

L’implémentation ATL retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject:: Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) dans le SDK Windows.

##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject

Indique que le contrôle est incorporé.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Valeur de retour

L’implémentation ATL retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IRunnableObject:: SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
