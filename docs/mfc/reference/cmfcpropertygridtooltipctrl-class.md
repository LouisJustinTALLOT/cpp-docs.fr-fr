---
title: CMFCPropertyGridToolTipCtrl, classe
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
ms.openlocfilehash: 82d5f021204628121be242845583797348d02120
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840750"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl, classe

Implémente un contrôle ToolTip que la [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) utilise pour afficher des info-bulles.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Construit un objet `CMFCPropertyGridToolTipCtrl`.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[CMFCPropertyGridToolTipCtrl :: Create](#create)|Crée une fenêtre pour le contrôle ToolTip.|
|[CMFCPropertyGridToolTipCtrl ::D eactivate](#deactivate)|Désactive et masque le contrôle ToolTip.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Retourne les coordonnées de la dernière position du contrôle ToolTip.|
|[CMFCPropertyGridToolTipCtrl :: Hide](#hide)|Masque le contrôle ToolTip.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour traduire les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Définit l’espacement entre le texte de l’info-bulle et la bordure de la fenêtre d’info-bulle.|
|[CMFCPropertyGridToolTipCtrl :: Track](#track)|Affiche le contrôle ToolTip.|

## <a name="remarks"></a>Notes

Les info-bulles s’affichent lorsque le pointeur se trouve sur un nom de propriété. La classe [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) affiche une info-bulle pour qu’elle soit facilement lisible par l’utilisateur. En règle générale, la position d’une info-bulle est déterminée par la position du pointeur. En utilisant cette classe, l’info-bulle apparaît sur le nom de la propriété et ressemble à l’extension de propriété naturelle, afin que le nom de propriété soit entièrement visible.

MFC crée automatiquement ce contrôle et l’utilise dans la [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCPropertyGridToolTipCtrl` classe et comment afficher le contrôle ToolTip.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxpropertygridtooltipctrl. h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a> CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Construit un objet `CMFCPropertyGridToolTipCtrl`.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a> CMFCPropertyGridToolTipCtrl :: Create

Crée une fenêtre pour le contrôle ToolTip.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la fenêtre parente.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fenêtre a été créée avec succès ; Sinon, FALSe.

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a> CMFCPropertyGridToolTipCtrl ::D eactivate

Désactive et masque le contrôle ToolTip.

```cpp
void Deactivate();
```

### <a name="remarks"></a>Notes

Cette méthode définit la dernière position et le texte sur des valeurs vides, afin que les appels ultérieurs à [CMFCPropertyGridToolTipCtrl :: Track](#track) affichent l’info-bulle.

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a> CMFCPropertyGridToolTipCtrl::GetLastRect

Retourne les coordonnées de la dernière position du contrôle ToolTip.

```cpp
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
à Contient la dernière position du contrôle ToolTip.

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a> CMFCPropertyGridToolTipCtrl :: Hide

Masque le contrôle ToolTip.

```cpp
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a> CMFCPropertyGridToolTipCtrl::SetTextMargin

Définit l’espacement entre le texte de l’info-bulle et la bordure de la fenêtre d’info-bulle.

```cpp
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Paramètres

*nTextMargin*<br/>
dans Spécifie l’espacement entre le texte du contrôle ToolTip et la bordure de la fenêtre d’info-bulle. La valeur par défaut est 10 pixels.

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a> CMFCPropertyGridToolTipCtrl :: Track

Affiche le contrôle ToolTip.

```cpp
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
dans Spécifie la position et la taille du contrôle ToolTip.

*strText*<br/>
dans Spécifie le texte à afficher dans l’info-bulle.

### <a name="remarks"></a>Notes

Cette méthode affiche le contrôle ToolTip à la position et à la taille spécifiées par *Rect*. Si la position, la taille et le texte n’ont pas changé depuis la dernière fois que cette méthode a été appelée, cette méthode n’a aucun effet.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
