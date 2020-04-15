---
title: Classe CMFCImageEditorDialog
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 23c2a919428689fe107b82041bd87b758ede2bc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367464"
---
# <a name="cmfcimageeditordialog-class"></a>Classe CMFCImageEditorDialog

La `CMFCImageEditorDialog` classe prend en charge une boîte de dialogue d’éditeur d’images.

## <a name="syntax"></a>Syntaxe

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Construit un objet `CMFCImageEditorDialog`.|

## <a name="remarks"></a>Notes

La `CMFCImageEditorDialog` classe fournit une boîte de dialogue qui comprend:

- Une zone d’image que vous utilisez pour modifier les pixels individuels d’une image.

- Dessiner des outils pour modifier les pixels dans la zone d’image.

- Une palette de couleurs pour spécifier la couleur utilisée par les outils de dessin.

- Une zone de prévisualisation qui affiche l’effet de votre modification.

L’illustration suivante montre une boîte de dialogue d’éditeur d’images.

![Boîte de dialogue CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "Boîte de dialogue CMFCImageEditorDialog")

Une façon d’utiliser un `CMFCImageEditorDialog` objet `CBitmap` est de lui transmettre une image à modifier. Ne créez pas une grande image parce que la zone d’édition d’image a une taille limitée et la taille logique de pixel est ajustée pour s’adapter à la zone. Appelez `DoModal` la méthode pour démarrer une boîte de dialogue modal.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afximageeditordialog.h

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a>CMFCImageEditorDialog::CMFCImageEditorDialog

Construit un objet `CMFCImageEditorDialog`.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>Paramètres

*pBitmap (en)*<br/>
Pointeur vers une image.

*pParent*<br/>
Pointeur vers la fenêtre parente de la boîte de dialogue actuelle de l’éditeur d’images.

*nBitsPixel*<br/>
Le nombre de bits utilisés pour représenter la couleur d’un seul pixel, qui est également appelé profondeur de couleur.  Si le *paramètre nBitsPixel* est de -1, la profondeur de couleur est dérivée de l’image spécifiée par le paramètre *pBitmap.* La valeur par défaut est -1.

### <a name="return-value"></a>Valeur de retour

Pour modifier une image, passez un `CMFCImageEditorDialog` pointeur d’image au constructeur. Ensuite, `DoModal` appelez la méthode pour ouvrir une boîte de dialogue modal. Lorsque `DoModal` la méthode revient, la bitmap contient la nouvelle image.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCImageEditorDialog` un objet de la classe. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
