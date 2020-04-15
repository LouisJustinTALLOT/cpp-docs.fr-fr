---
title: Classe CMFCToolTipInfo
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
ms.openlocfilehash: 000a2fd33928e59685efa6f145406542a4935819
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377334"
---
# <a name="cmfctooltipinfo-class"></a>Classe CMFCToolTipInfo

Stocke des informations sur l'apparence visuelle des info-bulles.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolTipInfo
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCToolTipInfo::operator=](#operator_eq)||

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCToolTipInfo:m_bBalloonTooltip](#m_bballoontooltip)|Variable booléenne qui indique si l'info-bulle a l'aspect d'une bulle.|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Variable booléenne qui indique si les étiquettes d'info-bulle s'affichent en caractères gras.|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Variable booléenne qui indique si l'info-bulle contient une description.|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Variable booléenne qui indique si l'info-bulle contient une icône.|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Variable booléenne qui indique si un séparateur s'affiche entre l'étiquette et la description de l'info-bulle.|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Variable booléenne qui indique si l'info-bulle a des angles arrondis.|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Une variable Boolean qui indique si l’apparence de l’outil doit être contrôlée par un gestionnaire visuel (voir [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)).|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Couleur de la bordure de l'info-bulle.|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Couleur de l'arrière-plan de l'info-bulle.|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Couleur du dégradé dans l'info-bulle.|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Couleur du texte de l'info-bulle.|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Angle du dégradé dans l'info-bulle.|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Largeur maximale, en pixels, de la description figurant dans l'info-bulle.|

## <a name="remarks"></a>Notes

Utilisez [cmFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) `CMFCToolTipInfo`Class , et [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md) ensemble pour implémenter des outils personnalisés dans votre application. Pour un exemple de la façon d’utiliser ces classes de pointe d’outil, voir le sujet de classe [CMFCToolTipCtrl.](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="example"></a>Exemple

L'exemple suivant montre comment définir les valeurs des différentes variables membres de la classe `CMFCToolTipInfo`.

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtooltipctrl.h

## <a name="cmfctooltipinfom_bballoontooltip"></a><a name="m_bballoontooltip"></a>CMFCToolTipInfo:m_bBalloonTooltip

Spécifie le style d’affichage de toutes les outils.

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>Notes

TRUE indique que les outils utilisent le style ballon, FALSE indique que les outils utilisent le style rectangulaire.

## <a name="cmfctooltipinfom_bboldlabel"></a><a name="m_bboldlabel"></a>CMFCToolTipInfo:m_bBoldLabel

Précise si la police du texte de l’outil est audacieuse.

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>Notes

Définissez ce membre à TRUE pour afficher le texte de l’outil avec une police audacieuse, ou FALSE pour afficher des étiquettes tooltip avec des polices non-bold.

## <a name="cmfctooltipinfom_bdrawdescription"></a><a name="m_bdrawdescription"></a>CMFCToolTipInfo:m_bDrawDescription

Précise si chaque outil affiche le texte de description.

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>Notes

Définissez ce membre à TRUE pour afficher la description, ou FALSE pour masquer la description. Vous pouvez spécifier la description sur un tooltip en appelant [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)

## <a name="cmfctooltipinfom_bdrawicon"></a><a name="m_bdrawicon"></a>CMFCToolTipInfo:m_bDrawIcon

Précise si toutes les icônes d’affichage tooltips.

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>Notes

Définissez ce membre à TRUE pour afficher une icône sur chaque boîte à outils, ou FALSE pour afficher des outils sans icônes.

## <a name="cmfctooltipinfom_bdrawseparator"></a><a name="m_bdrawseparator"></a>CMFCToolTipInfo:m_bDrawSeparator

Précise si chaque outil a un séparateur entre son étiquette et sa description.

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>Notes

Définissez ce membre à TRUE pour afficher le séparateur entre l’étiquette et la description de l’outil, ou FALSE pour afficher des outils sans séparateur.

## <a name="cmfctooltipinfom_broundedcorners"></a><a name="m_broundedcorners"></a>CMFCToolTipInfo:m_bRoundedCorners

Précise si toutes les outils ont des coins arrondis.

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>Notes

Définissez ce membre à TRUE pour afficher les coins arrondis sur les outils, ou FALSE pour afficher des coins rectangulaires sur des outils.

## <a name="cmfctooltipinfom_clrborder"></a><a name="m_clrborder"></a>CMFCToolTipInfo:m_clrBorder

Specifie la couleur des bordures sur toutes les outils.

```
COLORREF m_clrBorder;
```

## <a name="cmfctooltipinfom_clrfill"></a><a name="m_clrfill"></a>CMFCToolTipInfo:m_clrFill

Spécifie la couleur des arrière-plans de bout d’outil.

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>Notes

Si [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) est -1, la couleur de `m_clrFill`fond tooltip est . Sinon, `m_clrFill` spécifie la couleur du `m_clrFillGradient` début du gradient et spécifie la couleur de la fin du gradient. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) détermine la direction du gradient.

## <a name="cmfctooltipinfom_clrfillgradient"></a><a name="m_clrfillgradient"></a>CMFCToolTipInfo:m_clrFillGradient

Specifie la couleur de fin pour un fond de gradient pour les outils.

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>Notes

S’il `m_clrFillGradient` est de -1, il n’y a pas de gradient. Sinon, la couleur initiale de gradient est spécifiée par [CMFCToolTipInfo::m_clrFill](#m_clrfill) `m_clrFillGradient`et la couleur de finition de gradient est spécifiée par . [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) détermine la direction du gradient.

## <a name="cmfctooltipinfom_clrtext"></a><a name="m_clrtext"></a>CMFCToolTipInfo:m_clrText

Spécifie la couleur du texte de toutes les outils.

```
COLORREF m_clrText;
```

## <a name="cmfctooltipinfom_ngradientangle"></a><a name="m_ngradientangle"></a>CMFCToolTipInfo:m_nGradientAngle

Spécifie l’angle auquel un gradient est dessiné sur le fond des outils.

```
int m_nGradientAngle;
```

### <a name="remarks"></a>Notes

`m_nGradientAngle`spécifie l’angle, en degrés, que le gradient sur le fond des outils est décalé de l’horizontale. S’il `m_nGradientAngle` est de 0, le gradient est tiré de gauche à droite. S’il `m_nGradientAngle` se situe entre 1 et 360, le gradient tourne dans le sens des aiguilles d’une montre par ce nombre de degrés. S’il `m_nGradientAngle` est de -1, ce qui est la valeur par défaut, le gradient est tiré de haut en bas. C’est la `m_nGradientAngle` même chose que le réglage à 90.

[CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` spécifie la couleur du début du gradient et [cmFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` spécifie la couleur de la fin du gradient. S’il `m_clrFillGradient` est de -1, il n’y a pas de gradient.

## <a name="cmfctooltipinfom_nmaxdescrwidth"></a><a name="m_nmaxdescrwidth"></a>CMFCToolTipInfo:m_nMaxDescrWidth

Spécifie la largeur maximale de la description qu’il a affichée dans chaque boîte à outils. Si la largeur de la description dépasse la valeur spécifiée, le texte est enveloppé.

```
int m_nMaxDescrWidth;
```

## <a name="cmfctooltipinfom_bvislmanagertheme"></a><a name="m_bvislmanagertheme"></a>CMFCToolTipInfo:m_bVislManagerTheme

Précise si le gestionnaire visuel de l’application contrôle l’apparence de toutes les outils.

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>Notes

Si `m_bVislManagerTheme` c’est VRAI, chaque outil demande un nouveau [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) du gestionnaire visuel de l’application avant qu’ils apparaissent sur l’écran, et utilise les valeurs de cet objet pour déterminer leur apparence. Les autres membres de votre [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) sont ignorés.

## <a name="cmfctooltipinfooperator"></a><a name="operator_eq"></a>CMFCToolTipInfo::opérateur

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>Paramètres

[dans] *src*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)<br/>
[Classe CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)
