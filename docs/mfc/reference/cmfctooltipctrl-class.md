---
title: CMFCToolTipCtrl, classe
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
ms.openlocfilehash: 5376fd21f84411c86ade564d7c76d073ccb909a6
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273690"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl, classe

Implémentation d’info-bulle étendue basée sur [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md). Une info-bulle basée sur la classe `CMFCToolTipCtrl` peut afficher une icône, une étiquette et une description. Vous pouvez personnaliser son apparence visuelle en utilisant un dégradé, un texte personnalisé et des couleurs de bordure, un texte en gras, des angles arrondis ou un style d'info-bulle.

Pour plus d’informations, consultez le code source situé dans le dossier **VC\\ATLMFC\\SRC\\MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
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
|[CMFCToolTipCtrl :: SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Spécifie l'apparence visuelle d'une info-bulle en utilisant un objet `CMFCToolTipInfo`.|

## <a name="remarks"></a>Notes

Utilisez `CMFCToolTipCtrl`les `CMFCToolTipInfo`objets de [classe](../../mfc/reference/ctooltipmanager-class.md) , et CTooltipManager pour implémenter des info-bulles personnalisées dans votre application.

Par exemple, pour utiliser des info-bulles en forme de bulle, procédez comme suit :

1. Utilisez la méthode de la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md) pour initialiser le gestionnaire d’info-bulles dans votre application.

2. Créez une structure `CMFCToolTipInfo` pour spécifier le style visuel souhaité :

```
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
3. Utilisez la méthode [CTooltipManager :: SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) pour définir le style visuel de toutes les info-bulles de l’application à l’aide des styles `CMFCToolTipInfo` définis dans l’objet :

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```
Vous pouvez aussi faire dériver une nouvelle classe de `CMFCToolTipCtrl` pour contrôler le comportement et le rendu des info-bulles. Pour spécifier une nouvelle classe de contrôle d'info-bulle, utilisez la méthode `CTooltipManager::SetTooltipParams` :

```
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```
Pour restaurer la classe de contrôle d'info-bulle par défaut et rétablir l'état par défaut de l'apparence des info-bulles, spécifiez la valeur NULL dans les paramètres de classe Runtime et d'informations sur les info-bulles dans `SetTooltipParams` :

```
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

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtooltipctrl. h

##  <a name="cmfctooltipctrl"></a>  CMFCToolTipCtrl::CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Paramètres

dans *pParams*<br/>

### <a name="remarks"></a>Notes

##  <a name="geticonsize"></a>  CMFCToolTipCtrl::GetIconSize

Retourne la taille d'une icône dans une info-bulle.

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Valeur de retour

Taille de l’icône, en pixels.

##  <a name="getparams"></a>  CMFCToolTipCtrl::GetParams

Retourne les paramètres d'affichage d'une info-bulle.

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Valeur de retour

Les paramètres d’affichage de l’info-bulle actuels, qui sont stockés dans un objet de [classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) .

##  <a name="ondrawborder"></a>  CMFCToolTipCtrl::OnDrawBorder

Dessine la bordure d'une info-bulle.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rect*<br/>
dans Rectangle englobant de l’info-bulle.

*clrLine*<br/>
dans Couleur de la bordure.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour personnaliser l’apparence de la bordure de l’info-bulle.

##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>
dans *Rect*<br/>
dans *bCalcOnly*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="ondrawicon"></a>  CMFCToolTipCtrl::OnDrawIcon

Affiche une icône dans une info-bulle.

```
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectImage*<br/>
dans Coordonnées de l’icône.

### <a name="return-value"></a>Valeur de retour

TRUE si l’icône a été dessinée. Sinon, FALSe.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour afficher une icône personnalisée. Vous devez également substituer [CMFCToolTipCtrl :: GetIconSize](#geticonsize) pour permettre à l’info-bulle de calculer correctement la disposition du texte et de la description.

##  <a name="ondrawlabel"></a>  CMFCToolTipCtrl::OnDrawLabel

Dessine l'étiquette d'une info-bulle ou calcule la taille de l'étiquette.

```
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rect*<br/>
dans Rectangle englobant de la zone d’étiquette.

*bCalcOnly*<br/>
dans Si la valeur est TRUE, l’étiquette n’est pas dessinée.

### <a name="return-value"></a>Valeur de retour

Taille de l’étiquette, en pixels.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée si vous souhaitez personnaliser l’apparence de l’étiquette d’info-bulle.

##  <a name="ondrawseparator"></a>  CMFCToolTipCtrl::OnDrawSeparator

Dessine le séparateur entre l'étiquette et la description dans une info-bulle.

```
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*x1*<br/>
dans Coordonnée horizontale de l’extrémité gauche du séparateur.

*x2*<br/>
dans Coordonnée horizontale de l’extrémité droite du séparateur.

*Y*<br/>
dans Coordonnée verticale du séparateur.

### <a name="remarks"></a>Notes

L’implémentation par défaut dessine une ligne à partir du point (x1, y) jusqu’au point (x2, y).

Substituez cette méthode dans une classe dérivée pour personnaliser l’apparence du séparateur.

##  <a name="onfillbackground"></a>  CMFCToolTipCtrl::OnFillBackground

Remplit l'arrière-plan de l'info-bulle.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rect*<br/>
dans Spécifie le rectangle englobant de la zone à remplir.

*clrText*<br/>
dans Couleur de premier plan de l’info-bulle.

*clrLine*<br/>
dans Couleur des bordures et de la ligne de délimiteur entre l’étiquette et la description.

### <a name="remarks"></a>Notes

L’implémentation par défaut remplit le rectangle spécifié par *Rect* avec la couleur ou le modèle spécifié par l’appel le plus récent à [CMFCToolTipCtrl :: SetParams](#setparams).

Substituez cette méthode dans une classe dérivée si vous souhaitez personnaliser l’apparence de l’info-bulle.

##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription

Définit la description affichée par l'info-bulle.

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Paramètres

*strDesrciption*<br/>
dans Texte de description.

### <a name="remarks"></a>Notes

Le texte de description s’affiche dans l’info-bulle sous le séparateur.

##  <a name="setfixedwidth"></a>  CMFCToolTipCtrl::SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Paramètres

dans *nWidthRegular*<br/>
[in] *nWidthLargeImage*<br/>

### <a name="remarks"></a>Notes

##  <a name="sethotribbonbutton"></a>  CMFCToolTipCtrl::SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Paramètres

dans *pRibbonButton*<br/>

### <a name="remarks"></a>Notes

##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Paramètres

dans *PT*<br/>

### <a name="remarks"></a>Notes

##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams

Spécifie l’apparence visuelle d’une info-bulle à l’aide d’un objet de [classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) .

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Paramètres

*pParams*<br/>
dans Pointeur vers un objet de [classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) qui contient les paramètres d’affichage.

### <a name="remarks"></a>Notes

Chaque fois que l’info-bulle est affichée, elle est dessinée à l’aide des couleurs et des styles visuels que *pParams* spécifie. La valeur de *pParams* est stockée dans le membre `m_Params`protégé, accessible par une classe dérivée qui substitue [CMFCToolTipCtrl :: OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl :: OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl :: OnDrawLabel ](#ondrawlabel), [CMFCToolTipCtrl :: OnDrawSeparator](#ondrawseparator)ou [CMFCToolTipCtrl :: OnFillBackground](#onfillbackground) pour conserver l’apparence spécifiée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl, classe](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager, classe](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo, classe](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)
