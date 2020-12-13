---
description: 'En savoir plus sur : classe CMFCToolBarFontSizeComboBox'
title: CMFCToolBarFontSizeComboBox, classe
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
ms.openlocfilehash: a355e62f2ef538372d70b9b2b393bc16bff2ef4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331751"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox, classe

Bouton de barre d’outils qui contient un contrôle zone de liste déroulante qui permet à l’utilisateur de sélectionner une taille de police.

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
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Remplit la liste de la zone de liste déroulante avec toutes les tailles de police prises en charge pour une police spécifiée.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Définit la taille de police en twips.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser un `CMFCToolBarFontSizeComboBox` objet avec un objet de [classe CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) pour permettre à un utilisateur de sélectionner une police et une taille de police.

Vous pouvez ajouter un bouton de zone de liste déroulante de taille de police à une barre d’outils tout comme vous ajoutez un bouton de zone de liste déroulante de police. Pour plus d’informations, consultez [CMFCToolBarFontComboBox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Lorsque l’utilisateur sélectionne une nouvelle police dans un `CMFCToolBarFontComboBox` objet, vous pouvez remplir la zone de liste déroulante taille de la police avec les tailles prises en charge pour cette police à l’aide de la méthode [CMFCToolBarFontSizeComboBox :: RebuildFontSizes](#rebuildfontsizes) .

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes dans la `CMFCToolBarFontSizeComboBox` classe pour configurer un `CMFCToolBarFontSizeComboBox` objet. L’exemple montre comment récupérer la taille de police, en twips, à partir de la zone de texte, remplir la zone de liste déroulante de taille de police avec toutes les tailles valides de la police donnée et spécifier la taille de police en twips. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxtoolbarfontcombobox. h

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a> CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Construit un objet `CMFCToolBarFontSizeComboBox`.

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a> CMFCToolBarFontSizeComboBox::GetTwipSize

Récupère la taille de police, en twips, à partir de la zone de texte d’une zone de liste déroulante de taille de police.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Si la valeur de retour est positive, il s’agit de la taille de police en twips. Elle est-1 si la zone de texte de la zone de liste déroulante est vide. Il s’agit de-2 si une erreur se produit.

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a> CMFCToolBarFontSizeComboBox::RebuildFontSizes

Remplit une zone de liste déroulante de taille de police avec toutes les tailles valides de la police donnée.

```cpp
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Paramètres

*strFontName*<br/>
dans Spécifie un nom de police.

### <a name="remarks"></a>Notes

Appelez cette fonction lorsque vous souhaitez effectuer une synchronisation entre la sélection dans une zone de liste déroulante de police et une zone de liste déroulante de taille de police, telle qu’une [classe CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a> CMFCToolBarFontSizeComboBox::SetTwipSize

Arrondit la taille spécifiée (en twips) à la taille la plus proche en points, puis affecte cette valeur à la taille sélectionnée dans la zone de liste déroulante.

```cpp
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize*<br/>
dans Spécifie la taille de la police (en twips) à définir.

### <a name="remarks"></a>Notes

Vous pouvez récupérer la taille de police valide précédente ultérieurement en appelant la méthode [CMFCToolBarFontSizeComboBox :: GetTwipSize](#gettwipsize) .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton, classe](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : ajout de contrôles aux barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
