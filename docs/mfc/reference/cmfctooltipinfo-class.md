---
description: 'En savoir plus sur : classe CMFCToolTipInfo'
title: CMFCToolTipInfo, classe
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
ms.openlocfilehash: 06ceca500ad92d5f3a27e2740a298d9c1bbfe1cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143427"
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo, classe

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
|[CMFCToolTipInfo :: m_bBalloonTooltip](#m_bballoontooltip)|Variable booléenne qui indique si l'info-bulle a l'aspect d'une bulle.|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Variable booléenne qui indique si les étiquettes d'info-bulle s'affichent en caractères gras.|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Variable booléenne qui indique si l'info-bulle contient une description.|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Variable booléenne qui indique si l'info-bulle contient une icône.|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Variable booléenne qui indique si un séparateur s'affiche entre l'étiquette et la description de l'info-bulle.|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Variable booléenne qui indique si l'info-bulle a des angles arrondis.|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Variable booléenne qui indique si l’apparence de l’info-bulle doit être contrôlée par un gestionnaire visuel (consultez [CMFCVisualManager, classe](../../mfc/reference/cmfcvisualmanager-class.md)).|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Couleur de la bordure de l'info-bulle.|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Couleur de l'arrière-plan de l'info-bulle.|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Couleur du dégradé dans l'info-bulle.|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Couleur du texte de l'info-bulle.|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Angle du dégradé dans l'info-bulle.|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Largeur maximale, en pixels, de la description figurant dans l'info-bulle.|

## <a name="remarks"></a>Notes

Utilisez conjointement la classe [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo` et la [classe CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) pour implémenter des info-bulles personnalisées dans votre application. Pour obtenir un exemple d’utilisation de ces classes d’info-bulle, consultez la rubrique relative à la [classe CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) .

## <a name="example"></a>Exemple

L'exemple suivant montre comment définir les valeurs des différentes variables membres de la classe `CMFCToolTipInfo`.

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxtooltipctrl. h

## <a name="cmfctooltipinfom_bballoontooltip"></a><a name="m_bballoontooltip"></a> CMFCToolTipInfo :: m_bBalloonTooltip

Spécifie le style d’affichage de toutes les info-bulles.

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>Notes

TRUE indique que les info-bulles utilisent le style de bulle, FALSe indique que les info-bulles utilisent le style rectangulaire.

## <a name="cmfctooltipinfom_bboldlabel"></a><a name="m_bboldlabel"></a> CMFCToolTipInfo :: m_bBoldLabel

Spécifie si la police du texte de l’info-bulle est en gras.

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre pour afficher le texte info-bulle avec une police en gras, ou FALSe pour afficher les étiquettes d’info-bulle avec une police non gras.

## <a name="cmfctooltipinfom_bdrawdescription"></a><a name="m_bdrawdescription"></a> CMFCToolTipInfo :: m_bDrawDescription

Spécifie si chaque info-bulle affiche le texte de description.

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre pour afficher la description, ou FALSe pour masquer la description. Vous pouvez spécifier la description dans une info-bulle en appelant [CMFCToolTipCtrl :: SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)

## <a name="cmfctooltipinfom_bdrawicon"></a><a name="m_bdrawicon"></a> CMFCToolTipInfo :: m_bDrawIcon

Spécifie si toutes les info-bulles affichent des icônes.

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre pour afficher une icône sur chaque info-bulle, ou FALSe pour afficher des info-bulles sans icônes.

## <a name="cmfctooltipinfom_bdrawseparator"></a><a name="m_bdrawseparator"></a> CMFCToolTipInfo :: m_bDrawSeparator

Spécifie si chaque info-bulle a un séparateur entre son étiquette et sa description.

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre pour afficher le séparateur entre l’étiquette et la description de l’info-bulle, ou FALSe pour afficher les info-bulles sans séparateur.

## <a name="cmfctooltipinfom_broundedcorners"></a><a name="m_broundedcorners"></a> CMFCToolTipInfo :: m_bRoundedCorners

Spécifie si toutes les info-bulles ont des angles arrondis.

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre pour afficher des angles arrondis sur les info-bulles, ou FALSe pour afficher des angles rectangulaires sur les info-bulles.

## <a name="cmfctooltipinfom_clrborder"></a><a name="m_clrborder"></a> CMFCToolTipInfo :: m_clrBorder

Spécifie la couleur des bordures sur toutes les info-bulles.

```
COLORREF m_clrBorder;
```

## <a name="cmfctooltipinfom_clrfill"></a><a name="m_clrfill"></a> CMFCToolTipInfo :: m_clrFill

Spécifie la couleur des arrière-plans de l’info-bulle.

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>Notes

Si [CMFCToolTipInfo :: m_clrFillGradient](#m_clrfillgradient) est-1, la couleur d’arrière-plan de l’info-bulle est `m_clrFill` . Sinon, `m_clrFill` spécifie la couleur du début du dégradé et `m_clrFillGradient` spécifie la couleur de la fin du dégradé. [CMFCToolTipInfo :: m_nGradientAngle](#m_ngradientangle) détermine le sens du dégradé.

## <a name="cmfctooltipinfom_clrfillgradient"></a><a name="m_clrfillgradient"></a> CMFCToolTipInfo :: m_clrFillGradient

Spécifie la couleur de fin d’un arrière-plan dégradé pour les info-bulles.

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>Notes

Si `m_clrFillGradient` est-1, il n’y a pas de dégradé. Dans le cas contraire, la couleur initiale du dégradé est spécifiée par [CMFCToolTipInfo :: m_clrFill](#m_clrfill) et la couleur de fin du dégradé est spécifiée par `m_clrFillGradient` . [CMFCToolTipInfo :: m_nGradientAngle](#m_ngradientangle) détermine le sens du dégradé.

## <a name="cmfctooltipinfom_clrtext"></a><a name="m_clrtext"></a> CMFCToolTipInfo :: m_clrText

Spécifie la couleur du texte de toutes les info-bulles.

```
COLORREF m_clrText;
```

## <a name="cmfctooltipinfom_ngradientangle"></a><a name="m_ngradientangle"></a> CMFCToolTipInfo :: m_nGradientAngle

Spécifie l’angle auquel un dégradé est dessiné sur l’arrière-plan des info-bulles.

```
int m_nGradientAngle;
```

### <a name="remarks"></a>Notes

`m_nGradientAngle` Spécifie l’angle, en degrés, que le dégradé sur l’arrière-plan des info-bulles est décalé par rapport à l’horizontale. Si `m_nGradientAngle` a la valeur 0, le dégradé est dessiné de gauche à droite. Si `m_nGradientAngle` est compris entre 1 et 360, le dégradé est pivoté dans le sens des aiguilles d’une montre en ce nombre de degrés. Si `m_nGradientAngle` est-1, qui est la valeur par défaut, le dégradé est dessiné de haut en bas. Cela revient `m_nGradientAngle` à définir sur 90.

[CMFCToolTipInfo :: m_clrFill](#m_clrfill) `clrFill` spécifie la couleur du début du dégradé et [CMFCToolTipInfo :: m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` spécifie la couleur de la fin du dégradé. Si `m_clrFillGradient` est-1, il n’y a pas de dégradé.

## <a name="cmfctooltipinfom_nmaxdescrwidth"></a><a name="m_nmaxdescrwidth"></a> CMFCToolTipInfo :: m_nMaxDescrWidth

Spécifie la largeur maximale de la description affichée dans chaque info-bulle. Si la largeur de la description dépasse la valeur spécifiée, le texte est renvoyé à la boucle.

```
int m_nMaxDescrWidth;
```

## <a name="cmfctooltipinfom_bvislmanagertheme"></a><a name="m_bvislmanagertheme"></a> CMFCToolTipInfo :: m_bVislManagerTheme

Spécifie si le gestionnaire visuel de l’application contrôle l’apparence de toutes les info-bulles.

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>Notes

Si `m_bVislManagerTheme` a la valeur true, chaque info-bulle demande un nouveau [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) à partir du gestionnaire visuel de l’application avant qu’il n’apparaisse à l’écran, et utilise les valeurs de cet objet pour déterminer son apparence. Les autres membres de votre [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) sont ignorés.

## <a name="cmfctooltipinfooperator"></a><a name="operator_eq"></a> CMFCToolTipInfo :: Operator =

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>Paramètres

dans *src*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CTooltipManager, classe](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipCtrl, classe](../../mfc/reference/cmfctooltipctrl-class.md)
