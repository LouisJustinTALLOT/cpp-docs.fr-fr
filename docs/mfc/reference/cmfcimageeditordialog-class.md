---
description: 'En savoir plus sur : classe CMFCImageEditorDialog'
title: CMFCImageEditorDialog, classe
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 6c25cf4a1a8d0cc5852049a06c3a140cbb00a118
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265387"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog, classe

La `CMFCImageEditorDialog` classe prend en charge une boîte de dialogue d’éditeur d’images.

## <a name="syntax"></a>Syntaxe

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCImageEditorDialog :: CMFCImageEditorDialog](#cmfcimageeditordialog)|Construit un objet `CMFCImageEditorDialog`.|

## <a name="remarks"></a>Notes

La `CMFCImageEditorDialog` classe fournit une boîte de dialogue qui inclut les éléments suivants :

- Zone d’image que vous utilisez pour modifier des pixels individuels dans une image.

- Outils de dessin pour modifier les pixels de la zone d’image.

- Palette de couleurs pour spécifier la couleur utilisée par les outils de dessin.

- Zone d’aperçu qui affiche l’effet de votre modification.

L’illustration suivante montre une boîte de dialogue de l’éditeur d’images.

![Boîte de dialogue CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "Boîte de dialogue CMFCImageEditorDialog")

L’une des façons d’utiliser un `CMFCImageEditorDialog` objet est de le passer à une `CBitmap` image à modifier. Ne créez pas une grande image, car la zone d’édition de l’image a une taille limitée et la taille de pixel logique est ajustée pour s’ajuster à la zone. Appelez la `DoModal` méthode pour démarrer une boîte de dialogue modale.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afximageeditordialog. h

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a> CMFCImageEditorDialog :: CMFCImageEditorDialog

Construit un objet `CMFCImageEditorDialog`.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>Paramètres

*pBitmap*<br/>
Pointeur vers une image.

*pParent*<br/>
Pointeur vers la fenêtre parente de la boîte de dialogue Éditeur d’images en cours.

*nBitsPixel*<br/>
Nombre de bits utilisés pour représenter la couleur d’un pixel unique, également appelé profondeur de couleur.  Si le paramètre *nBitsPixel* est-1, la profondeur de couleur est dérivée de l’image spécifiée par le paramètre *pBitmap* . La valeur par défaut est -1.

### <a name="return-value"></a>Valeur renvoyée

Pour modifier une image, transmettez un pointeur d’image vers le `CMFCImageEditorDialog` constructeur. Appelez ensuite la `DoModal` méthode pour ouvrir une boîte de dialogue modale. Lorsque la `DoModal` méthode retourne, la bitmap contient la nouvelle image.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCImageEditorDialog` classe. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)
