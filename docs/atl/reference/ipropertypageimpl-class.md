---
description: 'En savoir plus sur : IPropertyPageImpl, classe'
title: IPropertyPageImpl, classe
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
ms.openlocfilehash: c3b8a52d3aff0beeb175a18af56a207284ff538d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158138"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl, classe

Cette classe implémente `IUnknown` et fournit une implémentation par défaut de l’interface [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IPropertyPageImpl` .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[IPropertyPageImpl :: IPropertyPageImpl](#ipropertypageimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IPropertyPageImpl :: Activate](#activate)|Crée la fenêtre de boîte de dialogue pour la page de propriétés.|
|[IPropertyPageImpl :: apply](#apply)|Applique les valeurs de page de propriétés actuelles aux objets sous-jacents spécifiés via `SetObjects` . L’implémentation ATL retourne S_OK.|
|[IPropertyPageImpl ::D eactivate](#deactivate)|Détruit la fenêtre créée avec `Activate` .|
|[IPropertyPageImpl :: GetPageInfo](#getpageinfo)|Récupère des informations sur la page de propriétés.|
|[IPropertyPageImpl :: help](#help)|Appelle l’aide de Windows pour la page de propriétés.|
|[IPropertyPageImpl :: IsPageDirty](#ispagedirty)|Indique si la page de propriétés a été modifiée depuis son activation.|
|[IPropertyPageImpl :: Move](#move)|Positionne et redimensionne la boîte de dialogue page de propriétés.|
|[IPropertyPageImpl :: SetDirty](#setdirty)|Signale que l’état de la page de propriétés est modifié ou inchangé.|
|[IPropertyPageImpl :: SetObjects](#setobjects)|Fournit un tableau de `IUnknown` pointeurs pour les objets associés à la page de propriétés. Ces objets reçoivent les valeurs de la page de propriétés actuelle via un appel à `Apply` .|
|[IPropertyPageImpl :: SetPageSite](#setpagesite)|Fournit la page de propriétés avec un `IPropertyPageSite` pointeur, par le biais duquel la page de propriétés communique avec le frame de propriété.|
|[IPropertyPageImpl :: Show](#show)|Rend la boîte de dialogue page de propriétés visible ou invisible.|
|[IPropertyPageImpl :: TranslateAccelerator](#translateaccelerator)|Traite une séquence de touches spécifiée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IPropertyPageImpl :: m_bDirty](#m_bdirty)|Spécifie si l’état de la page de propriétés a changé.|
|[IPropertyPageImpl :: m_dwDocString](#m_dwdocstring)|Stocke l’identificateur de ressource associé à la chaîne de texte décrivant la page de propriétés.|
|[IPropertyPageImpl :: m_dwHelpContext](#m_dwhelpcontext)|Stocke l’identificateur de contexte pour la rubrique d’aide associée à la page de propriétés.|
|[IPropertyPageImpl :: m_dwHelpFile](#m_dwhelpfile)|Stocke l’identificateur de ressource associé au nom du fichier d’aide décrivant la page de propriétés.|
|[IPropertyPageImpl :: m_dwTitle](#m_dwtitle)|Stocke l’identificateur de ressource associé à la chaîne de texte qui apparaît dans l’onglet de la page de propriétés.|
|[IPropertyPageImpl :: m_nObjects](#m_nobjects)|Stocke le nombre d’objets associés à la page de propriétés.|
|[IPropertyPageImpl :: m_pPageSite](#m_ppagesite)|Pointe vers l' `IPropertyPageSite` interface par le biais de laquelle la page de propriétés communique avec le frame de propriété.|
|[IPropertyPageImpl :: m_ppUnk](#m_ppunk)|Pointe vers un tableau de `IUnknown` pointeurs vers les objets associés à la page de propriétés.|
|[IPropertyPageImpl :: m_size](#m_size)|Stocke, en pixels, la hauteur et la largeur de la boîte de dialogue de la page de propriétés.|

## <a name="remarks"></a>Notes

L’interface [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) permet à un objet de gérer une page de propriétés particulière dans une feuille de propriétés. `IPropertyPageImpl`La classe fournit une implémentation par défaut de cette interface et implémente `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="ipropertypageimplactivate"></a><a name="activate"></a> IPropertyPageImpl :: Activate

Crée la fenêtre de boîte de dialogue pour la page de propriétés.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Notes

Par défaut, la boîte de dialogue est toujours non modale, quelle que soit la valeur du paramètre *bModal* .

Consultez [IPropertyPage :: Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) dans la SDK Windows.

## <a name="ipropertypageimplapply"></a><a name="apply"></a> IPropertyPageImpl :: apply

Applique les valeurs de page de propriétés actuelles aux objets sous-jacents spécifiés via `SetObjects` .

```
HRESULT Apply();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IPropertyPage :: apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) dans le SDK Windows.

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a> IPropertyPageImpl ::D eactivate

Détruit la fenêtre de boîte de dialogue créée avec [Activate](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Notes

Consultez [IPropertyPage ::D eactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) dans le SDK Windows.

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a> IPropertyPageImpl :: GetPageInfo

Remplit la structure *pPageInfo* avec les informations contenues dans les membres de données.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Notes

`GetPageInfo` charge les ressources de type chaîne associées à [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile)et [m_dwTitle](#m_dwtitle).

Consultez [IPropertyPage :: GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) dans le SDK Windows.

## <a name="ipropertypageimplhelp"></a><a name="help"></a> IPropertyPageImpl :: help

Appelle l’aide de Windows pour la page de propriétés.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Notes

Consultez [IPropertyPage :: help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) dans le SDK Windows.

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a> IPropertyPageImpl :: IPropertyPageImpl

Constructeur.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Notes

Initialise tous les membres de données.

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a> IPropertyPageImpl :: IsPageDirty

Indique si la page de propriétés a été modifiée depuis son activation.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Notes

`IsPageDirty` retourne S_OK si la page a été modifiée depuis son activation.

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a> IPropertyPageImpl :: m_bDirty

Spécifie si l’état de la page de propriétés a changé.

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a> IPropertyPageImpl :: m_nObjects

Stocke le nombre d’objets associés à la page de propriétés.

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a> IPropertyPageImpl :: m_dwHelpContext

Stocke l’identificateur de contexte pour la rubrique d’aide associée à la page de propriétés.

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a> IPropertyPageImpl :: m_dwDocString

Stocke l’identificateur de ressource associé à la chaîne de texte décrivant la page de propriétés.

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a> IPropertyPageImpl :: m_dwHelpFile

Stocke l’identificateur de ressource associé au nom du fichier d’aide décrivant la page de propriétés.

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a> IPropertyPageImpl :: m_dwTitle

Stocke l’identificateur de ressource associé à la chaîne de texte qui apparaît dans l’onglet de la page de propriétés.

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a> IPropertyPageImpl :: m_pPageSite

Pointe vers l’interface [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) par le biais de laquelle la page de propriétés communique avec le frame de propriété.

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a> IPropertyPageImpl :: m_ppUnk

Pointe vers un tableau de `IUnknown` pointeurs vers les objets associés à la page de propriétés.

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a> IPropertyPageImpl :: m_size

Stocke, en pixels, la hauteur et la largeur de la boîte de dialogue de la page de propriétés.

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a> IPropertyPageImpl :: Move

Positionne et redimensionne la boîte de dialogue page de propriétés.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Notes

Consultez [IPropertyPage :: Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) dans le SDK Windows.

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a> IPropertyPageImpl :: SetDirty

Signale que l’état de la page de propriétés est modifié ou inchangé, en fonction de la valeur de *bDirty*.

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Paramètres

*bDirty*<br/>
dans Si la valeur est TRUE, l’état de la page de propriétés est marqué comme modifié. Dans le cas contraire, elle est marquée comme inchangée.

### <a name="remarks"></a>Notes

Si nécessaire, `SetDirty` indique au frame que la page de propriétés a changé.

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a> IPropertyPageImpl :: SetObjects

Fournit un tableau de `IUnknown` pointeurs pour les objets associés à la page de propriétés.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Notes

Consultez [IPropertyPage :: SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) dans le SDK Windows.

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a> IPropertyPageImpl :: SetPageSite

Fournit la page de propriétés avec un pointeur [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) , par le biais duquel la page de propriétés communique avec le frame de propriété.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Notes

Consultez [IPropertyPage :: SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) dans le SDK Windows.

## <a name="ipropertypageimplshow"></a><a name="show"></a> IPropertyPageImpl :: Show

Rend la boîte de dialogue page de propriétés visible ou invisible.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Notes

Consultez [IPropertyPage :: Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) dans le SDK Windows.

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a> IPropertyPageImpl :: TranslateAccelerator

Traite la séquence de touches spécifiée dans `pMsg` .

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Notes

Consultez [IPropertyPage :: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[IPropertyPage2Impl, classe](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl, classe](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl, classe](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
