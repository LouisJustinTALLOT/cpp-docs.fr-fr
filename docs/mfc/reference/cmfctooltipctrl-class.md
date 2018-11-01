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
ms.openlocfilehash: e8ab9485cb2613e88ef136b3c470af9915bf7725
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564865"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl, classe

Implémentation d’info-bulle étendue basée sur [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md). Une info-bulle basée sur la classe `CMFCToolTipCtrl` peut afficher une icône, une étiquette et une description. Vous pouvez personnaliser son apparence visuelle en utilisant un dégradé, un texte personnalisé et des couleurs de bordure, un texte en gras, des angles arrondis ou un style d'info-bulle.

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

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
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Spécifie l'apparence visuelle d'une info-bulle en utilisant un objet `CMFCToolTipInfo`.|

## <a name="remarks"></a>Notes

Utilisez `CMFCToolTipCtrl`, `CMFCToolTipInfo`, et [ctooltipmanager, classe](../../mfc/reference/ctooltipmanager-class.md) objets pour implémenter des info-bulles personnalisées dans votre application.

Par exemple, pour utiliser des info-bulles en forme de bulle, procédez comme suit :

1. Utilisez le [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md) méthode pour initialiser le Gestionnaire d’info-bulle dans votre application.

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
    params.m_clrFill = RGB (255,
    255,
    255);

    params.m_clrFillGradient = RGB (228,
    228,
    240);

    params.m_clrText = RGB (61,
    83,
    80);

    params.m_clrBorder = RGB (144,
    149,
    168);

}
```
3. Utilisez le [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) méthode pour définir le style visuel pour toutes les info-bulles dans l’application en utilisant les styles définis dans le `CMFCToolTipInfo` objet :

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

## <a name="requirements"></a>Spécifications

**En-tête :** afxtooltipctrl.h

##  <a name="cmfctooltipctrl"></a>  CMFCToolTipCtrl::CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Paramètres

[in] *pParams*<br/>

### <a name="remarks"></a>Notes

##  <a name="geticonsize"></a>  CMFCToolTipCtrl::GetIconSize

Retourne la taille d'une icône dans une info-bulle.

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Valeur de retour

La taille de l’icône, en pixels.

##  <a name="getparams"></a>  CMFCToolTipCtrl::GetParams

Retourne les paramètres d'affichage d'une info-bulle.

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Valeur de retour

Les paramètres d’affichage info-bulle actuel, qui sont stockées dans un [cmfctooltipinfo, classe](../../mfc/reference/cmfctooltipinfo-class.md) objet.

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
[in] Pointeur vers un contexte de périphérique.

*Rect*<br/>
[in] Le rectangle englobant de l’info-bulle.

*clrLine*<br/>
[in] Couleur de bordure.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour personnaliser l’apparence de la bordure d’info-bulle.

##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Paramètres

[in] *pDC*<br/>
[in] *rect*<br/>
[in] *bCalcOnly*<br/>

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
[in] Pointeur vers un contexte de périphérique.

*rectImage*<br/>
[in] Coordonnées de l’icône.

### <a name="return-value"></a>Valeur de retour

TRUE si l’icône a été dessinée. Sinon, FALSE.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour afficher une icône personnalisée. Vous devez également substituer [CMFCToolTipCtrl::GetIconSize](#geticonsize) pour activer l’info-bulle calculer correctement la disposition du texte et la description.

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
[in] Pointeur vers un contexte de périphérique.

*Rect*<br/>
[in] Rectangle englobant de la zone d’étiquette.

*bCalcOnly*<br/>
[in] Si la valeur est TRUE, l’étiquette ne sera pas dessinée.

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
[in] Pointeur vers un contexte de périphérique.

*x1*<br/>
[in] Coordonnée horizontale de l’extrémité gauche du séparateur.

*x2*<br/>
[in] Coordonnée horizontale de l’extrémité droite du séparateur.

*Y*<br/>
[in] Coordonnée verticale du séparateur.

### <a name="remarks"></a>Notes

L’implémentation par défaut Dessine une ligne à partir du point (x1, y) au point (x2, y).

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
[in] Pointeur vers un contexte de périphérique.

*Rect*<br/>
[in] Spécifie le rectangle englobant de la zone à remplir.

*clrText*<br/>
[in] Info-bulle couleur de premier plan.

*clrLine*<br/>
[in] Couleur de bordure et la ligne de séparateur entre l’étiquette et description.

### <a name="remarks"></a>Notes

L’implémentation par défaut remplit le rectangle spécifié par *rect* avec la couleur ou le modèle spécifié par l’appel le plus récent à [CMFCToolTipCtrl::SetParams](#setparams).

Substituez cette méthode dans une classe dérivée si vous souhaitez personnaliser l’apparence de l’info-bulle.

##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription

Définit la description affichée par l'info-bulle.

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Paramètres

*strDesrciption*<br/>
[in] Texte de description.

### <a name="remarks"></a>Notes

Le texte de description s’affiche dans l’info-bulle sous le séparateur.

##  <a name="setfixedwidth"></a>  CMFCToolTipCtrl::SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Paramètres

[in] *nWidthRegular*<br/>
[in] *nWidthLargeImage*<br/>

### <a name="remarks"></a>Notes

##  <a name="sethotribbonbutton"></a>  CMFCToolTipCtrl::SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Paramètres

[in] *pRibbonButton*<br/>

### <a name="remarks"></a>Notes

##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Paramètres

[in] *pt*<br/>

### <a name="remarks"></a>Notes

##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams

Spécifie l’apparence visuelle d’une info-bulle à l’aide un [cmfctooltipinfo, classe](../../mfc/reference/cmfctooltipinfo-class.md) objet.

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Paramètres

*pParams*<br/>
[in] Pointeur vers un [cmfctooltipinfo, classe](../../mfc/reference/cmfctooltipinfo-class.md) objet qui contient les paramètres d’affichage.

### <a name="remarks"></a>Notes

Chaque fois que l’info-bulle s’affiche, il est dessiné à l’aide de couleurs et styles visuels qui *pParams* spécifie. La valeur de *pParams* est stocké dans le membre protégé `m_Params`, qui peut être accédé par une classe dérivée qui substitue [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl : : OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator), ou [CMFCToolTipCtrl::OnFillBackground](#onfillbackground)de conserver l’apparence spécifiée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl, classe](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager, classe](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo, classe](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)
