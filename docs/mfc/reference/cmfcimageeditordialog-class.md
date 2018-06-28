---
title: Classe de CMFCImageEditorDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af19a9dcb207afa482f54e26540a6b706d607ce0
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040767"
---
# <a name="cmfcimageeditordialog-class"></a>Classe de CMFCImageEditorDialog
La `CMFCImageEditorDialog` classe prend en charge une image de boîte de dialogue de l’éditeur.  
  
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
 La `CMFCImageEditorDialog` classe fournit une boîte de dialogue qui inclut :  
  
-   Une zone d’image qui vous permet de modifier les pixels individuels dans une image.  
  
-   Outils pour modifier les pixels de la zone de dessin.  
  
-   Une palette de couleurs pour spécifier la couleur qui est utilisée par les outils de dessin.  
  
-   Une zone d’aperçu qui affiche l’effet de votre modification.  
  
 L’illustration suivante montre un éditeur d’images de boîte de dialogue.  
  
 ![Boîte de dialogue CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "imageedit")  
  
 Une des façons d’utiliser un `CMFCImageEditorDialog` objet consiste à passer un `CBitmap` image à modifier. Ne créez pas une grande image, car l’image de zone de modification a une taille limitée et la taille en pixels logiques est ajustée pour tenir dans la zone. Appelez le `DoModal` méthode pour démarrer une boîte de dialogue modale.  
  
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
 *pBitmap*  
 Pointeur vers une image.  
  
 *pParent*  
 Pointeur vers la fenêtre parente de la boîte de dialogue Éditeur image actuelle.  
  
 *nBitsPixel*  
 Le nombre de bits utilisés pour représenter la couleur d’un pixel, qui est également appelé profondeur de couleur.  Si le *nBitsPixel* paramètre est -1, la profondeur de couleur est dérivée de l’image spécifiée par la *pBitmap* paramètre. La valeur par défaut est -1.  
  
### <a name="return-value"></a>Valeur de retour  
 Pour modifier une image, passer un pointeur d’image pour le `CMFCImageEditorDialog` constructeur. Appelez ensuite la `DoModal` méthode pour ouvrir la boîte de dialogue modale. Lorsque la `DoModal` méthode est retournée, la bitmap contient la nouvelle image.  
  
### <a name="remarks"></a>Notes  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCImageEditorDialog` classe. Cet exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]  
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)
