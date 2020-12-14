---
description: 'En savoir plus sur : classe CMFCOutlookBarTabCtrl'
title: CMFCOutlookBarTabCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: b969fbb592fc3098dc8d287004fab90da6f30111
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333495"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

Contrôle onglet qui a l'apparence visuelle du **Volet de navigation** dans Microsoft Outlook.
Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Constructeur par défaut.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl :: AddControl](#addcontrol)|Ajoute un contrôle Windows sous la forme d’un nouvel onglet dans la barre Outlook.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Appelé par l’infrastructure pour déterminer les dimensions de la zone d’édition qui apparaît lorsqu’un utilisateur renomme un onglet. (Substitue `CMFCBaseTabCtrl::CalcRectEdit` .)|
|[CMFCOutlookBarTabCtrl :: CanShowFewerPageButtons](#canshowfewerpagebuttons)|Appelée par l’infrastructure pendant le redimensionnement des opérations pour déterminer si moins de boutons de la page d’onglets Outlook peuvent être affichés que ce qui est actuellement visible.|
|[CMFCOutlookBarTabCtrl :: CanShowMorePageButtons](#canshowmorepagebuttons)|Appelée par l’infrastructure pendant le redimensionnement des opérations pour déterminer si d’autres boutons de la page d’onglets Outlook peuvent être affichés que ceux actuellement visibles.|
|[CMFCOutlookBarTabCtrl :: Create](#create)|Crée le contrôle onglet de barre Outlook.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCOutlookBarTabCtrl :: EnableAnimation](#enableanimation)|Spécifie si l’animation qui se produit pendant le basculement entre les onglets actifs est activée.|
|[CMFCOutlookBarTabCtrl :: EnableInPlaceEdit](#enableinplaceedit)|Spécifie si un utilisateur peut modifier les étiquettes de texte sur les boutons d’onglet de la barre Outlook. (Substitue [CMFCBaseTabCtrl :: EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl :: EnableScrollButtons](#enablescrollbuttons)|Appelée par l’infrastructure pour activer les boutons qui permettent à l’utilisateur de faire défiler les boutons du volet barre Outlook.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identifie le volet qui contient un point spécifié. (Substitue [CMFCBaseTabCtrl :: FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl :: GetBorderSize](#getbordersize)|Retourne la taille de bordure du contrôle onglet Outlook.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Récupère la taille et la position de la zone d’onglet du contrôle onglet. (Substitue [CMFCBaseTabCtrl :: GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCOutlookBarTabCtrl :: GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl :: IsAnimation](#isanimation)|Détermine si l’animation qui se produit pendant le basculement entre les onglets actifs est activée.|
|[CMFCOutlookBarTabCtrl :: IsMode2003](#ismode2003)|Détermine si le contrôle onglet de la barre Outlook est dans un mode qui émule Microsoft Outlook 2003.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Détermine si un point se trouve à l’intérieur de la zone d’onglet. (Substitue [CMFCBaseTabCtrl :: IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Détermine si un onglet est détachable. (Substitue [CMFCBaseTabCtrl :: IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Appelé par le Framework lorsqu’un onglet est inséré ou supprimé. (Substitue `CMFCBaseTabCtrl::OnChangeTabs`.)|
|[CMFCOutlookBarTabCtrl :: OnShowFewerPageButtons](#onshowfewerpagebuttons)|Appelée par l’infrastructure pour réduire le nombre de boutons de page d’onglets visibles.|
|[CMFCOutlookBarTabCtrl :: OnShowMorePageButtons](#onshowmorepagebuttons)|Appelée par l’infrastructure pour augmenter le nombre de boutons de page d’onglets visibles.|
|[CMFCOutlookBarTabCtrl :: OnShowOptions](#onshowoptions)|Affiche la boîte de dialogue **Options du volet de navigation** .|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Recalcule la disposition interne du contrôle onglet. (Substitue [CMFCBaseTabCtrl :: RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl :: SetActiveTab](#setactivetab)|Définit l’onglet actif. (Substitue [CMFCBaseTabCtrl :: SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl :: SetBorderSize](#setbordersize)|Définit la taille de bordure du contrôle onglet Outlook.|
|[CMFCOutlookBarTabCtrl :: SetPageButtonTextAlign](#setpagebuttontextalign)|Définit l’alignement des étiquettes de texte sur les boutons d’onglet de la barre Outlook.|
|[CMFCOutlookBarTabCtrl :: SetToolbarImageList](#settoolbarimagelist)|Définit l’image bitmap qui contient les icônes affichées en bas de la barre Outlook en mode Outlook 2003 (voir la [classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBarTabCtrl :: SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Notes

Pour créer une barre Outlook avec prise en charge de l’ancrage, utilisez un `CMFCOutlookBar` objet pour héberger le contrôle onglet de barre Outlook. Pour plus d’informations, consultez [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment initialiser un `CMFCOutlookBarTabCtrl` objet et utiliser différentes méthodes dans la `CMFCOutlookBarTabCtrl` classe. L’exemple montre comment activer la modification sur place de l’étiquette de texte sur les boutons de page d’onglets de la barre Outlook, activer l’animation, activer les poignées de défilement qui permettent à l’utilisateur de faire défiler les boutons du volet barre Outlook, définir la taille de bordure du contrôle onglet Outlook et définir l’alignement des étiquettes de texte sur les boutons de la barre Outlook. Cet extrait de code fait partie de l' [exemple de démonstration Outlook](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxoutlookbartabctrl. h

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a> CMFCOutlookBarTabCtrl :: AddControl

Ajoute un contrôle Windows sous la forme d’un nouvel onglet dans la barre Outlook.

```cpp
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>Paramètres

*pWndCtrl*<br/>
dans Pointeur vers un contrôle à ajouter.

*lpszName*<br/>
dans Spécifie le nom de l’onglet.

*bDetachable*<br/>
dans Si la valeur est TRUE, la page sera créée comme détachable.

*nImageID*<br/>
dans Index d’image dans la liste d’images internes pour l’image à afficher dans le nouvel onglet.

*dwControlBarStyle*<br/>
dans Spécifie le style AFX_ CBRS_ * pour les volets d’ancrage encapsulés.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour ajouter un contrôle en tant que nouvelle page d’une barre Outlook.

Cette fonction appelle en interne sur [CMFCBaseTabCtrl :: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).

Si vous affectez à *bDetachable* la valeur true, `AddControl` crée en interne un `CDockablePaneAdapter` objet et encapsule le contrôle ajouté. Il définit automatiquement la classe Runtime de la fenêtre à onglets sur la classe Runtime de `CMFCOutlookBar` et la classe Runtime de la trame flottante sur `CMultiPaneFrameWnd` .

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `AddControl` méthode dans la `CMFCOutlookBarTabCtrl` classe. Cet extrait de code fait partie de l' [exemple de démonstration Outlook](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a> CMFCOutlookBarTabCtrl :: CanShowFewerPageButtons

Appelée par l’infrastructure pendant le redimensionnement des opérations pour déterminer si le nombre de boutons de page d’onglets Outlook peut être affiché en moins que ceux actuellement visibles.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE s’il existe plusieurs boutons ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le contrôle onglet de barre Outlook ajoute ou supprime dynamiquement des onglets de l’affichage en fonction de la quantité d’espace disponible. Cette méthode est utilisée par l’infrastructure pour faciliter ce processus.

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a> CMFCOutlookBarTabCtrl :: CanShowMorePageButtons

Appelée par l’infrastructure pendant le redimensionnement des opérations pour déterminer si d’autres boutons de la page d’onglets Outlook peuvent être affichés que ceux actuellement visibles.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si des boutons ne sont pas actuellement visibles ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Le contrôle onglet de barre Outlook ajoute ou supprime dynamiquement des onglets de l’affichage, en fonction de la quantité d’espace disponible. Cette méthode est utilisée par l’infrastructure pour faciliter ce processus.

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a> CMFCOutlookBarTabCtrl :: Create

Crée le contrôle onglet de barre Outlook.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Spécifie la taille et la position initiales, en pixels.

*pParentWnd*<br/>
dans Pointe vers la fenêtre parente. Ne doit pas avoir la valeur NULL.

*nID*<br/>
dans ID du contrôle.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le contrôle a été créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

En règle générale, les contrôles onglet de barre Outlook sont créés lorsque la [classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md) contrôle le message WM_CREATE du processus.

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a> CMFCOutlookBarTabCtrl :: EnableAnimation

Spécifie si l’animation qui se produit pendant le basculement entre les onglets actifs est activée.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans Spécifie si l’animation doit être activée ou désactivée.

### <a name="remarks"></a>Notes

Appelez cette fonction pour activer et désactiver l’animation. Lorsque l’utilisateur ouvre une page d’onglets, la légende de la page s’affiche en haut ou en aval si l’animation est activée. Si l’animation est désactivée, la page est immédiatement active.

Par défaut, l’animation est activée.

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a> CMFCOutlookBarTabCtrl :: EnableInPlaceEdit

Spécifie si un utilisateur peut modifier les étiquettes de texte sur les boutons de la page d’onglets de la barre Outlook.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Si la valeur est TRUE, active la modification sur place de l’étiquette de texte. Si la valeur est FALSe, désactivez la modification sur place.

### <a name="remarks"></a>Notes

Appelez cette fonction pour activer ou désactiver la modification sur place des étiquettes de texte sur les boutons de la page d’onglets. Par défaut, la modification sur place est désactivée.

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a> CMFCOutlookBarTabCtrl :: EnableScrollButtons

Appelée par l’infrastructure pour activer les poignées de défilement qui permettent à l’utilisateur de faire défiler les boutons du volet barre Outlook.

```cpp
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans Détermine si les boutons de défilement sont affichés.

*bIsUp*<br/>
dans Détermine si la barre de défilement supérieure est affichée.

*bIsDown*<br/>
dans Détermine si la barre de défilement inférieure est affichée.

### <a name="remarks"></a>Notes

Active l’affichage des boutons de défilement. Cette méthode est appelée par l’infrastructure lorsque l’onglet actif change pour restaurer les boutons de défilement.

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a> CMFCOutlookBarTabCtrl :: GetBorderSize

Retourne la taille de bordure du contrôle onglet Outlook.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille de la bordure, en pixels.

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a> CMFCOutlookBarTabCtrl :: GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a> CMFCOutlookBarTabCtrl :: IsAnimation

Spécifie si l’animation qui se produit pendant le basculement entre les onglets actifs est activée.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’animation est activée ; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez la fonction [CMFCOutlookBarTabCtrl :: EnableAnimation](#enableanimation) pour activer ou désactiver l’animation.

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a> CMFCOutlookBarTabCtrl :: IsMode2003

Détermine si le contrôle onglet de la barre Outlook est dans un mode qui émule Microsoft Outlook 2003.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le contrôle onglet de barre Outlook est en mode Outlook 2003 ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette valeur est définie par [CMFCOutlookBar :: SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a> CMFCOutlookBarTabCtrl :: OnShowFewerPageButtons

Appelée par l’infrastructure pour réduire le nombre de boutons de page d’onglets visibles.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Notes

Cette méthode ajuste le nombre de boutons d’onglets de page visibles lorsque le contrôle est redimensionné.

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a> CMFCOutlookBarTabCtrl :: OnShowMorePageButtons

Appelée par l’infrastructure pour augmenter le nombre de boutons de page d’onglets visibles.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Notes

Cette méthode ajuste le nombre de boutons de page d’onglets qui sont visibles lorsque le contrôle est redimensionné.

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a> CMFCOutlookBarTabCtrl :: OnShowOptions

Affiche la boîte de dialogue **Options du volet de navigation** .

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Notes

La boîte de dialogue **Options du volet de navigation** permet à l’utilisateur de sélectionner les boutons de page d’onglets à afficher et l’ordre dans lequel ils sont affichés.

Cette méthode est appelée par l’infrastructure quand l’utilisateur sélectionne l’élément de menu **Options du volet de navigation** dans le menu de personnalisation du contrôle.

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a> CMFCOutlookBarTabCtrl :: SetActiveTab

Définit l’onglet actif. L’onglet actif est celui qui est ouvert, avec son contenu visible.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Paramètres

*iTab*<br/>
dans Index de base zéro d’un onglet à ouvrir.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’onglet spécifié a été ouvert avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

L’effet visuel de la définition de l’onglet actif varie selon que vous avez activé l’animation. Pour plus d’informations, consultez [CMFCOutlookBarTabCtrl :: EnableAnimation](#enableanimation).

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a> CMFCOutlookBarTabCtrl :: SetBorderSize

Définit la taille de bordure du contrôle onglet Outlook.

```cpp
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Paramètres

*nBorderSize*<br/>
dans Spécifie la nouvelle taille de bordure en pixels.

### <a name="remarks"></a>Notes

Définit la nouvelle taille de bordure et recalcule la disposition de fenêtre Outlook.

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a> CMFCOutlookBarTabCtrl :: SetPageButtonTextAlign

Définit l’alignement des étiquettes de texte sur les boutons d’onglet de la barre Outlook.

```cpp
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*uiAlign*<br/>
dans Spécifie l’alignement du texte.

*bRedraw*<br/>
dans Si la valeur est TRUE, la fenêtre Outlook est redessinée.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour modifier l’alignement du texte pour les boutons de page.

*uiAlign* peut prendre l’une des valeurs suivantes :

|Constante|Signification|
|--------------|-------------|
|TA_LEFT|Alignement à gauche|
|TA_CENTER|Alignement centré|
|TA_RIGHT|Alignement à droite|

La valeur par défaut est TA_CENTER.

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a> CMFCOutlookBarTabCtrl :: SetToolbarImageList

Définit l’image bitmap qui contient les icônes affichées en bas de la barre Outlook en mode Outlook 2003.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
dans Spécifie l’ID de ressource de l’image à charger.

*adéquat*<br/>
dans Spécifie la largeur, en pixels, d’une image dans la liste d’images.

*clrTransp*<br/>
dans Valeur RVB qui spécifie la couleur transparente.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite ; Sinon, retourne FALSe.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour attacher une liste d’images dont les images seront affichées sur les boutons de la barre d’outils en mode Microsoft Office 2003. Les index d’images doivent correspondre aux index de page.

Cette méthode ne doit pas être appelée si elle n’est pas en mode Microsoft Office 2003. Pour plus d’informations, consultez [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a> CMFCOutlookBarTabCtrl :: SetVisiblePageButtons

```cpp
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Paramètres

dans *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl, classe](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane, classe](../../mfc/reference/cmfcoutlookbarpane-class.md)
