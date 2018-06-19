---
title: Classe de CStatic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
dev_langs:
- C++
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3b1a5dcfc8481727bffd8b80e0bb1b230d56ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375002"
---
# <a name="cstatic-class"></a>Classe de CStatic
Fournit les fonctionnalités d'un contrôle statique Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStatic : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStatic::CStatic](#cstatic)|Construit un objet `CStatic`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CStatic::Create](#create)|Crée le contrôle statique Windows et l’attache à le `CStatic` objet.|  
|[CStatic::DrawItem](#drawitem)|Substituez pour dessiner un contrôle statique owner-drawn.|  
|[CStatic::GetBitmap](#getbitmap)|Récupère le handle de l’image bitmap précédemment défini avec [SetBitmap](#setbitmap).|  
|[CStatic::GetCursor](#getcursor)|Récupère le handle de l’image de curseur défini précédemment avec [SetCursor](#setcursor).|  
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Récupère le handle du métafichier amélioré précédemment défini avec [SetEnhMetaFile](#setenhmetafile).|  
|[CStatic::GetIcon](#geticon)|Récupère le handle de l’icône précédemment défini avec [SetIcon](#seticon).|  
|[CStatic::SetBitmap](#setbitmap)|Spécifie une image bitmap à afficher dans le contrôle statique.|  
|[CStatic::SetCursor](#setcursor)|Spécifie une image de curseur à afficher dans le contrôle statique.|  
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Spécifie un métafichier amélioré à afficher dans le contrôle statique.|  
|[CStatic::SetIcon](#seticon)|Spécifie l’icône à afficher dans le contrôle statique.|  
  
## <a name="remarks"></a>Notes  
 Un contrôle statique affiche une chaîne de texte, boîte, rectangle, icône, curseur, bitmap ou métafichier amélioré. Il peut être utilisé pour étiqueter, de zone ou de séparer des autres contrôles. Normalement, un contrôle statique n’accepte aucune entrée et ne fournit aucune sortie ; Toutefois, il peut avertir son parent de clics de souris s’il est créé avec **SS_NOTIFY** style.  
  
 Créez un contrôle statique en deux étapes. Tout d’abord, appelez le constructeur pour construire le `CStatic` de l’objet, puis appelez le [créer](#create) fonction membre pour créer le contrôle statique et l’attacher à la `CStatic` objet.  
  
 Si vous créez un `CStatic` objet dans une boîte de dialogue (via une ressource de boîte de dialogue), le `CStatic` objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.  
  
 Si vous créez un `CStatic` de l’objet dans une fenêtre, vous devrez peut-être également détruire. A `CStatic` objet créé sur la pile au sein d’une fenêtre est automatiquement détruit. Si vous créez le `CStatic` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet pour détruire lorsque vous avez terminé avec lui.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="create"></a>  CStatic::Create  
 Crée le contrôle statique Windows et l’attache à le `CStatic` objet.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszText,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID = 0xffff);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszText`  
 Spécifie le texte à placer dans le contrôle. Si **NULL**, aucun texte ne seront visible.  
  
 `dwStyle`  
 Spécifie le style de fenêtre du contrôle statique. Appliquer n’importe quelle combinaison de [styles du contrôle statique](../../mfc/reference/styles-used-by-mfc.md#static-styles) au contrôle.  
  
 `rect`  
 Spécifie la position et la taille du contrôle statique. Il peut être soit un `RECT` structure ou un `CRect` objet.  
  
 `pParentWnd`  
 Spécifie le `CStatic` fenêtre parente, généralement un `CDialog` objet. Il ne doit pas être **NULL**.  
  
 `nID`  
 Spécifie l’ID de contrôle. du contrôle statique  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Construire un `CStatic` objet en deux étapes. Tout d’abord, appelez le constructeur `CStatic`, puis appelez **créer**, ce qui crée le contrôle statique Windows et l’attache à le `CStatic` objet.  
  
 Appliquez ce qui suit [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à un contrôle statique :  
  
- **WS_CHILD** toujours  
  
- **WS_VISIBLE** généralement  
  
- **WS_DISABLED** rarement  
  
 Si vous souhaitez afficher une image bitmap, un curseur, une icône ou un métafichier dans le contrôle statique, vous devez appliquer l’une des opérations suivantes [styles statiques](../../mfc/reference/styles-used-by-mfc.md#static-styles):  
  
- **SS_BITMAP** utiliser ce style pour les images bitmap.  
  
- **SS_ICON** utiliser ce style pour les icônes et curseurs.  
  
- **SS_ENHMETAFILE** utiliser ce style pour les métafichiers améliorés.  
  
 Pour les curseurs, bitmaps et icônes, vous pouvez souhaiter utiliser le style suivant :  
  
- **SS_CENTERIMAGE** utiliser pour centrer l’image dans le contrôle statique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="cstatic"></a>  CStatic::CStatic  
 Construit un objet `CStatic`.  
  
```  
CStatic();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="drawitem"></a>  CStatic::DrawItem  
 Appelé par l’infrastructure pour dessiner un contrôle statique owner-drawn.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpDrawItemStruct`  
 Un pointeur vers un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure. La structure contient des informations sur l’élément doit être dessiné et le type de dessin nécessaire.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour implémenter le dessin pour un owner-drawn **CStatic** objet (le contrôle a le style **SS_OWNERDRAW**).  
  
##  <a name="getbitmap"></a>  CStatic::GetBitmap  
 Obtient le handle de l’image bitmap, précédemment défini avec [SetBitmap](#setbitmap), qui est associé à `CStatic`.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle vers l’image bitmap actuelle, ou **NULL** si aucune image bitmap n’a été défini.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="getcursor"></a>  CStatic::GetCursor  
 Obtient le handle du curseur, défini précédemment avec [SetCursor](#setcursor), qui est associé à `CStatic`.  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle du curseur actuel, ou **NULL** si aucun curseur n’a été défini.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile  
 Obtient le handle du métafichier amélioré, précédemment défini avec [SetEnhMetafile](#setenhmetafile), qui est associé à `CStatic`.  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle vers le métafichier amélioré en cours, ou **NULL** si aucun métafichier amélioré n’a été défini.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="geticon"></a>  CStatic::GetIcon  
 Obtient le handle de l’icône précédemment défini avec [SetIcon](#seticon), qui est associé à `CStatic`.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle vers l’icône en cours, ou **NULL** si aucune icône n’a pas été définie.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="setbitmap"></a>  CStatic::SetBitmap  
 Associe une nouvelle image bitmap avec le contrôle statique.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 `hBitmap`  
 Handle de l’image bitmap à dessiner dans le contrôle statique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de la bitmap qui a été précédemment associé au contrôle statique, ou `NULL` si aucune image bitmap a été associé au contrôle statique.  
  
### <a name="remarks"></a>Notes  
 La bitmap est dessinée automatiquement dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique doit être redimensionné à la taille de l’image bitmap.  
  
 Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, et notamment :  
  
-   SS_BITMAP utiliser toujours ce style pour les images bitmap.  
  
-   Utilisez SS_CENTERIMAGE pour centrer l’image dans le contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera rempli par la couleur du pixel dans le coin supérieur gauche de l’image bitmap.  
  
-   MFC fournit la classe `CBitmap`, que vous pouvez utiliser lorsque vous avez besoin de plus avec une image bitmap que simplement appeler Win32 fonctionnent `LoadBitmap`. `CBitmap`, qui contient un type d’objet GDI, est souvent utilisée en coopération avec `CStatic`, qui est un `CWnd` classe qui est utilisé pour afficher un objet graphique comme un contrôle statique.  
  
 `CImage` est une classe ATL/MFC qui vous permet de plus facilement travailler avec les bitmaps indépendants du périphérique (DIB). Pour plus d’informations, consultez [CImage (classe)](../../atl-mfc-shared/reference/cimage-class.md).  
  
-   Utilisation typique consiste à donner `CStatic::SetBitmap` un objet GDI qui est retourné par l’opérateur HBITMAP d’un `CBitmap` ou `CImage` objet. Le code ressemble à la ligne suivante.  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
L’exemple suivant crée deux `CStatic` objets sur le tas. Il charge ensuite l’autre avec une image bitmap de système à l’aide de `CBitmap::LoadOEMBitmap` et l’autre à partir d’un fichier à l’aide de `CImage::Load`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="setcursor"></a>  CStatic::SetCursor  
 Associe une nouvelle image de curseur avec le contrôle statique.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Paramètres  
 `hCursor`  
 Handle du curseur dans le contrôle statique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du curseur associé précédemment au contrôle statique, ou **NULL** si aucun curseur n’a été associé au contrôle statique.  
  
### <a name="remarks"></a>Notes  
 Le curseur est dessiné automatiquement dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique doit être redimensionné à la taille du curseur.  
  
 Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, notamment les suivantes :  
  
- **SS_ICON** utiliser ce style toujours pour les icônes et curseurs.  
  
- **SS_CENTERIMAGE** utilisation au centre du contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera rempli avec la couleur d’arrière-plan du contrôle statique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile  
 Associe une nouvelle image métafichier amélioré avec le contrôle statique.  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>Paramètres  
 `hMetaFile`  
 Handle du métafichier amélioré à dessiner dans le contrôle statique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du métafichier amélioré précédemment associé au contrôle statique, ou **NULL** si aucun métafichier amélioré a été associé au contrôle statique.  
  
### <a name="remarks"></a>Notes  
 Métafichier amélioré sera dessiné automatiquement dans le contrôle statique. Métafichier amélioré est ajusté en fonction de la taille du contrôle statique.  
  
 Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, notamment les suivantes :  
  
- **SS_ENHMETAFILE** utiliser ce style toujours des métafichiers améliorés.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="seticon"></a>  CStatic::SetIcon  
 Associe une nouvelle image d’icône avec le contrôle statique.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Paramètres  
 `hIcon`  
 Handle de l’icône à dessiner dans le contrôle statique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de l’icône précédemment associé au contrôle statique, ou **NULL** si aucune icône n’a été associé au contrôle statique.  
  
### <a name="remarks"></a>Notes  
 L’icône sera dessiné automatiquement dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique doit être redimensionné à la taille de l’icône.  
  
 Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, notamment les suivantes :  
  
- **SS_ICON** utiliser ce style toujours pour les icônes et curseurs.  
  
- **SS_CENTERIMAGE** utilisation au centre du contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera rempli avec la couleur d’arrière-plan du contrôle statique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Classe de CButton](../../mfc/reference/cbutton-class.md)   
 [CComboBox (classe)](../../mfc/reference/ccombobox-class.md)   
 [Classe CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (classe)](../../mfc/reference/clistbox-class.md)   
 [Classe de CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [CDialog, classe](../../mfc/reference/cdialog-class.md)
