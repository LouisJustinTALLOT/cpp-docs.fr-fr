---
title: CMFCLinkCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: 79edff8be6e2c37baa938fc5b624253932609e17
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754247"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl, classe

La `CMFCLinkCtrl` classe affiche un bouton sous forme d’hyperlien et invoque la cible du lien lorsque le bouton est cliqué.

## <a name="syntax"></a>Syntaxe

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|Affiche une URL spécifiée sous forme de texte boutonné.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Définit le protocole implicite (par exemple, "http:") de l’URL.|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Resizes le bouton pour contenir le texte du bouton ou bitmap.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Appelé par le cadre avant que le rectangle de mise au point du bouton est dessiné.|

## <a name="remarks"></a>Notes

Lorsque vous cliquez sur un `CMFCLinkCtrl` bouton dérivé de la classe, le cadre `ShellExecute` passe l’URL du bouton comme paramètre de la méthode. Ensuite, `ShellExecute` la méthode ouvre la cible de l’URL.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir `CMFCLinkCtrl` la taille d’un objet, et comment `CMFCLinkCtrl` définir une url et une boîte à outils dans un objet. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxlinkctrl.h

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect

Appelé par le cadre avant que le rectangle de mise au point du bouton est dessiné.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*rectClient*<br/>
[dans] Un rectangle qui limite le contrôle du lien.

### <a name="remarks"></a>Notes

Remplacez cette méthode lorsque vous souhaitez utiliser votre propre code pour dessiner le rectangle de mise au point du bouton.

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a>CMFCLinkCtrl::SetURL

Affiche une URL spécifiée sous forme de texte boutonné.

```cpp
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Paramètres

*lpszURL*<br/>
[dans] Le bouton texte à afficher.

### <a name="remarks"></a>Notes

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix

Définit le protocole implicite (par exemple, "http:") de l’URL.

```cpp
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Paramètres

*lpszPrefix*<br/>
[dans] Le préfixe du protocole URL.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir le préfixe URL. Le préfixe n’est pas affiché sur le visage du bouton, mais vous pouvez l’utiliser pour aider à naviguer vers la cible de l’URL.

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent

Resizes le bouton pour contenir le texte du bouton ou bitmap.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Paramètres

*bVCenter (en)*<br/>
[dans] VRAI pour centrer le texte du bouton et la bitmap verticalement entre le haut et le bas du contrôle de lien ; autrement, FALSE. La valeur par défaut est FALSE.

*bHCenter (en)*<br/>
[dans] VRAI pour centrer le texte du bouton et bitmap horizontalement entre les côtés gauche et droit du contrôle du lien; autrement, FALSE. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur de retour

Un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) qui contient la nouvelle taille du contrôle du lien.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl, classe](../../mfc/reference/clinkctrl-class.md)<br/>
[Classe CMFCButton](../../mfc/reference/cmfcbutton-class.md)
