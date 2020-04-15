---
title: Classe CMFCToolBarFontSizeComboBox
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
ms.openlocfilehash: 09811b14ed805b1965015a32a25c0b67c947ff4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358303"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>Classe CMFCToolBarFontSizeComboBox

Un bouton de barre d’outils qui contient un contrôle de boîte combo qui permet à l’utilisateur de sélectionner une taille de police.

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
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Retourne la taille de la police sélectionnée en twips.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Remplit la liste des boîtes combo avec toutes les tailles de police prises en charge pour une police spécifiée.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Définit la taille de la police en twips.|

## <a name="remarks"></a>Notes

Vous pouvez `CMFCToolBarFontSizeComboBox` utiliser un objet avec un objet [cmFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md) pour permettre à un utilisateur de sélectionner une police et une taille de police.

Vous pouvez ajouter un bouton de boîte combo taille de police à une barre d’outils tout comme vous ajoutez un bouton de boîte combo police. Pour plus d’informations, voir [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Lorsque l’utilisateur sélectionne une `CMFCToolBarFontComboBox` nouvelle police dans un objet, vous pouvez remplir la boîte combo taille de police avec les tailles prises en utilisant la [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) méthode.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `CMFCToolBarFontSizeComboBox` différentes méthodes `CMFCToolBarFontSizeComboBox` dans la classe pour configurer un objet. L’exemple illustre comment récupérer la taille de la police, en twips, à partir de la boîte de texte, remplir la boîte combo taille de police avec toutes les tailles valides de la police donnée, et spécifier la taille de la police en twips. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Construit un objet `CMFCToolBarFontSizeComboBox`.

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize

Récupère la taille de la police, en twips, à partir de la boîte de texte d’une boîte combo de taille de police.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est positive, c’est la taille de la police en twips. Il est -1 si la boîte de texte de la boîte combo est vide. Il est de -2 si une erreur se produit.

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::RebuildFontSizes

Remplit une boîte combo de taille de police avec toutes les tailles valides de la police donnée.

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Paramètres

*strFontName (en)*<br/>
[dans] Spécifie un nom de police.

### <a name="remarks"></a>Notes

Appelez cette fonction lorsque vous souhaitez synchroniser entre la sélection dans une boîte combo police et une boîte combo de taille de police, comme une [classe CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize

Arrondit la taille spécifiée (en twips) à la taille la plus proche en points, puis définit la taille sélectionnée dans la boîte de combo à cette valeur.

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize (en)*<br/>
[dans] Spécifie la taille de la police (en twips) à régler.

### <a name="remarks"></a>Notes

Vous pouvez récupérer la taille de police valide précédente plus tard en appelant la [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) méthode.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton, classe](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::RemplacerButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : placement de contrôles dans les barres d'outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
