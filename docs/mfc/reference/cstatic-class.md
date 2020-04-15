---
title: Classe CStatic
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
ms.openlocfilehash: e5c3705c0aa2fd90e73cb54ba5a97c252ed2cf83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371641"
---
# <a name="cstatic-class"></a>Classe CStatic

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
|[CStatic::Créer](#create)|Crée le contrôle statique Windows et `CStatic` le fixe à l’objet.|
|[CStatic::DrawItem](#drawitem)|Remplacer pour dessiner un contrôle statique dessiné par le propriétaire.|
|[CStatic::GetBitmap](#getbitmap)|Récupère la poignée de la bitmap précédemment réglée avec [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Récupère la poignée de l’image curseur précédemment réglée avec [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Récupère la poignée du métaafile amélioré précédemment réglé avec [SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Récupère la poignée de l’icône précédemment définie avec [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Spécifie une bitmap à afficher dans le contrôle statique.|
|[CStatic::SetCursor](#setcursor)|Spécifie une image de curseur à afficher dans le contrôle statique.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Spécifie un métaafile amélioré à afficher dans le contrôle statique.|
|[CStatic::SetIcon](#seticon)|Spécifie une icône à afficher dans le contrôle statique.|

## <a name="remarks"></a>Notes

Un contrôle statique affiche une chaîne de texte, une boîte, un rectangle, une icône, un curseur, une bitmap ou un métaafile amélioré. Il peut être utilisé pour étiqueter, boxer ou séparer d’autres commandes. Un contrôle statique ne prend normalement aucune entrée et ne fournit aucune sortie; cependant, il peut avertir son parent des clics de souris si elle est créée avec SS_NOTIFY style.

Créez un contrôle statique en deux étapes. Tout d’abord, appelez `CStatic` le constructeur pour construire l’objet, puis appelez la `CStatic` fonction membre [Créer](#create) pour créer le contrôle statique et l’attacher à l’objet.

Si vous `CStatic` créez un objet dans une boîte de `CStatic` dialogue (via une ressource de dialogue), l’objet est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous `CStatic` créez un objet à l’intérieur d’une fenêtre, vous devrez peut-être aussi le détruire. Un `CStatic` objet créé sur la pile à l’intérieur d’une fenêtre est automatiquement détruit. Si vous `CStatic` créez l’objet sur le tas en utilisant la **nouvelle** fonction, vous devez appeler **supprimer** sur l’objet pour le détruire lorsque vous en avez fini avec elle.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a>CStatic::Créer

Crée le contrôle statique Windows et `CStatic` le fixe à l’objet.

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
Spécifie le texte à placer dans le contrôle. Si NULL, aucun texte ne sera visible.

*dwStyle (en)*<br/>
Spécifie le style de fenêtre du contrôle statique. Appliquer toute combinaison de styles de [contrôle statiques](../../mfc/reference/styles-used-by-mfc.md#static-styles) au contrôle.

*Rect*<br/>
Spécifie la position et la taille du contrôle statique. Il peut s’agir `RECT` `CRect` d’une structure ou d’un objet.

*pParentWnd*<br/>
Spécifie la `CStatic` fenêtre `CDialog` parente, généralement un objet. Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle du contrôle statique.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Construire `CStatic` un objet en deux étapes. Tout d’abord, `CStatic`appelez le `Create`constructeur, puis appelez , ce qui `CStatic` crée le contrôle statique Windows et le fixe à l’objet.

Appliquer les styles de [fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle statique :

- WS_CHILD toujours

- WS_VISIBLE Habituellement

- WS_DISABLED Rarement

Si vous devez afficher une bitmap, curseur, icône ou metafile dans le contrôle statique, vous devrez appliquer l’un des [styles statiques](../../mfc/reference/styles-used-by-mfc.md#static-styles)suivants :

- SS_BITMAP Utilisez ce style pour les bitmaps.

- SS_ICON Utilisez ce style pour les curseurs et les icônes.

- SS_ENHMETAFILE Utilisez ce style pour des métafiles améliorées.

Pour les curseurs, les bitmaps ou les icônes, vous pouvez également utiliser le style suivant :

- SS_CENTERIMAGE Utiliser pour centrer l’image dans le contrôle statique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a>CStatic::CStatic

Construit un objet `CStatic`.

```
CStatic();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a>CStatic::DrawItem

Appelé par le cadre pour dessiner un contrôle statique dessiné par le propriétaire.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur vers une structure [DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct) La structure contient des informations sur l’élément à dessiner et le type de dessin requis.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour implémenter `CStatic` le dessin d’un objet dessiné par le propriétaire (le contrôle a le style SS_OWNERDRAW).

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a>CStatic::GetBitmap

Obtient la poignée de la bitmap, précédemment réglé avec `CStatic` [SetBitmap](#setbitmap), qui est associé à .

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée à la bitmap actuelle, ou NULL si aucune bitmap n’a été réglée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a>CStatic::GetCursor

Obtient la poignée du curseur, précédemment réglé avec [SetCursor](#setcursor), qui est associé `CStatic`à .

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valeur de retour

Une poignée au curseur actuel, ou NULL si aucun curseur n’a été réglé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Obtient la poignée du metafile amélioré, précédemment réglé avec [SetEnhMetafile](#setenhmetafile), qui est associé `CStatic`à .

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée au métaafile amélioré actuel, ou NULL si aucun metafile amélioré n’a été défini.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a>CStatic::GetIcon

Obtient la poignée de l’icône, précédemment réglé avec `CStatic` [SetIcon](#seticon), qui est associé à .

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée à l’icône actuelle, ou NULL si aucune icône n’a été définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a>CStatic::SetBitmap

Associe une nouvelle bitmap au contrôle statique.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Paramètres

*hBitmap (en)*<br/>
Poignée de la bitmap à tirer dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

La poignée de la bitmap qui était auparavant associée au contrôle statique, ou NULL si aucune bitmap n’était associée au contrôle statique.

### <a name="remarks"></a>Notes

La bitmap sera automatiquement dessinée dans le contrôle statique. Par défaut, il sera dessiné dans le coin supérieur gauche et le contrôle statique sera redimensionné à la taille de la bitmap.

Vous pouvez utiliser différents styles de fenêtre et de contrôle statique, y compris ceux-ci:

- SS_BITMAP Utilisez ce style toujours pour les bitmaps.

- SS_CENTERIMAGE Utiliser pour centrer l’image dans le contrôle statique. Si l’image est plus grande que le contrôle statique, elle sera coupée. S’il est plus petit que le contrôle statique, l’espace vide autour de l’image sera rempli par la couleur du pixel dans le coin supérieur gauche de la bitmap.

- MFC fournit `CBitmap`la classe , que vous pouvez utiliser lorsque vous avez à faire plus `LoadBitmap`avec une image bitmap que d’appeler simplement la fonction Win32 . `CBitmap`, qui contient un type d’objet GDI, est souvent utilisé en coopération avec `CStatic`, qui est une `CWnd` classe qui est utilisé pour afficher un objet graphique comme un contrôle statique.

`CImage`est une classe ATL/MFC qui vous permet de travailler plus facilement avec des bitmaps indépendants (DIB). Pour plus d’informations, voir [CImage Class](../../atl-mfc-shared/reference/cimage-class.md).

- L’utilisation typique `CStatic::SetBitmap` est de donner un objet GDI qui `CBitmap` est `CImage` retourné par l’opérateur HBITMAP d’un ou d’un objet. Le code pour ce faire ressemble à la ligne suivante.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

L’exemple suivant `CStatic` crée deux objets sur le tas. Il charge ensuite l’un avec `CBitmap::LoadOEMBitmap` un bitmap système `CImage::Load`en utilisant et l’autre à partir d’un fichier en utilisant .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a>CStatic::SetCursor

Associe une nouvelle image de curseur au contrôle statique.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Paramètres

*hCursor*<br/>
Poignée du curseur à tirer dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

La poignée du curseur précédemment associée au contrôle statique, ou NULL si aucun curseur n’était associé au contrôle statique.

### <a name="remarks"></a>Notes

Le curseur sera automatiquement tiré dans le contrôle statique. Par défaut, il sera dessiné dans le coin supérieur gauche et le contrôle statique sera redimensionné à la taille du curseur.

Vous pouvez utiliser différents styles de contrôle de fenêtre et statiques, y compris les suivants :

- SS_ICON Utilisez ce style toujours pour les curseurs et les icônes.

- SS_CENTERIMAGE Utiliser pour centrer dans le contrôle statique. Si l’image est plus grande que le contrôle statique, elle sera coupée. S’il est plus petit que le contrôle statique, l’espace vide autour de l’image sera rempli de la couleur de fond du contrôle statique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Associe une nouvelle image métadique améliorée avec le contrôle statique.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Paramètres

*hMetaFile (en)*<br/>
Poignée du metafile amélioré à tirer dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

La poignée du metafile amélioré précédemment associé au contrôle statique, ou NULL si aucun metafile amélioré n’était associé au contrôle statique.

### <a name="remarks"></a>Notes

Le métaafile amélioré sera automatiquement dessiné dans le contrôle statique. Le métafaisile amélioré est mis à l’échelle pour s’adapter à la taille du contrôle statique.

Vous pouvez utiliser différents styles de contrôle de fenêtre et statiques, y compris les suivants :

- SS_ENHMETAFILE Utilisez ce style toujours pour des métafiles améliorées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a>CStatic::SetIcon

Associe une nouvelle image d’icône au contrôle statique.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*hIcon (en)*<br/>
Poignée de l’icône à dessiner dans le contrôle statique.

### <a name="return-value"></a>Valeur de retour

La poignée de l’icône précédemment associée au contrôle statique, ou NULL si aucune icône n’était associée au contrôle statique.

### <a name="remarks"></a>Notes

L’icône sera automatiquement dessinée dans le contrôle statique. Par défaut, il sera dessiné dans le coin supérieur gauche et le contrôle statique sera redimensionné à la taille de l’icône.

Vous pouvez utiliser différents styles de contrôle de fenêtre et statiques, y compris les suivants :

- SS_ICON Utilisez ce style toujours pour les curseurs et les icônes.

- SS_CENTERIMAGE Utiliser pour centrer dans le contrôle statique. Si l’image est plus grande que le contrôle statique, elle sera coupée. S’il est plus petit que le contrôle statique, l’espace vide autour de l’image sera rempli de la couleur de fond du contrôle statique.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Classe CButton](../../mfc/reference/cbutton-class.md)<br/>
[Classe CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar, classe](../../mfc/reference/cscrollbar-class.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)
