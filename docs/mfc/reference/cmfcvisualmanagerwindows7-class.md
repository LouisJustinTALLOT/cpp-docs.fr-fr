---
title: Cmfcvisualmanagerwindows7, classe
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
ms.openlocfilehash: e729201f1a6b6fd41286cc6af2b8c08fc7ee697c
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565517"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>Cmfcvisualmanagerwindows7, classe

Le `CMFCVisualManagerWindows7` donne à une application l’apparence d’une application de Windows 7.

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
|`CMFCVisualManagerWindows7::CleanUp`|Efface tous les objets dans l’interface utilisateur et réinitialise les menus.|
|`CMFCVisualManagerWindows7::DrawNcBtn`|Dessine un bouton dans la zone non cliente sur le frame. Les utilisations de framework cette méthode pour dessiner réduire, agrandir, fermer et restaurer des boutons dans le coin supérieur droit du frame de fenêtre. Cette méthode est appelée uniquement lorsque le programme utilise une `Aero` thème.|
|`CMFCVisualManagerWindows7::DrawNcText`|Dessine le texte dans la zone non cliente sur le frame. Le framework utilise cette méthode pour dessiner le titre de l’application dans la barre de titre en haut de la fenêtre frame.|
|`CMFCVisualManagerWindows7::DrawSeparator`|Dessine un séparateur sur la [cmfctoolbar, classe](../../mfc/reference/cmfctoolbar-class.md).|
|`CMFCVisualManagerWindows7::GetRibbonBar`|Récupère le [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) associé à l’interface utilisateur.|
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](#getribboneditbackgroundcolor)|Obtient une couleur d’arrière-plan de la ruban modifier.|
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|Substitue [CMFCVisualManager::GetRibbonPopupBorderSize](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|Substitue [CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|Overrides [CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|Overrides [CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|Substitue [CMFCVisualManager::IsOwnerDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|
|`CMFCVisualManagerWindows7::IsRibbonPresent`|Détermine si un `CMFCRibbonBar` est présent et visible.|
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|Substitue [CMFCVisualManagerWindows::OnDrawButtonBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|Substitue [CMFCVisualManagerWindows::OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|Substitue [CMFCVisualManagerWindows::OnDrawComboDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|Overrides [CMFCVisualManager::OnDrawDefaultRibbonImage](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|Substitue [CMFCVisualManagerWindows::OnDrawMenuBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|Substitue [CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|Substitue [CMFCVisualManager::OnDrawMenuLabel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|Remplacements `CMFCVisualManager::OnDrawRadioButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|Substitue [CMFCVisualManager::OnDrawRibbonApplicationButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|Substitue [CMFCVisualManager::OnDrawRibbonButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|Substitue [CMFCVisualManager::OnDrawRibbonCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|Substitue [CMFCVisualManager::OnDrawRibbonCaptionButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|Substitue [CMFCVisualManager::OnDrawRibbonCategory](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|Substitue [CMFCVisualManager::OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|Substitue [CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|Substitue [CMFCVisualManager::OnDrawRibbonGalleryButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|Remplacements `CMFCVisualManager::OnDrawRibbonLaunchButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|Substitue [CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|Substitue [CMFCVisualManager::OnDrawRibbonPanel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|Substitue [CMFCVisualManager::OnDrawRibbonPanelCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|Substitue [CMFCVisualManager::OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|Substitue [CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|Substitue [CMFCVisualManager::OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|Substitue [CMFCVisualManager::OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|Substitue [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|Substitue [CMFCVisualManager::OnDrawRibbonStatusBarPane](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|Substitue [CMFCVisualManager::OnDrawRibbonTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|Substitue [CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|
|`CMFCVisualManagerWindows7::OnFillBarBackground`|Substitue [CMFCVisualManagerWindows::OnFillBarBackground](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|Substitue [CMFCVisualManagerWindows::OnFillButtonInterior](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](#onfillmenuimagerect)|L’infrastructure appelle cette méthode quand il remplit la zone autour des images d’élément de menu.|
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|Substitue [CMFCVisualManager::OnFillRibbonButton](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|Overrides [CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|Overrides [CMFCVisualManagerWindows::OnHighlightMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|
|`CMFCVisualManagerWindows7::OnNcActivate`|Substitue [CMFCVisualManager::OnNcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|
|`CMFCVisualManagerWindows7::OnNcPaint`|Substitue [CMFCVisualManager::OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|Overrides [CMFCVisualManagerWindows::OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|
|`CMFCVisualManagerWindows7::SetResourceHandle`|Définit le handle de ressource qui décrit les attributs du Gestionnaire visuel.|
|`CMFCVisualManagerWindows7::SetStyle`|Définit le jeu de couleurs de la `CMFCVisualManagerWindows7` l’interface graphique utilisateur.|

## <a name="remarks"></a>Notes

Utilisez la `CMFCVisualManagerWindows7` classe pour modifier l’apparence de votre application pour imiter une application de Windows 7 par défaut. Cette classe n’est peut-être pas valide si votre application s’exécute sur une version de Windows antérieure à Windows 7. Dans ce scénario, l’application utilise le Gestionnaire visuel par défaut défini dans [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md).

Le CMFCVisualManagerWindows7 hérite plusieurs méthodes à la fois le [CMFCVisualManagerWindows, classe](../../mfc/reference/cmfcvisualmanagerwindows-class.md) et `CMFCVisualManager` classe. Les méthodes répertoriées dans la section précédente sont nouvelles pour la `CMFCVisualManagerWindows7` classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

`CMFCVisualManagerWindows7`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxvisualmanagerwindows7.h

##  <a name="_dtorcmfcvisualmanagerwindows7"></a>  CMFCVisualManagerWindows7 :: ~ CMFCVisualManagerWindows7

Destructeur par défaut.

```
virtual ~CMFCVisualManagerWindows7();
```

##  <a name="cmfcvisualmanagerwindows7"></a>  CMFCVisualManagerWindows7::CMFCVisualManagerWindows7

Constructeur par défaut.

```
CMFCVisualManagerWindows7();
```

##  <a name="getribboneditbackgroundcolor"></a>  CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor

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
[in] Pointeur vers le contrôle d’édition. Cette valeur ne peut pas être NULL.

*bIsHighlighted*<br/>
[out] Retourne si la zone du ruban est mis en surbrillance.

*bIsPaneHighlighted*<br/>
[out] Retourne la valeur TRUE si le ruban du panneau qui contient *pEdit* est mis en surbrillance.

*bIsDisabled*<br/>
[out] Retourne si *pEdit* est désactivé.

### <a name="return-value"></a>Valeur de retour

La couleur d’arrière-plan de la zone d’édition *pEdit*.

### <a name="remarks"></a>Notes

##  <a name="onfillmenuimagerect"></a>  CMFCVisualManagerWindows7::OnFillMenuImageRect

L’infrastructure appelle cette méthode quand il remplit la zone autour d’une image d’élément de menu.

```
virtual void OnFillMenuImageRect(
    CDC* pDC,
    CMFCToolBarButton* pButton,
    CRect rectangle,
    CMFCVisualManager::AFX_BUTTON_STATE state);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers le contexte de périphérique d’un bouton de menu.

*pButton*<br/>
[in] Un pointeur vers un `CMFCToolBarButton`. L’infrastructure complète l’arrière-plan de ce bouton.

*rectangle*<br/>
[in] Un rectangle qui spécifie les limites de la zone d’image de bouton menu.

*state*<br/>
[in] L’état du bouton.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager, classe](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerWindows, classe](../../mfc/reference/cmfcvisualmanagerwindows-class.md)
