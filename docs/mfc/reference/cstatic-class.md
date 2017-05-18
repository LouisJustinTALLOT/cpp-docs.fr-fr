---
title: Classe de CStatic | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- enhanced metafiles
- cursors, displaying
- static controls
- controls [MFC], static
- icons, displaying
- CStatic class
- enhanced metafiles, displaying
- bitmaps, displaying
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0209fad1b84b782cdec7927cb5a04e9bb3083d64
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="cstatic-class"></a>CStatic (classe)
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
 Un contrôle statique affiche une chaîne de texte, boîte, rectangle, icône, curseur, bitmap ou métafichier amélioré. Il peut servir à étiqueter, zone ou séparer des autres contrôles. Normalement, un contrôle statique ne demande aucune saisie et ne fournit aucune sortie ; Toutefois, il peut informer son parent de clics de souris si elle est créée avec **SS_NOTIFY** style.  
  
 Créez un contrôle statique en deux étapes. Tout d’abord, appelez le constructeur pour construire le `CStatic` de l’objet, puis appelez le [créer](#create) fonction membre pour créer le contrôle statique et l’attacher à la `CStatic` objet.  
  
 Si vous créez un `CStatic` objet dans une boîte de dialogue (via une ressource de boîte de dialogue), le `CStatic` automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.  
  
 Si vous créez un `CStatic` de l’objet dans une fenêtre, vous serez peut-être amené à détruire. Un `CStatic` créé sur la pile dans une fenêtre est automatiquement détruit. Si vous créez le `CStatic` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet à détruire lorsque vous avez terminé avec lui.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="create"></a>CStatic::Create  
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
 Spécifie le texte à placer dans le contrôle. Si **NULL**, aucun texte ne sera visible.  
  
 `dwStyle`  
 Spécifie le style de fenêtre du contrôle statique. Appliquer n’importe quelle combinaison de [styles de contrôle statique](../../mfc/reference/static-styles.md) au contrôle.  
  
 `rect`  
 Spécifie la position et la taille du contrôle statique. Il peut être soit un `RECT` structure ou un `CRect` objet.  
  
 `pParentWnd`  
 Spécifie le `CStatic` fenêtre parente, généralement un `CDialog` objet. Il ne doit pas être **NULL**.  
  
 `nID`  
 Spécifie l’ID de contrôle. du contrôle statique  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Remarques  
 Construire un `CStatic` objet en deux étapes. Tout d’abord, appelez le constructeur `CStatic`, puis appelez **créer**, qui crée le contrôle statique Windows et l’attache à le `CStatic` objet.  
  
 Appliquez ce qui suit [styles de fenêtre](../../mfc/reference/window-styles.md) à un contrôle statique :  
  
- **WS_CHILD** toujours  
  
- **WS_VISIBLE** généralement  
  
- **WS_DISABLED** rarement  
  
 Si vous souhaitez afficher un bitmap, un curseur, une icône ou un métafichier dans le contrôle statique, vous devez appliquer l’une des opérations suivantes [styles statiques](../../mfc/reference/static-styles.md):  
  
- **SS_BITMAP** utiliser ce style pour les images bitmap.  
  
- **SS_ICON** utiliser ce style pour les icônes et les curseurs.  
  
- **SS_ENHMETAFILE** utiliser ce style pour les métafichiers améliorés.  
  
 Pour les curseurs, des bitmaps ou des icônes, vous souhaiterez également utiliser le style suivant :  
  
- **SS_CENTERIMAGE** permet de centrer l’image dans le contrôle statique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&1;](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="cstatic"></a>CStatic::CStatic  
 Construit un objet `CStatic`.  
  
```  
CStatic();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&2;](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="drawitem"></a>CStatic::DrawItem  
 Appelé par l’infrastructure pour dessiner un contrôle statique owner-drawn.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpDrawItemStruct`  
 Un pointeur vers un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure. La structure contient des informations sur l’élément à dessiner et le type de dessin requis.  
  
### <a name="remarks"></a>Remarques  
 Remplacez cette fonction pour implémenter le dessin pour un owner-drawn **CStatic** objet (le contrôle a le style **SS_OWNERDRAW**).  
  
##  <a name="getbitmap"></a>CStatic::GetBitmap  
 Obtient le handle de l’image bitmap, précédemment défini avec [SetBitmap](#setbitmap), qui est associé à `CStatic`.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle de bitmap actuel, ou **NULL** si aucune image bitmap n’a été définie.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&3;](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="getcursor"></a>CStatic::GetCursor  
 Obtient le handle du curseur, défini précédemment avec [SetCursor](#setcursor), qui est associé à `CStatic`.  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle du curseur en cours, ou **NULL** si aucun curseur n’a été définie.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&4;](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="getenhmetafile"></a>CStatic::GetEnhMetaFile  
 Obtient le handle du métafichier amélioré, précédemment défini avec [SetEnhMetafile](#setenhmetafile), qui est associé à `CStatic`.  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle de métafichier amélioré en cours, ou **NULL** si aucun métafichier amélioré n’a été défini.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&5;](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="geticon"></a>CStatic::GetIcon  
 Obtient le handle de l’icône, précédemment défini avec [SetIcon](#seticon), qui est associé à `CStatic`.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle de l’icône en cours, ou **NULL** si aucune icône n’a pas été définie.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&6;](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="setbitmap"></a>CStatic::SetBitmap  
 Associe une nouvelle image bitmap au contrôle statique.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Paramètres  
 `hBitmap`  
 Handle de l’image bitmap dans le contrôle statique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de l’image bitmap qui a été précédemment associé à un contrôle statique, ou `NULL` si aucune image bitmap a été associé au contrôle statique.  
  
### <a name="remarks"></a>Notes  
 La bitmap est dessinée automatiquement dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique sera redimensionné à la taille de la bitmap.  
  
 Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, et notamment :  
  
-   SS_BITMAP utilisez toujours ce style pour les images bitmap.  
  
-   Utilisation de SS_CENTERIMAGE pour centrer l’image dans le contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera rempli par la couleur du pixel dans le coin supérieur gauche de la bitmap.  
  
-   MFC fournit la classe `CBitmap`, que vous pouvez utiliser lorsque vous avez à plus avec une image bitmap de juste appeler Win32 fonction `LoadBitmap`. `CBitmap`, qui contient un type d’objet GDI, est souvent utilisé en coopération avec `CStatic`, qui est un `CWnd` classe qui est utilisée pour l’affichage d’un objet graphique comme un contrôle statique.  
  
 `CImage`est une classe ATL/MFC qui vous permet de travailler facilement avec les bitmaps indépendants du périphérique (DIB). Pour plus d’informations, consultez [CImage (classe)](../../atl-mfc-shared/reference/cimage-class.md).  
  
-   L’utilisation classique consiste à donner `CStatic::SetBitmap` un objet GDI qui est retourné par l’opérateur HBITMAP d’un `CBitmap` ou `CImage` objet. Le code permettant cela ressemble à la ligne suivante.  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
L’exemple suivant crée deux `CStatic` objets sur le tas. Il charge ensuite une avec une image bitmap du système via `CBitmap::LoadOEMBitmap` et l’autre à partir d’un fichier à l’aide de `CImage::Load`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&3;](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="setcursor"></a>CStatic::SetCursor  
 Associe une nouvelle image de curseur avec le contrôle statique.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Paramètres  
 `hCursor`  
 Handle du curseur dans le contrôle statique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du curseur associé précédemment au contrôle statique, ou **NULL** si aucun curseur n’a été associé au contrôle statique.  
  
### <a name="remarks"></a>Remarques  
 Le curseur sera dessiné automatiquement dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique sera redimensionné à la taille du curseur.  
  
 Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, y compris les éléments suivants :  
  
- **SS_ICON** utiliser ce style toujours pour les icônes et les curseurs.  
  
- **SS_CENTERIMAGE** utilisation au centre du contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera remplie avec la couleur d’arrière-plan du contrôle statique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&4;](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="setenhmetafile"></a>CStatic::SetEnhMetaFile  
 Associe une nouvelle image de métafichier amélioré avec le contrôle statique.  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>Paramètres  
 `hMetaFile`  
 Handle du métafichier amélioré dans le contrôle statique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du métafichier amélioré précédemment associé au contrôle statique, ou **NULL** si aucun métafichier amélioré a été associé au contrôle statique.  
  
### <a name="remarks"></a>Notes  
 Métafichier amélioré sera automatiquement dessiné dans le contrôle statique. Métafichier amélioré est redimensionné pour s’ajuster à la taille du contrôle statique.  
  
 Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, y compris les éléments suivants :  
  
- **SS_ENHMETAFILE** utiliser ce style toujours des métafichiers améliorés.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&5;](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="seticon"></a>CStatic::SetIcon  
 Associe une nouvelle image de l’icône du contrôle statique.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Paramètres  
 `hIcon`  
 Handle de l’icône qui s’affichera dans le contrôle statique.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de l’icône précédemment associé au contrôle statique, ou **NULL** si aucune icône n’a été associé au contrôle statique.  
  
### <a name="remarks"></a>Remarques  
 L’icône sera automatiquement dessinée dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique sera redimensionné à la taille de l’icône.  
  
 Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, y compris les éléments suivants :  
  
- **SS_ICON** utiliser ce style toujours pour les icônes et les curseurs.  
  
- **SS_CENTERIMAGE** utilisation au centre du contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera remplie avec la couleur d’arrière-plan du contrôle statique.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CStatic n °&6;](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [CButton (classe)](../../mfc/reference/cbutton-class.md)   
 [CComboBox (classe)](../../mfc/reference/ccombobox-class.md)   
 [Classe CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (classe)](../../mfc/reference/clistbox-class.md)   
 [CScrollBar (classe)](../../mfc/reference/cscrollbar-class.md)   
 [CDialog (classe)](../../mfc/reference/cdialog-class.md)

