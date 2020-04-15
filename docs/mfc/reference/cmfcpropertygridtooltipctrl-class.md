---
title: Classe CMFCPropertyGridToolTipCtrl
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
ms.openlocfilehash: 94d75f914e5f7928d08dd2a87997ab02c4f16832
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361789"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Classe CMFCPropertyGridToolTipCtrl

Implémente un contrôle de pointe d’outil que la [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) utilise pour afficher les outils.

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
|[CMFCPropertyGridToolTipCtrl::Créer](#create)|Crée une fenêtre pour le contrôle de l’outiltip.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Désactive et cache le contrôle de l’outil.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Retourne les coordonnées de la dernière position du contrôle de l’outil.|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Cache le contrôle de l’outil.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour traduire les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Définit l’espacement entre le texte de l’outil et la bordure de la fenêtre de pointe d’outil.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Affiche le contrôle de l’outil.|

## <a name="remarks"></a>Notes

Les outils sont affichés lorsque le pointeur repose sur un nom de propriété. La classe [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) affiche une boîte à outils afin qu’elle soit facilement lisible par l’utilisateur. Habituellement, la position d’un tooltip est déterminée par la position du pointeur. En utilisant cette classe, l’outil apparaît sur le nom de propriété et ressemble à l’extension de propriété naturelle, de sorte que le nom de la propriété est entièrement visible.

MFC crée automatiquement ce contrôle et l’utilise dans la [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCPropertyGridToolTipCtrl` un objet de la classe, et comment afficher le contrôle de l’outiltip.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpropertygridtooltipctrl.h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Construit un objet `CMFCPropertyGridToolTipCtrl`.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a>CMFCPropertyGridToolTipCtrl::Créer

Crée une fenêtre pour le contrôle de l’outiltip.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Un pointeur à la fenêtre parente.

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre a été créée avec succès; autrement, FALSE.

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deactivate

Désactive et cache le contrôle de l’outil.

```
void Deactivate();
```

### <a name="remarks"></a>Notes

Cette méthode définit la dernière position et le texte aux valeurs vides, de sorte que les appels futurs vers [CMFCPropertyGridToolTipCtrl: :Track](#track) afficher l’outiltip.

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect

Retourne les coordonnées de la dernière position du contrôle de l’outil.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[out] Contient la dernière position du contrôle de l’outiltip.

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a>CMFCPropertyGridToolTipCtrl::Hide

Cache le contrôle de l’outil.

```
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin

Définit l’espacement entre le texte de l’outil et la bordure de la fenêtre de pointe d’outil.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Paramètres

*nTextMargin (en)*<br/>
[dans] Spécifie l’espacement entre le texte de contrôle de l’outil et la bordure de la fenêtre de pointe. La valeur par défaut est de 10 pixels.

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a>CMFCPropertyGridToolTipCtrl::Track

Affiche le contrôle de l’outil.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[dans] Spécifie la position et la taille du contrôle de l’outil.

*strText (en)*<br/>
[dans] Spécifie le texte à montrer dans la pointe d’outils.

### <a name="remarks"></a>Notes

Cette méthode affiche le contrôle de la pointe d’outil à la position et la taille spécifiées par *rect*. Si la position, la taille et le texte n’ont pas changé depuis la dernière fois que cette méthode a été appelée, cette méthode n’a aucun effet.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
