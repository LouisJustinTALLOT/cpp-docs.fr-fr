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
ms.openlocfilehash: 929fc1c8166f249fe3babc724b2c0bcd9cb99676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369711"
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
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Appelé par le cadre pour traduire les messages de fenêtre avant qu’ils ne soient expédiés. (Substitue `CMFCButton::PreTranslateMessage`.)|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Modifie la taille du bouton en fonction de son texte et de sa taille d’image.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Précise s’il faut afficher le menu pop-up système par défaut ou pour utiliser [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Précise si le menu pop-up apparaîtra en dessous ou à droite du bouton.|
|[CMFCMenuButton:m_bStayPressed](#m_bstaypressed)|Précise si le bouton du menu change d’état après que l’utilisateur a libéré le bouton.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Une poignée au menu Windows ci-joint.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Un identifiant qui indique l’élément choisi par l’utilisateur dans le menu pop-up.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Autoriser le traitement par défaut (sur le texte/image du bouton).|

## <a name="remarks"></a>Notes

La `CMFCMenuButton` classe est dérivée de la [classe CMFCButton](../../mfc/reference/cmfcbutton-class.md) qui est, à son tour, dérivée de la [classe CButton](../../mfc/reference/cbutton-class.md). Par conséquent, `CMFCMenuButton` vous pouvez utiliser dans votre `CButton`code de la même façon que vous utiliseriez .

Lorsque vous `CMFCMenuButton`créez un , vous devez passer dans une poignée au menu pop-up associé. Ensuite, appelez `CMFCMenuButton::SizeToContent`la fonction . `CMFCMenuButton::SizeToContent`vérifie que la taille du bouton est suffisante pour inclure une flèche qui indique l’endroit où la fenêtre pop-up apparaîtra - à savoir, en dessous ou à droite du bouton.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir la poignée du menu attaché au bouton, redimensionner le bouton en fonction de son texte et de la taille de l’image, et définir le menu pop-up qui est affiché par le cadre. Cet extrait de code fait partie de [l’échantillon De Nouveaux Contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxmenubutton.h

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton

Construit un nouvel objet [CMFCMenuButton.](../../mfc/reference/cmfcmenubutton-class.md)

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu

Une variable de membre Boolean qui indique quel menu pop-up le cadre affiche.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Notes

Si `m_bOSMenu` c’est VRAI, `TrackPopupMenu` le cadre appelle la méthode héritée de cet objet. Sinon, le cadre appelle [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow

Une variable de membre Boolean qui indique l’emplacement du menu pop-up.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur appuie sur le bouton menu, l’application affiche un menu pop-up. Le cadre affichera le menu pop-up soit sous le bouton ou à droite du bouton. Le bouton a également une petite flèche qui indique où le menu pop-up apparaîtra. Si `m_bRightArrow` c’est VRAI, le cadre affiche le menu pop-up à droite du bouton. Sinon, il affiche le menu pop-up sous le bouton.

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a>CMFCMenuButton:m_bStayPressed

Une variable de membre Boolean qui indique si le bouton du menu apparaît pressé pendant que l’utilisateur fait une sélection à partir du menu pop-up.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Notes

Si `m_bStayPressed` le membre est FALSE, le bouton du menu ne devient pas pressé lorsque les utilisations clique sur le bouton. Dans ce cas, le cadre affiche uniquement le menu pop-up.

Si `m_bStayPressed` le membre est VRAI, le bouton du menu est pressé lorsque l’utilisateur clique sur le bouton. Il reste pressé jusqu’à ce que l’utilisateur ferme le menu pop-up, soit en faisant une sélection ou en annulant.

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a>CMFCMenuButton::m_hMenu

Le manche au menu ci-joint.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Notes

Le cadre affiche le menu indiqué par cette variable de membre lorsque l’utilisateur clique sur le bouton menu.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Un intégrant qui indique l’élément que l’utilisateur sélectionne dans le menu pop-up.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Notes

La valeur de cette variable de membre est nulle si l’utilisateur annule le menu sans faire de sélection ou si une erreur se produit.

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a>CMFCMenuButton::m_bDefaultClick

Permet le traitement par défaut du texte ou des images sur le bouton.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Notes

La configuration m_bDefaultClick à de fausses causes le bouton pour afficher le menu lorsque vous cliquez n’importe où sur le bouton.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Un intégrant qui indique l’élément que l’utilisateur sélectionne dans le menu pop-up.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Notes

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage

Appelé par le cadre pour traduire les messages de fenêtre avant qu’ils ne soient expédiés.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
[dans] Indique une structure [MSG](/windows/win32/api/winuser/ns-winuser-msg) qui contient le message à traiter.

### <a name="return-value"></a>Valeur de retour

Nonzero si le message a été traduit et ne doit pas être envoyé; 0 si le message n’a pas été traduit et doit être envoyé.

### <a name="remarks"></a>Notes

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCMenuButton::SizeToContent

Modifie la taille du bouton en fonction de sa taille de texte et de sa taille d’image.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Paramètres

*bCalcOnly*<br/>
[dans] Un paramètre Boolean qui indique si cette méthode resizes le bouton .

### <a name="return-value"></a>Valeur de retour

Un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) qui spécifie la nouvelle taille du bouton.

### <a name="remarks"></a>Notes

Si vous appelez cette fonction et *bCalcOnly* est VRAI, `SizeToContent` calculera seulement la nouvelle taille du bouton.

La nouvelle taille du bouton est calculée pour s’adapter au texte, à l’image et à la flèche du bouton. Le cadre ajoute également en marges prédéfinies de 10 pixels pour le bord horizontal et de 5 pixels pour le bord vertical.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCButton](../../mfc/reference/cmfcbutton-class.md)
