---
title: CImageList, classe
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: eff2d0c1de88ebd9d949ebe197563c87c17e5b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372450"
---
# <a name="cimagelist-class"></a>CImageList, classe

Fournit les fonctionnalités du contrôle commun de liste d'images Windows.

## <a name="syntax"></a>Syntaxe

```
class CImageList : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|Construit un objet `CImageList`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CImageList::Ajouter](#add)|Ajoute une image ou des images à une liste d’images.|
|[CImageList::Attach](#attach)|Attache une liste d’images à un `CImageList` objet.|
|[CImageList::BeginDrag](#begindrag)|Commence à glisser une image.|
|[CImageList::Copie](#copy)|Copie d’une `CImageList` image à l’intérieur d’un objet.|
|[CImageList::Créer](#create)|Initialise une liste d’images et `CImageList` la fixe à un objet.|
|[CImageList::DeleteImageList](#deleteimagelist)|Supprime une liste d’images.|
|[CImageList::DeleteTempMap](#deletetempmap)|Appelé par le gestionnaire [CWinApp](../../mfc/reference/cwinapp-class.md) temps `CImageList` inactiv `FromHandle`pour supprimer tout objet temporaire créé par .|
|[CImageList::Detach](#detach)|Détache un objet de liste `CImageList` d’images d’un objet et renvoie une poignée à une liste d’images.|
|[CImageList::DragEnter](#dragenter)|Verrouille les mises à jour pendant une opération de traînée et affiche l’image de traînée à une position spécifiée.|
|[CImageList::DragLeave](#dragleave)|Déverrouiller la fenêtre et cache l’image de traînée afin que la fenêtre puisse être mise à jour.|
|[CImageList::DragMove](#dragmove)|Déplace l’image qui est traîné au cours d’une opération de drag-and-drop.|
|[CImageList::DragShowNolock](#dragshownolock)|Affiche ou cache l’image de traînée lors d’une opération de traînée, sans verrouiller la fenêtre.|
|[CImageList::Draw](#draw)|Dessine l’image qui est traîné au cours d’une opération de drag-and-drop.|
|[CImageList::DrawEx](#drawex)|Dessine un élément de liste d’images dans le contexte de l’appareil spécifié. La fonction utilise le style de dessin spécifié et mélange l’image avec la couleur spécifiée.|
|[CImageList::DrawIndirect](#drawindirect)|Dessine une image à partir d’une liste d’images.|
|[CImageList::EndDrag](#enddrag)|Fin de l’opération de traînée.|
|[CImageList::ExtractIcon](#extracticon)|Crée une icône basée sur une image et un masque dans une liste d’images.|
|[CImageList::DeHandle](#fromhandle)|Renvoie un `CImageList` pointeur à un objet lorsqu’on lui donne une poignée sur une liste d’images. Si aucun objet `CImageList` n'est attaché au handle, un objet `CImageList` temporaire est créé et attaché.|
|[CImageList::DeHandlePermanent](#fromhandlepermanent)|Renvoie un `CImageList` pointeur à un objet lorsqu’on lui donne une poignée sur une liste d’images. Si `CImageList` un objet n’est pas attaché à la poignée, NULL est retourné.|
|[CImageList::GetBkColor](#getbkcolor)|Récupère la couleur de fond actuelle pour une liste d’images.|
|[CImageList::GetDragImage](#getdragimage)|Obtient la liste d’images temporaire qui est utilisée pour le dragage.|
|[CImageList::GetImageCount](#getimagecount)|Récupère le nombre d’images dans une liste d’images.|
|[CImageList::GetImageInfo](#getimageinfo)|Récupère des informations sur une image.|
|[CImageList::GetSafeHandle](#getsafehandle)|Récupère `m_hImageList`.|
|[CImageList::Lire](#read)|Lit une liste d’images à partir d’une archive.|
|[CImageList::Supprimer](#remove)|Supprime une image d’une liste d’images.|
|[CImageList::Remplacer](#replace)|Remplace une image dans une liste d’images par une nouvelle image.|
|[CImageList::SetBkColor](#setbkcolor)|Définit la couleur de fond pour une liste d’images.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Crée une nouvelle image de drag.|
|[CImageList::SetImageCount](#setimagecount)|Réinitialise le nombre d’images dans une liste d’images.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Ajoute l’index zéro d’une image à la liste des images à utiliser comme masques de superposition.|
|[CImageList::Écrire](#write)|Rédige une liste d’images à une archive.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CImageList::opérateur HIMAGELIST](#operator_himagelist)|Retourne le HIMAGELIST `CImageList`attaché à la .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Une poignée contenant la liste d’images attachée à cet objet.|

## <a name="remarks"></a>Notes

Une « liste d’images » est une collection d’images de même taille, dont chacune peut être mentionnée par son index zéro. Les listes d’images sont utilisées pour gérer efficacement de grands ensembles d’icônes ou de bitmaps. Toutes les images d’une liste d’images sont contenues dans un seul bitmap large en format d’appareil d’écran. Une liste d’images peut également inclure une bitmap monochrome qui contient des masques utilisés pour dessiner des images de manière transparente (style icône). L’interface de programmation d’applications Microsoft Win32 (API) fournit des fonctions de liste d’images qui vous permettent de dessiner des images, de créer et de détruire des listes d’images, d’ajouter et de supprimer des images, de remplacer des images, de fusionner des images et de faire glisser des images.

Ce contrôle (et `CImageList` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT version 3.51 et plus tard.

Pour plus d’informations sur l’utilisation `CImageList`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation de [CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a>CImageList::Ajouter

Appelez cette fonction pour ajouter une ou plusieurs images ou une icône à une liste d’images.

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*pbmImage*<br/>
Pointeur sur la bitmap contenant l’image ou les images. Le nombre d’images est déduit de la largeur de la bitmap.

*pbmMask*<br/>
Pointeur sur la bitmap contenant le masque. Si aucun masque n’est utilisé avec la liste d’images, ce paramètre est ignoré.

*crMask*<br/>
Couleur utilisée pour générer le masque. Chaque pixel de cette couleur dans la bitmap donnée est changé en noir et le bit correspondant dans le masque est réglé à un.

*hIcon (en)*<br/>
Poignée de l’icône qui contient la bitmap et le masque pour la nouvelle image.

### <a name="return-value"></a>Valeur de retour

Indice zéro de la première nouvelle image en cas de succès; autrement - 1.

### <a name="remarks"></a>Notes

Vous êtes responsable de la libération de la poignée d’icône lorsque vous en avez fini avec elle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a>CImageList::Attach

Appelez cette fonction pour joindre `CImageList` une liste d’images à un objet.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Une poignée à un objet de liste d’images.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’attachement a été réussi; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a>CImageList::BeginDrag

Appelez cette fonction pour commencer à glisser une image.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Paramètres

*nImage (en)*<br/>
Index zéro de l’image à glisser.

*ptHotSpot*<br/>
Coordonnées de la position de traînée de départ (généralement, la position du curseur). Les coordonnées sont relatives au coin supérieur gauche de l’image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction crée une liste d’images temporaire qui est utilisée pour le dragage. L’image combine l’image spécifiée et son masque avec le curseur actuel. En réponse aux messages WM_MOUSEMOVE suivants, vous pouvez déplacer `DragMove` l’image de drague en utilisant la fonction membre. Pour mettre fin à l’opération de traînée, vous pouvez utiliser la `EndDrag` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList::CImageList

Construit un objet `CImageList`.

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a>CImageList::Copie

Cette fonction membre implémente le comportement de la fonction Win32 [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy), tel que décrit dans le SDK Windows.

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>Paramètres

*iDst (en)*<br/>
L’index zéro de l’image à utiliser comme destination de l’opération de copie.

*iSrc (en)*<br/>
L’index zéro de l’image à utiliser comme source de l’opération de copie.

*uFlags*<br/>
La valeur du drapeau bit qui spécifie le type d’opération de copie à faire. Ce paramètre peut être l’une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|ILCF_MOVE|L’image source est copiée à l’index de l’image de destination. Cette opération se traduit par de multiples cas d’une image donnée. ILCF_MOVE est la valeur par défaut.|
|ILCF_SWAP|Les images source et destination échangent des positions dans la liste d’images.|

*pSrc (en)*<br/>
Un pointeur `CImageList` à un objet qui est la cible de l’opération de copie.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a>CImageList::Créer

Initialise une liste d’images et la fixe à un objet [CImageList.](../../mfc/reference/cimagelist-class.md)

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>Paramètres

*Cx*<br/>
Dimensions de chaque image, en pixels.

*Cy*<br/>
Dimensions de chaque image, en pixels.

*nFlags*<br/>
Spécifie le type de liste d’images à créer. Ce paramètre peut être une combinaison des valeurs suivantes, `ILC_COLOR` mais il ne peut inclure qu’une seule des valeurs.

|Value|Signification|
|-----------|-------------|
|ILC_COLOR|Utilisez le comportement par défaut si aucun des autres ILC_COLOR sont spécifiés. Typiquement, la valeur par défaut est ILC_COLOR4; mais pour les conducteurs d’affichage plus anciens, la valeur par défaut est ILC_COLORDDB.|
|ILC_COLOR4|Utilisez une section de bits (16 couleurs) de bits (DIB) comme bitmap pour la liste d’images.|
|ILC_COLOR8|Utilisez une section DIB 8 bits. Les couleurs utilisées pour la table de couleur sont les mêmes couleurs que la palette de demi-teinte.|
|ILC_COLOR16|Utilisez une section DIB 16 bits (32/64k).|
|ILC_COLOR24|Utilisez une section DIB 24 bits.|
|ILC_COLOR32|Utilisez une section DIB 32 bits.|
|ILC_COLORDDB|Utilisez une bitmap dépendante de l’appareil.|
|ILC_MASK|Utilise un masque. La liste d’images contient deux bitmaps, dont l’un est un bitmap monochrome utilisé comme masque. Si cette valeur n’est pas incluse, la liste d’images ne contient qu’une seule bitmap. Voir [les images de dessin d’une liste d’images](../../mfc/drawing-images-from-an-image-list.md) pour plus d’informations sur les images masquées.|

*nInitial*<br/>
Nombre d’images que la liste d’images contient initialement.

*nGrow (nGrow)*<br/>
Nombre d’images par lesquelles la liste d’images peut augmenter lorsque le système a besoin de resize la liste pour faire place à de nouvelles images. Ce paramètre représente le nombre de nouvelles images que la liste d’images resized peut contenir.

*nBitmapID (en)*<br/>
Les Œd de ressources de la bitmap pour être associés à la liste d’images.

*crMask*<br/>
Couleur utilisée pour générer un masque. Chaque pixel de cette couleur dans le bitmap spécifié est changé en noir, et le bit correspondant dans le masque est réglé à un.

*lpszBitmapID*<br/>
Une chaîne contenant les Œd de ressources des images.

*liste d’images1*<br/>
Référence à un objet `CImageList`.

*nImage1*<br/>
Index de la première image existante.

*liste d’images2*<br/>
Référence à un objet `CImageList`.

*nImage2*<br/>
Index de la deuxième image existante.

*Dx*<br/>
Décalage de l’axe x de la deuxième image par rapport à la première image, en pixels.

*Dy*<br/>
Décalage de l’axe y de la deuxième image par rapport à la première image, en pixels.

*pImageList (en)*<br/>
Pointeur vers un objet `CImageList`.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CImageList` en deux étapes. Tout d’abord, appelez `Create`le constructeur, puis appelez , ce `CImageList` qui crée la liste d’images et l’attache à l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList::DeleteImageList

Appelez cette fonction pour supprimer une liste d’images.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList::DeleteTempMap

Appelé automatiquement `CWinApp` par le gestionnaire `DeleteTempMap` de temps `CImageList` d’arrêt, supprime tous les objets temporaires créés `ImageList` par [FromHandle](#fromhandle), mais ne détruit pas les poignées ( `hImageList`) temporairement associées aux objets.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a>CImageList::Detach

Appelez cette fonction pour détacher un `CImageList` objet de liste d’images d’un objet.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Valeur de retour

Une poignée à un objet de liste d’images.

### <a name="remarks"></a>Notes

Cette fonction renvoie une poignée à l’objet de liste d’images.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CImageList:Attach](#attach).

## <a name="cimagelistdragenter"></a><a name="dragenter"></a>CImageList::DragEnter

Au cours d’une opération de traînée, verrouille les mises à jour de la fenêtre spécifiée par *pWndLock* et affiche l’image de traînée à la position spécifiée par *point*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWndLock*<br/>
Pointeur vers la fenêtre qui possède l’image de traînée.

*Point*<br/>
Position à laquelle afficher l’image de traînée. Les coordonnées sont relatives au coin supérieur gauche de la fenêtre (et non à la zone client).

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les coordonnées sont relatives au coin supérieur gauche de la fenêtre, de sorte que vous devez compenser les largeurs des éléments de fenêtre, tels que la bordure, la barre de titre, et la barre de menu, lors de la spécifier les coordonnées.

Si *pWndLock* est NULL, cette fonction dessine l’image dans le contexte d’affichage associé à la fenêtre de bureau, et les coordonnées sont relatives au coin supérieur gauche de l’écran.

Cette fonction verrouille toutes les autres mises à jour de la fenêtre donnée pendant le fonctionnement de la traînée. Si vous avez besoin de faire n’importe quel dessin au cours d’une opération de traînée, comme mettre en évidence la cible d’une opération de drag-and-drop, vous pouvez temporairement cacher l’image traînée en utilisant la fonction [CImageList::DragLeave.](#dragleave)

### <a name="example"></a>Exemple

  Voir l’exemple pour [CImageList:BeginDrag](#begindrag).

## <a name="cimagelistdragleave"></a><a name="dragleave"></a>CImageList::DragLeave

Déverrouille la fenêtre spécifiée par *pWndLock* et cache l’image de traînée, permettant de mettre à jour la fenêtre.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Paramètres

*pWndLock*<br/>
Pointeur vers la fenêtre qui possède l’image de traînée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CImageList:EndDrag](#enddrag).

## <a name="cimagelistdragmove"></a><a name="dragmove"></a>CImageList::DragMove

Appelez cette fonction pour déplacer l’image qui est traîné au cours d’une opération de drag-and-drop.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Nouvelle position de traînée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée en réponse à un message WM_MOUSEMOVE. Pour commencer une opération `BeginDrag` de traînée, utilisez la fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList::DragShowNolock

Affiche ou cache l’image de traînée lors d’une opération de traînée, sans verrouiller la fenêtre.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
Précise si l’image de traînée doit être montrée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fonction [CImageList::DragEnter](#dragenter) verrouille toutes les mises à jour de la fenêtre lors d’une opération de traînée. Cette fonction, cependant, ne verrouille pas la fenêtre.

## <a name="cimagelistdraw"></a><a name="draw"></a>CImageList::Draw

Appelez cette fonction pour dessiner l’image qui est traîné au cours d’une opération de drag-and-drop.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte de l’appareil de destination.

*nImage (en)*<br/>
Indice zéro de l’image à dessiner.

*Pt*<br/>
Emplacement à partir duquel dessiner dans le contexte de l’appareil spécifié.

*nStyle*<br/>
Drapeau spécifiant le style de dessin. Il peut s’agir d’une ou de plusieurs de ces valeurs :

|Value|Signification|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Dessine l’image, mélangeant 25 pour cent avec le système mettre en évidence la couleur. Cette valeur n’a aucun effet si la liste d’images ne contient pas de masque.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Dessine l’image, mélangeant 50 pour cent avec le système mettre en évidence la couleur. Cette valeur n’a aucun effet si la liste d’images ne contient pas de masque.|
|ILD_MASK|Dessine le masque.|
|ILD_NORMAL|Dessine l’image en utilisant la couleur de fond pour la liste d’images. Si la couleur de fond est la valeur CLR_NONE, l’image est dessinée de manière transparente à l’aide du masque.|
|ILD_TRANSPARENT|Dessine l’image de façon transparente à l’aide du masque, quelle que soit la couleur de fond.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CImageList:SetOverlayImage](#setoverlayimage).

## <a name="cimagelistdrawex"></a><a name="drawex"></a>CImageList::DrawEx

Dessine un élément de liste d’images dans le contexte de l’appareil spécifié.

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte de l’appareil de destination.

*nImage (en)*<br/>
Indice zéro de l’image à dessiner.

*Pt*<br/>
Emplacement à partir duquel dessiner dans le contexte de l’appareil spécifié.

*Sz*<br/>
Taille de la partie de l’image à dessiner par rapport au coin supérieur gauche de l’image. Voir *dx et* *dy* dans [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) dans le Windows SDK.

*clrBk*<br/>
Couleur de fond de l’image. Voir *rgbBk* dans [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) dans le Windows SDK.

*clrFg*<br/>
Couleur de premier plan de l’image. Voir *rgbFg* dans [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) dans le Windows SDK.

*nStyle*<br/>
Drapeau spécifiant le style de dessin. Voir *fStyle* dans [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fonction utilise le style de dessin spécifié et mélange l’image avec la couleur spécifiée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList::DrawIndirect

Appelez cette fonction de membre pour dessiner une image à partir d’une liste d’images.

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>Paramètres

*pimldp pimldp*<br/>
Un pointeur à une structure [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) qui contient des informations sur l’opération de tirage.

*pDC*<br/>
Un pointeur vers le contexte de l’appareil de destination. Vous devez supprimer cet objet [CDC](../../mfc/reference/cdc-class.md) lorsque vous en avez fini avec lui.

*nImage (en)*<br/>
L’index zéro de l’image à dessiner.

*Pt*<br/>
Une structure [POINT](/previous-versions/dd162805\(v=vs.85\)) contenant les coordonnées x et y où l’image sera dessinée.

*Sz*<br/>
Une structure [SIZE](/windows/win32/api/windef/ns-windef-size) indiquant la taille de l’image à dessiner.

*ptOrigin*<br/>
Une structure [POINT](/previous-versions/dd162805\(v=vs.85\)) contenant les coordonnées x et y spécifiant le coin supérieur gauche de l’opération de dessin par rapport à l’image elle-même. Les pixels de l’image qui sont à gauche de la x-coordonner et au-dessus de la y-coordinate ne sont pas dessinés.

*fStyle (en)*<br/>
Drapeau spécifiant le style de dessin et, en option, l’image de superposition. Voir la section Remarques pour plus d’informations sur l’image de superposition. L’implémentation par défaut MFC, ILD_NORMAL, dessine l’image en utilisant la couleur de fond pour la liste d’images. Si la couleur de fond est la valeur CLR_NONE, l’image est dessinée de manière transparente à l’aide d’un masque.

D’autres styles possibles sont décrits sous le membre *fStyle* de la structure [IMAGELISTDRAWPARAMS.](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)

*dwRop*<br/>
Valeur spécifiant un code d’opération raster. Ces codes définissent comment les données de couleur pour le rectangle source seront combinés avec les données de couleur pour le rectangle de destination pour atteindre la couleur finale. L’implémentation par défaut de MFC, SRCCOPY, copie le rectangle source directement au rectangle de destination. Ce paramètre est ignoré si le *paramètre fStyle* n’inclut pas le drapeau ILD_ROP.

D’autres valeurs possibles sont décrites sous le membre *dwRop* de la structure [IMAGELISTDRAWPARAMS.](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)

*rgbBack (rgbBack)*<br/>
La couleur de fond d’image, par défaut CLR_DEFAULT. Ce paramètre peut être une valeur RGB définie par l’application ou l’une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|CLR_DEFAULT|Couleur de fond par défaut. L’image est dessinée à l’aide de la couleur de fond de la liste d’images.|
|CLR_NONE|Pas de couleur de fond. L’image est dessinée de manière transparente.|

*rgbFore (en)*<br/>
Couleur de premier plan d’image, par défaut CLR_DEFAULT. Ce paramètre peut être une valeur RGB définie par l’application ou l’une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|CLR_DEFAULT|Couleur de premier plan par défaut. L’image est dessinée à l’aide du système mettre en évidence la couleur comme la couleur du premier plan.|
|CLR_NONE|Pas de couleur de mélange. L’image est mélangée avec la couleur du contexte de l’appareil de destination.|

Ce paramètre n’est utilisé que si *fStyle* inclut le drapeau ILD_BLEND25 ou ILD_BLEND50.

*fState (États-Unis)*<br/>
Drapeau spécifiant l’état de dessin. Ce membre peut contenir un ou plusieurs drapeaux d’état de liste d’images.

*Cadre*<br/>
Affecte le comportement des effets saturants et alpha-mélange.

Lorsqu’il est utilisé avec ILS_SATURATE, ce membre détient la valeur qui est ajoutée à chaque composant couleur du triplet RGB pour chaque pixel de l’icône.

Lorsqu’il est utilisé avec ILS_APLHA, ce membre détient la valeur pour le canal alpha. Cette valeur peut être de 0 à 255, avec 0 étant complètement transparent, et 255 étant complètement opaque.

*crEffect (en)*<br/>
Une valeur [COLORREF](/windows/win32/gdi/colorref) utilisée pour les effets de lueur et d’ombre.

### <a name="return-value"></a>Valeur de retour

VRAI si l’image est dessinée avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Utilisez la première version si vous souhaitez remplir la structure Win32 vous-même. Utilisez la deuxième version si vous souhaitez profiter d’un ou plusieurs arguments par défaut de MFC, ou évitez de gérer la structure.

Une image superposée est une image qui est dessinée au-dessus de l’image principale, spécifiée dans cette fonction de membre par le paramètre *nImage.* Dessinez un masque de superposition en utilisant la fonction [membre Draw](#draw) avec l’index unique du masque de superposition spécifié à l’aide de la macro [INDEXTOOVERLAYMASK.](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a>CImageList::EndDrag

Appelez cette fonction pour mettre fin à une opération de traînée.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Notes

Pour commencer une opération `BeginDrag` de traînée, utilisez la fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a>CImageList::ExtractIcon

Appelez cette fonction pour créer une icône basée sur une image et son masque connexe dans une liste d’images.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Paramètres

*nImage (en)*<br/>
Indice zéro de l’image.

### <a name="return-value"></a>Valeur de retour

Poignée de l’icône en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Cette méthode s’appuie sur le comportement de la [macro ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) pour créer l’icône. Reportez-vous à la macro [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) pour plus d’informations sur la création et le nettoyage des icônes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList::DeHandle

Renvoie un `CImageList` pointeur à un objet lorsqu’on lui donne une poignée sur une liste d’images.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Spécifie la liste d’images.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CImageList` à un objet en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si `CImageList` un n’est pas déjà `CImageList` attaché à la poignée, un objet temporaire est créé et attaché. Cet `CImageList` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, date à laquelle tous les objets temporaires sont supprimés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList::DeHandlePermanent

Renvoie un `CImageList` pointeur à un objet lorsqu’on lui donne une poignée sur une liste d’images.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Spécifie la liste d’images.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CImageList` à un objet en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si `CImageList` un objet n’est pas attaché à la poignée, NULL est retourné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList::GetBkColor

Appelez cette fonction pour récupérer la couleur de fond actuelle pour une liste d’images.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de couleur `CImageList` RGB de la couleur de fond d’objet.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CImageList:SetBkColor](#setbkcolor).

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a>CImageList::GetDragImage

Obtient la liste d’images temporaire qui est utilisée pour le dragage.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Paramètres

*lpPoint (en)*<br/>
Adresse d’une structure [POINT](/previous-versions/dd162805\(v=vs.85\)) qui reçoit la position de traînée actuelle.

*lpPointHotSpot*<br/>
Adresse d’une `POINT` structure qui reçoit le décalage de l’image de traînée par rapport à la position de traînée.

### <a name="return-value"></a>Valeur de retour

En cas de succès, un pointeur à la liste d’images temporaire qui est utilisé pour le dragage; autrement, NULL.

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a>CImageList::GetImageCount

Appelez cette fonction pour récupérer le nombre d’images dans une liste d’images.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’images.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CImageList:ExtractIcon](#extracticon).

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a>CImageList::GetImageInfo

Appelez cette fonction pour récupérer des informations sur une image.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Paramètres

*nImage (en)*<br/>
Indice zéro de l’image.

*pImageInfo*<br/>
Pointeur vers une structure [IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo) qui reçoit des informations sur l’image. Les informations contenues dans cette structure peuvent être utilisées pour manipuler directement les bitmaps pour l’image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La `IMAGEINFO` structure contient des informations sur une image dans une liste d’images.

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList::GetSafeHandle

Appelez cette fonction `m_hImageList` pour récupérer le membre de données.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée à la liste d’images ci-jointe; autrement NULL si aucun objet n’est attaché.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a>CImageList::m_hImageList

Une poignée de la liste d’images attachée à cet objet.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Notes

Le `m_hImageList` membre des données est une variable publique de type HIMAGELIST.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList::opérateur HIMAGELIST

Utilisez cet opérateur pour obtenir `CImageList` la poignée attachée de l’objet.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, une poignée `CImageList` à la liste d’images représentée par l’objet; autrement NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de coulée, qui prend en charge l’utilisation directe d’un objet HIMAGELIST.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a>CImageList::Lire

Appelez cette fonction pour lire une liste d’images à partir d’une archive.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Paramètres

*Parchive*<br/>
Un pointeur `CArchive` à un objet à partir duquel la liste d’images doit être lue.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a>CImageList::Supprimer

Appelez cette fonction pour supprimer une image d’un objet de liste d’images.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Paramètres

*nImage (en)*<br/>
Index zéro de l’image à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Tous les éléments suivant *nImage* se déplacent maintenant vers le bas d’une position. Par exemple, si une liste d’images contient deux éléments, la suppression du premier élément entraînera l’élément restant d’être maintenant dans la première position. *nImage*0 pour l’élément en première position.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a>CImageList::Remplacer

Appelez cette fonction pour remplacer une image dans une liste d’images par une nouvelle image.

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*nImage (en)*<br/>
Index zéro de l’image à remplacer.

*pbmImage*<br/>
Un pointeur à la bitmap contenant l’image.

*pbmMask*<br/>
Un pointeur à la bitmap contenant le masque. Si aucun masque n’est utilisé avec la liste d’images, ce paramètre est ignoré.

*hIcon (en)*<br/>
Une poignée à l’icône qui contient la bitmap et le masque pour la nouvelle image.

### <a name="return-value"></a>Valeur de retour

La version de retour BOOL retourne nonzero si réussi; sinon 0.

La version de retour **int** retourne l’index zéro de l’image en cas de succès; autrement - 1.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre après avoir appelé [SetImageCount](#setimagecount) pour attribuer les nouvelles images valides aux numéros d’index d’image de placeholder.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CImageList:SetImageCount](#setimagecount).

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList::SetBkColor

Appelez cette fonction pour définir la couleur de fond pour une liste d’images.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Paramètres

*Cr*<br/>
Couleur de fond à définir. Il peut être CLR_NONE. Dans ce cas, les images sont dessinées de manière transparente à l’aide du masque.

### <a name="return-value"></a>Valeur de retour

La couleur de fond précédente en cas de succès; sinon CLR_NONE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList::SetDragCursorImage

Crée une nouvelle image de drag en combinant l’image donnée (généralement une image curseur de souris) avec l’image de traînée actuelle.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Paramètres

*nDrag (en)*<br/>
Index de la nouvelle image à combiner avec l’image de traînée.

*ptHotSpot*<br/>
Position du point chaud dans la nouvelle image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Parce que les fonctions de dragage utilisent la nouvelle image lors d’une opération de traînée, vous devez utiliser la fonction Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) pour cacher le curseur de souris réelle après avoir appelé `CImageList::SetDragCursorImage`. Sinon, le système peut sembler être composé de deux curseurs de souris pour la durée de l'opération Glisser-déplacer.

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a>CImageList::SetImageCount

Appelez cette fonction de membre pour `CImageList` réinitialiser le nombre d’images dans un objet.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Paramètres

*uNewCompe*<br/>
La valeur spécifiant le nouveau nombre total d’images dans la liste d’images.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Si vous appelez cette fonction de membre pour augmenter le nombre d’images dans la liste d’images, appelez [Remplacer](#replace) chaque image supplémentaire pour attribuer les nouveaux index aux images valides. Si vous ne parvenez pas à attribuer les index à des images valides, les opérations de dessin qui créent les nouvelles images seront imprévisibles.

Si vous diminuez la taille d’une liste d’images en utilisant cette fonction, les images tronquées sont libérées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>CImageList::SetOverlayImage

Appelez cette fonction pour ajouter l’index zéro d’une image à la liste des images à utiliser comme masques de superposition.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Paramètres

*nImage (en)*<br/>
Index zéro de l’image à utiliser comme masque de superposition.

*nOverlay (en)*<br/>
Indice unique du masque de superposition.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Jusqu’à quatre indices peuvent être ajoutés à la liste.

Un masque de superposition est une image dessinée de façon transparente sur une autre image. Dessinez un masque de superposition sur une image en utilisant la fonction [membre CImageList::Draw](#draw) avec l’index unique du masque de superposition spécifié à l’aide de la macro INDEXTOOVERLAYMASK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a>CImageList::Écrire

Appelez cette fonction pour écrire un objet de liste d’images à une archive.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Paramètres

*Parchive*<br/>
Un pointeur `CArchive` d’un objet dans lequel la liste d’images doit être stockée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl, classe](../../mfc/reference/ctabctrl-class.md)
