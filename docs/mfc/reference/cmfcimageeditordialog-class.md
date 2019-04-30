---
title: CMFCImageEditorDialog, classe
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 97f16fa00b2e90fd9c43bf9b6792b4eafe7d7b88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394526"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog, classe

Le `CMFCImageEditorDialog` classe prend en charge une image de boîte de dialogue Éditeur.

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

Le `CMFCImageEditorDialog` classe fournit une boîte de dialogue qui inclut :

- Une zone d’image qui vous permettent de modifier des pixels individuels dans une image.

- Outils pour modifier les pixels dans la zone de dessin.

- Une palette de couleurs pour spécifier la couleur qui est utilisée par les outils de dessin.

- Une zone d’aperçu qui affiche l’effet de votre modification.

L’illustration suivante montre un éditeur d’images de boîte de dialogue.

![Boîte de dialogue CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "boîte de dialogue CMFCImageEditorDialog")

Une façon d’utiliser un `CMFCImageEditorDialog` objet consiste à passer un `CBitmap` image à modifier. Ne créez pas une grande image, car l’image de zone de modification a une taille limitée et la taille en pixels logiques est ajustée à la zone. Appelez le `DoModal` méthode de démarrage d’une boîte de dialogue modale.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afximageeditordialog.h

##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog

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
Pointeur vers la fenêtre parente de la boîte de dialogue Éditeur image actuelle.

*nBitsPixel*<br/>
Le nombre de bits utilisés pour représenter la couleur d’un pixel unique, qui est également désignée comme la profondeur de couleur.  Si le *nBitsPixel* paramètre est -1, la profondeur de couleur est dérivée de l’image spécifiée par la *pBitmap* paramètre. La valeur par défaut est -1.

### <a name="return-value"></a>Valeur de retour

Pour modifier une image, passez un pointeur de l’image vers le `CMFCImageEditorDialog` constructeur. Appelez ensuite la `DoModal` méthode pour ouvrir une boîte de dialogue modale. Lorsque le `DoModal` méthode est retournée, la bitmap contient la nouvelle image.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCImageEditorDialog` classe. Cet exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)
