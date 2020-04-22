---
title: Classe IPropertyPageImpl
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: 154bfb5beb258ff26649f44f0bd4c23fb8708977
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745862"
---
# <a name="ipropertypageimpl-class"></a>Classe IPropertyPageImpl

Cette classe `IUnknown` implémente et fournit une implémentation par défaut de l’interface [IPropertyPage.](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IPropertyPageImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPropertyPageImpl::Activer](#activate)|Crée la fenêtre de boîte de dialogue pour la page de propriété.|
|[IPropertyPageImpl::Appliquer](#apply)|Applique les valeurs actuelles de la `SetObjects`page de propriété aux objets sous-jacents spécifiés par . La mise en œuvre d’ATL S_OK.|
|[IPropertyPageImpl::Deactivate](#deactivate)|Détruit la fenêtre `Activate`créée avec .|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Récupère des informations sur la page de propriété.|
|[IPropertyPageImpl::Aide](#help)|Invoque l’aide De Windows pour la page de propriété.|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Indique si la page de propriété a changé depuis qu’elle a été activée.|
|[IPropertyPageImpl::Move](#move)|Positionne et resize la boîte de dialogue de la page de propriété.|
|[IPropertyPageImpl::SetDirty](#setdirty)|Signale l’état de la page de propriété comme changé ou inchangé.|
|[IPropertyPageImpl::SetObjects](#setobjects)|Fournit un `IUnknown` tableau de pointeurs pour les objets associés à la page de propriété. Ces objets reçoivent les valeurs actuelles `Apply`de la page de propriété par le biais d’un appel à .|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Fournit à la `IPropertyPageSite` page de propriété un pointeur, à travers lequel la page de propriété communique avec le cadre de propriété.|
|[IPropertyPageImpl::Show](#show)|Rend la boîte de dialogue de la page de propriété visible ou invisible.|
|[IPropertyPageImpl::TranslateAccelerator IPropertyPageImpl::TranslateAccelerator IPropertyPageImpl::TranslateAccelerator IProp](#translateaccelerator)|Traite une frappe spécifiée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Précise si l’état de la page de propriété a changé.|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Stocke l’identifiant de ressource associé à la chaîne de texte décrivant la page de propriété.|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Stocke l’identifiant de contexte pour le sujet d’aide associé à la page de propriété.|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Stocke l’identifiant de ressource associé au nom du fichier d’aide décrivant la page de propriété.|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Stocke l’identifiant de ressource associé à la chaîne de texte qui apparaît dans l’onglet pour la page de propriété.|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Stocke le nombre d’objets associés à la page de propriété.|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Points à `IPropertyPageSite` l’interface à travers laquelle la page de propriété communique avec le cadre de propriété.|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Points à un `IUnknown` tableau de pointeurs aux objets associés à la page de propriété.|
|[IPropertyPageImpl::m_size](#m_size)|Stocke la hauteur et la largeur de la boîte de dialogue de la page de propriété, en pixels.|

## <a name="remarks"></a>Notes

[L’interface IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) permet à un objet de gérer une page de propriété particulière dans une feuille de propriété. La `IPropertyPageImpl` classe fournit une implémentation par défaut de cette interface et implémente en `IUnknown` envoyant des informations à l’appareil de décharge dans les versions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ipropertypageimplactivate"></a><a name="activate"></a>IPropertyPageImpl::Activer

Crée la fenêtre de boîte de dialogue pour la page de propriété.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Notes

Par défaut, la boîte de dialogue est toujours sans mode, quelle que soit la valeur du paramètre *bModal.*

Voir [IPropertyPage::Activez](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) dans le SDK Windows.

## <a name="ipropertypageimplapply"></a><a name="apply"></a>IPropertyPageImpl::Appliquer

Applique les valeurs actuelles de la `SetObjects`page de propriété aux objets sous-jacents spécifiés par .

```
HRESULT Apply();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IPropertyPage::Appliquer](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) dans le SDK Windows.

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a>IPropertyPageImpl::Deactivate

Détruit la fenêtre de boîte de dialogue créée avec [Activate](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Notes

Voir [IPropertyPage::Deactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) dans le SDK Windows.

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo

Remplit la structure *pPageInfo* avec des informations contenues dans les membres des données.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Notes

`GetPageInfo`charge les ressources de chaîne associées à [m_dwDocString,](#m_dwdocstring) [m_dwHelpFile,](#m_dwhelpfile)et [m_dwTitle](#m_dwtitle).

Voir [IPropertyPage:GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) dans le SDK Windows.

## <a name="ipropertypageimplhelp"></a><a name="help"></a>IPropertyPageImpl::Aide

Invoque l’aide De Windows pour la page de propriété.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Notes

Voir [IPropertyPage:Help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) in the Windows SDK.

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl

Constructeur.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Notes

Initialise tous les membres des données.

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty

Indique si la page de propriété a changé depuis qu’elle a été activée.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Notes

`IsPageDirty`retourne S_OK si la page a changé depuis qu’elle a été activée.

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty

Précise si l’état de la page de propriété a changé.

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects

Stocke le nombre d’objets associés à la page de propriété.

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext

Stocke l’identifiant de contexte pour le sujet d’aide associé à la page de propriété.

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString

Stocke l’identifiant de ressource associé à la chaîne de texte décrivant la page de propriété.

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile

Stocke l’identifiant de ressource associé au nom du fichier d’aide décrivant la page de propriété.

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle

Stocke l’identifiant de ressource associé à la chaîne de texte qui apparaît dans l’onglet pour la page de propriété.

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite

Indique l’interface [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) à travers laquelle la page de propriété communique avec le cadre de la propriété.

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk

Points à un `IUnknown` tableau de pointeurs aux objets associés à la page de propriété.

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a>IPropertyPageImpl::m_size

Stocke la hauteur et la largeur de la boîte de dialogue de la page de propriété, en pixels.

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a>IPropertyPageImpl::Move

Positionne et resize la boîte de dialogue de la page de propriété.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Notes

Voir [IPropertyPage:Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) in the Windows SDK.

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a>IPropertyPageImpl::SetDirty

Signale l’état de la page de propriété comme changé ou inchangé, selon la valeur de *bDirty*.

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Paramètres

*bDirty (en)*<br/>
[dans] Si VRAI, l’état de la page de propriété est marqué comme changé. Sinon, il est marqué comme inchangé.

### <a name="remarks"></a>Notes

Si nécessaire, `SetDirty` informe le cadre que la page de propriété a changé.

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a>IPropertyPageImpl::SetObjects

Fournit un `IUnknown` tableau de pointeurs pour les objets associés à la page de propriété.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Notes

Voir [IPropertyPage:SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) in the Windows SDK.

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a>IPropertyPageImpl::SetPageSite

Fournit la page de propriété avec un pointeur [IPropertyPageSite,](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) à travers lequel la page de propriété communique avec le cadre de propriété.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Notes

Voir [IPropertyPage:SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) dans le SDK Windows.

## <a name="ipropertypageimplshow"></a><a name="show"></a>IPropertyPageImpl::Show

Rend la boîte de dialogue de la page de propriété visible ou invisible.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Notes

Voir [IPropertyPage:Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) in the Windows SDK.

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator IPropertyPageImpl::TranslateAccelerator IPropertyPageImpl::TranslateAccelerator IProp

Processus de la `pMsg`frappe spécifiée dans .

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Notes

Voir [IPropertyPage:TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)<br/>
[Classe IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
