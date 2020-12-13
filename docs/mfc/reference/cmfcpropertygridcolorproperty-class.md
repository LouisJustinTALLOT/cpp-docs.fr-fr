---
description: 'En savoir plus sur : classe CMFCPropertyGridColorProperty'
title: CMFCPropertyGridColorProperty, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 7673044a149dc1b5171167ed0854918434651dc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334699"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty, classe

La classe `CMFCPropertyGridColorProperty` prend en charge un élément de contrôle de liste de propriétés qui ouvre une boîte de dialogue de sélection de couleur.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Construit un objet `CMFCPropertyGridColorProperty`.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Active le bouton *automatique* dans la boîte de dialogue de sélection de couleur. (Le bouton automatique standard est intitulé **automatique**.)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Active le bouton *autre* dans la boîte de dialogue de sélection de couleur. (Le bouton autre standard est intitulé **plus de couleurs**.)|
|`CMFCPropertyGridColorProperty::FormatProperty`|Met en forme la représentation textuelle d'une valeur de propriété. (Substitue [CMFCPropertyGridProperty :: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Obtient la couleur actuelle de la propriété.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Appelé par l'infrastructure quand l'utilisateur clique sur un bouton contenu dans une propriété. (Substitue [CMFCPropertyGridProperty :: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Appelé par l'infrastructure pour afficher la valeur de propriété. (Substitue [CMFCPropertyGridProperty :: OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|Appelé par l'infrastructure quand l'utilisateur s'apprête à modifier une valeur de propriété. (Substitue [CMFCPropertyGridProperty :: OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Appelé par l'infrastructure quand la valeur d'une propriété modifiable a changé. (Substitue [CMFCPropertyGridProperty :: OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Définit une nouvelle couleur pour la propriété.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Spécifie le nombre de colonnes de la grille de propriétés de couleur actuelle.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Définit la valeur d'origine d'une propriété modifiable.|

## <a name="remarks"></a>Notes

La classe `CMFCPropertyGridColorProperty` prend en charge une propriété de couleur qui peut être ajoutée à un contrôle de liste de propriétés. Pour plus d’informations, consultez la [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet de la classe `CMFCPropertyGridColorProperty` et configurer cet objet à l'aide de différentes méthodes de la classe `CMFCPropertyGridColorProperty`. Le code explique comment activer les boutons automatique et autre et comment définir la couleur et le nombre de colonnes. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxpropertygridctrl. h

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a> CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

Construit un objet `CMFCPropertyGridColorProperty`.

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
[in] Nom de la propriété.

*color*<br/>
dans Valeur de couleur de la propriété.

*pPalette*<br/>
dans Pointeur désignant une palette de couleurs. La valeur par défaut est NULL.

*lpszDescr*<br/>
dans Description de la propriété. La valeur par défaut est NULL.

*dwData*<br/>
dans Données spécifiques à l’application, telles qu’un entier ou un pointeur vers d’autres données associées à la propriété. La valeur par défaut est 0.

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCPropertyGridColorProperty::EnableAutomaticButton

Active le bouton *automatique* dans la boîte de dialogue de sélection de couleur. (Le bouton automatique standard est intitulé **automatique**.)

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Texte de l’étiquette du bouton automatique.

*colorAutomatic*<br/>
dans Valeur de couleur RVB de la couleur automatique (par défaut).

*bEnable*<br/>
dans TRUE pour activer le bouton automatique ; Sinon, FALSe. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a> CMFCPropertyGridColorProperty::EnableOtherButton

Active le bouton *autre* dans la boîte de dialogue de sélection de couleur. (Le bouton autre standard est intitulé **plus de couleurs**.)

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Texte de l’étiquette de l’autre bouton.

*bAltColorDlg*<br/>
dans TRUE pour afficher la `CMFCColorDialog` boîte de dialogue ; FALSe pour afficher la boîte de dialogue de sélection de couleur standard. La valeur par défaut est TRUE.

*bEnable*<br/>
dans TRUE pour afficher l’autre bouton ; Sinon, FALSe.  La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a> CMFCPropertyGridColorProperty :: GetColor

Obtient la couleur actuelle de la propriété.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur de couleur RVB.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a> CMFCPropertyGridColorProperty :: SetColor

Définit une nouvelle couleur pour la propriété.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Valeur de couleur RVB.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a> CMFCPropertyGridColorProperty::SetColumnsNumber

Spécifie le nombre de colonnes de la grille de propriétés de couleur actuelle.

```cpp
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Paramètres

*nColumnsNumber*<br/>
dans Nombre de colonnes par défaut dans la grille des propriétés de couleur.

### <a name="remarks"></a>Notes

Cette méthode définit la valeur du `m_nColumnsNumber` membre de données protégé.

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a> CMFCPropertyGridColorProperty::SetOriginalValue

Définit la valeur d'origine d'une propriété modifiable.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Paramètres

*varValue*<br/>
dans Valeur.

### <a name="remarks"></a>Notes

Utilisez la méthode [CMFCPropertyGridProperty :: ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) pour réinitialiser la valeur d’origine d’une propriété modifiée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty, classe](../../mfc/reference/cmfcpropertygridproperty-class.md)
