---
description: 'En savoir plus sur : classe CMFCLinkCtrl'
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
ms.openlocfilehash: 6951f086ac99c4b8a8260a79ee08d54476694350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265218"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl, classe

La `CMFCLinkCtrl` classe affiche un bouton sous forme de lien hypertexte et appelle la cible du lien lorsque l’utilisateur clique sur le bouton.

## <a name="syntax"></a>Syntaxe

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCLinkCtrl :: SetURL](#seturl)|Affiche une URL spécifiée comme texte du bouton.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Définit le protocole implicite (par exemple, « http : ») de l’URL.|
|[CMFCLinkCtrl :: SizeToContent](#sizetocontent)|Redimensionne le bouton pour qu’il contienne le texte du bouton ou l’image bitmap.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Appelé par le Framework avant le dessin du rectangle de focus du bouton.|

## <a name="remarks"></a>Notes

Lorsque vous cliquez sur un bouton dérivé de la `CMFCLinkCtrl` classe, le Framework passe l’URL du bouton en tant que paramètre à la `ShellExecute` méthode. Ensuite, la `ShellExecute` méthode ouvre la cible de l’URL.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir la taille d’un `CMFCLinkCtrl` objet et comment définir une URL et une info-bulle dans un `CMFCLinkCtrl` objet. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

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

**En-tête :** afxlinkctrl. h

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a> CMFCLinkCtrl::OnDrawFocusRect

Appelé par le Framework avant le dessin du rectangle de focus du bouton.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectClient*<br/>
dans Rectangle qui délimite le contrôle de lien.

### <a name="remarks"></a>Notes

Substituez cette méthode lorsque vous souhaitez utiliser votre propre code pour dessiner le rectangle de focus du bouton.

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a> CMFCLinkCtrl :: SetURL

Affiche une URL spécifiée comme texte du bouton.

```cpp
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Paramètres

*lpszURL*<br/>
dans Texte du bouton à afficher.

### <a name="remarks"></a>Notes

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a> CMFCLinkCtrl::SetURLPrefix

Définit le protocole implicite (par exemple, « http : ») de l’URL.

```cpp
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Paramètres

*lpszPrefix*<br/>
dans Préfixe du protocole d’URL.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir le préfixe d’URL. Le préfixe n’est pas affiché sur le visage du bouton, mais vous pouvez l’utiliser pour naviguer jusqu’à la cible de l’URL.

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a> CMFCLinkCtrl :: SizeToContent

Redimensionne le bouton pour qu’il contienne le texte du bouton ou l’image bitmap.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Paramètres

*bVCenter*<br/>
dans TRUE pour centrer verticalement le texte du bouton et la bitmap entre le haut et le bas du contrôle de lien ; Sinon, FALSe. La valeur par défaut est FALSE.

*bHCenter*<br/>
dans TRUE pour centrer le texte du bouton et la bitmap horizontalement entre les côtés gauche et droit du contrôle de lien ; Sinon, FALSe. La valeur par défaut est FALSE.

### <a name="return-value"></a>Valeur renvoyée

Objet [CSize](../../atl-mfc-shared/reference/csize-class.md) qui contient la nouvelle taille du contrôle de lien.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl, classe](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton, classe](../../mfc/reference/cmfcbutton-class.md)
