---
title: IViewObjectExImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 3aead41f317d175eac9dcb094aa2070d82dc6185
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495504"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl, classe

Cette classe implémente `IUnknown` et fournit des implémentations par défaut des interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)et [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IViewObjectExImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Dessine une représentation du contrôle dans un contexte de périphérique (Device Context).|
|[IViewObjectExImpl::Freeze](#freeze)|Fige la représentation dessinée d’un contrôle afin qu’il ne soit pas `Unfreeze`modifié jusqu’à un. L’implémentation ATL retourne E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Récupère une connexion de récepteur de notifications existante sur le contrôle, le cas échéant.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Retourne la palette logique utilisée par le contrôle pour le dessin. L’implémentation ATL retourne E_NOTIMPL.|
|[IViewObjectExImpl::GetExtent](#getextent)|Récupère la taille d’affichage du contrôle en unités HIMETRIC (0,01 millimètres par unité) du membre de classe de contrôle [CComControlBase :: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Fournit des indicateurs de dimensionnement à partir du conteneur pour l’objet à utiliser lorsque l’utilisateur le redimensionne.|
|[IViewObjectExImpl::GetRect](#getrect)|Retourne un rectangle décrivant un aspect de dessin demandé. L’implémentation ATL retourne E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Retourne des informations sur l’opacité de l’objet et les aspects de dessin pris en charge.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Vérifie si le point spécifié se trouve dans le rectangle spécifié et retourne une valeur [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) dans `pHitResult`.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Vérifie si le rectangle d’affichage du contrôle chevauche un point dans le rectangle d’emplacement spécifié et retourne une valeur `pHitResult`HITRESULT dans.|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Configure une connexion entre le contrôle et un récepteur de notifications afin que le récepteur puisse être averti des modifications apportées à la vue du contrôle.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Libère la représentation dessinée du contrôle. L’implémentation ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

Les interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)et [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) permettent à un contrôle de s’afficher directement, et de créer et de gérer un récepteur de notifications pour notifier le conteneur des modifications apportées à l’affichage du contrôle. L' `IViewObjectEx` interface fournit la prise en charge des fonctionnalités de contrôle étendues, telles que le dessin sans scintillement, les contrôles non rectangulaires et transparents, et le test de positionnement (par exemple, la fermeture d’un clic de souris doit être prise en compte sur le contrôle). La `IViewObjectExImpl` classe fournit une implémentation par défaut de ces interfaces et `IUnknown` implémente en envoyant des informations à l’appareil de vidage dans les versions Debug.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl. h

##  <a name="draw"></a>  IViewObjectExImpl::Draw

Dessine une représentation du contrôle dans un contexte de périphérique (Device Context).

```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```

### <a name="remarks"></a>Notes

Cette méthode appelle `CComControl::OnDrawAdvanced` qui, à son tour, appelle la `OnDraw` méthode de votre classe de contrôle. Une `OnDraw` méthode est automatiquement ajoutée à votre classe de contrôle lorsque vous créez votre contrôle à l’aide de l’Assistant contrôle ATL. La valeur par défaut `OnDraw` de l’Assistant dessine un rectangle avec l’étiquette « ATL 3,0 ».

Consultez [IViewObject ::D RAW](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) dans le SDK Windows.

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

Fige la représentation dessinée d’un contrôle afin qu’il ne soit pas `Unfreeze`modifié jusqu’à un. L’implémentation ATL retourne E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Notes

Consultez [IViewObject :: Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) dans le SDK Windows.

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

Récupère une connexion de récepteur de notifications existante sur le contrôle, le cas échéant.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Notes

Le récepteur de notifications est stocké dans la classe de contrôle Data Member [CComControlBase :: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Consultez [IViewObject :: GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) dans la SDK Windows.

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

Retourne la palette logique utilisée par le contrôle pour le dessin. L’implémentation ATL retourne E_NOTIMPL.

```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```

### <a name="remarks"></a>Notes

Consultez [IViewObject :: GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) dans la SDK Windows.

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

Récupère la taille d’affichage du contrôle en unités HIMETRIC (0,01 millimètres par unité) du membre de classe de contrôle [CComControlBase :: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Notes

Consultez [IViewObject2 :: GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) dans le SDK Windows.

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

Fournit des indicateurs de dimensionnement à partir du conteneur pour l’objet à utiliser lorsque l’utilisateur le redimensionne.

```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```

### <a name="remarks"></a>Notes

Si `dwAspect` est DVASPECT_CONTENT et *pExtentInfo-> dwExtentMode* est DVEXTENT_CONTENT, définit * `psizel` sur le membre de données de la classe de contrôle [CComControlBase :: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). Sinon, retourne une erreur HRESULT.

Consultez [IViewObjectEx :: GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) dans le SDK Windows.

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

Retourne un rectangle décrivant un aspect de dessin demandé. L’implémentation ATL retourne E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Notes

Consultez [IViewObjectEx :: getRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) dans le SDK Windows.

##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus

Retourne des informations sur l’opacité de l’objet et les aspects de dessin pris en charge.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Notes

Par défaut, ATL définit `pdwStatus` pour indiquer que le contrôle prend en charge VIEWSTATUS_OPAQUE (les valeurs possibles sont dans l’énumération [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) ).

Consultez [IViewObjectEx :: GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) dans le SDK Windows.

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

Vérifie si le point spécifié se trouve dans le rectangle spécifié et retourne une valeur [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) dans `pHitResult`.

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Notes

La valeur peut être HITRESULT_HIT ou HITRESULT_OUTSIDE.

Si `dwAspect` est égal à [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), la méthode retourne S_OK. Sinon, la méthode retourne E_FAIL.

Consultez [IViewObjectEx :: QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) dans le SDK Windows.

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

Vérifie si le rectangle d’affichage du contrôle chevauche un point dans le rectangle d’emplacement spécifié et retourne une valeur [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) dans `pHitResult`.

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Notes

La valeur peut être HITRESULT_HIT ou HITRESULT_OUTSIDE.

Si `dwAspect` est égal à [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), la méthode retourne S_OK. Sinon, la méthode retourne E_FAIL.

Consultez [IViewObjectEx :: QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) dans le SDK Windows.

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

Configure une connexion entre le contrôle et un récepteur de notifications afin que le récepteur puisse être averti des modifications apportées à la vue du contrôle.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Notes

Le pointeur vers l’interface [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) sur le récepteur de notifications est stocké dans la classe de contrôle Data Member [CComControlBase :: m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Consultez [IViewObject :: SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) dans la SDK Windows.

##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze

Libère la représentation dessinée du contrôle. L’implémentation ATL retourne E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Notes

Consultez SDK Windows l’en---------------- [:](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze)

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Implémentez cette méthode pour fermer le handle associé à cet objet.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Paramètres

*hHandle*<br/>
Handle à fermer.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Le handle passé à cette méthode a été précédemment associé à cet objet par un appel à [CWorkerThread :: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant illustre une implémentation simple de `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Implémentez cette méthode pour exécuter du code lorsque le handle associé à cet objet est signalé.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Paramètres

*dwParam*<br/>
Paramètre utilisateur.

*hObject*<br/>
Handle qui a été signalé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Le handle et le DWORD/pointeur passés à cette méthode étaient précédemment associés à cet objet par un appel à [CWorkerThread :: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant illustre une implémentation simple de `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de contrôles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Tutoriel](../../atl/active-template-library-atl-tutorial.md)<br/>
[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
