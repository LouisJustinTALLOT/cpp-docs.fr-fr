---
title: CMFCMenuButton, classe
ms.date: 07/15/2019
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: d7c23cbda0a5af4dc3fa6b2d9f59497acc9bf5ff
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505207"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton, classe

Bouton qui affiche un menu contextuel et signale les sélections de l'utilisateur dans les menus.

## <a name="syntax"></a>Syntaxe

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Construit un objet `CMFCMenuButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Appelé par l’infrastructure pour traduire les messages de fenêtre avant qu’ils ne soient distribués. (Substitue `CMFCButton::PreTranslateMessage`.)|
|[CMFCMenuButton,:: SizeToContent](#sizetocontent)|Modifie la taille du bouton en fonction de sa taille de texte et d’image.|

### <a name="data-members"></a>Membres de données

|Nom|Description|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Spécifie s’il faut afficher le menu contextuel système par défaut ou utiliser [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Spécifie si le menu contextuel s’affiche en dessous ou à droite du bouton.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Spécifie si le bouton de menu modifie son état après que l’utilisateur a libéré le bouton.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Handle du menu Windows attaché.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identificateur qui indique l’élément sélectionné par l’utilisateur dans le menu contextuel.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Autoriser le traitement par défaut (sur le texte du bouton).|

## <a name="remarks"></a>Notes

La `CMFCMenuButton` classe est dérivée de la [classe CMFCButton](../../mfc/reference/cmfcbutton-class.md) qui est, à son tour, dérivée de la [classe CButton](../../mfc/reference/cbutton-class.md). Par conséquent, vous pouvez `CMFCMenuButton` utiliser dans votre code de la même façon que `CButton`vous le feriez.

Lorsque vous créez un `CMFCMenuButton`, vous devez transmettre un handle au menu contextuel associé. Ensuite, appelez la fonction `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent`vérifie que la taille du bouton est suffisante pour inclure une flèche pointant vers l’emplacement où la fenêtre contextuelle s’affiche, à savoir, en dessous ou à droite du bouton.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir la poignée du menu attaché au bouton, redimensionner le bouton en fonction de sa taille de texte et d’image et définir le menu contextuel affiché par le Framework. Cet extrait de code fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxmenubutton. h

##  <a name="cmfcmenubutton"></a>  CMFCMenuButton::CMFCMenuButton

Construit un nouvel objet [CMFCMenuButton,](../../mfc/reference/cmfcmenubutton-class.md) .

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu

Variable membre booléenne qui indique le menu contextuel affiché par l’infrastructure.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Notes

Si `m_bOSMenu` a la valeur true, l’infrastructure appelle `TrackPopupMenu` la méthode héritée pour cet objet. Dans le cas contraire, l’infrastructure appelle [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow

Variable membre booléenne qui indique l’emplacement du menu contextuel.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Notes

Quand l’utilisateur appuie sur le bouton de menu, l’application affiche un menu contextuel. L’infrastructure affiche le menu contextuel sous le bouton ou à droite du bouton. Le bouton comporte également une petite flèche qui indique où le menu contextuel s’affiche. Si `m_bRightArrow` a la valeur true, l’infrastructure affiche le menu contextuel à droite du bouton. Dans le cas contraire, le menu contextuel s’affiche sous le bouton.

##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed

Variable membre booléenne qui indique si le bouton de menu est activé pendant que l’utilisateur effectue une sélection dans le menu contextuel.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Notes

Si le `m_bStayPressed` membre a la valeur false, le bouton de menu n’est pas activé lorsque utilise le bouton. Dans ce cas, l’infrastructure affiche uniquement le menu contextuel.

Si le `m_bStayPressed` membre a la valeur true, le bouton de menu est activé lorsque l’utilisateur clique sur le bouton. Elle reste activée jusqu’à ce que l’utilisateur ferme le menu contextuel, soit en effectuant une sélection, soit en annulant.

##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu

Handle du menu attaché.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Notes

L’infrastructure affiche le menu indiqué par cette variable membre lorsque l’utilisateur clique sur le bouton de menu.

##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult

Entier qui indique l’élément que l’utilisateur sélectionne dans le menu contextuel.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Notes

La valeur de cette variable membre est égale à zéro si l’utilisateur annule le menu sans effectuer de sélection ou si une erreur se produit.

##  <a name="m_bdefaultclick"></a>  CMFCMenuButton::m_bDefaultClick

Autorise le traitement par défaut du texte ou des images sur le bouton.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Notes

Si vous affectez à m_bDefaultClick la valeur false, le bouton affiche le menu lorsque vous cliquez n’importe où sur le bouton.

##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult

Entier qui indique l’élément que l’utilisateur sélectionne dans le menu contextuel.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Notes

##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage

Appelé par l’infrastructure pour traduire les messages de fenêtre avant qu’ils ne soient distribués.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
dans Pointe vers une structure [MSG](/windows/win32/api/winuser/ns-winuser-msg) qui contient le message à traiter.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le message a été traduit et ne doit pas être distribué; 0 si le message n’a pas été traduit et doit être distribué.

### <a name="remarks"></a>Notes

##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent

Modifie la taille du bouton en fonction de la taille du texte et de la taille de l’image.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Paramètres

*bCalcOnly*<br/>
dans Paramètre booléen qui indique si cette méthode redimensionne le bouton.

### <a name="return-value"></a>Valeur de retour

Objet [CSize](../../atl-mfc-shared/reference/csize-class.md) qui spécifie la nouvelle taille du bouton.

### <a name="remarks"></a>Notes

Si vous appelez cette fonction et que *bCalcOnly* a la `SizeToContent` valeur true, calcule uniquement la nouvelle taille du bouton.

La nouvelle taille du bouton est calculée pour s’ajuster au texte du bouton, à l’image et à la flèche. L’infrastructure ajoute également des marges prédéfinies de 10 pixels pour le bord horizontal et de 5 pixels pour le bord vertical.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton, classe](../../mfc/reference/cmfcbutton-class.md)
