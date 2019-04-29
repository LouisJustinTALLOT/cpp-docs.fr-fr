---
title: Cmfcpropertygridtooltipctrl, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: 6c14ed1f11a7a414332b34566a314459d76b911b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310472"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Cmfcpropertygridtooltipctrl, classe

Implémente une info-bulle de contrôle qui le [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) utilise pour afficher des info-bulles.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Construit un objet `CMFCPropertyGridToolTipCtrl`.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Crée une fenêtre pour le contrôle d’info-bulle.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Désactive et masque le contrôle d’info-bulle.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Retourne les coordonnées de la dernière position du contrôle d’info-bulle.|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Masque le contrôle d’info-bulle.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour traduire les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) . (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Définit l’espacement entre le texte d’info-bulle et la bordure de la fenêtre d’info-bulle.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Affiche le contrôle d’info-bulle.|

## <a name="remarks"></a>Notes

Info-bulles sont affichent lorsque le pointeur se trouve sur un nom de propriété. Le [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) classe affiche une info-bulle afin qu’elles soient facilement lisibles par l’utilisateur. En règle générale, la position d’une info-bulle est déterminée par la position du pointeur. À l’aide de cette classe, l’info-bulle s’affiche sur le nom de propriété et ressemble à l’extension naturelle de propriété, afin que le nom de propriété est entièrement visible.

MFC crée ce contrôle automatiquement et l’utilise dans le [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCPropertyGridToolTipCtrl` classe et comment afficher le contrôle d’info-bulle.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxpropertygridtooltipctrl.h

##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Construit un objet `CMFCPropertyGridToolTipCtrl`.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create

Crée une fenêtre pour le contrôle d’info-bulle.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Pointeur vers la fenêtre parente.

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre a été créée avec succès ; Sinon, FALSE.

##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate

Désactive et masque le contrôle d’info-bulle.

```
void Deactivate();
```

### <a name="remarks"></a>Notes

Cette méthode définit la dernière position et texte sur des valeurs vides, afin que les appels à venir [CMFCPropertyGridToolTipCtrl::Track](#track) afficher l’info-bulle.

##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect

Retourne les coordonnées de la dernière position du contrôle d’info-bulle.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
[out] Contient la dernière position du contrôle d’info-bulle.

##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide

Masque le contrôle d’info-bulle.

```
void Hide();
```

##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin

Définit l’espacement entre le texte d’info-bulle et la bordure de la fenêtre d’info-bulle.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Paramètres

*nTextMargin*<br/>
[in] Spécifie l’espacement entre le texte info-bulle du contrôle et la bordure de la fenêtre d’info-bulle. La valeur par défaut est 10 pixels.

##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track

Affiche le contrôle d’info-bulle.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
[in] Spécifie la position et la taille du contrôle d’info-bulle.

*strText*<br/>
[in] Spécifie le texte à afficher dans l’info-bulle.

### <a name="remarks"></a>Notes

Cette méthode affiche le contrôle d’info-bulle à la position et la taille spécifiée par *rect*. Si la position, la taille et le texte n’ont pas changé depuis la dernière fois que cette méthode a été appelée, cette méthode n’a aucun effet.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
