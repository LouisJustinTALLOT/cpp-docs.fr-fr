---
title: Cstatic, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 02e2f20cc568e8846923f7189da3ea45478fc289
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323867"
---
# <a name="cstatic-class"></a>Cstatic, classe

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
|[CStatic::Create](#create)|Crée le contrôle statique Windows et l’attache à la `CStatic` objet.|
|[CStatic::DrawItem](#drawitem)|Méthode override pour dessiner un contrôle statique owner-drawn.|
|[CStatic::GetBitmap](#getbitmap)|Récupère le handle de l’image bitmap précédemment défini avec [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Récupère le handle de l’image curseur défini précédemment avec [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Récupère le handle du métafichier amélioré précédemment défini avec [SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Récupère le handle de l’icône précédemment défini avec [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Spécifie une image bitmap à afficher dans le contrôle statique.|
|[CStatic::SetCursor](#setcursor)|Spécifie une image de curseur à afficher dans le contrôle statique.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Spécifie un métafichier amélioré à afficher dans le contrôle statique.|
|[CStatic::SetIcon](#seticon)|Spécifie l’icône à afficher dans le contrôle statique.|

## <a name="remarks"></a>Notes

Un contrôle statique affiche une chaîne de texte, boîte, rectangle, icône, curseur, bitmap ou métafichier amélioré. Il peut servir à étiqueter, zone ou séparer des autres contrôles. Normalement, un contrôle statique ne prend aucune entrée et ne fournit aucune sortie ; Toutefois, il peut informer son parent de clics de souris s’il est créé avec le style SS_NOTIFY.

Créer un contrôle statique en deux étapes. Tout d’abord, appelez le constructeur pour construire le `CStatic` de l’objet, puis appelez le [créer](#create) fonction membre pour créer le contrôle statique et l’attacher à la `CStatic` objet.

Si vous créez un `CStatic` objet au sein d’une boîte de dialogue (via une ressource de boîte de dialogue), le `CStatic` automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CStatic` de l’objet dans une fenêtre, vous serez peut-être amené à détruire. Un `CStatic` objet créé sur la pile au sein d’une fenêtre est automatiquement détruit. Si vous créez le `CStatic` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet à détruire lorsque vous avez terminé avec lui.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="create"></a>  CStatic::Create

Crée le contrôle statique Windows et l’attache à la `CStatic` objet.

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Spécifie le texte à placer dans le contrôle. Si NULL, aucun texte ne seront visible.

*dwStyle*<br/>
Spécifie le style de fenêtre du contrôle statique. Appliquer n’importe quelle combinaison de [styles de contrôle statique](../../mfc/reference/styles-used-by-mfc.md#static-styles) au contrôle.

*rect*<br/>
Spécifie la position et la taille du contrôle statique. Il peut s’agir un `RECT` structure ou un `CRect` objet.

*pParentWnd*<br/>
Spécifie le `CStatic` fenêtre parente, généralement un `CDialog` objet. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle. du contrôle statique

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Construire un `CStatic` objet en deux étapes. Tout d’abord, appelez le constructeur `CStatic`, puis appelez `Create`, ce qui crée le contrôle statique Windows et l’attache à la `CStatic` objet.

Appliquer les éléments suivants [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à un contrôle statique :

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

Si vous voulez afficher un bitmap, un curseur, une icône ou un métafichier dans le contrôle statique, vous devez appliquer l’une des opérations suivantes [styles statiques](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP utiliser ce style pour les bitmaps.

- SS_ICON utiliser ce style pour les icônes et curseurs.

- SS_ENHMETAFILE utiliser ce style de métafichiers améliorés.

Pour les curseurs, des bitmaps ou des icônes, peut également voulez-vous utiliser le style suivant :

- Utilisation de SS_CENTERIMAGE pour centrer l’image dans le contrôle statique.

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

*lpDrawItemStruct*<br/>
Un pointeur vers un [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) structure. La structure contient des informations sur l’élément à dessiner et le type de dessin requis.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour implémenter le dessin pour un owner-drawn `CStatic` objet (le contrôle a le style SS_OWNERDRAW).

##  <a name="getbitmap"></a>  CStatic::GetBitmap

Obtient le handle de l’image bitmap, précédemment défini avec [SetBitmap](#setbitmap), qui est associé à `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valeur de retour

Handle vers l’image bitmap active, ou NULL si aucune bitmap n’a pas été définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>  CStatic::GetCursor

Obtient le handle du curseur, précédemment défini avec [SetCursor](#setcursor), qui est associé à `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valeur de retour

Handle vers le curseur actuel, ou NULL si aucun curseur n’a été définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile

Obtient le handle du métafichier amélioré, précédemment défini avec [SetEnhMetafile](#setenhmetafile), qui est associé à `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Valeur de retour

Handle du métafichier amélioré actuel, ou NULL si aucun métafichier amélioré n’a pas été définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>  CStatic::GetIcon

Obtient le handle de l’icône, précédemment défini avec [SetIcon](#seticon), qui est associé à `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valeur de retour

Handle vers l’icône actuelle, ou NULL si aucune icône n’a pas été définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>  CStatic::SetBitmap

Associe une nouvelle image bitmap avec le contrôle statique.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap*<br/>
Handle de la bitmap à dessiner dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

Le handle de la bitmap qui a été associé précédemment avec le contrôle statique, ou NULL si aucune bitmap a été associé au contrôle statique.

### <a name="remarks"></a>Notes

L’image bitmap sera automatiquement dessinée dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique est redimensionné à la taille de la bitmap.

Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, notamment :

- SS_BITMAP utilisez toujours ce style pour les bitmaps.

- Utilisation de SS_CENTERIMAGE pour centrer l’image dans le contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera rempli par la couleur du pixel dans le coin supérieur gauche de l’image bitmap.

- MFC fournit la classe `CBitmap`, que vous pouvez utiliser lorsque vous avez à plus avec une image bitmap que simplement appeler Win32 fonction `LoadBitmap`. `CBitmap`, qui contient un type d’objet GDI, est souvent utilisé en coopération avec `CStatic`, qui est un `CWnd` classe qui est utilisée pour l’affichage d’un objet graphique comme un contrôle statique.

`CImage` est une classe ATL/MFC qui vous permet de plus facilement travailler avec les bitmaps indépendants du périphérique (DIB). Pour plus d’informations, consultez [classe CImage](../../atl-mfc-shared/reference/cimage-class.md).

- Utilisation typique consiste à donner `CStatic::SetBitmap` un objet GDI qui est retourné par l’opérateur HBITMAP d’un `CBitmap` ou `CImage` objet. Le code pour effectuer cela ressemble à la ligne suivante.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
L’exemple suivant crée deux `CStatic` objets sur le tas. Il charge ensuite une avec un bitmap de système en utilisant `CBitmap::LoadOEMBitmap` et l’autre à partir d’un fichier `CImage::Load`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>  CStatic::SetCursor

Associe une nouvelle image de curseur avec le contrôle statique.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Paramètres

*hCursor*<br/>
Handle du curseur à dessiner dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

Le handle du curseur associé précédemment avec le contrôle statique, ou NULL si aucun curseur n’a été associé au contrôle statique.

### <a name="remarks"></a>Notes

Le curseur sera dessiné automatiquement dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique est redimensionné à la taille du curseur.

Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, notamment les suivantes :

- SS_ICON utilisez toujours ce style pour les icônes et curseurs.

- Utilisation de SS_CENTERIMAGE pour centrer dans le contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera rempli avec la couleur d’arrière-plan du contrôle statique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile

Associe une nouvelle image métafichier amélioré avec le contrôle statique.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Paramètres

*hMetaFile*<br/>
Handle du métafichier amélioré à dessiner dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

Le handle du métafichier amélioré précédemment associé avec le contrôle statique, ou NULL si aucun métafichier amélioré a été associé au contrôle statique.

### <a name="remarks"></a>Notes

Métafichier amélioré sera automatiquement dessiné dans le contrôle statique. Métafichier amélioré est mis à l’échelle pour s’ajuster à la taille du contrôle statique.

Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, notamment les suivantes :

- SS_ENHMETAFILE, utilisez toujours ce style de métafichiers améliorés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>  CStatic::SetIcon

Associe une nouvelle image d’icône avec le contrôle statique.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*hIcon*<br/>
Handle de l’icône qui s’affichera dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

Handle de l’icône précédemment associée à la contrôle statique, ou NULL si aucune icône n’a été associé au contrôle statique.

### <a name="remarks"></a>Notes

L’icône sera automatiquement dessinée dans le contrôle statique. Par défaut, il est dessiné dans le coin supérieur gauche et le contrôle statique est redimensionné à la taille de l’icône.

Vous pouvez utiliser différents de fenêtre et de styles de contrôle statique, notamment les suivantes :

- SS_ICON utilisez toujours ce style pour les icônes et curseurs.

- Utilisation de SS_CENTERIMAGE pour centrer dans le contrôle statique. Si l’image est plus grande que le contrôle statique, il apparaît découpé. Si elle est inférieure à celle du contrôle statique, l’espace vide autour de l’image sera rempli avec la couleur d’arrière-plan du contrôle statique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)
