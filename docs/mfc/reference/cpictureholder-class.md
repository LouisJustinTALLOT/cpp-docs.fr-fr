---
description: 'En savoir plus sur : classe CPictureHolder'
title: CPictureHolder, classe
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: 47eacb66191e21b300aaa0d06bc23155fabaf651
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301475"
---
# <a name="cpictureholder-class"></a>CPictureHolder, classe

Implémente une propriété Picture, qui permet à l’utilisateur d’afficher une image dans votre contrôle.

## <a name="syntax"></a>Syntaxe

```
class CPictureHolder
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPictureHolder :: CPictureHolder](#cpictureholder)|Construit un objet `CPictureHolder`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPictureHolder :: CreateEmpty](#createempty)|Crée un objet `CPictureHolder` vide.|
|[CPictureHolder :: CreateFromBitmap](#createfrombitmap)|Crée un `CPictureHolder` objet à partir d’une image bitmap.|
|[CPictureHolder :: CreateFromIcon](#createfromicon)|Crée un `CPictureHolder` objet à partir d’une icône.|
|[CPictureHolder :: CreateFromMetafile](#createfrommetafile)|Crée un `CPictureHolder` objet à partir d’un métafichier.|
|[CPictureHolder :: GetDisplayString](#getdisplaystring)|Récupère la chaîne affichée dans l’Explorateur de propriétés d’un conteneur de contrôles.|
|[CPictureHolder :: GetPictureDispatch](#getpicturedispatch)|Retourne l' `CPictureHolder` interface de l’objet `IDispatch` .|
|[CPictureHolder :: GetType](#gettype)|Indique si l' `CPictureHolder` objet est une bitmap, un métafichier ou une icône.|
|[CPictureHolder :: Render](#render)|Génère le rendu de l’image.|
|[CPictureHolder :: SetPictureDispatch](#setpicturedispatch)|Définit l' `CPictureHolder` interface de l’objet `IDispatch` .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPictureHolder :: m_pPict](#m_ppict)|Pointeur vers un objet image.|

## <a name="remarks"></a>Notes

`CPictureHolder` n’a pas de classe de base.

Avec la propriété d’image stock, le développeur peut spécifier une bitmap, une icône ou un métafichier à afficher.

Pour plus d’informations sur la création de propriétés d’image personnalisées, consultez l’article [contrôles ActiveX MFC : utilisation d’images dans un contrôle ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CPictureHolder`

## <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a> CPictureHolder :: CPictureHolder

Construit un objet `CPictureHolder`.

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a> CPictureHolder :: CreateEmpty

Crée un `CPictureHolder` objet vide et le connecte à une `IPicture` interface.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet est créé avec succès ; Sinon, 0.

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a> CPictureHolder :: CreateFromBitmap

Utilise une bitmap pour initialiser l’objet image dans un `CPictureHolder` .

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Paramètres

*idResource*<br/>
ID de ressource d’une ressource bitmap.

*pBitmap*<br/>
Pointeur vers un objet [CBitmap](../../mfc/reference/cbitmap-class.md) .

*pPal*<br/>
Pointeur vers un objet [cpalette](../../mfc/reference/cpalette-class.md) .

*bTransferOwnership*<br/>
Indique si l’objet Picture prend la propriété des objets bitmap et palette.

*hbm*<br/>
Handle de l’image bitmap à partir de laquelle l' `CPictureHolder` objet est créé.

*hpal*<br/>
Handle de la palette utilisée pour le rendu de l’image bitmap.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet est créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* a la valeur true, l’appelant ne doit pas utiliser l’objet bitmap ou palette de quelque manière que ce soit après le retour de cet appel. Si *bTransferOwnership* a la valeur false, l’appelant est chargé de s’assurer que les objets bitmap et palette restent valides pendant toute la durée de vie de l’objet image.

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a> CPictureHolder :: CreateFromIcon

Utilise une icône pour initialiser l’objet image dans un `CPictureHolder` .

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Paramètres

*idResource*<br/>
ID de ressource d’une ressource bitmap.

*hIcon*<br/>
Handle de l’icône à partir de laquelle l' `CPictureHolder` objet est créé.

*bTransferOwnership*<br/>
Indique si l’objet Picture prend la propriété de l’objet Icon.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet est créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* a la valeur true, l’appelant ne doit pas utiliser l’objet Icon de quelque façon que ce soit après le retour de cet appel. Si *bTransferOwnership* a la valeur false, l’appelant est chargé de s’assurer que l’objet Icon reste valide pendant toute la durée de vie de l’objet Picture.

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a> CPictureHolder :: CreateFromMetafile

Utilise un métafichier pour initialiser l’objet image dans un `CPictureHolder` .

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Paramètres

*hmf*<br/>
Handle vers le métafichier utilisé pour créer l' `CPictureHolder` objet.

*xExt*<br/>
X étendue de l’image.

*yExt*<br/>
Étendue Y de l’image.

*bTransferOwnership*<br/>
Indique si l’objet Picture prend la propriété de l’objet Metafile.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet est créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Si *bTransferOwnership* a la valeur true, l’appelant ne doit pas utiliser l’objet Metafile de quelque façon que ce soit après le retour de cet appel. Si *bTransferOwnership* a la valeur false, l’appelant est chargé de s’assurer que l’objet Metafile reste valide pendant toute la durée de vie de l’objet Picture.

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a> CPictureHolder :: GetDisplayString

Récupère la chaîne affichée dans l’Explorateur de propriétés d’un conteneur.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Paramètres

*strValue*<br/>
Référence à la [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui doit contenir la chaîne d’affichage.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la chaîne est récupérée avec succès ; Sinon, 0.

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a> CPictureHolder :: GetPictureDispatch

Cette fonction retourne un pointeur vers l' `CPictureHolder` interface de l’objet `IPictureDisp` .

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `CPictureHolder` interface de l’objet `IPictureDisp` .

### <a name="remarks"></a>Notes

Une fois terminé, l’appelant doit appeler `Release` sur ce pointeur.

## <a name="cpictureholdergettype"></a><a name="gettype"></a> CPictureHolder :: GetType

Indique si l’image est une bitmap, un métafichier ou une icône.

```
short GetType();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur indiquant le type de l’image. Les valeurs possibles et leurs significations sont les suivantes :

|Valeur|Signification|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder` l’objet est unititialized.|
|PICTYPE_NONE|`CPictureHolder` l’objet est vide.|
|PICTYPE_BITMAP|L’image est une image bitmap.|
|PICTYPE_METAFILE|Picture est un métafichier.|
|PICTYPE_ICON|L’image est une icône.|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a> CPictureHolder :: m_pPict

Pointeur vers l' `CPictureHolder` interface de l’objet `IPicture` .

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a> CPictureHolder :: Render

Génère le rendu de l’image dans le rectangle référencé par *rcRender*.

```cpp
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers le contexte d’affichage dans lequel l’image doit être rendue.

*rcRender*<br/>
Rectangle dans lequel l’image doit être rendue.

*rcWBounds*<br/>
Rectangle représentant le rectangle englobant de l’objet qui restitue l’image. Pour un contrôle, ce rectangle est le paramètre *rcBounds* passé à une substitution de [COleControl :: OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a> CPictureHolder :: SetPictureDispatch

Connecte l' `CPictureHolder` objet à une `IPictureDisp` interface.

```cpp
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
Pointeur vers la nouvelle `IPictureDisp` interface.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder, classe](../../mfc/reference/cfontholder-class.md)
