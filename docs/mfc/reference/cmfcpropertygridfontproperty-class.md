---
title: CMFCPropertyGridFontProperty, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: a3c5b806482a97d64a9ffab92877781cb8778b6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505123"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty, classe

La `CMFCPropertyGridFileProperty` classe prend en charge un élément de contrôle de liste de propriétés qui ouvre une boîte de dialogue de sélection de police.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Construit un objet `CMFCPropertyGridFontProperty`.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Met en forme la représentation textuelle d'une valeur de propriété. (Substitue [CMFCPropertyGridProperty:: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Récupère la couleur de police sélectionnée par l’utilisateur dans la boîte de dialogue police.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Récupère la police que l’utilisateur sélectionne dans la boîte de dialogue police.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Appelé par l'infrastructure quand l'utilisateur clique sur un bouton contenu dans une propriété. (Substitue [CMFCPropertyGridProperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxpropertygridctrl. h

##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

Construit un objet `CMFCPropertyGridFontProperty`.

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
dans Nom de la propriété.

*lf*<br/>
dans Structure de police logique qui spécifie les attributs de la police.

*dwFontDialogFlags*<br/>
dans Styles appliqués à la boîte de dialogue police qui s’affiche lorsque vous cliquez sur le bouton déroulant de la valeur de propriété. La valeur par défaut est la combinaison au niveau du bit (OR) de CF_EFFECTS et CF_SCREENFONTS. Pour plus d’informations, consultez le paramètre flags de la [structure CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszDescr*<br/>
dans Description de la propriété font. La valeur par défaut est NULL.

*dwData*<br/>
dans Données spécifiques à l’application, telles qu’un entier ou un pointeur vers d’autres données associées à la propriété. La valeur par défaut est 0.

*color*<br/>
dans Couleur de la police. La valeur par défaut est la couleur par défaut.

### <a name="remarks"></a>Notes

Un `CMFCPropertyGridFontProperty` objet représente une propriété de police dans un contrôle de police de la grille des propriétés.

### <a name="example"></a>Exemples

L’exemple suivant montre comment construire un objet de la `CMFCPropertyGridFontProperty` classe. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor

Récupère la couleur de police sélectionnée par l’utilisateur dans la boîte de dialogue police.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de couleur RVB qui représente la couleur de police sélectionnée.

### <a name="remarks"></a>Notes

##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont

Récupère la police que l’utilisateur sélectionne dans la boîte de dialogue police.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) qui décrit la police sélectionnée.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty, classe](../../mfc/reference/cmfcpropertygridproperty-class.md)
