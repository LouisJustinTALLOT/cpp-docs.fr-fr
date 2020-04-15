---
title: Classe IViewObjectExImpl
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
ms.openlocfilehash: 59c5657dcd892544f7e790b52325cb9ecba0dd56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326341"
---
# <a name="iviewobjecteximpl-class"></a>Classe IViewObjectExImpl

Cette classe `IUnknown` implémente et fournit des implémentations par défaut des interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)et [IViewObjectEx.](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IViewObjectExImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Entraîne une représentation du contrôle sur le contexte d’un appareil.|
|[IViewObjectExImpl::Freeze](#freeze)|Gele la représentation tirée d’un contrôle de `Unfreeze`sorte qu’il ne changera pas jusqu’à ce qu’un . La mise en œuvre d’ATL E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Récupère une connexion d’évier de conseil existante sur le contrôle, s’il y en a une.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Retourne la palette logique utilisée par le contrôle pour le dessin. La mise en œuvre d’ATL E_NOTIMPL.|
|[IViewObjectExImpl::GetExtent](#getextent)|Récupère la taille de l’écran du contrôle dans les unités HIMETRIC (0,01 millimètre par unité) du membre des données de la classe de contrôle [CComControlBase ::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Fournit des conseils de dimensionnement à partir du conteneur pour l’objet à utiliser que l’utilisateur le resize.|
|[IViewObjectExImpl::GetRect](#getrect)|Retourne un rectangle décrivant un aspect de dessin demandé. La mise en œuvre d’ATL E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Retourne des informations sur l’opacité de l’objet et quels aspects de dessin sont pris en charge.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Vérifie si le point spécifié se trouve dans le `pHitResult`rectangle spécifié et renvoie une valeur [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en .|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Vérifie si le rectangle d’affichage du contrôle chevauche n’importe quel point `pHitResult`dans le rectangle d’emplacement spécifié et renvoie une valeur HITRESULT en .|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Définit une connexion entre le contrôle et un évier de conseil afin que l’évier puisse être informé des changements dans la vue du contrôle.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Dégele la représentation tirée du contrôle. La mise en œuvre d’ATL E_NOTIMPL.|

## <a name="remarks"></a>Notes

Les interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)et [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) permettent à un contrôle de s’afficher directement, et de créer et de gérer un évier de conseil pour aviser le conteneur des changements dans l’écran de commande. L’interface `IViewObjectEx` fournit un support pour les fonctionnalités de contrôle étendues telles que le dessin sans scintillement, les contrôles non rectangulaires et transparents, et les essais de hit (par exemple, la proximité d’un clic de souris doit être considérée sur le contrôle). La `IViewObjectExImpl` classe fournit une implémentation `IUnknown` par défaut de ces interfaces et instruments en envoyant des informations à l’appareil de décharge dans les versions de débogé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="iviewobjecteximpldraw"></a><a name="draw"></a>IViewObjectExImpl::Draw

Entraîne une représentation du contrôle sur le contexte d’un appareil.

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

Cette méthode `CComControl::OnDrawAdvanced` appelle qui à son `OnDraw` tour appelle la méthode de votre classe de contrôle. Une `OnDraw` méthode est automatiquement ajoutée à votre classe de contrôle lorsque vous créez votre contrôle avec le assistant de contrôle ATL. Le défaut de `OnDraw` l’Assistant dessine un rectangle avec l’étiquette "ATL 3.0".

Voir [IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) dans le SDK Windows.

## <a name="iviewobjecteximplfreeze"></a><a name="freeze"></a>IViewObjectExImpl::Freeze

Gele la représentation tirée d’un contrôle de `Unfreeze`sorte qu’il ne changera pas jusqu’à ce qu’un . La mise en œuvre d’ATL E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Notes

Voir [IViewObject::Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) in the Windows SDK.

## <a name="iviewobjecteximplgetadvise"></a><a name="getadvise"></a>IViewObjectExImpl::GetAdvise

Récupère une connexion d’évier de conseil existante sur le contrôle, s’il y en a une.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Notes

L’évier de conseil est stocké dans le membre de données de classe de contrôle [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Voir [IViewObject:GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) in the Windows SDK.

## <a name="iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a>IViewObjectExImpl::GetColorSet

Retourne la palette logique utilisée par le contrôle pour le dessin. La mise en œuvre d’ATL E_NOTIMPL.

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

Voir [IViewObject:GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) dans le Windows SDK.

## <a name="iviewobjecteximplgetextent"></a><a name="getextent"></a>IViewObjectExImpl::GetExtent

Récupère la taille de l’écran du contrôle dans les unités HIMETRIC (0,01 millimètre par unité) du membre des données de la classe de contrôle [CComControlBase ::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Notes

Voir [IViewObject2:GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) dans le Windows SDK.

## <a name="iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent

Fournit des conseils de dimensionnement à partir du conteneur pour l’objet à utiliser que l’utilisateur le resize.

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

S’il `dwAspect` est DVASPECT_CONTENT et *pExtentInfo->dwExtentMode* est DVEXTENT_CONTENT, `psizel` définit - à la classe de données membre de la classe de contrôle [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). Sinon, renvoie une erreur HRESULT.

Voir [IViewObjectEx:GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) dans le SDK Windows.

## <a name="iviewobjecteximplgetrect"></a><a name="getrect"></a>IViewObjectExImpl::GetRect

Retourne un rectangle décrivant un aspect de dessin demandé. La mise en œuvre d’ATL E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Notes

Voir [IViewObjectEx:GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) dans le Windows SDK.

## <a name="iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus

Retourne des informations sur l’opacité de l’objet et quels aspects de dessin sont pris en charge.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Notes

Par défaut, ATL s’établit `pdwStatus` pour indiquer que le contrôle prend en charge VIEWSTATUS_OPAQUE (les valeurs possibles sont dans le recensement [VIEWSTATUS).](/windows/win32/api/ocidl/ne-ocidl-viewstatus)

Voir [IViewObjectEx:GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) dans le SDK Windows.

## <a name="iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint

Vérifie si le point spécifié se trouve dans le `pHitResult`rectangle spécifié et renvoie une valeur [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en .

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

Si `dwAspect` elle est égale [DVASPECT_CONTENT,](/windows/win32/api/wtypes/ne-wtypes-dvaspect)la méthode renvoie S_OK. Sinon, la méthode revient E_FAIL.

Voir [IViewObjectEx:QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) dans le SDK Windows.

## <a name="iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect

Vérifie si le rectangle d’affichage du contrôle chevauche n’importe quel point `pHitResult`dans le rectangle d’emplacement spécifié et renvoie une valeur [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en .

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

Si `dwAspect` elle est égale [DVASPECT_CONTENT,](/windows/win32/api/wtypes/ne-wtypes-dvaspect)la méthode renvoie S_OK. Sinon, la méthode revient E_FAIL.

Voir [IViewObjectEx:QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) dans le SDK Windows.

## <a name="iviewobjecteximplsetadvise"></a><a name="setadvise"></a>IViewObjectExImpl::SetAdvise

Définit une connexion entre le contrôle et un évier de conseil afin que l’évier puisse être informé des changements dans la vue du contrôle.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Notes

Le pointeur de [l’interface IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) sur l’évier de conseil est stocké dans le membre de données de classe de contrôle [CComControlBase:m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Voir [IViewObject:SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) in the Windows SDK.

## <a name="iviewobjecteximplunfreeze"></a><a name="unfreeze"></a>IViewObjectExImpl::Unfreeze

Dégele la représentation tirée du contrôle. La mise en œuvre d’ATL E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Notes

Voir [IViewObject:Unfreeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) in the Windows SDK.

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle

Implémentez cette méthode pour fermer la poignée associée à cet objet.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Paramètres

*hHandle*<br/>
La poignée à fermer.

### <a name="return-value"></a>Valeur de retour

Retour S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

La poignée passée à cette méthode était auparavant associée à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant montre `IWorkerThreadClient::CloseHandle`une simple implémentation de .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Exécuter

Implémentez cette méthode pour exécuter le code lorsque la poignée associée à cet objet devient signalée.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Paramètres

*dwParam dwParam*<br/>
Le paramètre de l’utilisateur.

*hObject*<br/>
La poignée qui est devenue signalée.

### <a name="return-value"></a>Valeur de retour

Retour S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

La poignée et DWORD / pointeur passé à cette méthode ont été précédemment associés à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Exemple

Le code suivant montre `IWorkerThreadClient::Execute`une simple implémentation de .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX contrôle les interfaces](/windows/win32/com/activex-controls-interfaces)<br/>
[Didacticiel](../../atl/active-template-library-atl-tutorial.md)<br/>
[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
