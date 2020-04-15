---
title: Classe CMFCToolTipCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
ms.openlocfilehash: 6c8bb41b82d1dca9235e1184c2152a61c07c8071
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377355"
---
# <a name="cmfctooltipctrl-class"></a>Classe CMFCToolTipCtrl

Implémentation d’info-bulle étendue basée sur [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md). Une info-bulle basée sur la classe `CMFCToolTipCtrl` peut afficher une icône, une étiquette et une description. Vous pouvez personnaliser son apparence visuelle en utilisant un dégradé, un texte personnalisé et des couleurs de bordure, un texte en gras, des angles arrondis ou un style d'info-bulle.

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```cpp
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Retourne la taille d'une icône dans une info-bulle.|
|[CMFCToolTipCtrl::GetParams](#getparams)|Retourne les paramètres d'affichage d'une info-bulle.|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Dessine la bordure d'une info-bulle.|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Affiche une icône dans une info-bulle.|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Dessine l'étiquette d'une info-bulle ou calcule la taille de l'étiquette.|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Dessine le séparateur entre l'étiquette et la description dans une info-bulle.|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Remplit l'arrière-plan de l'info-bulle.|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Définit la description affichée par l'info-bulle.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Spécifie l'apparence visuelle d'une info-bulle en utilisant un objet `CMFCToolTipInfo`.|

## <a name="remarks"></a>Notes

Utilisez `CMFCToolTipCtrl` `CMFCToolTipInfo`des objets de [classe CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) ensemble pour implémenter des outils personnalisés dans votre application.

Par exemple, pour utiliser des info-bulles en forme de bulle, procédez comme suit :

1. Utilisez la méthode [de la classe CWinAppEx](../../mfc/reference/cwinappex-class.md) pour initialiser le gestionnaire de pointe dans votre application.

2. Créez une structure `CMFCToolTipInfo` pour spécifier le style visuel souhaité :

    ```cpp
    CMFCToolTipInfo params;
    params.m_bBoldLabel = FALSE;
    params.m_bDrawDescription = FALSE;
    params.m_bDrawIcon = FALSE;
    params.m_bRoundedCorners = TRUE;
    params.m_bDrawSeparator = FALSE;
    if (m_bCustomColors)
    {
        params.m_clrFill = RGB (255, 255, 255);
        params.m_clrFillGradient = RGB (228, 228, 240);
        params.m_clrText = RGB (61, 83, 80);
        params.m_clrBorder = RGB (144, 149, 168);

    }
    ```

3. Utilisez la méthode [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) pour définir le style visuel de toutes les `CMFCToolTipInfo` outils de l’application en utilisant les styles définis dans l’objet :

    ```cpp
    theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
        RUNTIME_CLASS (CMFCToolTipCtrl), &params);
    ```

Vous pouvez aussi faire dériver une nouvelle classe de `CMFCToolTipCtrl` pour contrôler le comportement et le rendu des info-bulles. Pour spécifier une nouvelle classe de contrôle d'info-bulle, utilisez la méthode `CTooltipManager::SetTooltipParams` :

```cpp
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

Pour restaurer la classe de contrôle d'info-bulle par défaut et rétablir l'état par défaut de l'apparence des info-bulles, spécifiez la valeur NULL dans les paramètres de classe Runtime et d'informations sur les info-bulles dans `SetTooltipParams` :

```cpp
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet `CMFCToolTipCtrl`, définir la description affichée par l'info-bulle et définir la largeur du contrôle info-bulle.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtooltipctrl.h

## <a name="cmfctooltipctrlcmfctooltipctrl"></a><a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl

```cpp
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Paramètres

[dans] *pParams pParams*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfctooltipctrlgeticonsize"></a><a name="geticonsize"></a>CMFCToolTipCtrl::GetIconSize

Retourne la taille d'une icône dans une info-bulle.

```cpp
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Valeur de retour

La taille de l’icône, en pixels.

## <a name="cmfctooltipctrlgetparams"></a><a name="getparams"></a>CMFCToolTipCtrl::GetParams

Retourne les paramètres d'affichage d'une info-bulle.

```cpp
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Valeur de retour

Les paramètres d’affichage de l’outil en cours, qui sont stockés dans un objet [cmFCToolTipInfo Class.](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="cmfctooltipctrlondrawborder"></a><a name="ondrawborder"></a>CMFCToolTipCtrl::OnDrawBorder

Dessine la bordure d'une info-bulle.

```cpp
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Le rectangle de délimitation de l’outiltip.

*clrLine*<br/>
[dans] Couleur de la frontière.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour personnaliser l’apparence de la bordure de l’outil.

## <a name="cmfctooltipctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCToolTipCtrl::OnDrawDescription

```cpp
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Paramètres

[dans] *pDC (pDC)*<br/>
[dans] *rect*<br/>
[dans] *bCalcOnly*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfctooltipctrlondrawicon"></a><a name="ondrawicon"></a>CMFCToolTipCtrl::OnDrawIcon

Affiche une icône dans une info-bulle.

```cpp
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*rectImage*<br/>
[dans] Coordonnées de l’icône.

### <a name="return-value"></a>Valeur de retour

VRAI si l’icône a été dessinée. Sinon FALSE.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour afficher une icône personnalisée. Vous devez également remplacer [CMFCToolTipCtrl::GetIconSize](#geticonsize) pour permettre à l’outiltip de calculer correctement la disposition du texte et de la description.

## <a name="cmfctooltipctrlondrawlabel"></a><a name="ondrawlabel"></a>CMFCToolTipCtrl::OnDrawLabel

Dessine l'étiquette d'une info-bulle ou calcule la taille de l'étiquette.

```cpp
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Rectangle de délimitation de la zone d’étiquette.

*bCalcOnly*<br/>
[dans] Si VRAI, l’étiquette ne sera pas dessinée.

### <a name="return-value"></a>Valeur de retour

Taille de l’étiquette, en pixels.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée si vous souhaitez personnaliser l’apparence de l’étiquette tooltip.

## <a name="cmfctooltipctrlondrawseparator"></a><a name="ondrawseparator"></a>CMFCToolTipCtrl::OnDrawSeparator

Dessine le séparateur entre l'étiquette et la description dans une info-bulle.

```cpp
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*x1*<br/>
[dans] Coordonnées horizontales de l’extrémité gauche du séparateur.

*x2*<br/>
[dans] Coordonnées horizontales de l’extrémité droite du séparateur.

*O*<br/>
[dans] Coordonnées verticales du séparateur.

### <a name="remarks"></a>Notes

L’implémentation par défaut trace une ligne du point (x1, y) au point (x2, y).

Remplacer cette méthode dans une classe dérivée pour personnaliser l’apparence du séparateur.

## <a name="cmfctooltipctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCToolTipCtrl::OnFillBackground

Remplit l'arrière-plan de l'info-bulle.

```cpp
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Spécifie le rectangle de délimitation de la zone à remplir.

*clrText*<br/>
[dans] Couleur de premier plan d’outil.

*clrLine*<br/>
[dans] Couleur des bordures et ligne de délimitation entre l’étiquette et la description.

### <a name="remarks"></a>Notes

L’implémentation par défaut remplit le rectangle qui est spécifié par *rect* avec la couleur ou le modèle spécifié par l’appel le plus récent à [CMFCToolTipCtrl::SetParams](#setparams).

Remplacer cette méthode dans une classe dérivée si vous voulez personnaliser l’apparence de l’outiltip.

## <a name="cmfctooltipctrlsetdescription"></a><a name="setdescription"></a>CMFCToolTipCtrl::SetDescription

Définit la description affichée par l'info-bulle.

```cpp
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Paramètres

*strDesrciption (en)*<br/>
[dans] Texte de description.

### <a name="remarks"></a>Notes

Le texte de description est affiché sur l’outiltip sous le séparateur.

## <a name="cmfctooltipctrlsetfixedwidth"></a><a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth

```cpp
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Paramètres

[dans] *nWidthRegular (en)*<br/>
[dans] *nWidthLargeImage*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfctooltipctrlsethotribbonbutton"></a><a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton

```cpp
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Paramètres

[dans] *pRibbonButton*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfctooltipctrlsetlocation"></a><a name="setlocation"></a>CMFCToolTipCtrl::SetLocation

```cpp
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Paramètres

[dans] *pt*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfctooltipctrlsetparams"></a><a name="setparams"></a>CMFCToolTipCtrl::SetParams

Specifie l’apparence visuelle d’un tooltip à l’aide d’un objet [cmFCToolTipInfo Class.](../../mfc/reference/cmfctooltipinfo-class.md)

```cpp
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Paramètres

*pParams pParams*<br/>
[dans] Pointeur vers un objet [cmFCToolTipInfo Class](../../mfc/reference/cmfctooltipinfo-class.md) qui contient les paramètres d’affichage.

### <a name="remarks"></a>Notes

Chaque fois que l’outil est affiché, il est dessiné en utilisant les couleurs et les styles visuels qui *pParams* spécifie. La valeur de *pParams* est `m_Params`stockée dans le membre protégé , qui peut être consulté par une classe dérivée qui remplace [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl::OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator), ou [CMFCToolTipCtrl::OnFillBackground](#onfillbackground) pour maintenir l’apparence spécifiée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)<br/>
[Classe CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)<br/>
[Classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)
