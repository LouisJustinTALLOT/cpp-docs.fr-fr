---
title: CStatic, classe
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
ms.openlocfilehash: fc0164b2d0046ca2d36291696dd6137a9fcef069
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447433"
---
# <a name="cstatic-class"></a>CStatic, classe

Fournit les fonctionnalités d'un contrôle statique Windows.

## <a name="syntax"></a>Syntaxe

```
class CStatic : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Construit un objet `CStatic`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CStatic :: Create](#create)|Crée le contrôle statique Windows et l’attache à l’objet `CStatic`.|
|[CStatic ::D rawItem](#drawitem)|Substituez pour dessiner un contrôle statique dessiné par le propriétaire.|
|[CStatic::GetBitmap](#getbitmap)|Récupère le handle de la bitmap précédemment définie avec [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Récupère le handle de l’image de curseur précédemment définie avec [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Récupère le handle du métafichier amélioré précédemment défini avec [SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Récupère le handle de l’icône précédemment définie avec [seticon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Spécifie une image bitmap à afficher dans le contrôle statique.|
|[CStatic::SetCursor](#setcursor)|Spécifie une image de curseur à afficher dans le contrôle statique.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Spécifie un métafichier amélioré à afficher dans le contrôle statique.|
|[CStatic::SetIcon](#seticon)|Spécifie une icône à afficher dans le contrôle statique.|

## <a name="remarks"></a>Notes

Un contrôle statique affiche une chaîne de texte, une zone, un rectangle, une icône, un curseur, une image bitmap ou un métafichier amélioré. Il peut être utilisé pour étiqueter, Box ou séparer d’autres contrôles. Un contrôle statique ne prend normalement aucune entrée et ne fournit aucune sortie ; Toutefois, il peut notifier son parent de clics de souris s’il est créé avec SS_NOTIFY style.

Créez un contrôle statique en deux étapes. Tout d’abord, appelez le constructeur pour construire l’objet `CStatic`, puis appelez la fonction membre [Create](#create) pour créer le contrôle statique et l’attacher à l’objet `CStatic`.

Si vous créez un objet `CStatic` dans une boîte de dialogue (par le biais d’une ressource de boîte de dialogue), l’objet `CStatic` est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un objet `CStatic` dans une fenêtre, vous devrez peut-être également le détruire. Un objet `CStatic` créé sur la pile au sein d’une fenêtre est automatiquement détruit. Si vous créez l’objet `CStatic` sur le segment de mémoire à l’aide de la fonction **New** , vous devez appeler **Delete** sur l’objet pour le détruire lorsque vous avez terminé de l’utiliser.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="create"></a>CStatic :: Create

Crée le contrôle statique Windows et l’attache à l’objet `CStatic`.

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
Spécifie le texte à placer dans le contrôle. Si la valeur est NULL, aucun texte ne sera visible.

*dwStyle*<br/>
Spécifie le style de fenêtre du contrôle statique. Appliquez une combinaison quelconque de [styles de contrôle statiques](../../mfc/reference/styles-used-by-mfc.md#static-styles) au contrôle.

*rectangulaire*<br/>
Spécifie la position et la taille du contrôle statique. Il peut s’agir d’une structure `RECT` ou d’un objet `CRect`.

*pParentWnd*<br/>
Spécifie l' `CStatic` fenêtre parente, généralement un objet `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle du contrôle statique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Construisez un objet `CStatic` en deux étapes. Tout d’abord, appelez le constructeur `CStatic`, puis appelez `Create`, qui crée le contrôle statique Windows et l’attache à l’objet `CStatic`.

Appliquez les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle statique :

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

Si vous envisagez d’afficher une bitmap, un curseur, une icône ou un métafichier dans le contrôle statique, vous devez appliquer l’un des [styles statiques](../../mfc/reference/styles-used-by-mfc.md#static-styles)suivants :

- SS_BITMAP utilisez ce style pour les bitmaps.

- SS_ICON utilisez ce style pour les curseurs et les icônes.

- SS_ENHMETAFILE utiliser ce style pour les refichiers améliorés.

Pour les curseurs, les bitmaps ou les icônes, vous pouvez également utiliser le style suivant :

- SS_CENTERIMAGE utiliser pour centrer l’image dans le contrôle statique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>CStatic::CStatic

Construit un objet `CStatic`.

```
CStatic();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>CStatic ::D rawItem

Appelé par l’infrastructure pour dessiner un contrôle statique dessiné par le propriétaire.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . La structure contient des informations sur l’élément à dessiner et le type de dessin requis.

### <a name="remarks"></a>Notes

Substituez cette fonction pour implémenter le dessin pour un objet `CStatic` owner-drawn (le contrôle a le style SS_OWNERDRAW).

##  <a name="getbitmap"></a>CStatic::GetBitmap

Obtient le handle de l’image bitmap, précédemment définie avec [SetBitmap](#setbitmap), qui est associé à `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valeur de retour

Handle vers la bitmap actuelle, ou NULL si aucune bitmap n’a été définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>CStatic::GetCursor

Obtient le handle du curseur, précédemment défini avec [SetCursor](#setcursor), qui est associé à `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valeur de retour

Handle du curseur actuel, ou NULL si aucun curseur n’a été défini.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Obtient le handle du métafichier amélioré, précédemment défini avec [SetEnhMetafile](#setenhmetafile), qui est associé à `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Valeur de retour

Handle vers le métafichier amélioré actuel, ou NULL si aucun métafichier amélioré n’a été défini.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>CStatic::GetIcon

Obtient le handle de l’icône, précédemment définie avec [seticon](#seticon), qui est associé à `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valeur de retour

Handle de l’icône actuelle, ou NULL si aucune icône n’a été définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>CStatic::SetBitmap

Associe une nouvelle bitmap au contrôle statique.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap*<br/>
Handle de l’image bitmap à dessiner dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

Handle de la bitmap précédemment associée au contrôle statique, ou NULL si aucune bitmap n’a été associée au contrôle statique.

### <a name="remarks"></a>Notes

L’image bitmap sera automatiquement dessinée dans le contrôle statique. Par défaut, il est dessiné dans l’angle supérieur gauche et le contrôle statique est redimensionné à la taille de l’image bitmap.

Vous pouvez utiliser divers styles de contrôle de fenêtre et statique, y compris les suivants :

- SS_BITMAP Utilisez toujours ce style pour les bitmaps.

- SS_CENTERIMAGE utiliser pour centrer l’image dans le contrôle statique. Si l’image est plus grande que le contrôle statique, elle est découpée. S’il est plus petit que le contrôle statique, l’espace vide autour de l’image sera rempli par la couleur du pixel dans le coin supérieur gauche de la bitmap.

- MFC fournit la classe `CBitmap`, que vous pouvez utiliser lorsque vous devez faire plus avec une image bitmap que d’appeler simplement la fonction Win32 `LoadBitmap`. `CBitmap`, qui contient un type d’objet GDI, est souvent utilisé en collaboration avec `CStatic`, qui est une classe `CWnd` utilisée pour afficher un objet graphique en tant que contrôle statique.

`CImage` est une classe ATL/MFC qui vous permet de travailler plus facilement avec les bitmaps indépendantes des appareils (DIB). Pour plus d’informations, consultez la [classe CImage](../../atl-mfc-shared/reference/cimage-class.md).

- L’utilisation classique consiste à fournir `CStatic::SetBitmap` un objet GDI qui est retourné par l’opérateur HBITMAP d’un objet `CBitmap` ou `CImage`. Le code permettant d’effectuer cette opération ressemble à la ligne suivante.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

L’exemple suivant crée deux objets `CStatic` sur le tas. Il charge ensuite l’un avec une bitmap système à l’aide de `CBitmap::LoadOEMBitmap` et l’autre à partir d’un fichier à l’aide de `CImage::Load`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>CStatic::SetCursor

Associe une nouvelle image de curseur au contrôle statique.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Paramètres

*hCursor*<br/>
Handle du curseur à dessiner dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

Handle du curseur précédemment associé au contrôle statique, ou NULL si aucun curseur n’a été associé au contrôle statique.

### <a name="remarks"></a>Notes

Le curseur est automatiquement dessiné dans le contrôle statique. Par défaut, il est dessiné dans l’angle supérieur gauche et le contrôle statique est redimensionné à la taille du curseur.

Vous pouvez utiliser divers styles de contrôle de fenêtre et statique, notamment les suivants :

- SS_ICON Utilisez toujours ce style pour les curseurs et les icônes.

- SS_CENTERIMAGE utiliser pour centrer dans le contrôle statique. Si l’image est plus grande que le contrôle statique, elle est découpée. S’il est plus petit que le contrôle statique, l’espace vide autour de l’image sera rempli avec la couleur d’arrière-plan du contrôle statique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Associe une nouvelle image de métafichier amélioré au contrôle statique.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Paramètres

*hMetaFile*<br/>
Handle du métafichier amélioré à dessiner dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

Handle du métafichier amélioré précédemment associé au contrôle statique, ou NULL si aucun métafichier amélioré n’a été associé au contrôle statique.

### <a name="remarks"></a>Notes

Le métafichier amélioré est automatiquement dessiné dans le contrôle statique. Le métafichier amélioré est mis à l’échelle pour s’ajuster à la taille du contrôle statique.

Vous pouvez utiliser divers styles de contrôle de fenêtre et statique, notamment les suivants :

- SS_ENHMETAFILE utiliser ce style toujours pour les refichiers améliorés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>CStatic::SetIcon

Associe une nouvelle image icône au contrôle statique.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*hIcon*<br/>
Handle de l’icône à dessiner dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

Handle de l’icône précédemment associée au contrôle statique, ou NULL si aucune icône n’a été associée au contrôle statique.

### <a name="remarks"></a>Notes

L’icône sera automatiquement dessinée dans le contrôle statique. Par défaut, il est dessiné dans l’angle supérieur gauche et le contrôle statique est redimensionné à la taille de l’icône.

Vous pouvez utiliser divers styles de contrôle de fenêtre et statique, notamment les suivants :

- SS_ICON Utilisez toujours ce style pour les curseurs et les icônes.

- SS_CENTERIMAGE utiliser pour centrer dans le contrôle statique. Si l’image est plus grande que le contrôle statique, elle est découpée. S’il est plus petit que le contrôle statique, l’espace vide autour de l’image sera rempli avec la couleur d’arrière-plan du contrôle statique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox, classe](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)
