---
title: CImageList (classe)
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
ms.openlocfilehash: 28693aaa32ab5f4baaf773a7bac64c491d55cf78
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212395"
---
# <a name="cimagelist-class"></a>CImageList (classe)

Fournit les fonctionnalités du contrôle commun de liste d'images Windows.

## <a name="syntax"></a>Syntaxe

```
class CImageList : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CImageList :: CImageList](#cimagelist)|Construit un objet `CImageList`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CImageList :: Add](#add)|Ajoute une image ou des images à une liste d’images.|
|[CImageList :: Attach](#attach)|Joint une liste d’images à un `CImageList` objet.|
|[CImageList :: BeginDrag](#begindrag)|Commence à faire glisser une image.|
|[CImageList :: Copy](#copy)|Copie une image dans un `CImageList` objet.|
|[CImageList :: Create](#create)|Initialise une liste d’images et l’attache à un `CImageList` objet.|
|[CImageList ::D eleteImageList](#deleteimagelist)|Supprime une liste d’images.|
|[CImageList ::D eleteTempMap](#deletetempmap)|Appelée par le gestionnaire de temps d’inactivité [CWinApp](../../mfc/reference/cwinapp-class.md) pour supprimer tout `CImageList` objet temporaire créé par `FromHandle` .|
|[CImageList ::D Etach](#detach)|Détache un objet de liste d’images d’un `CImageList` objet et retourne un handle vers une liste d’images.|
|[CImageList ::D ragEnter](#dragenter)|Verrouille les mises à jour pendant une opération glisser-déplacer et affiche l’image de glissement à la position spécifiée.|
|[CImageList ::D ragLeave](#dragleave)|Déverrouille la fenêtre et masque l’image de glissement pour permettre la mise à jour de la fenêtre.|
|[CImageList ::D ragMove](#dragmove)|Déplace l’image glissée pendant une opération de glisser-déplacer.|
|[CImageList ::D ragShowNolock](#dragshownolock)|Affiche ou masque l’image de glissement pendant une opération glisser, sans verrouiller la fenêtre.|
|[CImageList ::D RAW](#draw)|Dessine l’image glissée pendant une opération de glisser-déplacer.|
|[CImageList ::D rawEx](#drawex)|Dessine un élément de liste d’images dans le contexte de périphérique spécifié. La fonction utilise le style de dessin spécifié et fusionne l’image avec la couleur spécifiée.|
|[CImageList ::D rawIndirect](#drawindirect)|Dessine une image à partir d’une liste d’images.|
|[CImageList :: EndDrag](#enddrag)|Termine une opération glisser.|
|[CImageList :: ExtractIcon](#extracticon)|Crée une icône basée sur une image et un masque dans une liste d’images.|
|[CImageList :: FromHandle](#fromhandle)|Retourne un pointeur vers un `CImageList` objet en fonction d’un handle vers une liste d’images. Si aucun objet `CImageList` n'est attaché au handle, un objet `CImageList` temporaire est créé et attaché.|
|[CImageList :: FromHandlePermanent](#fromhandlepermanent)|Retourne un pointeur vers un `CImageList` objet en fonction d’un handle vers une liste d’images. Si un `CImageList` objet n’est pas attaché au handle, la valeur null est retournée.|
|[CImageList :: GetBkColor](#getbkcolor)|Récupère la couleur d’arrière-plan actuelle pour une liste d’images.|
|[CImageList :: GetDragImage](#getdragimage)|Obtient la liste d’images temporaires utilisée pour le déplacement.|
|[CImageList :: GetImageCount](#getimagecount)|Récupère le nombre d’images dans une liste d’images.|
|[CImageList :: GetImageInfo](#getimageinfo)|Récupère des informations sur une image.|
|[CImageList :: GetSafeHandle](#getsafehandle)|Récupère `m_hImageList` .|
|[CImageList :: Read](#read)|Lit une liste d’images à partir d’une archive.|
|[CImageList :: Remove](#remove)|Supprime une image d’une liste d’images.|
|[CImageList :: replace](#replace)|Remplace une image dans une liste d’images par une nouvelle image.|
|[CImageList :: SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan d’une liste d’images.|
|[CImageList :: SetDragCursorImage](#setdragcursorimage)|Crée une image de glissement.|
|[CImageList :: SetImageCount](#setimagecount)|Réinitialise le nombre d’images dans une liste d’images.|
|[CImageList :: SetOverlayImage](#setoverlayimage)|Ajoute l’index de base zéro d’une image à la liste d’images à utiliser comme masques de superposition.|
|[CImageList :: Write](#write)|Écrit une liste d’images dans une archive.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CImageList :: Operator HIMAGELIST](#operator_himagelist)|Retourne le HIMAGELIST attaché à `CImageList` .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CImageList :: m_hImageList](#m_himagelist)|Handle contenant la liste d’images jointe à cet objet.|

## <a name="remarks"></a>Notes

Une « liste d’images » est une collection d’images de même taille, chacune d’elles pouvant être référencée par son index de base zéro. Les listes d’images permettent de gérer efficacement de grands ensembles d’icônes ou de bitmaps. Toutes les images d’une liste d’images sont contenues dans un seul bitmap de grande largeur dans le format de l’appareil à l’écran. Une liste d’images peut également inclure une bitmap monochrome qui contient des masques utilisés pour dessiner des images en toute transparence (style d’icône). L’interface de programmation d’applications (API) Microsoft Win32 fournit des fonctions de liste d’images qui vous permettent de dessiner des images, de créer et de détruire des listes d’images, d’ajouter et de supprimer des images, de remplacer des images, de fusionner des images et de faire glisser des images.

Ce contrôle (et par conséquent la `CImageList` classe) est uniquement disponible pour les programmes qui s’exécutent sous windows 95/98 et Windows NT version 3,51 et versions ultérieures.

Pour plus d’informations sur l’utilisation de `CImageList` , consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a>CImageList :: Add

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
Pointeur vers l’image bitmap contenant l’image ou les images. Le nombre d’images est déduit à partir de la largeur de l’image bitmap.

*pbmMask*<br/>
Pointeur vers l’image bitmap qui contient le masque. Si aucun masque n’est utilisé avec la liste d’images, ce paramètre est ignoré.

*crMask*<br/>
Couleur utilisée pour générer le masque. Chaque pixel de cette couleur dans l’image bitmap donnée est remplacé par le noir et le bit correspondant dans le masque est défini sur un.

*hIcon*<br/>
Handle de l’icône qui contient la bitmap et le masque de la nouvelle image.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la première nouvelle image en cas de réussite ; sinon-1.

### <a name="remarks"></a>Notes

Vous êtes responsable de la libération du descripteur d’icône lorsque vous n’en avez plus besoin.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a>CImageList :: Attach

Appelez cette fonction pour attacher une liste d’images à un `CImageList` objet.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Handle d’un objet de liste d’images.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la pièce jointe a abouti ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a>CImageList :: BeginDrag

Appelez cette fonction pour commencer à faire glisser une image.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image à faire glisser.

*ptHotSpot*<br/>
Coordonnées de la position de départ du glissement (en général, la position du curseur). Les coordonnées sont relatives au coin supérieur gauche de l’image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction crée une liste d’images temporaire qui est utilisée pour le glissement. L’image combine l’image spécifiée et son masque avec le curseur actuel. En réponse aux messages d’WM_MOUSEMOVE suivants, vous pouvez déplacer l’image glisser à l’aide de la `DragMove` fonction membre. Pour terminer l’opération glisser, vous pouvez utiliser la `EndDrag` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList :: CImageList

Construit un objet `CImageList`.

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a>CImageList :: Copy

Cette fonction membre implémente le comportement de la fonction Win32 [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy), comme décrit dans le SDK Windows.

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

*iDst*<br/>
Index de base zéro de l’image à utiliser comme destination de l’opération de copie.

*iSrc*<br/>
Index de base zéro de l’image à utiliser comme source de l’opération de copie.

*uFlags*<br/>
Valeur de l’indicateur binaire qui spécifie le type d’opération de copie à effectuer. Ce paramètre peut prendre l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|ILCF_MOVE|L’image source est copiée dans l’index de l’image de destination. Cette opération entraîne l’exécution de plusieurs instances d’une image donnée. ILCF_MOVE est la valeur par défaut.|
|ILCF_SWAP|Les images source et de destination échangent des positions dans la liste d’images.|

*pSrc*<br/>
Pointeur vers un `CImageList` objet qui est la cible de l’opération de copie.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a>CImageList :: Create

Initialise une liste d’images et l’attache à un objet [CImageList](../../mfc/reference/cimagelist-class.md) .

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

*adéquat*<br/>
Dimensions de chaque image, en pixels.

*CY*<br/>
Dimensions de chaque image, en pixels.

*nFlags*<br/>
Spécifie le type de liste d’images à créer. Ce paramètre peut être une combinaison des valeurs suivantes, mais il ne peut inclure qu’une seule des `ILC_COLOR` valeurs.

|Valeur|Signification|
|-----------|-------------|
|ILC_COLOR|Utilisez le comportement par défaut si aucun des autres indicateurs ILC_COLOR * n’est spécifié. En règle générale, la valeur par défaut est ILC_COLOR4 ; Toutefois, pour les anciens pilotes d’affichage, la valeur par défaut est ILC_COLORDDB.|
|ILC_COLOR4|Utilisez une section DIB (Device-Independent Bitmap) 4 bits (16 couleurs) comme bitmap de la liste d’images.|
|ILC_COLOR8|Utilisez une section DIB 8 bits. Les couleurs utilisées pour la table de couleurs sont les mêmes que celles de la palette de demi-teintes.|
|ILC_COLOR16|Utilisez une section DIB 16 bits (32/64 Ko).|
|ILC_COLOR24|Utilisez une section DIB de 24 bits.|
|ILC_COLOR32|Utilisez une section DIB 32 bits.|
|ILC_COLORDDB|Utilisez une image bitmap dépendante de l’appareil.|
|ILC_MASK|Utilise un masque. La liste d’images contient deux bitmaps, dont l’un est une bitmap monochrome utilisée comme masque. Si cette valeur n’est pas incluse, la liste d’images contient une seule bitmap. Pour plus d’informations sur les images masquées, consultez [dessin d’images à partir d’une liste](../../mfc/drawing-images-from-an-image-list.md) d’images.|

*nInitial*<br/>
Nombre d’images que contient initialement la liste d’images.

*nGrow*<br/>
Nombre d’images par lesquelles la liste d’images peut croître lorsque le système doit redimensionner la liste pour faire de la place pour de nouvelles images. Ce paramètre représente le nombre de nouvelles images que la liste d’images redimensionnées peut contenir.

*nBitmapID*<br/>
ID de ressource de l’image bitmap à associer à la liste d’images.

*crMask*<br/>
Couleur utilisée pour générer un masque. Chaque pixel de cette couleur dans l’image bitmap spécifiée est remplacé par le noir et le bit correspondant dans le masque est défini sur un.

*lpszBitmapID*<br/>
Chaîne contenant les ID de ressource des images.

*imageList1*<br/>
Référence à un objet `CImageList`.

*nImage1*<br/>
Index de la première image existante.

*imagelist2*<br/>
Référence à un objet `CImageList`.

*nImage2*<br/>
Index de la deuxième image existante.

*DX*<br/>
Décalage de l’axe x de la deuxième image par rapport à la première image, en pixels.

*DY*<br/>
Décalage de l’axe y de la deuxième image par rapport à la première image, en pixels.

*pImageList*<br/>
Pointeur vers un objet `CImageList`.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CImageList` en deux étapes. Tout d’abord, appelez le constructeur, puis appelez `Create` , qui crée la liste d’images et l’attache à l' `CImageList` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList ::D eleteImageList

Appelez cette fonction pour supprimer une liste d’images.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList ::D eleteTempMap

Appelée automatiquement par le `CWinApp` Gestionnaire de temps d’inactivité, `DeleteTempMap` supprime tous les `CImageList` objets temporaires créés par [FromHandle](#fromhandle), mais ne détruit pas les handles ( `hImageList` ) qui sont temporairement associés aux `ImageList` objets.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a>CImageList ::D Etach

Appelez cette fonction pour détacher un objet de liste d’images d’un `CImageList` objet.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Valeur de retour

Handle d’un objet de liste d’images.

### <a name="remarks"></a>Notes

Cette fonction retourne un handle vers l’objet de liste d’images.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CImageList :: Attach](#attach).

## <a name="cimagelistdragenter"></a><a name="dragenter"></a>CImageList ::D ragEnter

Pendant une opération glisser, verrouille les mises à jour de la fenêtre spécifiée par *pWndLock* et affiche l’image de glissement à la position spécifiée par *point*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWndLock*<br/>
Pointeur vers la fenêtre qui possède l’image de glissement.

*point*<br/>
Position à laquelle afficher l’image de glissement. Les coordonnées sont relatives au coin supérieur gauche de la fenêtre (et non à la zone cliente).

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les coordonnées sont relatives au coin supérieur gauche de la fenêtre. par conséquent, vous devez compenser les largeurs des éléments de la fenêtre, tels que la bordure, la barre de titre et la barre de menus, lorsque vous spécifiez les coordonnées.

Si *pWndLock* a la valeur null, cette fonction dessine l’image dans le contexte d’affichage associé à la fenêtre du bureau, et les coordonnées sont relatives au coin supérieur gauche de l’écran.

Cette fonction verrouille toutes les autres mises à jour de la fenêtre donnée pendant l’opération glisser. Si vous devez effectuer un dessin au cours d’une opération glisser-déplacer, telle que la mise en surbrillance de la cible d’une opération de glisser-déplacer, vous pouvez masquer temporairement l’image glissée à l’aide de la fonction [CImageList ::D ragleave](#dragleave) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CImageList :: BeginDrag](#begindrag).

## <a name="cimagelistdragleave"></a><a name="dragleave"></a>CImageList ::D ragLeave

Déverrouille la fenêtre spécifiée par *pWndLock* et masque l’image de glissement, ce qui permet la mise à jour de la fenêtre.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Paramètres

*pWndLock*<br/>
Pointeur vers la fenêtre qui possède l’image de glissement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CImageList :: EndDrag](#enddrag).

## <a name="cimagelistdragmove"></a><a name="dragmove"></a>CImageList ::D ragMove

Appelez cette fonction pour déplacer l’image glissée pendant une opération de glisser-déplacer.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Nouvelle position de glissement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée en réponse à un message de WM_MOUSEMOVE. Pour commencer une opération glisser, utilisez la `BeginDrag` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList ::D ragShowNolock

Affiche ou masque l’image de glissement pendant une opération glisser, sans verrouiller la fenêtre.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
Spécifie si l’image de glissement doit être affichée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fonction [CImageList ::D ragenter](#dragenter) verrouille toutes les mises à jour de la fenêtre pendant une opération glisser. Toutefois, cette fonction ne verrouille pas la fenêtre.

## <a name="cimagelistdraw"></a><a name="draw"></a>CImageList ::D RAW

Appelez cette fonction pour dessiner l’image glissée pendant une opération de glisser-déplacer.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers le contexte de périphérique de destination.

*nImage*<br/>
Index de base zéro de l’image à dessiner.

*pt*<br/>
Emplacement à partir duquel dessiner dans le contexte de périphérique spécifié.

*nStyle*<br/>
Indicateur spécifiant le style de dessin. Il peut s’agir d’une ou plusieurs des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Dessine l’image, en fusionnant 25% avec la couleur de surbrillance du système. Cette valeur n’a aucun effet si la liste d’images ne contient pas de masque.|
|ILD_BLEND50, ILD_SELECTED ILD_BLEND|Dessine l’image, en fusionnant 50% avec la couleur de surbrillance du système. Cette valeur n’a aucun effet si la liste d’images ne contient pas de masque.|
|ILD_MASK|Dessine le masque.|
|ILD_NORMAL|Dessine l’image à l’aide de la couleur d’arrière-plan de la liste d’images. Si la couleur d’arrière-plan est la valeur CLR_NONE, l’image est dessinée de manière transparente à l’aide du masque.|
|ILD_TRANSPARENT|Dessine l’image de manière transparente à l’aide du masque, quelle que soit la couleur d’arrière-plan.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CImageList :: SetOverlayImage](#setoverlayimage).

## <a name="cimagelistdrawex"></a><a name="drawex"></a>CImageList ::D rawEx

Dessine un élément de liste d’images dans le contexte de périphérique spécifié.

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

*Maîtres*<br/>
Pointeur vers le contexte de périphérique de destination.

*nImage*<br/>
Index de base zéro de l’image à dessiner.

*pt*<br/>
Emplacement à partir duquel dessiner dans le contexte de périphérique spécifié.

*SZ*<br/>
Taille de la partie de l’image à dessiner par rapport à l’angle supérieur gauche de l’image. Consultez *DX* et *dy* dans [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) dans le SDK Windows.

*clrBk*<br/>
Couleur d’arrière-plan de l’image. Consultez *rgbBk* dans [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) dans le SDK Windows.

*clrFg*<br/>
Couleur de premier plan de l’image. Consultez *rgbFg* dans [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) dans le SDK Windows.

*nStyle*<br/>
Indicateur spécifiant le style de dessin. Consultez *fStyle* dans [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fonction utilise le style de dessin spécifié et fusionne l’image avec la couleur spécifiée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList ::D rawIndirect

Appelez cette fonction membre pour dessiner une image à partir d’une liste d’images.

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

*pimldp*<br/>
Pointeur vers une structure [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) qui contient des informations sur l’opération de dessin.

*Maîtres*<br/>
Pointeur vers le contexte de périphérique de destination. Vous devez supprimer cet objet [CDC](../../mfc/reference/cdc-class.md) lorsque vous n’en avez plus besoin.

*nImage*<br/>
Index de base zéro de l’image à dessiner.

*pt*<br/>
Structure de [points](/windows/win32/api/windef/ns-windef-point) contenant les coordonnées x et y à laquelle l’image sera dessinée.

*SZ*<br/>
Structure de [taille](/windows/win32/api/windef/ns-windef-size) indiquant la taille de l’image à dessiner.

*ptOrigin*<br/>
Structure de [points](/windows/win32/api/windef/ns-windef-point) contenant les coordonnées x et y qui spécifient l’angle supérieur gauche de l’opération de dessin par rapport à l’image elle-même. Les pixels de l’image situés à gauche de la coordonnée x et au-dessus de la coordonnée y ne sont pas dessinés.

*fStyle*<br/>
Indicateur spécifiant le style de dessin et, éventuellement, l’image de superposition. Pour plus d’informations sur l’image de superposition, consultez la section Notes. L’implémentation par défaut de MFC, ILD_NORMAL, dessine l’image à l’aide de la couleur d’arrière-plan de la liste d’images. Si la couleur d’arrière-plan est la valeur CLR_NONE, l’image est dessinée de manière transparente à l’aide d’un masque.

D’autres styles possibles sont décrits dans le membre *fStyle* de la structure [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) .

*dwRop*<br/>
Valeur spécifiant un code d’opération Raster. Ces codes définissent la façon dont les données de couleur du rectangle source sont combinées avec les données de couleur du rectangle de destination pour obtenir la couleur finale. L’implémentation par défaut de MFC, SRCCOPY, copie le rectangle source directement dans le rectangle de destination. Ce paramètre est ignoré si le paramètre *fStyle* n’inclut pas l’indicateur ILD_ROP.

D’autres valeurs possibles sont décrites dans le membre *dwRop* de la structure [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) .

*rgbBack*<br/>
Couleur d’arrière-plan de l’image, par défaut CLR_DEFAULT. Ce paramètre peut être une valeur RVB définie par l’application ou l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|CLR_DEFAULT|Couleur d’arrière-plan par défaut. L’image est dessinée à l’aide de la couleur d’arrière-plan de la liste d’images.|
|CLR_NONE|Aucune couleur d’arrière-plan. L’image est dessinée de manière transparente.|

*rgbFore*<br/>
Couleur de premier plan de l’image, par défaut CLR_DEFAULT. Ce paramètre peut être une valeur RVB définie par l’application ou l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|CLR_DEFAULT|Couleur de premier plan par défaut. L’image est dessinée à l’aide de la couleur de surbrillance du système comme couleur de premier plan.|
|CLR_NONE|Aucune couleur de fusion. L’image est fusionnée avec la couleur du contexte de périphérique de destination.|

Ce paramètre est utilisé uniquement si *fStyle* comprend l’indicateur ILD_BLEND25 ou ILD_BLEND50.

*fState*<br/>
Indicateur spécifiant l’état du dessin. Ce membre peut contenir un ou plusieurs indicateurs d’état de liste d’images.

*Frame*<br/>
Affecte le comportement des effets de saturation et de fusion alpha.

Lorsqu’il est utilisé avec ILS_SATURATE, ce membre contient la valeur qui est ajoutée à chaque composant de couleur de l’triplet RVB pour chaque pixel de l’icône.

Lorsqu’il est utilisé avec ILS_APLHA, ce membre contient la valeur du canal alpha. Cette valeur peut être comprise entre 0 et 255, 0 étant complètement transparent et 255 entièrement opaque.

*crEffect*<br/>
Valeur [COLORREF](/windows/win32/gdi/colorref) utilisée pour les effets de lumière et d’ombre.

### <a name="return-value"></a>Valeur de retour

TRUE si l’image est correctement dessinée ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez la première version si vous souhaitez remplir la structure Win32 vous-même. Utilisez la deuxième version si vous souhaitez tirer parti d’un ou plusieurs des arguments par défaut de MFC, ou évitez de gérer la structure.

Une image de superposition est une image dessinée au-dessus de l’image principale, spécifiée dans cette fonction membre par le paramètre *nimage* . Dessinez un masque de superposition à l’aide de la fonction membre [Draw](#draw) avec l’index de base 1 du masque de superposition spécifié à l’aide de la macro [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a>CImageList :: EndDrag

Appelez cette fonction pour terminer une opération glisser.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Notes

Pour commencer une opération glisser, utilisez la `BeginDrag` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a>CImageList :: ExtractIcon

Appelez cette fonction pour créer une icône basée sur une image et son masque associé dans une liste d’images.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image.

### <a name="return-value"></a>Valeur de retour

Handle de l’icône en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Cette méthode s’appuie sur le comportement de la macro [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) pour créer l’icône. Pour plus d’informations sur la création et le nettoyage d’icônes, reportez-vous à la macro [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList :: FromHandle

Retourne un pointeur vers un `CImageList` objet en fonction d’un handle vers une liste d’images.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Spécifie la liste d’images.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CImageList` objet en cas de réussite ; sinon, null.

### <a name="remarks"></a>Notes

Si un `CImageList` n’est pas déjà attaché au handle, un `CImageList` objet temporaire est créé et attaché. Cet `CImageList` objet temporaire est valide uniquement jusqu’à la prochaine période d’inactivité de l’application dans sa boucle d’événements, auquel cas tous les objets temporaires sont supprimés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList :: FromHandlePermanent

Retourne un pointeur vers un `CImageList` objet en fonction d’un handle vers une liste d’images.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Spécifie la liste d’images.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CImageList` objet en cas de réussite ; sinon, null.

### <a name="remarks"></a>Notes

Si un `CImageList` objet n’est pas attaché au handle, la valeur null est retournée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList :: GetBkColor

Appelez cette fonction pour récupérer la couleur d’arrière-plan actuelle d’une liste d’images.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de couleur RVB de la `CImageList` couleur d’arrière-plan de l’objet.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CImageList :: SetBkColor](#setbkcolor).

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a>CImageList :: GetDragImage

Obtient la liste d’images temporaires utilisée pour le déplacement.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Paramètres

*lpPoint*<br/>
Adresse d’une structure de [point](/windows/win32/api/windef/ns-windef-point) qui reçoit la position actuelle de glissement.

*lpPointHotSpot*<br/>
Adresse d’une `POINT` structure qui reçoit le décalage de l’image de glissement par rapport à la position de glissement.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, pointeur vers la liste d’images temporaires utilisée pour le déplacement ; Sinon, NULL.

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a>CImageList :: GetImageCount

Appelez cette fonction pour récupérer le nombre d’images dans une liste d’images.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’images.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CImageList :: ExtractIcon](#extracticon).

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a>CImageList :: GetImageInfo

Appelez cette fonction pour récupérer les informations relatives à une image.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image.

*pImageInfo*<br/>
Pointeur vers une structure [IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo) qui reçoit des informations sur l’image. Les informations de cette structure peuvent être utilisées pour manipuler directement les bitmaps de l’image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La `IMAGEINFO` structure contient des informations sur une image dans une liste d’images.

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList :: GetSafeHandle

Appelez cette fonction pour récupérer le `m_hImageList` membre de données.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Valeur de retour

Handle de la liste d’images attachée ; Sinon, la valeur est NULL si aucun objet n’est attaché.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a>CImageList :: m_hImageList

Handle de la liste d’images jointe à cet objet.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Notes

Le `m_hImageList` membre de données est une variable publique de type HIMAGELIST.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList :: Operator HIMAGELIST

Utilisez cet opérateur pour recevoir le handle attaché de l' `CImageList` objet.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle vers la liste d’images représentée par l' `CImageList` objet ; sinon, null.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast qui prend en charge l’utilisation directe d’un objet HIMAGELIST.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a>CImageList :: Read

Appelez cette fonction pour lire une liste d’images à partir d’une archive.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Paramètres

*pArchive*<br/>
Pointeur vers un `CArchive` objet à partir duquel la liste d’images doit être lue.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a>CImageList :: Remove

Appelez cette fonction pour supprimer une image d’un objet de liste d’images.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Tous les éléments suivants *nimage* descendent d’une position. Par exemple, si une liste d’images contient deux éléments, le fait de supprimer le premier élément entraînera l’élément restant dans la première position. *nimage*= 0 pour l’élément à la première position.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a>CImageList :: replace

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

*nImage*<br/>
Index de base zéro de l’image à remplacer.

*pbmImage*<br/>
Pointeur vers l’image bitmap contenant l’image.

*pbmMask*<br/>
Pointeur vers l’image bitmap qui contient le masque. Si aucun masque n’est utilisé avec la liste d’images, ce paramètre est ignoré.

*hIcon*<br/>
Handle vers l’icône qui contient l’image bitmap et le masque de la nouvelle image.

### <a name="return-value"></a>Valeur de retour

La version qui retourne BOOL retourne une valeur différente de zéro en cas de réussite ; Sinon, 0.

La version qui **`int`** retourne l’index de base zéro de l’image en cas de réussite ; sinon-1.

### <a name="remarks"></a>Notes

Appelez cette fonction membre après avoir appelé [SetImageCount](#setimagecount) pour assigner les nouvelles images valides aux numéros d’index d’image d’espace réservé.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CImageList :: SetImageCount](#setimagecount).

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList :: SetBkColor

Appelez cette fonction pour définir la couleur d’arrière-plan d’une liste d’images.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Paramètres

*CR*<br/>
Couleur d’arrière-plan à définir. Il peut être CLR_NONE. Dans ce cas, les images sont dessinées en toute transparence à l’aide du masque.

### <a name="return-value"></a>Valeur de retour

La couleur d’arrière-plan précédente en cas de réussite ; sinon CLR_NONE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList :: SetDragCursorImage

Crée une image de glissement en combinant l’image donnée (généralement une image de curseur de la souris) avec l’image de glissement actuelle.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Paramètres

*nDrag*<br/>
Index de la nouvelle image à combiner avec l’image de glissement.

*ptHotSpot*<br/>
Position de la zone réactive dans la nouvelle image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Étant donné que les fonctions de glissement utilisent la nouvelle image pendant une opération de glissement, vous devez utiliser la fonction [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) de Windows pour masquer le curseur de la souris réel après l’appel de `CImageList::SetDragCursorImage` . Sinon, le système peut sembler être composé de deux curseurs de souris pour la durée de l'opération Glisser-déplacer.

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a>CImageList :: SetImageCount

Appelez cette fonction membre pour réinitialiser le nombre d’images dans un `CImageList` objet.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Paramètres

*uNewCount*<br/>
Valeur qui spécifie le nouveau nombre total d’images dans la liste d’images.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Si vous appelez cette fonction membre pour augmenter le nombre d’images dans la liste d’images, appelez [Replace](#replace) pour chaque image supplémentaire afin d’affecter les nouveaux index aux images valides. Si vous ne parvenez pas à assigner les index à des images valides, les opérations de dessin qui créent les nouvelles images sont imprévisibles.

Si vous réduisez la taille d’une liste d’images à l’aide de cette fonction, les images tronquées sont libérées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>CImageList :: SetOverlayImage

Appelez cette fonction pour ajouter l’index de base zéro d’une image à la liste d’images à utiliser comme masques de superposition.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image à utiliser comme masque de superposition.

*nOverlay*<br/>
Index de base un du masque de superposition.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Jusqu’à quatre index peuvent être ajoutés à la liste.

Un masque de superposition est une image dessinée de manière transparente sur une autre image. Dessinez un masque de superposition sur une image à l’aide de la fonction membre [CImageList ::D RAW](#draw) avec l’index de base 1 du masque de superposition spécifié à l’aide de la macro INDEXTOOVERLAYMASK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a>CImageList :: Write

Appelez cette fonction pour écrire un objet de liste d’images dans une archive.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Paramètres

*pArchive*<br/>
Pointeur vers un `CArchive` objet dans lequel la liste d’images doit être stockée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl (classe)](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl (classe)](../../mfc/reference/ctabctrl-class.md)
