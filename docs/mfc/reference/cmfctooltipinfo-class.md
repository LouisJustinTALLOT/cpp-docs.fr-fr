---
title: Classe de CMFCToolTipInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb5cb4020b851f3522842951030c8155ee68516f
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037543"
---
# <a name="cmfctooltipinfo-class"></a>Classe de CMFCToolTipInfo
Stocke des informations sur l'apparence visuelle des info-bulles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolTipInfo  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolTipInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Variable booléenne qui indique si l'info-bulle a l'aspect d'une bulle.|  
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Variable booléenne qui indique si les étiquettes d'info-bulle s'affichent en caractères gras.|  
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Variable booléenne qui indique si l'info-bulle contient une description.|  
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Variable booléenne qui indique si l'info-bulle contient une icône.|  
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Variable booléenne qui indique si un séparateur s'affiche entre l'étiquette et la description de l'info-bulle.|  
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Variable booléenne qui indique si l'info-bulle a des angles arrondis.|  
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Variable booléenne qui indique si l’apparence de l’info-bulle doit être contrôlé par un gestionnaire visuel (consultez [CMFCVisualManager classe](../../mfc/reference/cmfcvisualmanager-class.md)).|  
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Couleur de la bordure de l'info-bulle.|  
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Couleur de l'arrière-plan de l'info-bulle.|  
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Couleur du dégradé dans l'info-bulle.|  
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Couleur du texte de l'info-bulle.|  
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Angle du dégradé dans l'info-bulle.|  
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Largeur maximale, en pixels, de la description figurant dans l'info-bulle.|  
  
## <a name="remarks"></a>Notes  
 Utilisez [CMFCToolTipCtrl classe](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, et [CTooltipManager classe](../../mfc/reference/ctooltipmanager-class.md) pour implémenter des info-bulles personnalisées dans votre application. Pour obtenir un exemple montrant comment utiliser ces classes d’info-bulle, consultez le [CMFCToolTipCtrl classe](../../mfc/reference/cmfctooltipctrl-class.md) rubrique.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment définir les valeurs des différentes variables membres de la classe `CMFCToolTipInfo`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxtooltipctrl.h  
  
##  <a name="m_bballoontooltip"></a>  CMFCToolTipInfo::m_bBalloonTooltip  
 Spécifie le style d’affichage de toutes les info-bulles.  
  
```  
BOOL m_bBalloonTooltip;  
```  
  
### <a name="remarks"></a>Notes  
 `TRUE` Indique que les info-bulles utilisent le style d’info-bulle, `FALSE` indique que les info-bulles utilisent le style rectangulaire.  
  
##  <a name="m_bboldlabel"></a>  CMFCToolTipInfo::m_bBoldLabel  
 Spécifie si la police du texte info-bulle est en gras.  
  
```  
BOOL m_bBoldLabel;  
```  
  
### <a name="remarks"></a>Notes  
 Attribuez à ce membre `TRUE` pour afficher le texte de l’info-bulle avec une police en gras, ou `FALSE` pour afficher les étiquettes de l’info-bulle avec gras la police.  
  
##  <a name="m_bdrawdescription"></a>  CMFCToolTipInfo::m_bDrawDescription  
 Spécifie si chaque info-bulle affiche le texte de description.  
  
```  
BOOL m_bDrawDescription;  
```  
  
### <a name="remarks"></a>Notes  
 Attribuez à ce membre `TRUE` pour afficher la description, ou `FALSE` pour masquer la description. Vous pouvez spécifier la description dans une info-bulle en appelant [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)  
  
##  <a name="m_bdrawicon"></a>  CMFCToolTipInfo::m_bDrawIcon  
 Spécifie si les info-bulles tous les affichent des icônes.  
  
```  
BOOL m_bDrawIcon;  
```  
  
### <a name="remarks"></a>Notes  
 Attribuez à ce membre `TRUE` pour afficher une icône sur chaque info-bulle, ou `FALSE` pour afficher des info-bulles sans icônes.  
  
##  <a name="m_bdrawseparator"></a>  CMFCToolTipInfo::m_bDrawSeparator  
 Spécifie si chaque info-bulle a un séparateur entre son étiquette et sa description.  
  
```  
BOOL m_bDrawSeparator;  
```  
  
### <a name="remarks"></a>Notes  
 Attribuez à ce membre `TRUE` pour afficher le séparateur entre l’étiquette d’info-bulle et la description, ou `FALSE` pour afficher des info-bulles avec aucun séparateur.  
  
##  <a name="m_broundedcorners"></a>  CMFCToolTipInfo::m_bRoundedCorners  
 Spécifie si toutes les info-bulles ont des angles arrondis.  
  
```  
BOOL m_bRoundedCorners;  
```  
  
### <a name="remarks"></a>Notes  
 Attribuez à ce membre `TRUE` pour afficher les angles arrondis sur les info-bulles, ou `FALSE` pour afficher les angles rectangulaires sur les info-bulles.  
  
##  <a name="m_clrborder"></a>  CMFCToolTipInfo::m_clrBorder  
 Spécifie la couleur des bordures sur toutes les info-bulles.  
  
```  
COLORREF m_clrBorder;  
```  
  
##  <a name="m_clrfill"></a>  CMFCToolTipInfo::m_clrFill  
 Spécifie la couleur d’arrière-plan des info-bulle.  
  
```  
COLORREF m_clrFill;  
```  
  
### <a name="remarks"></a>Notes  
 Si [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) est -1, la couleur d’arrière-plan info-bulle est `m_clrFill`. Dans le cas contraire, `m_clrFill` spécifie la couleur de début du dégradé et `m_clrFillGradient` spécifie la couleur de la fin du dégradé. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) détermine la direction du dégradé.  
  
##  <a name="m_clrfillgradient"></a>  CMFCToolTipInfo::m_clrFillGradient  
 Spécifie la couleur de fin pour un arrière-plan dégradé pour les info-bulles.  
  
```  
COLORREF m_clrFillGradient;  
```  
  
### <a name="remarks"></a>Notes  
 Si `m_clrFillGradient` est -1, il n’existe aucun dégradé. Sinon, la couleur initiale est spécifiée par [CMFCToolTipInfo::m_clrFill](#m_clrfill) et la couleur de fin de dégradé est spécifiée par `m_clrFillGradient`. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) détermine la direction du dégradé.  
  
##  <a name="m_clrtext"></a>  CMFCToolTipInfo::m_clrText  
 Spécifie la couleur du texte des info-bulles de tous les.  
  
```  
COLORREF m_clrText;  
```  
  
##  <a name="m_ngradientangle"></a>  CMFCToolTipInfo::m_nGradientAngle  
 Spécifie l’angle auquel un dégradé est dessiné sur l’arrière-plan des info-bulles.  
  
```  
int m_nGradientAngle;  
```  
  
### <a name="remarks"></a>Notes  
 `m_nGradientAngle` Spécifie l’angle, en degrés, que le dégradé de l’arrière-plan des info-bulles décalée par rapport à l’horizontale. Si `m_nGradientAngle` est 0, le dégradé est dessiné de gauche à droite. Si `m_nGradientAngle` est comprise entre 1 et 360, le dégradé de la rotation dans le sens horaire par le nombre de degrés. Si `m_nGradientAngle` est -1, qui est la valeur par défaut, le dégradé est dessiné à partir du haut vers le bas. Il est identique à un paramètre `m_nGradientAngle` à 90.  
  
 [CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` spécifie la couleur de début du dégradé et [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` spécifie la couleur de la fin du dégradé. Si `m_clrFillGradient` est -1, il n’existe aucun dégradé.  
  
##  <a name="m_nmaxdescrwidth"></a>  CMFCToolTipInfo::m_nMaxDescrWidth  
 Spécifie la largeur maximale de la description qu’il est affiché dans chaque info-bulle. Si la largeur de la description dépasse la valeur spécifiée, le texte est encapsulé.  
  
```  
int m_nMaxDescrWidth;  
```  
  
##  <a name="m_bvislmanagertheme"></a>  CMFCToolTipInfo::m_bVislManagerTheme  
 Spécifie si le Gestionnaire visuel de l’application contrôle l’apparence de toutes les info-bulles.  
  
```  
BOOL m_bVislManagerTheme;  
```  
  
### <a name="remarks"></a>Notes  
 Si `m_bVislManagerTheme` est `TRUE`, chaque info-bulle demande un nouveau [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) à partir du Gestionnaire visuel de l’application avant qu’ils s’affichent sur l’écran et utilise les valeurs de cet objet pour déterminer leur apparence. Les autres membres de votre [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) sont ignorés.  
  
##  <a name="operator_eq"></a>  CMFCToolTipInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *src*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl, classe](../../mfc/reference/cmfctooltipctrl-class.md)
