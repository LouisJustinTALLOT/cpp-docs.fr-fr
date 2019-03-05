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
ms.openlocfilehash: 3e8c524a95730282d0e35e5f791ebf229725e282
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298917"
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
|[CImageList::CImageList](#cimagelist)|Construit un objet `CImageList`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CImageList::Add](#add)|Ajoute une image ou des images à une liste d’images.|
|[CImageList::Attach](#attach)|Attache une liste d’images à un `CImageList` objet.|
|[CImageList::BeginDrag](#begindrag)|Commence à faire glisser une image.|
|[CImageList::Copy](#copy)|Copie une image dans un `CImageList` objet.|
|[CImageList::Create](#create)|Initialise une liste d’images et l’attache à un `CImageList` objet.|
|[CImageList::DeleteImageList](#deleteimagelist)|Supprime une liste d’images.|
|[CImageList::DeleteTempMap](#deletetempmap)|Appelé par le [CWinApp](../../mfc/reference/cwinapp-class.md) Gestionnaire de durée d’inactivité à supprimer n’importe quel temporaire `CImageList` objet créé par `FromHandle`.|
|[CImageList::Detach](#detach)|Détache un objet de liste d’images à partir d’un `CImageList` de l’objet et retourne un handle vers une liste d’images.|
|[CImageList::DragEnter](#dragenter)|Verrouille les mises à jour pendant une opération glisser et affiche l’image glissée à une position spécifiée.|
|[CImageList::DragLeave](#dragleave)|Déverrouille la fenêtre et masque l’image glissée afin que la fenêtre peut être mis à jour.|
|[CImageList::DragMove](#dragmove)|Déplace l’image qui est glissé pendant une opération de glisser-déplacer.|
|[CImageList::DragShowNolock](#dragshownolock)|Affiche ou masque l’image glissée pendant une opération glisser, sans verrouillage de la fenêtre.|
|[CImageList::Draw](#draw)|Dessine l’image qui est glissé pendant une opération de glisser-déplacer.|
|[CImageList::DrawEx](#drawex)|Dessine un élément de liste d’image dans le contexte de périphérique spécifié. La fonction utilise le style de dessin spécifié et fusionne l’image avec la couleur spécifiée.|
|[CImageList::DrawIndirect](#drawindirect)|Dessine une image à partir d’une liste d’images.|
|[CImageList::EndDrag](#enddrag)|Termine une opération glisser.|
|[CImageList::ExtractIcon](#extracticon)|Crée une icône basée sur une image et un masque dans une liste d’images.|
|[CImageList::FromHandle](#fromhandle)|Retourne un pointeur vers un `CImageList` lorsqu’un handle vers une liste d’images de l’objet. Si aucun objet `CImageList` n'est attaché au handle, un objet `CImageList` temporaire est créé et attaché.|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Retourne un pointeur vers un `CImageList` lorsqu’un handle vers une liste d’images de l’objet. Si un `CImageList` objet n’est pas attaché au handle, la valeur NULL est retournée.|
|[CImageList::GetBkColor](#getbkcolor)|Récupère la couleur d’arrière-plan actuelle pour une liste d’images.|
|[CImageList::GetDragImage](#getdragimage)|Obtient la liste d’images temporaire qui est utilisée pour faire glisser.|
|[CImageList::GetImageCount](#getimagecount)|Récupère le nombre d’images dans une liste d’images.|
|[CImageList::GetImageInfo](#getimageinfo)|Récupère des informations sur une image.|
|[CImageList::GetSafeHandle](#getsafehandle)|Récupère `m_hImageList`.|
|[CImageList::Read](#read)|Lit une liste d’images à partir d’une archive.|
|[CImageList::Remove](#remove)|Supprime une image à partir d’une liste d’images.|
|[CImageList::Replace](#replace)|Remplace une image dans une liste d’images avec une nouvelle image.|
|[CImageList::SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan pour une liste d’images.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Crée une nouvelle image glisser.|
|[CImageList::SetImageCount](#setimagecount)|Réinitialise le nombre d’images dans une liste d’images.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Ajoute l’index de base zéro d’une image à la liste des images à utiliser comme masques de superposition.|
|[CImageList::Write](#write)|Écrit une liste d’images dans une archive.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Retourne le HIMAGELIST attaché à la `CImageList`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Un handle qui contient la liste d’images associée à cet objet.|

## <a name="remarks"></a>Notes

Une « liste d’images » est une collection d’images de même taille, chacun d’eux peut être référencé par son index de base zéro. Listes d’images permettent de gérer efficacement de grands ensembles d’icônes ou de bitmaps. Toutes les images dans une liste d’images sont contenues dans une seule grande bitmap au format de dispositif d’écran. Une liste d’images peut également inclure une bitmap monochrome contenant des masques utilisés pour dessiner des images en toute transparence (style d’icône). Les API (interface) de programmation d’application Microsoft Win32 fournit image répertorie les fonctions qui vous permettent de dessiner des images, créer et détruire des listes d’images, ajouter et supprimer des images, remplacez les images, fusionner des images et faire glisser des images.

Ce contrôle (et par conséquent la `CImageList` classe) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT version 3.51 et ultérieures.

Pour plus d’informations sur l’utilisation de `CImageList`, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="add"></a>  CImageList::Add

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
Pointeur vers la bitmap qui contient l’ou les images. Le nombre d’images est déduit à partir de la largeur de la bitmap.

*pbmMask*<br/>
Pointeur vers la bitmap contenant le masque. Si aucun masque n’est utilisé avec la liste d’images, ce paramètre est ignoré.

*crMask*<br/>
Couleur utilisée pour générer le masque. Chaque pixel de cette couleur dans l’image bitmap donnée est modifiée en noir et le bit correspondant dans le masque est défini à un.

*hIcon*<br/>
Handle de l’icône qui contient l’image bitmap et un masque pour la nouvelle image.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la nouvelle image en cas de réussite ; Sinon, - 1.

### <a name="remarks"></a>Notes

Vous êtes chargé de libérer le handle de l’icône lorsque vous avez terminé avec lui.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>  CImageList::Attach

Appelez cette fonction pour attacher une liste d’images à un `CImageList` objet.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Handle vers un objet de liste d’images.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la pièce jointe a réussi ; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>  CImageList::BeginDrag

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
Coordonnées de départ glisser (en règle générale, la position du curseur). Les coordonnées sont exprimées par rapport à la partie supérieure gauche de l’image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction crée une liste d’images temporaire qui est utilisée pour faire glisser. L’image associe l’image spécifiée et son masque le curseur actuel. En réponse aux messages WM_MOUSEMOVE suivants, vous pouvez déplacer l’image glissée à l’aide de la `DragMove` fonction membre. Pour mettre fin à l’opération glisser, vous pouvez utiliser le `EndDrag` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>  CImageList::CImageList

Construit un objet `CImageList`.

```
CImageList();
```

##  <a name="copy"></a>  CImageList::Copy

Cette fonction membre implémente le comportement de la fonction Win32 [ImageList_Copy](/windows/desktop/api/commctrl/nf-commctrl-imagelist_copy), comme décrit dans le SDK Windows.

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
La valeur d’indicateur de bits qui spécifie le type d’opération de copie qu’il veut. Ce paramètre peut être une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|ILCF_MOVE|L’image source est copié dans l’index de l’image de destination. Cette opération entraîne plusieurs instances d’une image donnée. ILCF_MOVE est la valeur par défaut.|
|ILCF_SWAP|Les images source et destination échangent des positions dans la liste d’images.|

*pSrc*<br/>
Un pointeur vers un `CImageList` objet qui est la cible de l’opération de copie.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>  CImageList::Create

Initialise une liste d’images et l’attache à un [CImageList](../../mfc/reference/cimagelist-class.md) objet.

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

*cx*<br/>
Dimensions de chaque image, en pixels.

*cy*<br/>
Dimensions de chaque image, en pixels.

*nFlags*<br/>
Spécifie le type de liste d’images à créer. Ce paramètre peut être une combinaison des valeurs suivantes, mais il peut inclure uniquement un de le `ILC_COLOR` valeurs.

|Value|Signification|
|-----------|-------------|
|ILC_COLOR|Utiliser le comportement par défaut si aucun des autres ILC_COLOR * indicateurs est spécifié. En règle générale, la valeur par défaut est ILC_COLOR4 ; mais pour les anciens pilotes d’affichage, la valeur par défaut est ILC_COLORDDB.|
|ILC_COLOR4|Utiliser une section de bitmap indépendante du périphérique (DIB) 4 bits (16 couleurs) comme l’image bitmap pour la liste d’images.|
|ILC_COLOR8|Utiliser une section DIB 8 bits. Les couleurs utilisées pour la table des couleurs sont les mêmes couleurs comme la palette de demi-teintes.|
|ILC_COLOR16|Utiliser 16 bits (32 / 64k couleur) section DIB.|
|ILC_COLOR24|Utilisation d’une section DIB 24 bits.|
|ILC_COLOR32|Utilisation d’une section DIB 32 bits.|
|ILC_COLORDDB|Utiliser une image bitmap dépendant du périphérique.|
|ILC_MASK|Utilise un masque. La liste d’images contient deux images bitmap d'entre eux est un bitmap monochrome utilisé comme masque. Si cette valeur n’est pas incluse, la liste d’images contient uniquement une seule bitmap. Consultez [dessin des Images à partir d’une liste d’images](../../mfc/drawing-images-from-an-image-list.md) pour plus d’informations sur les images masquées.|

*nInitial*<br/>
Nombre d’images contenant la liste d’images initialement.

*nGrow*<br/>
Nombre d’images dont la liste d’images peut augmenter lorsque le système doit redimensionner la liste pour faire place aux nouvelles images. Ce paramètre représente le nombre de nouvelles images de que la liste d’images redimensionnées peut contenir.

*nBitmapID*<br/>
ID de ressource de la bitmap à associer à la liste d’images.

*crMask*<br/>
Couleur utilisée pour générer un masque. Chaque pixel de cette couleur dans la bitmap spécifiée devient noir, et le bit correspondant dans le masque est défini à un.

*lpszBitmapID*<br/>
Chaîne contenant les ID des images de ressource.

*imagelist1*<br/>
Référence à un objet `CImageList`.

*nImage1*<br/>
Index de la première image existante.

*imagelist2*<br/>
Référence à un objet `CImageList`.

*nImage2*<br/>
Index de la deuxième image existante.

*dx*<br/>
Décalage de l’axe x de la deuxième image par rapport à la première image, en pixels.

*dy*<br/>
Décalage de l’axe y de la deuxième image par rapport à la première image, en pixels.

*pImageList*<br/>
Pointeur vers un objet `CImageList` .

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CImageList` en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, ce qui crée la liste d’images et l’attache à la `CImageList` objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>  CImageList::DeleteImageList

Appelez cette fonction pour supprimer une liste d’images.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap

Appelé automatiquement par le `CWinApp` Gestionnaire de durée d’inactivité, `DeleteTempMap` supprime temporaires `CImageList` objets créés par [FromHandle](#fromhandle), mais ne détruit ne pas tous les handles ( `hImageList`) temporairement associés avec le `ImageList` objets.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>  CImageList::Detach

Appelez cette fonction pour détacher un objet de liste d’images à partir d’un `CImageList` objet.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Valeur de retour

Handle vers un objet de liste d’images.

### <a name="remarks"></a>Notes

Cette fonction retourne un handle pour l’objet de liste d’images.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CImageList::Attach](#attach).

##  <a name="dragenter"></a>  CImageList::DragEnter

Pendant une opération glisser, verrouille les mises à jour de la fenêtre spécifiée par *pWndLock* et affiche l’image glissée à la position spécifiée par *point*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWndLock*<br/>
Pointeur vers la fenêtre propriétaire de l’image glissée.

*point*<br/>
Position à laquelle afficher l’image glissée. Coordonnées sont exprimées par rapport à la partie supérieure gauche de la fenêtre (pas la zone cliente).

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les coordonnées sont exprimées par rapport à l’angle supérieur gauche de la fenêtre, donc vous devez compenser la largeur des éléments de la fenêtre, telles que la bordure, la barre de titre et la barre de menus, lorsque vous spécifiez les coordonnées.

Si *pWndLock* a la valeur NULL, cette fonction Dessine l’image dans le contexte d’affichage associé à la fenêtre du bureau, et les coordonnées sont relatives à l’angle supérieur gauche de l’écran.

Cette fonction verrouille toutes les autres mises à jour dans la fenêtre donnée pendant l’opération glisser. Si vous avez besoin effectuer un dessin pendant une opération glisser, telles que la mise en surbrillance de la cible d’une opération de glisser-déplacer, vous pouvez masquer temporairement l’image à l’aide de la [CImageList::DragLeave](#dragleave) (fonction).

### <a name="example"></a>Exemple

  Consultez l’exemple de [CImageList::BeginDrag](#begindrag).

##  <a name="dragleave"></a>  CImageList::DragLeave

Déverrouille la fenêtre spécifiée par *pWndLock* et masque l’image glissée, ce qui permet de la fenêtre à mettre à jour.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Paramètres

*pWndLock*<br/>
Pointeur vers la fenêtre propriétaire de l’image glissée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CImageList::EndDrag](#enddrag).

##  <a name="dragmove"></a>  CImageList::DragMove

Appelez cette fonction pour déplacer l’image qui est glissé pendant une opération de glisser-déplacer.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
Nouvelle position de glissement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée en réponse à un message WM_MOUSEMOVE. Pour commencer une opération glisser, utiliser le `BeginDrag` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>  CImageList::DragShowNolock

Affiche ou masque l’image glissée pendant une opération glisser, sans verrouillage de la fenêtre.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
Spécifie si l’image glissée doit être indiqué.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le [CImageList::DragEnter](#dragenter) fonction verrouille toutes les mises à jour dans la fenêtre pendant une opération glisser. Cette fonction, toutefois, ne verrouille pas de la fenêtre.

##  <a name="draw"></a>  CImageList::Draw

Appelez cette fonction pour dessiner l’image qui est glissé pendant une opération de glisser-déplacer.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte de périphérique de destination.

*nImage*<br/>
Index de base zéro de l’image à dessiner.

*pt*<br/>
Emplacement à partir duquel dessiner dans le contexte de périphérique spécifié.

*nStyle*<br/>
Indicateur qui spécifie le style de dessin. Il peut être une ou plusieurs des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Dessine l’image, 25 pour cent avec la couleur de surbrillance du système de fusion. Cette valeur n’a aucun effet si la liste d’images ne contient pas un masque.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Dessine l’image, 50 % avec la couleur de surbrillance du système de fusion. Cette valeur n’a aucun effet si la liste d’images ne contient pas un masque.|
|ILD_MASK|Dessine le masque.|
|ILD_NORMAL|Dessine l’image à l’aide de la couleur d’arrière-plan pour la liste d’images. Si vous définissez CLR_NONE comme est la couleur d’arrière-plan, l’image est dessinée de manière transparente en utilisant le masque.|
|ILD_TRANSPARENT|Dessine l’image en toute transparence en utilisant le masque, quelle que soit la couleur d’arrière-plan.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CImageList::SetOverlayImage](#setoverlayimage).

##  <a name="drawex"></a>  CImageList::DrawEx

Dessine un élément de liste d’image dans le contexte de périphérique spécifié.

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
Pointeur vers le contexte de périphérique de destination.

*nImage*<br/>
Index de base zéro de l’image à dessiner.

*pt*<br/>
Emplacement à partir duquel dessiner dans le contexte de périphérique spécifié.

*sz*<br/>
Taille de la partie de l’image à dessiner par rapport à l’angle supérieur gauche de l’image. Consultez *dx* et *dy* dans [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) dans le SDK Windows.

*clrBk*<br/>
Couleur d’arrière-plan de l’image. Consultez *rgbBk* dans [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) dans le SDK Windows.

*clrFg*<br/>
Couleur de premier plan de l’image. Consultez *rgbFg* dans [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) dans le SDK Windows.

*nStyle*<br/>
Indicateur qui spécifie le style de dessin. Consultez *fStyle* dans [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fonction utilise le style de dessin spécifié et fusionne l’image avec la couleur spécifiée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>  CImageList::DrawIndirect

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
Un pointeur vers un [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) structure qui contient des informations sur l’opération de dessin.

*pDC*<br/>
Pointeur vers le contexte de périphérique de destination. Vous devez supprimer cela [CDC](../../mfc/reference/cdc-class.md) objet lorsque vous avez terminé avec lui.

*nImage*<br/>
Index de base zéro de l’image à dessiner.

*pt*<br/>
Un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure contenant les coordonnées x et y où l’image sera dessiné.

*sz*<br/>
Un [taille](/windows/desktop/api/windef/ns-windef-tagsize) structure indiquant la taille de l’image à dessiner.

*ptOrigin*<br/>
Un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure contenant les coordonnées x et y spécifiant l’angle supérieur gauche de l’opération de dessin en ce qui concerne l’image elle-même. Pixels qui sont à gauche de la coordonnée x et versions ultérieures de la coordonnée y de l’image ne sont pas dessinés.

*fStyle*<br/>
Indicateur spécifiant le style de dessin et, éventuellement, l’image de superposition. Consultez la section Notes pour plus d’informations sur l’image de superposition. L’implémentation par défaut MFC, ILD_NORMAL, dessine l’image à l’aide de la couleur d’arrière-plan pour la liste d’images. Si vous définissez CLR_NONE comme est la couleur d’arrière-plan, l’image est dessinée de manière transparente à l’aide d’un masque.

Autres styles possibles sont décrits sous la *fStyle* membre de la [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) structure.

*dwRop*<br/>
Valeur qui spécifie un code d’opération de rastérisation. Ces codes définissent comment les données de couleur du rectangle source à combiner avec les données de couleur du rectangle de destination obtenir la couleur finale. L’implémentation par défaut de MFC SRCCOPY, copie le rectangle source directement vers le rectangle de destination. Ce paramètre est ignoré si le *fStyle* paramètre n’inclut pas l’indicateur ILD_ROP.

Autres valeurs possibles sont décrites sous la *dwRop* membre de la [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) structure.

*rgbBack*<br/>
La couleur d’arrière-plan image, par défaut CLR_DEFAULT. Ce paramètre peut être une valeur RVB définie par l’application ou l’une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|CLR_DEFAULT|Couleur d’arrière-plan par défaut. L’image est dessinée à l’aide de la couleur d’arrière-plan de liste image.|
|CLR_NONE|Aucune couleur d’arrière-plan. L’image est dessinée en toute transparence.|

*rgbFore*<br/>
Couleur de premier plan image, par défaut CLR_DEFAULT. Ce paramètre peut être une valeur RVB définie par l’application ou l’une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|CLR_DEFAULT|Couleur de premier plan par défaut. L’image est dessinée à l’aide de la couleur de surbrillance du système en tant que la couleur de premier plan.|
|CLR_NONE|Aucune couleur de dégradé. L’image est fusionnée avec la couleur du contexte de périphérique de destination.|

Ce paramètre est utilisé uniquement si *fStyle* inclut l’indicateur ILD_BLEND25 ou ILD_BLEND50.

*fState*<br/>
Indicateur qui spécifie l’état de dessin. Ce membre peut contenir un ou plusieurs indicateurs d’état de liste image.

*Frame*<br/>
Affecte le comportement des effets de saturation et le blindage alpha.

Lorsqu’il est utilisé avec ILS_SATURATE, ce membre contient la valeur qui est ajoutée à chaque composant de couleur des trois RVB pour chaque pixel de l’icône.

Lorsqu’il est utilisé avec ILS_APLHA, ce membre conserve la valeur pour le canal alpha. Cette valeur peut être comprise entre 0 et 255, 0 étant totalement transparent et 255 est complètement opaque.

*crEffect*<br/>
Un [COLORREF](/windows/desktop/gdi/colorref) valeur utilisée pour les effets de lumière et les clichés instantanés.

### <a name="return-value"></a>Valeur de retour

TRUE si l’image est dessinée avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez la première version si vous souhaitez remplir la structure Win32 vous-même. Utilisez la deuxième version si vous souhaitez tirer parti d’un ou plusieurs des arguments par défaut MFC, ou éviter de gérer la structure.

Une image de superposition est une image qui est dessinée par-dessus l’image principale, spécifiée dans cette fonction membre par la *nImage* paramètre. Dessiner un masque de superposition à l’aide de la [dessiner](#draw) fonction membre avec l’index de base de celle du masque de superposition spécifié à l’aide de la [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) macro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>  CImageList::EndDrag

Appelez cette fonction pour mettre fin à une opération glisser.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Notes

Pour commencer une opération glisser, utiliser le `BeginDrag` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>  CImageList::ExtractIcon

Appelez cette fonction pour créer une icône basée sur une image et son masque connexe dans une liste d’images.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image.

### <a name="return-value"></a>Valeur de retour

Handle de l’icône en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Cette méthode s’appuie sur le comportement de la [ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon) macro pour créer l’icône. Reportez-vous à la [ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon) macro pour plus d’informations sur la création de l’icône et le nettoyage.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>  CImageList::FromHandle

Retourne un pointeur vers un `CImageList` lorsqu’un handle vers une liste d’images de l’objet.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Spécifie la liste d’images.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CImageList` objet en cas de réussite ; sinon, NULL.

### <a name="remarks"></a>Notes

Si un `CImageList` n’est pas déjà attaché au handle, une table temporaire `CImageList` objet est créé et attaché. Ce fichier temporaire `CImageList` objet est valide uniquement jusqu'à ce que la prochaine fois que l’application possède les temps d’inactivité dans sa boucle de l’événement, moment auquel tous les objets temporaires sont supprimés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>  CImageList::FromHandlePermanent

Retourne un pointeur vers un `CImageList` lorsqu’un handle vers une liste d’images de l’objet.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Paramètres

*hImageList*<br/>
Spécifie la liste d’images.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CImageList` objet en cas de réussite ; sinon, NULL.

### <a name="remarks"></a>Notes

Si un `CImageList` objet n’est pas attaché au handle, la valeur NULL est retournée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>  CImageList::GetBkColor

Appelez cette fonction pour récupérer la couleur d’arrière-plan actuelle pour une liste d’images.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de couleur RVB de la `CImageList` couleur d’arrière-plan de l’objet.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CImageList::SetBkColor](#setbkcolor).

##  <a name="getdragimage"></a>  CImageList::GetDragImage

Obtient la liste d’images temporaire qui est utilisée pour faire glisser.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Paramètres

*lpPoint*<br/>
Adresse d’un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure recevant actuel faites glisser la position.

*lpPointHotSpot*<br/>
Adresse d’un `POINT` structure qui reçoit le décalage de l’image glissée par rapport à la position de glissement.

### <a name="return-value"></a>Valeur de retour

Si réussie, un pointeur vers l’image temporaire liste qui est utilisé pour les opérations de glissement ; Sinon, NULL.

##  <a name="getimagecount"></a>  CImageList::GetImageCount

Appelez cette fonction pour récupérer le nombre d’images dans une liste d’images.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’images.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CImageList::ExtractIcon](#extracticon).

##  <a name="getimageinfo"></a>  CImageList::GetImageInfo

Appelez cette fonction pour récupérer des informations sur une image.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image.

*pImageInfo*<br/>
Pointeur vers un [IMAGEINFO](/windows/desktop/api/commctrl/ns-commctrl-_imageinfo) structure qui reçoit des informations sur l’image. Les informations contenues dans cette structure peuvent être utilisés pour manipuler directement les bitmaps pour l’image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Le `IMAGEINFO` structure contient des informations sur une image dans une liste d’images.

##  <a name="getsafehandle"></a>  CImageList::GetSafeHandle

Appelez cette fonction pour récupérer le `m_hImageList` membre de données.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Valeur de retour

Un handle vers la liste d’images attachée ; Sinon, NULL si aucun objet n’est attaché.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>  CImageList::m_hImageList

Handle de la liste d’images associé à cet objet.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Notes

Le `m_hImageList` membre de données est une variable publique de type HIMAGELIST.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>  CImageList::operator HIMAGELIST

Utilisez cet opérateur pour obtenir le handle attaché de la `CImageList` objet.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Valeur de retour

Si réussie, un handle vers la liste d’images représenté par le `CImageList` de l’objet ; sinon, NULL.

### <a name="remarks"></a>Notes

Cet opérateur est un opérateur de cast, qui prend en charge l’utilisation directe d’un objet HIMAGELIST.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>  CImageList::Read

Appelez cette fonction pour lire une liste d’images à partir d’une archive.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Paramètres

*pArchive*<br/>
Un pointeur vers un `CArchive` objet à partir duquel la liste d’images doit être lu.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>  CImageList::Remove

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

Tous les éléments suivant *nImage* maintenant déplacer vers le bas une position. Par exemple, si une liste d’images comporte deux éléments, la suppression du premier élément entraîne l’élément restant maintenant se trouver dans la première position. *nImage*= 0 pour l’élément dans la première position.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>  CImageList::Replace

Appelez cette fonction pour remplacer une image dans une liste d’images avec une nouvelle image.

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
Pointeur vers la bitmap qui contient l’image.

*pbmMask*<br/>
Pointeur vers la bitmap contenant le masque. Si aucun masque n’est utilisé avec la liste d’images, ce paramètre est ignoré.

*hIcon*<br/>
Handle vers l’icône qui contient l’image bitmap et un masque pour la nouvelle image.

### <a name="return-value"></a>Valeur de retour

La version de retour de BOOL retourne différente de zéro en cas de réussite ; sinon 0.

La version retournant **int** retourne l’index de base zéro de l’image de cas de réussite ; sinon - 1.

### <a name="remarks"></a>Notes

Appelez cette fonction membre après avoir appelé [fonction SetImageCount](#setimagecount) pour affecter le nouveau, des images valides sur l’espace réservé d’image numéros d’index.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CImageList::SetImageCount](#setimagecount).

##  <a name="setbkcolor"></a>  CImageList::SetBkColor

Appelez cette fonction pour définir la couleur d’arrière-plan pour une liste d’images.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Paramètres

*cr*<br/>
Couleur d’arrière-plan à définir. Vous définissez CLR_NONE comme possible. Dans ce cas, les images sont dessinés en toute transparence à l’aide du masque.

### <a name="return-value"></a>Valeur de retour

La couleur d’arrière-plan précédente en cas de réussite ; vous sinon définissez CLR_NONE comme.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>  CImageList::SetDragCursorImage

Crée une nouvelle image glisser en combinant l’image donnée (généralement une image de curseur de souris) avec l’image glissée actuelle.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Paramètres

*nDrag*<br/>
Index de la nouvelle image doit être combinée avec l’image glissée.

*ptHotSpot*<br/>
Position de la zone réactive dans la nouvelle image.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Étant donné que les fonctions de glissement utilisent la nouvelle image pendant une opération glisser, vous devez utiliser le Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor) (fonction) pour masquer le curseur de souris réel après avoir appelé `CImageList::SetDragCursorImage`. Sinon, le système peut sembler être composé de deux curseurs de souris pour la durée de l'opération Glisser-déplacer.

##  <a name="setimagecount"></a>  CImageList::SetImageCount

Appelez cette fonction membre pour réinitialiser le nombre d’images dans un `CImageList` objet.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Paramètres

*uNewCount*<br/>
Valeur spécifiant le nouveau nombre total d’images dans la liste d’images.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Si vous appelez cette fonction membre pour augmenter le nombre d’images dans la liste d’images, puis appelez [remplacer](#replace) pour chaque image supplémentaire affecter les nouveaux index aux images valides. Si vous ne parvenez pas à attribuer les index à images valides, les opérations de dessin qui créent les nouvelles images seront imprévisibles.

Si vous diminuez la taille d’une liste d’images à l’aide de cette fonction, les images tronquées sont libérées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>  CImageList::SetOverlayImage

Appelez cette fonction pour ajouter des index de base zéro d’une image à la liste des images à utiliser comme masques de superposition.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Paramètres

*nImage*<br/>
Index de base zéro de l’image à utiliser comme un masque de superposition.

*nOverlay*<br/>
Index de base 1 du masque de superposition.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Jusqu'à quatre index peut être ajoutés à la liste.

Un masque de superposition est une image dessinée en toute transparence sur une autre image. Dessiner un masque de superposition sur une image à l’aide de la [CImageList::Draw](#draw) fonction membre avec l’index de base un du masque de superposition spécifié à l’aide de la macro INDEXTOOVERLAYMASK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>  CImageList::Write

Appelez cette fonction pour écrire un objet de liste d’images dans une archive.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Paramètres

*pArchive*<br/>
Un pointeur vers un `CArchive` objet dans lequel la liste d’images doit être stocké.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl, classe](../../mfc/reference/ctabctrl-class.md)
