---
description: 'En savoir plus sur : classe CMFCVisualManagerWindows7'
title: CMFCVisualManagerWindows7, classe
ms.date: 03/27/2019
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
helpviewer_keywords:
- CMFCVisualManagerWindows7 Class [MFC]
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
ms.openlocfilehash: 108d4144bbcfbfcb82d91678611435f14365302e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331639"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>CMFCVisualManagerWindows7, classe

`CMFCVisualManagerWindows7`Donne à une application l’apparence d’une application Windows 7.

## <a name="syntax"></a>Syntaxe

```
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7)|Constructeur par défaut.|
|[CMFCVisualManagerWindows7 :: ~ CMFCVisualManagerWindows7](#_dtorcmfcvisualmanagerwindows7)|Destructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCVisualManagerWindows7::CleanStyle`|Efface le style visuel actuel et réinitialise le style visuel par défaut.|
|`CMFCVisualManagerWindows7::CleanUp`|Efface tous les objets de l’interface utilisateur et réinitialise les menus.|
|`CMFCVisualManagerWindows7::DrawNcBtn`|Dessine un bouton dans la zone non cliente sur le frame. L’infrastructure utilise cette méthode pour dessiner des boutons de réduction, d’agrandissement, de fermeture et de restauration dans l’angle supérieur droit du cadre de la fenêtre. Cette méthode est appelée uniquement lorsque le programme utilise un `Aero` thème.|
|`CMFCVisualManagerWindows7::DrawNcText`|Dessine du texte dans la zone non cliente du frame. L’infrastructure utilise cette méthode pour dessiner le titre de l’application dans la barre de titre en haut de la fenêtre frame.|
|`CMFCVisualManagerWindows7::DrawSeparator`|Dessine un séparateur sur la [classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).|
|`CMFCVisualManagerWindows7::GetRibbonBar`|Récupère la [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) associée à l’interface utilisateur.|
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](#getribboneditbackgroundcolor)|Obtient la couleur d’arrière-plan d’une zone d’édition du ruban.|
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|Remplace [CMFCVisualManager :: GetRibbonPopupBorderSize](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|Remplace [CMFCVisualManager :: GetRibbonQuickAccessToolBarChevronOffset](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|Remplace [CMFCVisualManager :: GetRibbonQuickAccessToolBarRightMargin](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|Remplace [CMFCVisualManagerWindows :: IsHighlightWholeMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|Remplace [CMFCVisualManager :: IsOwnerDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|
|`CMFCVisualManagerWindows7::IsRibbonPresent`|Détermine si un `CMFCRibbonBar` est présent et visible.|
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|Remplace [CMFCVisualManagerWindows :: OnDrawButtonBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|Remplace [CMFCVisualManagerWindows :: OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|Remplace [CMFCVisualManagerWindows :: OnDrawComboDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|Remplace [CMFCVisualManager :: OnDrawDefaultRibbonImage](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|Remplace [CMFCVisualManagerWindows :: OnDrawMenuBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|Remplace [CMFCVisualManager :: OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|Remplace [CMFCVisualManager :: OnDrawMenuLabel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|Substitue `CMFCVisualManager::OnDrawRadioButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|Remplace [CMFCVisualManager :: OnDrawRibbonApplicationButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|Remplace [CMFCVisualManager :: OnDrawRibbonButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|Remplace [CMFCVisualManager :: OnDrawRibbonCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|Remplace [CMFCVisualManager :: OnDrawRibbonCaptionButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|Remplace [CMFCVisualManager :: OnDrawRibbonCategory](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|Remplace [CMFCVisualManager :: OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|Remplace [CMFCVisualManager :: OnDrawRibbonDefaultPaneButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|Remplace [CMFCVisualManager :: OnDrawRibbonGalleryButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|Substitue `CMFCVisualManager::OnDrawRibbonLaunchButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|Remplace [CMFCVisualManager :: OnDrawRibbonMenuCheckFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|Remplace [CMFCVisualManager :: OnDrawRibbonPanel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|Remplace [CMFCVisualManager :: OnDrawRibbonPanelCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|Remplace [CMFCVisualManager :: OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|Remplace [CMFCVisualManager :: OnDrawRibbonRecentFilesFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|Remplace [CMFCVisualManager :: OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|Remplace [CMFCVisualManager :: OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|Remplace [CMFCVisualManager :: OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|Remplace [CMFCVisualManager :: OnDrawRibbonStatusBarPane](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|Remplace [CMFCVisualManager :: OnDrawRibbonTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|Remplace [CMFCVisualManagerWindows :: OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|
|`CMFCVisualManagerWindows7::OnFillBarBackground`|Remplace [CMFCVisualManagerWindows :: OnFillBarBackground](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|Remplace [CMFCVisualManagerWindows :: OnFillButtonInterior](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](#onfillmenuimagerect)|L’infrastructure appelle cette méthode lorsqu’elle remplit la zone autour des images d’élément de menu.|
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|Remplace [CMFCVisualManager :: OnFillRibbonButton](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|Remplace [CMFCVisualManager :: OnFillRibbonQuickAccessToolBarPopup](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|Remplace [CMFCVisualManagerWindows :: OnHighlightMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|
|`CMFCVisualManagerWindows7::OnNcActivate`|Remplace [CMFCVisualManager :: OnNcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|
|`CMFCVisualManagerWindows7::OnNcPaint`|Remplace [CMFCVisualManager :: OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|Remplace [CMFCVisualManagerWindows :: OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|
|`CMFCVisualManagerWindows7::SetResourceHandle`|Définit le descripteur de ressource qui décrit les attributs du gestionnaire visuel.|
|`CMFCVisualManagerWindows7::SetStyle`|Définit le modèle de couleurs de l' `CMFCVisualManagerWindows7` interface graphique.|

## <a name="remarks"></a>Notes

Utilisez la `CMFCVisualManagerWindows7` classe pour modifier l’apparence de votre application pour imiter une application Windows 7 par défaut. Cette classe peut ne pas être valide si votre application s’exécute sur une version de Windows antérieure à Windows 7. Dans ce scénario, l’application utilise le gestionnaire visuel par défaut défini dans [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md).

CMFCVisualManagerWindows7 hérite de plusieurs méthodes de la [classe CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md) et de la `CMFCVisualManager` classe. Les méthodes répertoriées dans la section précédente sont des méthodes nouvelles pour la `CMFCVisualManagerWindows7` classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

`CMFCVisualManagerWindows7`

## <a name="requirements"></a>Spécifications

**En-tête :** afxvisualmanagerwindows7. h

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="_dtorcmfcvisualmanagerwindows7"></a> CMFCVisualManagerWindows7 :: ~ CMFCVisualManagerWindows7

Destructeur par défaut.

```
virtual ~CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="cmfcvisualmanagerwindows7"></a> CMFCVisualManagerWindows7::CMFCVisualManagerWindows7

Constructeur par défaut.

```
CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7getribboneditbackgroundcolor"></a><a name="getribboneditbackgroundcolor"></a> CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor

Obtient la couleur d’arrière-plan d’une zone d’édition du ruban.

```
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,
    BOOL bIsHighlighted,
    BOOL bIsPaneHighlighted,
    BOOL bIsDisabled);
```

### <a name="parameters"></a>Paramètres

*pEdit*<br/>
dans Pointeur vers le contrôle d’édition. Cette valeur ne peut pas être NULL.

*bIsHighlighted*<br/>
à Retourne une valeur indiquant si la zone du ruban est mise en surbrillance.

*bIsPaneHighlighted*<br/>
à Retourne la valeur TRUE si le panneau du ruban qui contient *pEdit* est mis en surbrillance.

*bIsDisabled*<br/>
à Retourne une valeur indiquant si *pEdit* est désactivé.

### <a name="return-value"></a>Valeur renvoyée

Couleur d’arrière-plan de la zone d’édition *pEdit*.

### <a name="remarks"></a>Notes

## <a name="cmfcvisualmanagerwindows7onfillmenuimagerect"></a><a name="onfillmenuimagerect"></a> CMFCVisualManagerWindows7::OnFillMenuImageRect

Le Framework appelle cette méthode lorsqu’il remplit la zone autour d’une image d’élément de menu.

```
virtual void OnFillMenuImageRect(
    CDC* pDC,
    CMFCToolBarButton* pButton,
    CRect rectangle,
    CMFCVisualManager::AFX_BUTTON_STATE state);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers le contexte de périphérique d’un bouton de menu.

*pButton*<br/>
dans Pointeur vers un `CMFCToolBarButton` . L’infrastructure remplit l’arrière-plan de ce bouton.

*Rectangle*<br/>
dans Rectangle qui spécifie les limites de la zone d’image du bouton de menu.

*state*<br/>
dans État du bouton.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager, classe](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerWindows, classe](../../mfc/reference/cmfcvisualmanagerwindows-class.md)
