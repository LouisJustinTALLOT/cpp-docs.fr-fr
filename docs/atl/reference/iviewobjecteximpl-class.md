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
ms.openlocfilehash: 0333f7e0e0d5b91665978082f112df6d16105dd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538513"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl, classe

Cette classe implémente `IUnknown` et fournit des implémentations par défaut de la [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), et [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) interfaces.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IViewObjectExImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Crée une représentation du contrôle sur un contexte de périphérique.|
|[IViewObjectExImpl::Freeze](#freeze)|Fige la représentation dessinée d’un contrôle afin qu’il n’évolueront pas avant une `Unfreeze`. L’implémentation de ATL retourne E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Récupère une connexion existante de récepteur de notifications sur le contrôle, le cas échéant.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Retourne la palette logique utilisée par le contrôle pour le dessin. L’implémentation de ATL retourne E_NOTIMPL.|
|[IViewObjectExImpl::GetExtent](#getextent)|Récupère la taille d’affichage du contrôle en unités HIMETRIC (0,01 millimètre par unité) à partir du membre de données de classe contrôle [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Fournit des indications de dimensionnement du conteneur pour l’objet à utiliser lorsque l’utilisateur le redimensionne.|
|[IViewObjectExImpl::GetRect](#getrect)|Retourne un rectangle décrivant un aspect de dessin demandé. L’implémentation de ATL retourne E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Retourne des informations relatives à l’opacité de l’objet et les aspects de dessin sont pris en charge.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Vérifie si le point spécifié se trouve dans le rectangle spécifié et retourne un [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) valeur dans `pHitResult`.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Vérifie si le rectangle d’affichage du contrôle chevauche n’importe quel point dans le rectangle de l’emplacement spécifié et retourne une valeur HITRESULT dans `pHitResult`.|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Configure une connexion entre le contrôle et un récepteur de notifications et le récepteur peut être notifié sur les modifications apportées dans l’affichage du contrôle.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Libère la représentation sous forme de dessinée du contrôle. L’implémentation de ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

Le [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), et [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) interfaces permettent un contrôle de s’afficher directement et pour créer et gérer un récepteur de notifications pour notifier le conteneur des modifications dans l’affichage de contrôle. Le `IViewObjectEx` interface prend en charge les fonctionnalités de contrôle étendu tels que le scintillement dessin, les contrôles non rectangulaires et transparentes et le test de positionnement (par exemple, comment fermer un clic de souris doit être à prendre en considération sur le contrôle). Classe `IViewObjectExImpl` fournit une implémentation par défaut de ces interfaces et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="draw"></a>  IViewObjectExImpl::Draw

Crée une représentation du contrôle sur un contexte de périphérique.

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

Cette méthode appelle `CComControl::OnDrawAdvanced` qui appelle à son tour votre classe de contrôle `OnDraw` (méthode). Un `OnDraw` méthode est automatiquement ajoutée à votre classe de contrôle lorsque vous créez votre contrôle avec l’Assistant contrôle ATL. Par défaut de l’Assistant `OnDraw` Dessine un rectangle avec l’étiquette « ATL 3.0 ».

Consultez [IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw) dans le Kit de développement logiciel Windows.

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

Fige la représentation dessinée d’un contrôle afin qu’il n’évolueront pas avant une `Unfreeze`. L’implémentation de ATL retourne E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Notes

Consultez [IViewObject::Freeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-freeze) dans le Kit de développement logiciel Windows.

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

Récupère une connexion existante de récepteur de notifications sur le contrôle, le cas échéant.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Notes

Le récepteur de notifications est stocké dans le membre de données de classe de contrôle [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Consultez [IViewObject::GetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getadvise) dans le Kit de développement logiciel Windows.

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

Retourne la palette logique utilisée par le contrôle pour le dessin. L’implémentation de ATL retourne E_NOTIMPL.

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

Consultez [IViewObject::GetColorSet](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getcolorset) dans le Kit de développement logiciel Windows.

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

Récupère la taille d’affichage du contrôle en unités HIMETRIC (0,01 millimètre par unité) à partir du membre de données de classe contrôle [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Notes

Consultez [IViewObject2::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-iviewobject2-getextent) dans le Kit de développement logiciel Windows.

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

Fournit des indications de dimensionnement du conteneur pour l’objet à utiliser lorsque l’utilisateur le redimensionne.

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

Si `dwAspect` est DVASPECT_CONTENT et *pExtentInfo -> dwExtentMode* est DVEXTENT_CONTENT, définit * `psizel` au membre de données de la classe de contrôle [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). Sinon, retourne une erreur HRESULT.

Consultez [IViewObjectEx::GetNaturalExtent](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) dans le Kit de développement logiciel Windows.

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

Retourne un rectangle décrivant un aspect de dessin demandé. L’implémentation de ATL retourne E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Notes

Consultez [IViewObjectEx::GetRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getrect) dans le Kit de développement logiciel Windows.

##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus

Retourne des informations relatives à l’opacité de l’objet et les aspects de dessin sont pris en charge.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Notes

Par défaut, ATL définit `pdwStatus` pour indiquer que le contrôle prend en charge VIEWSTATUS_OPAQUE (les valeurs possibles sont dans le [double](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) énumération).

Consultez [IViewObjectEx::GetViewStatus](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) dans le Kit de développement logiciel Windows.

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

Vérifie si le point spécifié se trouve dans le rectangle spécifié et retourne un [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) valeur dans `pHitResult`.

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

Si `dwAspect` est égal à [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), la méthode retourne S_OK. Sinon, la méthode retourne E_FAIL.

Consultez [IViewObjectEx::QueryHitPoint](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) dans le Kit de développement logiciel Windows.

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

Vérifie si le rectangle d’affichage du contrôle chevauche n’importe quel point dans le rectangle de l’emplacement spécifié et retourne un [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) valeur dans `pHitResult`.

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

Si `dwAspect` est égal à [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), la méthode retourne S_OK. Sinon, la méthode retourne E_FAIL.

Consultez [IViewObjectEx::QueryHitRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) dans le Kit de développement logiciel Windows.

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

Configure une connexion entre le contrôle et un récepteur de notifications et le récepteur peut être notifié sur les modifications apportées dans l’affichage du contrôle.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Notes

Le pointeur vers le [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interface sur le récepteur de notifications est stocké dans le membre de données de classe de contrôle [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Consultez [IViewObject::SetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-setadvise) dans le Kit de développement logiciel Windows.

##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze

Libère la représentation sous forme de dessinée du contrôle. L’implémentation de ATL retourne E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Notes

Consultez [IViewObject::Unfreeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-unfreeze) dans le Kit de développement logiciel Windows.

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Implémentez cette méthode pour fermer le handle associé à cet objet.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Paramètres

*hHandle*<br/>
Le handle à fermer.

### <a name="return-value"></a>Valeur de retour

Sur la réussite ou une erreur HRESULT en cas d’échec, retourne S_OK.

### <a name="remarks"></a>Notes

Le handle passé à cette méthode a été précédemment associé à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant montre une implémentation simple de `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Implémentez cette méthode pour exécuter du code lorsque le handle associé à cet objet est signalé.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Paramètres

*dwParam*<br/>
Le paramètre utilisateur.

*hObject*<br/>
Le handle qui a été signalé.

### <a name="return-value"></a>Valeur de retour

Sur la réussite ou une erreur HRESULT en cas d’échec, retourne S_OK.

### <a name="remarks"></a>Notes

Le handle et la valeur DWORD/pointeur passé à cette méthode ont été précédemment associé à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant montre une implémentation simple de `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de contrôles ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Didacticiel](../../atl/active-template-library-atl-tutorial.md)<br/>
[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
