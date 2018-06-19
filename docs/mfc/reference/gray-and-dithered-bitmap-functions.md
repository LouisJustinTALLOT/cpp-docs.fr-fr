---
title: Fonctions d’image Bitmap tramée et grise | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
dev_langs:
- C++
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de887cdbe80642925bc935eb48726a59850f6f96
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375172"
---
# <a name="gray-and-dithered-bitmap-functions"></a>fonctions d'image bitmap tramée et grise
**Fonctions d’image bitmap grise**  
  
 MFC propose deux fonctions qui permettent de donner à une image bitmap l’apparence d’un contrôle désactivé.  
  
 ![Comparaison des versions d’icônes grises et d’origine](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
|||  
|-|-|  
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|Dessine une version grise d’une image bitmap.|  
|[AfxGetGrayBitmap](#afxgetgraybitmap)|Copie une version grise d’une image bitmap.|  
  
 **Fonctions d’image bitmap tramée**  
  
 MFC propose également deux fonctions qui permettent de remplacer l’arrière-plan d’une image bitmap par un motif tramé.  
  
 ![Comparaison des versions d’icônes dégradées et d’origine](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
|||  
|-|-|  
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|Dessine une image bitmap avec un arrière-plan tramé.|  
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|Copie une image bitmap avec un arrière-plan tramé.|  
  
##  <a name="afxdrawgraybitmap"></a>  AfxDrawGrayBitmap  
 Dessine une version grise d’une image bitmap.  
  
```   
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Pointe vers le contrôleur de domaine de destination.  
  
 *x*  
 Coordonnée x de destination.  
  
 *y*  
 Coordonnée y de destination.  
  
 `rSrc`  
 Image bitmap source.  
  
 `crBackground`  
 Nouvelle couleur d’arrière-plan (généralement grise, comme COLOR_MENU).  
  
### <a name="remarks"></a>Notes  
 Une image bitmap dessinée avec `AfxDrawGrayBitmap` a l’apparence d’un contrôle désactivé.  
  
 ![Comparaison des versions d’icônes grises et d’origine](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  

##  <a name="afxgetgraybitmap"></a>  AfxGetGrayBitmap  
 Copie une version grise d’une image bitmap.  
  
```   
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>Paramètres  
 `rSrc`  
 Image bitmap source.  
  
 `pDest`  
 Image bitmap de destination.  
  
 `crBackground`  
 Nouvelle couleur d’arrière-plan (généralement grise, comme COLOR_MENU).  
  
### <a name="remarks"></a>Notes  
 Une image bitmap copiée avec `AfxGetGrayBitmap` a l’apparence d’un contrôle désactivé.  
  
 ![Comparaison des versions d’icônes grises et d’origine](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="afxdrawditheredbitmap"></a>  AfxDrawDitheredBitmap  
 Dessine une image bitmap, en remplaçant son arrière-plan avec un motif tramé (outil d’analyse).  
  
```   
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Pointe vers le contrôleur de domaine de destination.  
  
 *x*  
 Coordonnée x de destination.  
  
 *y*  
 Coordonnée y de destination.  
  
 `rSrc`  
 Image bitmap source.  
  
 `cr1`  
 Une des couleurs de deux tramage, est généralement le blanc.  
  
 `cr2`  
 Autres tramage couleur, généralement gris clair (COLOR_MENU).  
  
### <a name="remarks"></a>Notes  
 Le bitmap source est dessiné sur le contrôleur de domaine de destination avec deux couleurs ( `cr1` et `cr2`) Damier remplacer l’arrière-plan de l’image bitmap. L’arrière-plan de l’image bitmap source est défini comme son blanc et tous les pixels correspondant à la couleur du pixel dans le coin supérieur gauche de l’image bitmap.  
  
 ![Comparaison des versions d’icônes dégradées et d’origine](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  


##  <a name="afxgetditheredbitmap"></a>  AfxGetDitheredBitmap  
 Copie une image bitmap, en remplaçant son arrière-plan avec un motif tramé (outil d’analyse).  
  
```   
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>Paramètres  
 `rSrc`  
 Image bitmap source.  
  
 `pDest`  
 Image bitmap de destination.  
  
 `cr1`  
 Une des couleurs de deux tramage, est généralement le blanc.  
  
 `cr2`  
 Autres tramage couleur, généralement gris clair (COLOR_MENU).  
  
### <a name="remarks"></a>Notes  
 Le bitmap source est copié vers le bitmap de destination avec deux couleurs ( `cr1` et `cr2`) Damier remplaçant arrière-plan de l’image du bitmap source. L’arrière-plan de l’image bitmap source est défini comme son blanc et tous les pixels correspondant à la couleur du pixel dans le coin supérieur gauche de l’image bitmap.  
  
 ![Comparaison des versions d’icônes dégradées et d’origine](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
