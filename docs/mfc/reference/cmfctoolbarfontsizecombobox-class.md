---
title: Cmfctoolbarfontsizecombobox, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: 43832f6c9b02c43fbe4a05cbea3add8783150113
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767663"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>Cmfctoolbarfontsizecombobox, classe

Un bouton de barre d’outils qui contient un contrôle de zone de liste déroulante qui permet à l’utilisateur à sélectionner une taille de police.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Construit un objet `CMFCToolBarFontSizeComboBox`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Retourne la taille de police sélectionnée en twips.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Remplit la zone de liste modifiable avec toutes les tailles de police pris en charge d’une police spécifiée.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Définit la taille de police en twips.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser un `CMFCToolBarFontSizeComboBox` de l’objet avec un [cmfctoolbarfontcombobox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objet pour permettre aux utilisateurs de sélectionner une police et la taille de police.

Vous pouvez ajouter un bouton de zone de liste déroulante Police taille à une barre d’outils comme vous ajoutez un bouton de zone de liste déroulante de police. Pour plus d’informations, consultez [cmfctoolbarfontcombobox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Lorsque l’utilisateur sélectionne une nouvelle police dans un `CMFCToolBarFontComboBox` de l’objet, vous pouvez remplir la zone de liste déroulante de taille de police avec les tailles prises en charge pour cette police à l’aide de la [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) (méthode).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCToolBarFontSizeComboBox` classe permettant de configurer un `CMFCToolBarFontSizeComboBox` objet. L’exemple illustre comment récupérer la taille de police, en twips, dans la zone de texte, remplir la zone de liste déroulante de taille de police avec toutes les tailles valides de la police donnée et spécifier la taille de police en twips. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Construit un objet `CMFCToolBarFontSizeComboBox`.

```
CMFCToolBarFontSizeComboBox();
```

##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize

Récupère la taille de police, en twips, à partir de la zone de texte d’une zone de liste déroulante de taille de police.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est positive, il est la taille de police en twips. Il est -1 si la zone de texte de la zone de liste déroulante est vide. Il est -2 si une erreur se produit.

##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes

Remplit une zone de liste déroulante de taille de police avec toutes les tailles valides de la police donnée.

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Paramètres

*strFontName*<br/>
[in] Spécifie un nom de police.

### <a name="remarks"></a>Notes

Appelez cette fonction lorsque vous souhaitez synchroniser entre la sélection dans une zone de liste déroulante de police et une zone de liste déroulante de taille de police, comme un [cmfctoolbarfontcombobox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize

Arrondit spécifié de taille (en twips) à la taille plus proche en points, puis définit la taille sélectionnée dans la zone de liste déroulante pour cette valeur.

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize*<br/>
[in] Spécifie la taille de police (en twips) pour définir.

### <a name="remarks"></a>Notes

Vous pouvez récupérer la taille de police valide précédent ultérieurement en appelant le [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) (méthode).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton, classe](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
