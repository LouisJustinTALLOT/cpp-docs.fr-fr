---
title: Cmfcpropertygridcolorproperty, classe
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
ms.openlocfilehash: 95dcbbc2b445e2ff67979b90816daed0fb0c0fba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403605"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>Cmfcpropertygridcolorproperty, classe

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
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Permet la *automatique* bouton dans la boîte de dialogue de sélection de couleur. (Le bouton automatique standard est intitulé **automatique**.)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Permet la *autres* bouton dans la boîte de dialogue de sélection de couleur. (La norme autres bouton est intitulé **couleurs supplémentaires**.)|
|`CMFCPropertyGridColorProperty::FormatProperty`|Met en forme la représentation textuelle d'une valeur de propriété. (Substitue [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Obtient la couleur actuelle de la propriété.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Appelé par l'infrastructure quand l'utilisateur clique sur un bouton contenu dans une propriété. (Substitue [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Appelé par l'infrastructure pour afficher la valeur de propriété. (Substitue [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|Appelé par l'infrastructure quand l'utilisateur s'apprête à modifier une valeur de propriété. (Substitue [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Appelé par l'infrastructure quand la valeur d'une propriété modifiable a changé. (Substitue [CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Définit une nouvelle couleur pour la propriété.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Spécifie le nombre de colonnes de la grille de propriétés de couleur actuelle.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Définit la valeur d'origine d'une propriété modifiable.|

## <a name="remarks"></a>Notes

La classe `CMFCPropertyGridColorProperty` prend en charge une propriété de couleur qui peut être ajoutée à un contrôle de liste de propriétés. Pour plus d’informations, consultez le [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet de la classe `CMFCPropertyGridColorProperty` et configurer cet objet à l'aide de différentes méthodes de la classe `CMFCPropertyGridColorProperty`. Le code explique comment activer les boutons automatique et autre et comment définir la couleur et le nombre de colonnes. Cet exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxpropertygridctrl.h

##  <a name="cmfcpropertygridcolorproperty"></a>  CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

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
[in] Le nom de la propriété.

*color*<br/>
[in] La valeur de couleur de la propriété.

*pPalette*<br/>
[in] Pointeur vers une palette de couleurs. La valeur par défaut est NULL.

*lpszDescr*<br/>
[in] La description de la propriété. La valeur par défaut est NULL.

*dwData*<br/>
[in] Données spécifiques à l’application, par exemple un entier ou un pointeur à d’autres données qui sont associés à la propriété. La valeur par défaut est 0.

##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton

Permet la *automatique* bouton dans la boîte de dialogue de sélection de couleur. (Le bouton automatique standard est intitulé **automatique**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[in] Le texte de l’étiquette du bouton automatique.

*colorAutomatic*<br/>
[in] La valeur de couleur RVB de la couleur automatique (par défaut).

*bEnable*<br/>
[in] TRUE pour activer le bouton automatique ; Sinon, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton

Permet la *autres* bouton dans la boîte de dialogue de sélection de couleur. (La norme autres bouton est intitulé **couleurs supplémentaires**.)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[in] Le texte de l’étiquette de l’autre bouton.

*bAltColorDlg*<br/>
[in] True pour afficher le `CMFCColorDialog` boîte de dialogue ; FALSE pour afficher la boîte de dialogue de sélection de couleur standard. La valeur par défaut est TRUE.

*bEnable*<br/>
[in] True pour afficher le bouton autre ; Sinon, FALSE.  La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor

Obtient la couleur actuelle de la propriété.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de couleur RVB.

### <a name="remarks"></a>Notes

##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor

Définit une nouvelle couleur pour la propriété.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
[in] Une valeur de couleur RVB.

### <a name="remarks"></a>Notes

##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber

Spécifie le nombre de colonnes de la grille de propriétés de couleur actuelle.

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Paramètres

*nColumnsNumber*<br/>
[in] Le nombre de colonnes dans la grille des propriétés couleur souhaité.

### <a name="remarks"></a>Notes

Cette méthode définit la valeur de la `m_nColumnsNumber` protégé de membre de données.

##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue

Définit la valeur d'origine d'une propriété modifiable.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Paramètres

*varValue*<br/>
[in] Une valeur.

### <a name="remarks"></a>Notes

Utilisez le [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) méthode pour réinitialiser la valeur d’origine d’une propriété modifiée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty, classe](../../mfc/reference/cmfcpropertygridproperty-class.md)
